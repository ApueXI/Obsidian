---
Created: 2025-08-12T08:45
---
## ==Separate Chaining Code Implementation==

```Python
class Node:
    def __init__(self, key, value):
        self.key = key
        self.value = value
        self.next = None

class HashTable:
    def __init__(self, capacity=10):
        self.capacity = capacity
        self.size = 0
        self.table = [None] * self.capacity
    
    def _hash(self, key):
        """Simple hash function using built-in hash()"""
        return hash(key) % self.capacity
    
    def insert(self, key, value):
        """Insert a key-value pair into the hash table"""
        index = self._hash(key)
        
        if self.table[index] is None:
            # No collision, create new node
            self.table[index] = Node(key, value)
            self.size += 1
        else:
            # Collision occurred, handle with chaining
            current = self.table[index]
            while current:
                if current.key == key:
                    # Key already exists, update value
                    current.value = value
                    return
                if current.next is None:
                    break
                current = current.next
            # Add new node at the end of the chain
            current.next = Node(key, value)
            self.size += 1
    
    def get(self, key):
        """Retrieve value by key"""
        index = self._hash(key)
        current = self.table[index]
        
        while current:
            if current.key == key:
                return current.value
            current = current.next
        
        raise KeyError(f"Key '{key}' not found")
    
    def delete(self, key):
        """Delete a key-value pair from the hash table"""
        index = self._hash(key)
        current = self.table[index]
        
        if current is None:
            raise KeyError(f"Key '{key}' not found")
        
        # If first node contains the key
        if current.key == key:
            self.table[index] = current.next
            self.size -= 1
            return
        
        # Search in the chain
        while current.next:
            if current.next.key == key:
                current.next = current.next.next
                self.size -= 1
                return
            current = current.next
        
        raise KeyError(f"Key '{key}' not found")
    
    def display(self):
        """Display the hash table contents"""
        for i in range(self.capacity):
            print(f"Bucket {i}: ", end="")
            current = self.table[i]
            if current is None:
                print("Empty")
            else:
                chain = []
                while current:
                    chain.append(f"({current.key}: {current.value})")
                    current = current.next
                print(" -> ".join(chain))

# Example usage
if __name__ == "__main__":
    ht = HashTable(7)  # Small capacity to demonstrate chaining
    
    # Insert some key-value pairs
    ht.insert("apple", 5)
    ht.insert("banana", 3)
    ht.insert("orange", 8)
    ht.insert("grape", 2)
    ht.insert("kiwi", 4)
    ht.insert("mango", 6)
    
    print("Hash Table Contents:")
    ht.display()
    
    print(f"\nSize: {ht.size}")
    
    # Test retrieval
    try:
        print(f"apple: {ht.get('apple')}")
        print(f"grape: {ht.get('grape')}")
    except KeyError as e:
        print(e)
    
    # Test deletion
    ht.delete("banana")
    print("\nAfter deleting 'banana':")
    ht.display()
```

## Separating Chaining HT Code Implementation

```Python
class Node:
    def __init__(self, key, value):
        self.key = key
        self.value = value
        self.next = None

class HashTable:
    def __init__(self, size=10):
        self.size = size
        self.buckets = [None] * size

    def _hash(self, key):
        return hash(key) % self.size

    def insert(self, key, value):
        index = self._hash(key)
        head = self.buckets[index]

        # Update if key exists
        current = head
        while current:
            if current.key == key:
                current.value = value
                return
            current = current.next

        # Insert new node at head
        new_node = Node(key, value)
        new_node.next = head
        self.buckets[index] = new_node

    def search(self, key):
        index = self._hash(key)
        current = self.buckets[index]
        while current:
            if current.key == key:
                return current.value
            current = current.next
        return None

    def delete(self, key):
        index = self._hash(key)
        current = self.buckets[index]
        prev = None

        while current:
            if current.key == key:
                if prev:
                    prev.next = current.next
                else:
                    self.buckets[index] = current.next
                return True
            prev = current
            current = current.next
        return False
```