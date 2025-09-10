---
Created: 2025-08-12T08:45
---
## ==Separate Chaining Code Implementation==

```C#
using System;
using System.Collections.Generic;

public class HashNode<TKey, TValue>
{
    public TKey Key { get; set; }
    public TValue Value { get; set; }
    public HashNode<TKey, TValue> Next { get; set; }

    public HashNode(TKey key, TValue value)
    {
        Key = key;
        Value = value;
        Next = null;
    }
}

public class HashTable<TKey, TValue>
{
    private HashNode<TKey, TValue>[] table;
    private int capacity;
    private int size;

    public HashTable(int capacity = 10)
    {
        this.capacity = capacity;
        this.size = 0;
        this.table = new HashNode<TKey, TValue>[capacity];
    }

    private int Hash(TKey key)
    {
        return Math.Abs(key.GetHashCode()) % capacity;
    }

    public void Insert(TKey key, TValue value)
    {
        int index = Hash(key);

        if (table[index] == null)
        {
            // No collision
            table[index] = new HashNode<TKey, TValue>(key, value);
            size++;
        }
        else
        {
            // Handle collision with chaining
            HashNode<TKey, TValue> current = table[index];

            while (current != null)
            {
                if (current.Key.Equals(key))
                {
                    // Key already exists, update value
                    current.Value = value;
                    return;
                }
                if (current.Next == null)
                    break;
                current = current.Next;
            }

            // Add new node at the end of the chain
            current.Next = new HashNode<TKey, TValue>(key, value);
            size++;
        }
    }

    public TValue Get(TKey key)
    {
        int index = Hash(key);
        HashNode<TKey, TValue> current = table[index];

        while (current != null)
        {
            if (current.Key.Equals(key))
            {
                return current.Value;
            }
            current = current.Next;
        }

        throw new KeyNotFoundException($"Key '{key}' not found");
    }

    public bool Delete(TKey key)
    {
        int index = Hash(key);
        HashNode<TKey, TValue> current = table[index];

        if (current == null)
            return false;

        // If first node contains the key
        if (current.Key.Equals(key))
        {
            table[index] = current.Next;
            size--;
            return true;
        }

        // Search in the chain
        while (current.Next != null)
        {
            if (current.Next.Key.Equals(key))
            {
                current.Next = current.Next.Next;
                size--;
                return true;
            }
            current = current.Next;
        }

        return false;
    }

    public void Resize()
    {
        int oldCapacity = capacity;
        capacity *= 2;

        HashNode<TKey, TValue>[] oldTable = table;
        table = new HashNode<TKey, TValue>[capacity];

        // Go through each bucket in the old table
        for (int i = 0; i < oldCapacity; i++)
        {
            HashNode<TKey, TValue> current = oldTable[i];

            while (current != null)
            {
                // Store the next node before we mess with pointers
                HashNode<TKey, TValue> nextNode = current.Next;

                // Recalculate the new index for this key
                int index = Hash(current.Key);

                // Insert at head of new list
                current.Next = table[index];
                table[index] = current;

                // Move to the next node in old list
                current = nextNode;
            }
        }

    }

    public void Display()
    {
        for (int i = 0; i < capacity; i++)
        {
            Console.Write($"Bucket {i}: ");
            HashNode<TKey, TValue> current = table[i];

            if (current == null)
            {
                Console.WriteLine("Empty");
            }
            else
            {
                List<string> chain = new List<string>();
                while (current != null)
                {
                    chain.Add($"({current.Key}: {current.Value})");
                    current = current.Next;
                }
                Console.WriteLine(string.Join(" -> ", chain));
            }
        }
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
        ht.Insert("apple", 5);
        ht.Insert("banana", 3);
        ht.Insert("orange", 8);
        ht.Insert("grape", 2);
        ht.Insert("kiwi", 4);
        ht.Insert("mango", 6);

        Console.WriteLine("Hash Table Contents:");
        ht.Display();

        Console.WriteLine($"\nSize: {ht.Size}");

        // Test retrieval
        try
        {
            Console.WriteLine($"apple: {ht.Get("apple")}");
            Console.WriteLine($"grape: {ht.Get("grape")}");
        }
        catch (KeyNotFoundException ex)
        {
            Console.WriteLine(ex.Message);
        }

        // Test deletion
        if (ht.Delete("banana"))
        {
            Console.WriteLine("\nAfter deleting 'banana':");
            ht.Display();
        }
        Console.WriteLine($"------------------");
        ht.Resize();

    }
}
```

## Separating Chaining HT Code Implementation

```C#
public class Node
{
    public string Key;
    public int Value;
    public Node Next;

    public Node(string key, int value)
    {
        Key = key;
        Value = value;
        Next = null;
    }
}

public class HashTable
{
    private Node[] buckets;
    private int size;

    public HashTable(int size = 10)
    {
        this.size = size;
        buckets = new Node[size];
    }

    private int Hash(string key)
    {
        return Math.Abs(key.GetHashCode()) % size;
    }

    public void Insert(string key, int value)
    {
        int index = Hash(key);
        Node head = buckets[index];

        Node current = head;
        while (current != null)
        {
            if (current.Key == key)
            {
                current.Value = value;
                return;
            }
            current = current.Next;
        }

        Node newNode = new Node(key, value)
        {
            Next = head
        };
        buckets[index] = newNode;
    }

    public int? Search(string key)
    {
        int index = Hash(key);
        Node current = buckets[index];

        while (current != null)
        {
            if (current.Key == key)
                return current.Value;
            current = current.Next;
        }
        return null;
    }

    public bool Delete(string key)
    {
        int index = Hash(key);
        Node current = buckets[index];
        Node prev = null;

        while (current != null)
        {
            if (current.Key == key)
            {
                if (prev != null)
                    prev.Next = current.Next;
                else
                    buckets[index] = current.Next;
                return true;
            }
            prev = current;
            current = current.Next;
        }
        return false;
    }
}
```