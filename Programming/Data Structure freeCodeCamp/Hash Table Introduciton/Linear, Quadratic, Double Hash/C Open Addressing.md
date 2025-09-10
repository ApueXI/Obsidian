---
Created: 2025-08-14T15:05
---
## ==Linear Probing==

```C#
using System;

public class HashTable<TKey, TValue> where TKey : IEquatable<TKey>
{
    private class Entry
    {
        public TKey Key { get; set; }
        public TValue Value { get; set; }
        public bool IsDeleted { get; set; }

        public Entry(TKey key, TValue value)
        {
            Key = key;
            Value = value;
            IsDeleted = false;
        }
    }

    private Entry[] table;
    private int capacity;
    private int size;

    public HashTable(int initialCapacity = 10)
    {
        capacity = initialCapacity;
        size = 0;
        table = new Entry[capacity];
    }

    private int Hash(TKey key)
    {
        return Math.Abs(key.GetHashCode()) % capacity;
    }

    private void Resize()
    {
        Entry[] oldTable = table;
        int oldCapacity = capacity;

        capacity *= 2;
        size = 0;
        table = new Entry[capacity];

        // Rehash all existing entries
        for (int i = 0; i < oldCapacity; i++)
        {
            if (oldTable[i] != null && !oldTable[i].IsDeleted)
            {
                Put(oldTable[i].Key, oldTable[i].Value);
            }
        }
    }

    public void Put(TKey key, TValue value)
    {
        if (key == null)
            throw new ArgumentNullException(nameof(key));

        if (size >= capacity * 0.7)
            Resize();

        int index = Hash(key);
        int originalIndex = index;

        while (true)
        {
            // Empty slot or deleted slot - insert here
            if (table[index] == null || table[index].IsDeleted)
            {
                if (table[index] == null)
                {
                    table[index] = new Entry(key, value);
                    size++;
                }
                else if (table[index].IsDeleted)
                {
                    table[index].Key = key;
                    table[index].Value = value;
                    table[index].IsDeleted = false;
                    size++;
                }
                return;
            }

            // Key already exists - update value
            if (table[index].Key.Equals(key) && !table[index].IsDeleted)
            {
                table[index].Value = value;
                return;
            }

            // Linear probing - move to next slot
            index = (index + 1) % capacity;

            // Table is full (shouldn't happen due to resize)
            if (index == originalIndex)
            {
                throw new InvalidOperationException("Hash table is full");
            }
        }
    }

    public TValue Get(TKey key)
    {
        if (key == null)
            throw new ArgumentNullException(nameof(key));

        int index = Hash(key);
        int originalIndex = index;

        while (table[index] != null)
        {
            if (table[index].Key.Equals(key) && !table[index].IsDeleted)
            {
                return table[index].Value;
            }

            index = (index + 1) % capacity;

            // Completed full circle
            if (index == originalIndex)
                break;
        }

        throw new KeyNotFoundException($"Key '{key}' not found");
    }

    public bool Delete(TKey key)
    {
        if (key == null)
            throw new ArgumentNullException(nameof(key));

        int index = Hash(key);
        int originalIndex = index;

        while (table[index] != null)
        {
            if (table[index].Key.Equals(key) && !table[index].IsDeleted)
            {
                table[index].IsDeleted = true;
                size--;
                return true;
            }

            index = (index + 1) % capacity;

            if (index == originalIndex)
                break;
        }

        return false;
    }

    public bool ContainsKey(TKey key)
    {
        try
        {
            Get(key);
            return true;
        }
        catch (KeyNotFoundException)
        {
            return false;
        }
    }

    public void Display()
    {
        Console.WriteLine("Hash Table Contents:");
        for (int i = 0; i < capacity; i++)
        {
            if (table[i] != null && !table[i].IsDeleted)
            {
                Console.WriteLine($"[{i}]: {table[i].Key} -> {table[i].Value} (ACTIVE)");
            }
            else if (table[i] != null && table[i].IsDeleted)
            {
                Console.WriteLine($"[{i}]: DELETED");
            }
            else
            {
                Console.WriteLine($"[{i}]: EMPTY");
            }
        }
        Console.WriteLine($"Size: {size}, Capacity: {capacity}");
    }

    public int Size => size;
    public int Capacity => capacity;
}

// Example usage
class Program
{
    static void Main(string[] args)
    {
        HashTable<string, int> ht = new HashTable<string, int>(7);

        // Insert some key-value pairs
        ht.Put("apple", 10);
        ht.Put("banana", 20);
        ht.Put("orange", 30);
        ht.Put("grape", 40);

        Console.WriteLine("After insertions:");
        ht.Display();
        Console.WriteLine();

        // Test retrieval
        try
        {
            Console.WriteLine($"apple: {ht.Get("apple")}");
            Console.WriteLine($"banana: {ht.Get("banana")}");
            Console.WriteLine();
        }
        catch (KeyNotFoundException ex)
        {
            Console.WriteLine(ex.Message);
        }

        // Test deletion
        ht.Delete("banana");
        Console.WriteLine("After deleting 'banana':");
        ht.Display();
        Console.WriteLine();

        // Test collision handling
        ht.Put("pear", 50);
        Console.WriteLine("After adding 'pear':");
        ht.Display();
    }
}
```

## ==Quadratic Probing==

```C#
using System;
using System.Collections.Generic;

public class HashTableQuadratic<TKey, TValue> where TKey : IEquatable<TKey>
{
    private class Entry
    {
        public TKey Key { get; set; }
        public TValue Value { get; set; }
        public bool IsDeleted { get; set; }

        public Entry(TKey key, TValue value)
        {
            Key = key;
            Value = value;
            IsDeleted = false;
        }
    }

    private Entry[] table;
    private int capacity;
    private int size;
    private const int C1 = 1;
    private const int C2 = 1;

    public HashTableQuadratic(int initialCapacity = 11)
    {
        capacity = NextPrime(initialCapacity);
        size = 0;
        table = new Entry[capacity];
    }

    private int Hash(TKey key)
    {
        return Math.Abs(key.GetHashCode()) % capacity;
    }

    private static bool IsPrime(int n)
    {
        if (n < 2) return false;
        for (int i = 2; i <= Math.Sqrt(n); i++)
        {
            if (n % i == 0) return false;
        }
        return true;
    }

    private static int NextPrime(int n)
    {
        n++;
        while (!IsPrime(n))
            n++;
        return n;
    }

    private int QuadraticProbe(TKey key, ProbeOperation operation)
    {
        int originalIndex = Hash(key);
        
        for (int i = 0; i < capacity; i++)
        {
            int currentIndex = (originalIndex + C1 * i + C2 * i * i) % capacity;
            
            switch (operation)
            {
                case ProbeOperation.Insert:
                    // For insertion: empty slot or deleted slot
                    if (table[currentIndex] == null || table[currentIndex].IsDeleted)
                        return currentIndex;
                    // Key already exists
                    if (table[currentIndex].Key.Equals(key) && !table[currentIndex].IsDeleted)
                        return currentIndex;
                    break;
                    
                case ProbeOperation.Find:
                    // For finding: exact match
                    if (table[currentIndex] != null && table[currentIndex].Key.Equals(key) && !table[currentIndex].IsDeleted)
                        return currentIndex;
                    // Empty slot means key doesn't exist
                    if (table[currentIndex] == null)
                        return -1;
                    break;
                    
                case ProbeOperation.Delete:
                    // For deletion: exact match
                    if (table[currentIndex] != null && table[currentIndex].Key.Equals(key) && !table[currentIndex].IsDeleted)
                        return currentIndex;
                    // Empty slot means key doesn't exist
                    if (table[currentIndex] == null)
                        return -1;
                    break;
            }
        }
        
        return -1; // Not found or table full
    }

    private void Resize()
    {
        Entry[] oldTable = table;
        int oldCapacity = capacity;

        capacity = NextPrime(capacity * 2);
        size = 0;
        table = new Entry[capacity];

        // Rehash all existing entries
        for (int i = 0; i < oldCapacity; i++)
        {
            if (oldTable[i] != null && !oldTable[i].IsDeleted)
            {
                Put(oldTable[i].Key, oldTable[i].Value);
            }
        }
    }

    public void Put(TKey key, TValue value)
    {
        if (key == null)
            throw new ArgumentNullException(nameof(key));

        if (size >= capacity * 0.5) // Lower load factor for quadratic probing
            Resize();

        int index = QuadraticProbe(key, ProbeOperation.Insert);

        if (index == -1)
            throw new InvalidOperationException("Hash table is full");

        // New key insertion
        if (table[index] == null || table[index].IsDeleted)
        {
            table[index] = new Entry(key, value);
            size++;
        }
        else
        {
            // Update existing key
            table[index].Value = value;
        }
    }

    public TValue Get(TKey key)
    {
        if (key == null)
            throw new ArgumentNullException(nameof(key));

        int index = QuadraticProbe(key, ProbeOperation.Find);

        if (index == -1)
            throw new KeyNotFoundException($"Key '{key}' not found");

        return table[index].Value;
    }

    public bool Delete(TKey key)
    {
        if (key == null)
            throw new ArgumentNullException(nameof(key));

        int index = QuadraticProbe(key, ProbeOperation.Delete);

        if (index == -1)
            return false;

        table[index].IsDeleted = true;
        size--;
        return true;
    }

    public bool ContainsKey(TKey key)
    {
        try
        {
            Get(key);
            return true;
        }
        catch (KeyNotFoundException)
        {
            return false;
        }
    }

    public void Display()
    {
        Console.WriteLine("Hash Table Contents (Quadratic Probing):");
        for (int i = 0; i < capacity; i++)
        {
            if (table[i] != null && !table[i].IsDeleted)
            {
                // Calculate probe sequence for this key
                var probeSequence = new List<int>();
                int originalIndex = Hash(table[i].Key);
                
                for (int j = 0; j < capacity; j++)
                {
                    int probeIndex = (originalIndex + C1 * j + C2 * j * j) % capacity;
                    probeSequence.Add(probeIndex);
                    if (probeIndex == i)
                        break;
                }
                
                Console.WriteLine($"[{i}]: {table[i].Key} -> {table[i].Value} (probes: [{string.Join(", ", probeSequence)}])");
            }
            else if (table[i] != null && table[i].IsDeleted)
            {
                Console.WriteLine($"[{i}]: DELETED");
            }
            else
            {
                Console.WriteLine($"[{i}]: EMPTY");
            }
        }
        
        Console.WriteLine($"Size: {size}, Capacity: {capacity}");
        Console.WriteLine($"Load Factor: {(double)size / capacity:F2}");
    }

    public void ProbeStatistics()
    {
        int totalProbes = 0;
        int activeKeys = 0;

        for (int i = 0; i < capacity; i++)
        {
            if (table[i] != null && !table[i].IsDeleted)
            {
                activeKeys++;
                int originalIndex = Hash(table[i].Key);
                int probes = 1;

                for (int j = 1; j < capacity; j++)
                {
                    int probeIndex = (originalIndex + C1 * j + C2 * j * j) % capacity;
                    if (probeIndex == i)
                    {
                        probes = j + 1;
                        break;
                    }
                }

                totalProbes += probes;
            }
        }

        if (activeKeys > 0)
        {
            double avgProbes = (double)totalProbes / activeKeys;
            Console.WriteLine($"Average probes per key: {avgProbes:F2}");
        }
        else
        {
            Console.WriteLine("No active keys in table");
        }
    }

    public int Size => size;
    public int Capacity => capacity;
    
    private enum ProbeOperation
    {
        Insert,
        Find,
        Delete
    }
}

// Example usage
class Program
{
    static void Main(string[] args)
    {
        var ht = new HashTableQuadratic<string, int>(11);

        // Insert some key-value pairs that will cause collisions
        string[] keys = { "apple", "banana", "orange", "grape", "kiwi", "mango", "pear" };
        int[] values = { 10, 20, 30, 40, 50, 60, 70 };

        Console.WriteLine("Inserting keys with quadratic probing:");
        for (int i = 0; i < keys.Length; i++)
        {
            ht.Put(keys[i], values[i]);
            Console.WriteLine($"Inserted {keys[i]}: {values[i]}");
        }

        Console.WriteLine("\nFinal hash table:");
        ht.Display();
        Console.WriteLine();

        // Show probing statistics
        ht.ProbeStatistics();
        Console.WriteLine();

        // Test retrieval
        try
        {
            Console.WriteLine($"apple: {ht.Get("apple")}");
            Console.WriteLine($"mango: {ht.Get("mango")}");
        }
        catch (KeyNotFoundException ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }

        // Test deletion
        Console.WriteLine($"\nDeleting 'banana': {ht.Delete("banana")}");
        Console.WriteLine("After deletion:");
        ht.Display();

        // Add more elements to test resizing
        Console.WriteLine("\nAdding more elements to trigger resize:");
        ht.Put("watermelon", 80);
        ht.Put("strawberry", 90);
        ht.Display();
    }
}
```

## ==Double Hashing==

```C#
using System;
using System.Collections.Generic;
using System.Linq;

public class HashTableDouble<TKey, TValue> where TKey : IEquatable<TKey>
{
    private class Entry
    {
        public TKey Key { get; set; }
        public TValue Value { get; set; }
        public bool IsDeleted { get; set; }

        public Entry(TKey key, TValue value)
        {
            Key = key;
            Value = value;
            IsDeleted = false;
        }
    }

    private Entry[] table;
    private int capacity;
    private int size;

    public HashTableDouble(int initialCapacity = 11)
    {
        capacity = NextPrime(initialCapacity);
        size = 0;
        table = new Entry[capacity];
    }

    private int Hash1(TKey key)
    {
        return Math.Abs(key.GetHashCode()) % capacity;
    }

    private int Hash2(TKey key)
    {
        // Secondary hash function - must never return 0
        int hashCode = Math.Abs(key.GetHashCode());
        int secondPrime = PrevPrime(capacity);
        int result = hashCode % secondPrime;
        return result == 0 ? 1 : result;
    }

    private static bool IsPrime(int n)
    {
        if (n < 2) return false;
        for (int i = 2; i <= Math.Sqrt(n); i++)
        {
            if (n % i == 0) return false;
        }
        return true;
    }

    private static int NextPrime(int n)
    {
        n++;
        while (!IsPrime(n))
            n++;
        return n;
    }

    private static int PrevPrime(int n)
    {
        n--;
        while (n > 1 && !IsPrime(n))
            n--;
        return n > 1 ? n : 2;
    }

    private int DoubleHashProbe(TKey key, ProbeOperation operation)
    {
        int h1 = Hash1(key);
        int h2 = Hash2(key);
        
        for (int i = 0; i < capacity; i++)
        {
            int index = (h1 + i * h2) % capacity;
            
            switch (operation)
            {
                case ProbeOperation.Insert:
                    // For insertion: empty slot or deleted slot
                    if (table[index] == null || table[index].IsDeleted)
                        return index;
                    // Key already exists
                    if (table[index].Key.Equals(key) && !table[index].IsDeleted)
                        return index;
                    break;
                    
                case ProbeOperation.Find:
                    // For finding: exact match
                    if (table[index] != null && table[index].Key.Equals(key) && !table[index].IsDeleted)
                        return index;
                    // Empty slot means key doesn't exist
                    if (table[index] == null)
                        return -1;
                    break;
                    
                case ProbeOperation.Delete:
                    // For deletion: exact match
                    if (table[index] != null && table[index].Key.Equals(key) && !table[index].IsDeleted)
                        return index;
                    // Empty slot means key doesn't exist
                    if (table[index] == null)
                        return -1;
                    break;
            }
        }
        
        return -1; // Not found or table full
    }

    private void Resize()
    {
        Entry[] oldTable = table;
        int oldCapacity = capacity;

        capacity = NextPrime(capacity * 2);
        size = 0;
        table = new Entry[capacity];

        // Rehash all existing entries
        for (int i = 0; i < oldCapacity; i++)
        {
            if (oldTable[i] != null && !oldTable[i].IsDeleted)
            {
                Put(oldTable[i].Key, oldTable[i].Value);
            }
        }
    }

    public void Put(TKey key, TValue value)
    {
        if (key == null)
            throw new ArgumentNullException(nameof(key));

        if (size >= capacity * 0.7)
            Resize();

        int index = DoubleHashProbe(key, ProbeOperation.Insert);

        if (index == -1)
            throw new InvalidOperationException("Hash table is full");

        // New key insertion
        if (table[index] == null || table[index].IsDeleted)
        {
            table[index] = new Entry(key, value);
            size++;
        }
        else
        {
            // Update existing key
            table[index].Value = value;
        }
    }

    public TValue Get(TKey key)
    {
        if (key == null)
            throw new ArgumentNullException(nameof(key));

        int index = DoubleHashProbe(key, ProbeOperation.Find);

        if (index == -1)
            throw new KeyNotFoundException($"Key '{key}' not found");

        return table[index].Value;
    }

    public bool Delete(TKey key)
    {
        if (key == null)
            throw new ArgumentNullException(nameof(key));

        int index = DoubleHashProbe(key, ProbeOperation.Delete);

        if (index == -1)
            return false;

        table[index].IsDeleted = true;
        size--;
        return true;
    }

    public bool ContainsKey(TKey key)
    {
        try
        {
            Get(key);
            return true;
        }
        catch (KeyNotFoundException)
        {
            return false;
        }
    }

    public void Display()
    {
        Console.WriteLine("Hash Table Contents (Double Hashing):");
        for (int i = 0; i < capacity; i++)
        {
            if (table[i] != null && !table[i].IsDeleted)
            {
                // Calculate probe sequence for this key
                int h1 = Hash1(table[i].Key);
                int h2 = Hash2(table[i].Key);
                var probeSequence = new List<int>();
                
                for (int j = 0; j < capacity; j++)
                {
                    int probeIndex = (h1 + j * h2) % capacity;
                    probeSequence.Add(probeIndex);
                    if (probeIndex == i)
                        break;
                }
                
                Console.WriteLine($"[{i}]: {table[i].Key} -> {table[i].Value}");
                Console.WriteLine($"      h1({table[i].Key}) = {h1}, h2({table[i].Key}) = {h2}");
                Console.WriteLine($"      probe sequence: [{string.Join(", ", probeSequence)}]");
            }
            else if (table[i] != null && table[i].IsDeleted)
            {
                Console.WriteLine($"[{i}]: DELETED");
            }
            else
            {
                Console.WriteLine($"[{i}]: EMPTY");
            }
        }
        
        Console.WriteLine($"Size: {size}, Capacity: {capacity}");
        Console.WriteLine($"Load Factor: {(double)size / capacity:F2}");
    }

    public void HashAnalysis(TKey key)
    {
        int h1 = Hash1(key);
        int h2 = Hash2(key);
        Console.WriteLine($"Hash analysis for key '{key}':");
        Console.WriteLine($"  h1({key}) = {h1}");
        Console.WriteLine($"  h2({key}) = {h2}");
        Console.WriteLine($"  Step size: {h2}");
        
        // Show first few probe positions
        Console.Write("  First 5 probe positions: ");
        for (int i = 0; i < 5; i++)
        {
            int pos = (h1 + i * h2) % capacity;
            Console.Write(pos);
            if (i < 4) Console.Write(", ");
        }
        Console.WriteLine();
    }

    public void ProbeStatistics()
    {
        int totalProbes = 0;
        int activeKeys = 0;
        int maxProbes = 0;

        for (int i = 0; i < capacity; i++)
        {
            if (table[i] != null && !table[i].IsDeleted)
            {
                activeKeys++;
                int h1 = Hash1(table[i].Key);
                int h2 = Hash2(table[i].Key);
                int probes = 1;

                for (int j = 1; j < capacity; j++)
                {
                    int probeIndex = (h1 + j * h2) % capacity;
                    if (probeIndex == i)
                    {
                        probes = j + 1;
                        break;
                    }
                }

                totalProbes += probes;
                maxProbes = Math.Max(maxProbes, probes);
            }
        }

        if (activeKeys > 0)
        {
            double avgProbes = (double)totalProbes / activeKeys;
            Console.WriteLine("Probing Statistics:");
            Console.WriteLine($"  Average probes per key: {avgProbes:F2}");
            Console.WriteLine($"  Maximum probes for any key: {maxProbes}");
            Console.WriteLine($"  Total probes: {totalProbes}");
        }
        else
        {
            Console.WriteLine("No active keys in table");
        }
    }

    public void CollisionAnalysis()
    {
        var h1Collisions = new Dictionary<int, List<TKey>>();
        var h2Values = new Dictionary<int, List<TKey>>();

        for (int i = 0; i < capacity; i++)
        {
            if (table[i] != null && !table[i].IsDeleted)
            {
                int h1 = Hash1(table[i].Key);
                int h2 = Hash2(table[i].Key);

                if (!h1Collisions.ContainsKey(h1))
                    h1Collisions[h1] = new List<TKey>();
                h1Collisions[h1].Add(table[i].Key);

                if (!h2Values.ContainsKey(h2))
                    h2Values[h2] = new List<TKey>();
                h2Values[h2].Add(table[i].Key);
            }
        }

        Console.WriteLine("Collision Analysis:");
        Console.WriteLine("h1 collisions (keys with same primary hash):");
        foreach (var kvp in h1Collisions.Where(x => x.Value.Count > 1))
        {
            Console.WriteLine($"  h1={kvp.Key}: [{string.Join(", ", kvp.Value)}]");
        }

        Console.WriteLine("h2 distribution (step sizes):");
        foreach (var kvp in h2Values.OrderBy(x => x.Key))
        {
            Console.WriteLine($"  h2={kvp.Key}: [{string.Join(", ", kvp.Value)}]");
        }
    }

    public int Size => size;
    public int Capacity => capacity;

    private enum ProbeOperation
    {
        Insert,
        Find,
        Delete
    }
}
```

```C#

// Example usage
class Program
{
    static void Main(string[] args)
    {
        var ht = new HashTableDouble<string, int>(11);

        // Insert some key-value pairs that will cause collisions
        var testData = new (string, int)[]
        {
            ("apple", 10), ("banana", 20), ("orange", 30), ("grape", 40),
            ("kiwi", 50), ("mango", 60), ("pear", 70), ("peach", 80)
        };

        Console.WriteLine("Inserting keys with double hashing:");
        foreach (var (key, value) in testData)
        {
            ht.Put(key, value);
            Console.WriteLine($"Inserted {key}: {value}");
            ht.HashAnalysis(key);
            Console.WriteLine();
        }

        Console.WriteLine("Final hash table:");
        ht.Display();
        Console.WriteLine();

        // Show collision analysis
        ht.CollisionAnalysis();
        Console.WriteLine();

        // Show probing statistics
        ht.ProbeStatistics();
        Console.WriteLine();

        // Test retrieval
        try
        {
            Console.WriteLine($"apple: {ht.Get("apple")}");
            Console.WriteLine($"mango: {ht.Get("mango")}");
        }
        catch (KeyNotFoundException ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }

        // Test deletion
        Console.WriteLine($"\nDeleting 'banana': {ht.Delete("banana")}");
        Console.WriteLine("After deletion:");
        ht.Display();

        // Demonstrate hash function properties
        Console.WriteLine("\nHash function demonstration:");
        string[] testKeys = { "test1", "test2", "collision", "example" };
        foreach (string key in testKeys)
        {
            ht.HashAnalysis(key);
        }
    }
}
```