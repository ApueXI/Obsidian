---
Created: 2025-08-14T15:05
---
## ==Linear Probing==

```C++
class HashTable:
    def __init__(self, capacity=10):
        self.capacity = capacity
        self.size = 0
        self.keys = [None] * self.capacity
        self.values = [None] * self.capacity
        self.deleted = [False] * self.capacity  # Track deleted slots
    
    def _hash(self, key):
        """Simple hash function"""
        if isinstance(key, str):
            return sum(ord(c) for c in key) % self.capacity
        return hash(key) % self.capacity
    
    def _resize(self):
        """Resize the hash table when load factor exceeds 0.7"""
        old_keys = self.keys
        old_values = self.values
        old_capacity = self.capacity
        
        self.capacity *= 2
        self.size = 0
        self.keys = [None] * self.capacity
        self.values = [None] * self.capacity
        self.deleted = [False] * self.capacity
        
        # Rehash all existing key-value pairs
        for i in range(old_capacity):
            if old_keys[i] is not None:
                self.put(old_keys[i], old_values[i])
    
    def put(self, key, value):
        """Insert or update a key-value pair"""
        if self.size >= self.capacity * 0.7:
            self._resize()
        
        index = self._hash(key)
        original_index = index
        
        while True:
            # Empty slot or deleted slot - insert here
            if self.keys[index] is None or self.deleted[index]:
                if self.keys[index] is None or self.deleted[index]:
                    self.size += 1
                self.keys[index] = key
                self.values[index] = value
                self.deleted[index] = False
                return
            
            # Key already exists - update value
            if self.keys[index] == key and not self.deleted[index]:
                self.values[index] = value
                return
            
            # Linear probing - move to next slot
            index = (index + 1) % self.capacity
            
            # Table is full (shouldn't happen due to resize)
            if index == original_index:
                raise Exception("Hash table is full")
    
    def get(self, key):
        """Retrieve value by key"""
        index = self._hash(key)
        original_index = index
        
        while self.keys[index] is not None:
            if self.keys[index] == key and not self.deleted[index]:
                return self.values[index]
            
            index = (index + 1) % self.capacity
            
            # Completed full circle
            if index == original_index:
                break
        
        raise KeyError(f"Key '{key}' not found")
    
    def delete(self, key):
        """Delete a key-value pair"""
        index = self._hash(key)
        original_index = index
        
        while self.keys[index] is not None:
            if self.keys[index] == key and not self.deleted[index]:
                self.deleted[index] = True
                self.size -= 1
                return True
            
            index = (index + 1) % self.capacity
            
            if index == original_index:
                break
        
        return False
    
    def contains(self, key):
        """Check if key exists in hash table"""
        try:
            self.get(key)
            return True
        except KeyError:
            return False
    
    def display(self):
        """Display the hash table contents"""
        print("Hash Table Contents:")
        for i in range(self.capacity):
            status = "DELETED" if self.deleted[i] else "ACTIVE"
            if self.keys[i] is not None and not self.deleted[i]:
                print(f"[{i}]: {self.keys[i]} -> {self.values[i]} ({status})")
            elif self.keys[i] is not None and self.deleted[i]:
                print(f"[{i}]: DELETED")
            else:
                print(f"[{i}]: EMPTY")
        print(f"Size: {self.size}, Capacity: {self.capacity}")


# Example usage
if __name__ == "__main__":
    ht = HashTable(7)
    
    # Insert some key-value pairs
    ht.put("apple", 10)
    ht.put("banana", 20)
    ht.put("orange", 30)
    ht.put("grape", 40)
    
    print("After insertions:")
    ht.display()
    print()
    
    # Test retrieval
    print(f"apple: {ht.get('apple')}")
    print(f"banana: {ht.get('banana')}")
    print()
    
    # Test deletion
    ht.delete("banana")
    print("After deleting 'banana':")
    ht.display()
    print()
    
    # Test collision handling
    ht.put("pear", 50)  # This might cause collision
    print("After adding 'pear':")
    ht.display()
```

## ==Quadratic Probing==

```Python
class HashTableQuadratic:
    def __init__(self, capacity=11):  # Prime number for better distribution
        self.capacity = capacity
        self.size = 0
        self.keys = [None] * self.capacity
        self.values = [None] * self.capacity
        self.deleted = [False] * self.capacity
    
    def _hash(self, key):
        """Simple hash function"""
        if isinstance(key, str):
            return sum(ord(c) for c in key) % self.capacity
        return hash(key) % self.capacity
    
    def _next_prime(self, n):
        """Find next prime number greater than n"""
        def is_prime(num):
            if num < 2:
                return False
            for i in range(2, int(num ** 0.5) + 1):
                if num % i == 0:
                    return False
            return True
        
        n += 1
        while not is_prime(n):
            n += 1
        return n
    
    def _resize(self):
        """Resize the hash table when load factor exceeds 0.5"""
        old_keys = self.keys
        old_values = self.values
        old_capacity = self.capacity
        
        self.capacity = self._next_prime(self.capacity * 2)
        self.size = 0
        self.keys = [None] * self.capacity
        self.values = [None] * self.capacity
        self.deleted = [False] * self.capacity
        
        # Rehash all existing key-value pairs
        for i in range(old_capacity):
            if old_keys[i] is not None:
                self.put(old_keys[i], old_values[i])
    
    def _quadratic_probe(self, key, operation='find'):
        """Quadratic probing: h(k) + c1*i + c2*i^2"""
        c1, c2 = 1, 1  # Quadratic constants
        index = self._hash(key)
        original_index = index
        i = 0
        
        while i < self.capacity:
            current_index = (original_index + c1 * i + c2 * i * i) % self.capacity
            
            if operation == 'insert':
                # For insertion: empty slot or deleted slot
                if self.keys[current_index] is None or self.deleted[current_index]:
                    return current_index
                # Key already exists
                if self.keys[current_index] == key and not self.deleted[current_index]:
                    return current_index
            
            elif operation == 'find':
                # For finding: exact match
                if self.keys[current_index] == key and not self.deleted[current_index]:
                    return current_index
                # Empty slot means key doesn't exist
                if self.keys[current_index] is None:
                    return -1
            
            elif operation == 'delete':
                # For deletion: exact match
                if self.keys[current_index] == key and not self.deleted[current_index]:
                    return current_index
                # Empty slot means key doesn't exist
                if self.keys[current_index] is None:
                    return -1
            
            i += 1
        
        return -1  # Not found or table full
    
    def put(self, key, value):
        """Insert or update a key-value pair"""
        if self.size >= self.capacity * 0.5:  # Lower load factor for quadratic probing
            self._resize()
        
        index = self._quadratic_probe(key, 'insert')
        
        if index == -1:
            raise Exception("Hash table is full")
        
        # New key insertion
        if self.keys[index] is None or self.deleted[index]:
            self.size += 1
        
        self.keys[index] = key
        self.values[index] = value
        self.deleted[index] = False
    
    def get(self, key):
        """Retrieve value by key"""
        index = self._quadratic_probe(key, 'find')
        
        if index == -1:
            raise KeyError(f"Key '{key}' not found")
        
        return self.values[index]
    
    def delete(self, key):
        """Delete a key-value pair"""
        index = self._quadratic_probe(key, 'delete')
        
        if index == -1:
            return False
        
        self.deleted[index] = True
        self.size -= 1
        return True
    
    def contains(self, key):
        """Check if key exists in hash table"""
        try:
            self.get(key)
            return True
        except KeyError:
            return False
    
    def display(self):
        """Display the hash table contents"""
        print("Hash Table Contents (Quadratic Probing):")
        for i in range(self.capacity):
            if self.keys[i] is not None and not self.deleted[i]:
                # Calculate probe sequence for this key
                probe_sequence = []
                c1, c2 = 1, 1
                original_index = self._hash(self.keys[i])
                for j in range(self.capacity):
                    probe_index = (original_index + c1 * j + c2 * j * j) % self.capacity
                    probe_sequence.append(probe_index)
                    if probe_index == i:
                        break
                
                print(f"[{i}]: {self.keys[i]} -> {self.values[i]} (probes: {probe_sequence})")
            elif self.keys[i] is not None and self.deleted[i]:
                print(f"[{i}]: DELETED")
            else:
                print(f"[{i}]: EMPTY")
        
        print(f"Size: {self.size}, Capacity: {self.capacity}")
        print(f"Load Factor: {self.size / self.capacity:.2f}")
    
    def probe_statistics(self):
        """Show probing statistics"""
        total_probes = 0
        active_keys = 0
        
        for i in range(self.capacity):
            if self.keys[i] is not None and not self.deleted[i]:
                active_keys += 1
                # Count probes needed for this key
                c1, c2 = 1, 1
                original_index = self._hash(self.keys[i])
                probes = 1
                
                for j in range(1, self.capacity):
                    probe_index = (original_index + c1 * j + c2 * j * j) % self.capacity
                    if probe_index == i:
                        probes = j + 1
                        break
                
                total_probes += probes
        
        if active_keys > 0:
            avg_probes = total_probes / active_keys
            print(f"Average probes per key: {avg_probes:.2f}")
        else:
            print("No active keys in table")


# Example usage
if __name__ == "__main__":
    ht = HashTableQuadratic(11)  # Prime capacity
    
    # Insert some key-value pairs that will cause collisions
    keys = ["apple", "banana", "orange", "grape", "kiwi", "mango", "pear"]
    values = [10, 20, 30, 40, 50, 60, 70]
    
    print("Inserting keys with quadratic probing:")
    for key, value in zip(keys, values):
        ht.put(key, value)
        print(f"Inserted {key}: {value}")
    
    print("\nFinal hash table:")
    ht.display()
    print()
    
    # Show probing statistics
    ht.probe_statistics()
    print()
    
    # Test retrieval
    try:
        print(f"apple: {ht.get('apple')}")
        print(f"mango: {ht.get('mango')}")
    except KeyError as e:
        print(f"Error: {e}")
    
    # Test deletion
    print(f"\nDeleting 'banana': {ht.delete('banana')}")
    print("After deletion:")
    ht.display()
    
    # Add more elements to test resizing
    print("\nAdding more elements to trigger resize:")
    ht.put("watermelon", 80)
    ht.put("strawberry", 90)
    ht.display()
```

  

## ==Double Hashing==

```Python
class HashTableDouble:
    def __init__(self, capacity=11):  # Prime number for better distribution
        self.capacity = capacity
        self.size = 0
        self.keys = [None] * self.capacity
        self.values = [None] * self.capacity
        self.deleted = [False] * self.capacity
    
    def _hash1(self, key):
        """Primary hash function"""
        if isinstance(key, str):
            return sum(ord(c) for c in key) % self.capacity
        return hash(key) % self.capacity
    
    def _hash2(self, key):
        """Secondary hash function - must never return 0"""
        if isinstance(key, str):
            hash_val = sum(ord(c) * (i + 1) for i, c in enumerate(key))
        else:
            hash_val = hash(key)
        
        # Use a prime smaller than capacity, ensure result is never 0
        second_prime = self.capacity - 1 if self._is_prime(self.capacity - 1) else self._prev_prime(self.capacity)
        result = hash_val % second_prime
        return result if result != 0 else 1
    
    def _is_prime(self, n):
        """Check if number is prime"""
        if n < 2:
            return False
        for i in range(2, int(n ** 0.5) + 1):
            if n % i == 0:
                return False
        return True
    
    def _next_prime(self, n):
        """Find next prime number greater than n"""
        n += 1
        while not self._is_prime(n):
            n += 1
        return n
    
    def _prev_prime(self, n):
        """Find previous prime number less than n"""
        n -= 1
        while n > 1 and not self._is_prime(n):
            n -= 1
        return n if n > 1 else 2
    
    def _resize(self):
        """Resize the hash table when load factor exceeds 0.7"""
        old_keys = self.keys
        old_values = self.values
        old_capacity = self.capacity
        
        self.capacity = self._next_prime(self.capacity * 2)
        self.size = 0
        self.keys = [None] * self.capacity
        self.values = [None] * self.capacity
        self.deleted = [False] * self.capacity
        
        # Rehash all existing key-value pairs
        for i in range(old_capacity):
            if old_keys[i] is not None:
                self.put(old_keys[i], old_values[i])
    
    def _double_hash_probe(self, key, operation='find'):
        """Double hashing: h1(k) + i * h2(k)"""
        h1 = self._hash1(key)
        h2 = self._hash2(key)
        i = 0
        
        while i < self.capacity:
            index = (h1 + i * h2) % self.capacity
            
            if operation == 'insert':
                # For insertion: empty slot or deleted slot
                if self.keys[index] is None or self.deleted[index]:
                    return index
                # Key already exists
                if self.keys[index] == key and not self.deleted[index]:
                    return index
            
            elif operation == 'find':
                # For finding: exact match
                if self.keys[index] == key and not self.deleted[index]:
                    return index
                # Empty slot means key doesn't exist
                if self.keys[index] is None:
                    return -1
            
            elif operation == 'delete':
                # For deletion: exact match
                if self.keys[index] == key and not self.deleted[index]:
                    return index
                # Empty slot means key doesn't exist
                if self.keys[index] is None:
                    return -1
            
            i += 1
        
        return -1  # Not found or table full
    
    def put(self, key, value):
        """Insert or update a key-value pair"""
        if self.size >= self.capacity * 0.7:
            self._resize()
        
        index = self._double_hash_probe(key, 'insert')
        
        if index == -1:
            raise Exception("Hash table is full")
        
        # New key insertion
        if self.keys[index] is None or self.deleted[index]:
            self.size += 1
        
        self.keys[index] = key
        self.values[index] = value
        self.deleted[index] = False
    
    def get(self, key):
        """Retrieve value by key"""
        index = self._double_hash_probe(key, 'find')
        
        if index == -1:
            raise KeyError(f"Key '{key}' not found")
        
        return self.values[index]
    
    def delete(self, key):
        """Delete a key-value pair"""
        index = self._double_hash_probe(key, 'delete')
        
        if index == -1:
            return False
        
        self.deleted[index] = True
        self.size -= 1
        return True
    
    def contains(self, key):
        """Check if key exists in hash table"""
        try:
            self.get(key)
            return True
        except KeyError:
            return False
    
    def display(self):
        """Display the hash table contents with hash analysis"""
        print("Hash Table Contents (Double Hashing):")
        for i in range(self.capacity):
            if self.keys[i] is not None and not self.deleted[i]:
                # Calculate probe sequence for this key
                h1 = self._hash1(self.keys[i])
                h2 = self._hash2(self.keys[i])
                probe_sequence = []
                
                for j in range(self.capacity):
                    probe_index = (h1 + j * h2) % self.capacity
                    probe_sequence.append(probe_index)
                    if probe_index == i:
                        break
                
                print(f"[{i}]: {self.keys[i]} -> {self.values[i]}")
                print(f"      h1({self.keys[i]}) = {h1}, h2({self.keys[i]}) = {h2}")
                print(f"      probe sequence: {probe_sequence}")
            elif self.keys[i] is not None and self.deleted[i]:
                print(f"[{i}]: DELETED")
            else:
                print(f"[{i}]: EMPTY")
        
        print(f"Size: {self.size}, Capacity: {self.capacity}")
        print(f"Load Factor: {self.size / self.capacity:.2f}")
    
    def hash_analysis(self, key):
        """Analyze hash functions for a specific key"""
        h1 = self._hash1(key)
        h2 = self._hash2(key)
        print(f"Hash analysis for key '{key}':")
        print(f"  h1({key}) = {h1}")
        print(f"  h2({key}) = {h2}")
        print(f"  Step size: {h2}")
        
        # Show first few probe positions
        print(f"  First 5 probe positions: ", end="")
        for i in range(5):
            pos = (h1 + i * h2) % self.capacity
            print(f"{pos}", end="")
            if i < 4:
                print(", ", end="")
        print()
    
    def probe_statistics(self):
        """Show probing statistics"""
        total_probes = 0
        active_keys = 0
        max_probes = 0
        
        for i in range(self.capacity):
            if self.keys[i] is not None and not self.deleted[i]:
                active_keys += 1
                # Count probes needed for this key
                h1 = self._hash1(self.keys[i])
                h2 = self._hash2(self.keys[i])
                probes = 1
                
                for j in range(1, self.capacity):
                    probe_index = (h1 + j * h2) % self.capacity
                    if probe_index == i:
                        probes = j + 1
                        break
                
                total_probes += probes
                max_probes = max(max_probes, probes)
        
        if active_keys > 0:
            avg_probes = total_probes / active_keys
            print(f"Probing Statistics:")
            print(f"  Average probes per key: {avg_probes:.2f}")
            print(f"  Maximum probes for any key: {max_probes}")
            print(f"  Total probes: {total_probes}")
        else:
            print("No active keys in table")
    
    def collision_analysis(self):
        """Analyze collision patterns"""
        h1_collisions = {}
        h2_values = {}
        
        for i in range(self.capacity):
            if self.keys[i] is not None and not self.deleted[i]:
                h1 = self._hash1(self.keys[i])
                h2 = self._hash2(self.keys[i])
                
                if h1 not in h1_collisions:
                    h1_collisions[h1] = []
                h1_collisions[h1].append(self.keys[i])
                
                if h2 not in h2_values:
                    h2_values[h2] = []
                h2_values[h2].append(self.keys[i])
        
        print("Collision Analysis:")
        print("h1 collisions (keys with same primary hash):")
        for h1, keys in h1_collisions.items():
            if len(keys) > 1:
                print(f"  h1={h1}: {keys}")
        
        print("h2 distribution (step sizes):")
        for h2, keys in sorted(h2_values.items()):
            print(f"  h2={h2}: {keys}")
```

```C#

# Example usage
if __name__ == "__main__":
    ht = HashTableDouble(11)  # Prime capacity
    
    # Insert some key-value pairs that will cause collisions
    test_data = [
        ("apple", 10), ("banana", 20), ("orange", 30), ("grape", 40),
        ("kiwi", 50), ("mango", 60), ("pear", 70), ("peach", 80)
    ]
    
    print("Inserting keys with double hashing:")
    for key, value in test_data:
        ht.put(key, value)
        print(f"Inserted {key}: {value}")
        ht.hash_analysis(key)
        print()
    
    print("Final hash table:")
    ht.display()
    print()
    
    # Show collision analysis
    ht.collision_analysis()
    print()
    
    # Show probing statistics
    ht.probe_statistics()
    print()
    
    # Test retrieval
    try:
        print(f"apple: {ht.get('apple')}")
        print(f"mango: {ht.get('mango')}")
    except KeyError as e:
        print(f"Error: {e}")
    
    # Test deletion
    print(f"\nDeleting 'banana': {ht.delete('banana')}")
    print("After deletion:")
    ht.display()
    
    # Demonstrate hash function properties
    print("\nHash function demonstration:")
    test_keys = ["test1", "test2", "collision", "example"]
    for key in test_keys:
        ht.hash_analysis(key)
```