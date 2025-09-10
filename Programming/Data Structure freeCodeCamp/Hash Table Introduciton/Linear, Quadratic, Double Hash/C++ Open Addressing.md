---
Created: 2025-08-14T15:05
---
## ==Linear Probing==

```C++
\#include <iostream>
\#include <vector>
\#include <string>
\#include <stdexcept>
\#include <functional>

template<typename K, typename V>
class HashTable {
private:
    struct Entry {
        K key;
        V value;
        bool isDeleted;
        bool isEmpty;
        
        Entry() : isDeleted(false), isEmpty(true) {}
        Entry(const K& k, const V& v) : key(k), value(v), isDeleted(false), isEmpty(false) {}
    };
    
    std::vector<Entry> table;
    int capacity;
    int size;
    
    int hash(const K& key) const {
        std::hash<K> hasher;
        return hasher(key) % capacity;
    }
    
    void resize() {
        std::vector<Entry> oldTable = table;
        int oldCapacity = capacity;
        
        capacity *= 2;
        size = 0;
        table = std::vector<Entry>(capacity);
        
        // Rehash all existing entries
        for (int i = 0; i < oldCapacity; i++) {
            if (!oldTable[i].isEmpty && !oldTable[i].isDeleted) {
                put(oldTable[i].key, oldTable[i].value);
            }
        }
    }

public:
    explicit HashTable(int initialCapacity = 10) : capacity(initialCapacity), size(0) {
        table.resize(capacity);
    }
    
    void put(const K& key, const V& value) {
        if (size >= capacity * 0.7) {
            resize();
        }
        
        int index = hash(key);
        int originalIndex = index;
        
        while (true) {
            // Empty slot or deleted slot - insert here
            if (table[index].isEmpty || table[index].isDeleted) {
                if (table[index].isEmpty || table[index].isDeleted) {
                    size++;
                }
                table[index] = Entry(key, value);
                return;
            }
            
            // Key already exists - update value
            if (table[index].key == key && !table[index].isDeleted) {
                table[index].value = value;
                return;
            }
            
            // Linear probing - move to next slot
            index = (index + 1) % capacity;
            
            // Table is full (shouldn't happen due to resize)
            if (index == originalIndex) {
                throw std::runtime_error("Hash table is full");
            }
        }
    }
    
    V get(const K& key) const {
        int index = hash(key);
        int originalIndex = index;
        
        while (!table[index].isEmpty) {
            if (table[index].key == key && !table[index].isDeleted) {
                return table[index].value;
            }
            
            index = (index + 1) % capacity;
            
            // Completed full circle
            if (index == originalIndex) {
                break;
            }
        }
        
        throw std::runtime_error("Key not found");
    }
    
    bool remove(const K& key) {
        int index = hash(key);
        int originalIndex = index;
        
        while (!table[index].isEmpty) {
            if (table[index].key == key && !table[index].isDeleted) {
                table[index].isDeleted = true;
                size--;
                return true;
            }
            
            index = (index + 1) % capacity;
            
            if (index == originalIndex) {
                break;
            }
        }
        
        return false;
    }
    
    bool contains(const K& key) const {
        try {
            get(key);
            return true;
        } catch (const std::runtime_error&) {
            return false;
        }
    }
    
    void display() const {
        std::cout << "Hash Table Contents:" << std::endl;
        for (int i = 0; i < capacity; i++) {
            if (!table[i].isEmpty && !table[i].isDeleted) {
                std::cout << "[" << i << "]: " << table[i].key 
                         << " -> " << table[i].value << " (ACTIVE)" << std::endl;
            } else if (!table[i].isEmpty && table[i].isDeleted) {
                std::cout << "[" << i << "]: DELETED" << std::endl;
            } else {
                std::cout << "[" << i << "]: EMPTY" << std::endl;
            }
        }
        std::cout << "Size: " << size << ", Capacity: " << capacity << std::endl;
    }
    
    int getSize() const { return size; }
    int getCapacity() const { return capacity; }
};

// Example usage
int main() {
    HashTable<std::string, int> ht(7);
    
    // Insert some key-value pairs
    ht.put("apple", 10);
    ht.put("banana", 20);
    ht.put("orange", 30);
    ht.put("grape", 40);
    
    std::cout << "After insertions:" << std::endl;
    ht.display();
    std::cout << std::endl;
    
    // Test retrieval
    try {
        std::cout << "apple: " << ht.get("apple") << std::endl;
        std::cout << "banana: " << ht.get("banana") << std::endl;
        std::cout << std::endl;
    } catch (const std::runtime_error& e) {
        std::cout << "Error: " << e.what() << std::endl;
    }
    
    // Test deletion
    ht.remove("banana");
    std::cout << "After deleting 'banana':" << std::endl;
    ht.display();
    std::cout << std::endl;
    
    // Test collision handling
    ht.put("pear", 50);
    std::cout << "After adding 'pear':" << std::endl;
    ht.display();
    
    return 0;
}
```

## ==Quadratic Probing==

```C++
\#include <iostream>
\#include <vector>
\#include <string>
\#include <stdexcept>
\#include <functional>
\#include <cmath>
\#include <iomanip>

template<typename K, typename V>
class HashTableQuadratic {
private:
    struct Entry {
        K key;
        V value;
        bool isDeleted;
        bool isEmpty;
        
        Entry() : isDeleted(false), isEmpty(true) {}
        Entry(const K& k, const V& v) : key(k), value(v), isDeleted(false), isEmpty(false) {}
    };
    
    std::vector<Entry> table;
    int capacity;
    int size;
    static const int C1 = 1;
    static const int C2 = 1;
    
    enum class ProbeOperation {
        INSERT,
        FIND,
        DELETE
    };
    
    int hash(const K& key) const {
        std::hash<K> hasher;
        return static_cast<int>(hasher(key) % capacity);
    }
    
    bool isPrime(int n) const {
        if (n < 2) return false;
        for (int i = 2; i <= sqrt(n); i++) {
            if (n % i == 0) return false;
        }
        return true;
    }
    
    int nextPrime(int n) const {
        n++;
        while (!isPrime(n)) {
            n++;
        }
        return n;
    }
    
    int quadraticProbe(const K& key, ProbeOperation operation) const {
        int originalIndex = hash(key);
        
        for (int i = 0; i < capacity; i++) {
            int currentIndex = (originalIndex + C1 * i + C2 * i * i) % capacity;
            
            switch (operation) {
                case ProbeOperation::INSERT:
                    // For insertion: empty slot or deleted slot
                    if (table[currentIndex].isEmpty || table[currentIndex].isDeleted) {
                        return currentIndex;
                    }
                    // Key already exists
                    if (table[currentIndex].key == key && !table[currentIndex].isDeleted) {
                        return currentIndex;
                    }
                    break;
                    
                case ProbeOperation::FIND:
                    // For finding: exact match
                    if (!table[currentIndex].isEmpty && table[currentIndex].key == key && !table[currentIndex].isDeleted) {
                        return currentIndex;
                    }
                    // Empty slot means key doesn't exist
                    if (table[currentIndex].isEmpty) {
                        return -1;
                    }
                    break;
                    
                case ProbeOperation::DELETE:
                    // For deletion: exact match
                    if (!table[currentIndex].isEmpty && table[currentIndex].key == key && !table[currentIndex].isDeleted) {
                        return currentIndex;
                    }
                    // Empty slot means key doesn't exist
                    if (table[currentIndex].isEmpty) {
                        return -1;
                    }
                    break;
            }
        }
        
        return -1; // Not found or table full
    }
    
    void resize() {
        std::vector<Entry> oldTable = table;
        int oldCapacity = capacity;
        
        capacity = nextPrime(capacity * 2);
        size = 0;
        table = std::vector<Entry>(capacity);
        
        // Rehash all existing entries
        for (int i = 0; i < oldCapacity; i++) {
            if (!oldTable[i].isEmpty && !oldTable[i].isDeleted) {
                put(oldTable[i].key, oldTable[i].value);
            }
        }
    }

public:
    explicit HashTableQuadratic(int initialCapacity = 11) : capacity(nextPrime(initialCapacity)), size(0) {
        table.resize(capacity);
    }
    
    void put(const K& key, const V& value) {
        if (size >= capacity * 0.5) { // Lower load factor for quadratic probing
            resize();
        }
        
        int index = quadraticProbe(key, ProbeOperation::INSERT);
        
        if (index == -1) {
            throw std::runtime_error("Hash table is full");
        }
        
        // New key insertion
        if (table[index].isEmpty || table[index].isDeleted) {
            size++;
        }
        
        table[index] = Entry(key, value);
    }
    
    V get(const K& key) const {
        int index = quadraticProbe(key, ProbeOperation::FIND);
        
        if (index == -1) {
            throw std::runtime_error("Key not found");
        }
        
        return table[index].value;
    }
    
    bool remove(const K& key) {
        int index = quadraticProbe(key, ProbeOperation::DELETE);
        
        if (index == -1) {
            return false;
        }
        
        table[index].isDeleted = true;
        size--;
        return true;
    }
    
    bool contains(const K& key) const {
        try {
            get(key);
            return true;
        } catch (const std::runtime_error&) {
            return false;
        }
    }
    
    void display() const {
        std::cout << "Hash Table Contents (Quadratic Probing):" << std::endl;
        for (int i = 0; i < capacity; i++) {
            if (!table[i].isEmpty && !table[i].isDeleted) {
                // Calculate probe sequence for this key
                std::vector<int> probeSequence;
                int originalIndex = hash(table[i].key);
                
                for (int j = 0; j < capacity; j++) {
                    int probeIndex = (originalIndex + C1 * j + C2 * j * j) % capacity;
                    probeSequence.push_back(probeIndex);
                    if (probeIndex == i) {
                        break;
                    }
                }
                
                std::cout << "[" << i << "]: " << table[i].key 
                         << " -> " << table[i].value << " (probes: [";
                for (size_t k = 0; k < probeSequence.size(); k++) {
                    std::cout << probeSequence[k];
                    if (k < probeSequence.size() - 1) std::cout << ", ";
                }
                std::cout << "])" << std::endl;
            } else if (!table[i].isEmpty && table[i].isDeleted) {
                std::cout << "[" << i << "]: DELETED" << std::endl;
            } else {
                std::cout << "[" << i << "]: EMPTY" << std::endl;
            }
        }
        
        std::cout << "Size: " << size << ", Capacity: " << capacity << std::endl;
        std::cout << "Load Factor: " << std::fixed << std::setprecision(2) 
                  << static_cast<double>(size) / capacity << std::endl;
    }
    
    void probeStatistics() const {
        int totalProbes = 0;
        int activeKeys = 0;
        
        for (int i = 0; i < capacity; i++) {
            if (!table[i].isEmpty && !table[i].isDeleted) {
                activeKeys++;
                int originalIndex = hash(table[i].key);
                int probes = 1;
                
                for (int j = 1; j < capacity; j++) {
                    int probeIndex = (originalIndex + C1 * j + C2 * j * j) % capacity;
                    if (probeIndex == i) {
                        probes = j + 1;
                        break;
                    }
                }
                
                totalProbes += probes;
            }
        }
        
        if (activeKeys > 0) {
            double avgProbes = static_cast<double>(totalProbes) / activeKeys;
            std::cout << "Average probes per key: " << std::fixed << std::setprecision(2) 
                      << avgProbes << std::endl;
        } else {
            std::cout << "No active keys in table" << std::endl;
        }
    }
    
    int getSize() const { return size; }
    int getCapacity() const { return capacity; }
};

// Example usage
int main() {
    HashTableQuadratic<std::string, int> ht(11);
    
    // Insert some key-value pairs that will cause collisions
    std::vector<std::string> keys = {"apple", "banana", "orange", "grape", "kiwi", "mango", "pear"};
    std::vector<int> values = {10, 20, 30, 40, 50, 60, 70};
    
    std::cout << "Inserting keys with quadratic probing:" << std::endl;
    for (size_t i = 0; i < keys.size(); i++) {
        ht.put(keys[i], values[i]);
        std::cout << "Inserted " << keys[i] << ": " << values[i] << std::endl;
    }
    
    std::cout << "\nFinal hash table:" << std::endl;
    ht.display();
    std::cout << std::endl;
    
    // Show probing statistics
    ht.probeStatistics();
    std::cout << std::endl;
    
    // Test retrieval
    try {
        std::cout << "apple: " << ht.get("apple") << std::endl;
        std::cout << "mango: " << ht.get("mango") << std::endl;
    } catch (const std::runtime_error& e) {
        std::cout << "Error: " << e.what() << std::endl;
    }
    
    // Test deletion
    std::cout << "\nDeleting 'banana': " << (ht.remove("banana") ? "success" : "failed") << std::endl;
    std::cout << "After deletion:" << std::endl;
    ht.display();
    
    // Add more elements to test resizing
    std::cout << "\nAdding more elements to trigger resize:" << std::endl;
    ht.put("watermelon", 80);
    ht.put("strawberry", 90);
    ht.display();
    
    return 0;
}
```

## ==Double Hashing==

```C++
\#include <iostream>
\#include <vector>
\#include <optional>

template<typename K, typename V>
class DoubleHashingHashTable {
private:
    struct Entry {
        K key;
        V value;
        bool deleted;
        
        Entry() : deleted(false) {}
        Entry(const K& k, const V& v) : key(k), value(v), deleted(false) {}
    };
    
    std::vector<std::optional<Entry>> table;
    int capacity;
    int size;
    
    // Primary hash function
    int hash1(const K& key) const {
        return std::hash<K>{}(key) % capacity;
    }
    
    // Secondary hash function (must return odd number to ensure coprimality)
    int hash2(const K& key) const {
        int h = std::hash<K>{}(key) % (capacity - 1);
        return (h % 2 == 0) ? h + 1 : h;  // Ensure odd number
    }
    
    // Double hashing probe sequence
    int probe(const K& key, int attempt) const {
        return (hash1(key) + attempt * hash2(key)) % capacity;
    }
    
    void rehash() {
        std::vector<std::optional<Entry>> oldTable = std::move(table);
        int oldCapacity = capacity;
        
        capacity *= 2;
        size = 0;
        table.assign(capacity, std::nullopt);
        
        // Reinsert all non-deleted entries
        for (const auto& entry : oldTable) {
            if (entry && !entry->deleted) {
                insert(entry->key, entry->value);
            }
        }
    }
    
public:
    explicit DoubleHashingHashTable(int initialCapacity = 11) 
        : capacity(initialCapacity), size(0) {
        // Ensure capacity is prime for better distribution
        table.assign(capacity, std::nullopt);
    }
    
    void insert(const K& key, const V& value) {
        if (size >= capacity * 0.7) {  // Load factor threshold
            rehash();
        }
        
        int attempt = 0;
        int index;
        
        do {
            index = probe(key, attempt);
            
            // If slot is empty or marked as deleted, insert here
            if (!table[index] || table[index]->deleted) {
                table[index] = Entry(key, value);
                size++;
                return;
            }
            
            // If key already exists, update value
            if (table[index]->key == key && !table[index]->deleted) {
                table[index]->value = value;
                return;
            }
            
            attempt++;
        } while (attempt < capacity);
        
        throw std::runtime_error("Hash table is full");
    }
    
    std::optional<V> search(const K& key) const {
        int attempt = 0;
        int index;
        
        do {
            index = probe(key, attempt);
            
            if (!table[index]) {
                return std::nullopt;  // Key not found
            }
            
            if (table[index]->key == key && !table[index]->deleted) {
                return table[index]->value;
            }
            
            attempt++;
        } while (attempt < capacity);
        
        return std::nullopt;  // Key not found
    }
    
    bool remove(const K& key) {
        int attempt = 0;
        int index;
        
        do {
            index = probe(key, attempt);
            
            if (!table[index]) {
                return false;  // Key not found
            }
            
            if (table[index]->key == key && !table[index]->deleted) {
                table[index]->deleted = true;
                size--;
                return true;
            }
            
            attempt++;
        } while (attempt < capacity);
        
        return false;  // Key not found
    }
    
    void display() const {
        std::cout << "Hash Table Contents:\n";
        for (int i = 0; i < capacity; i++) {
            std::cout << "[" << i << "]: ";
            if (table[i] && !table[i]->deleted) {
                std::cout << "(" << table[i]->key << ", " << table[i]->value << ")";
            } else if (table[i] && table[i]->deleted) {
                std::cout << "DELETED";
            } else {
                std::cout << "EMPTY";
            }
            std::cout << "\n";
        }
        std::cout << "Size: " << size << "/" << capacity << "\n\n";
    }
    
    int getSize() const { return size; }
    int getCapacity() const { return capacity; }
    double getLoadFactor() const { return (double)size / capacity; }
};
```

```C++

// Example usage
int main() {
    DoubleHashingHashTable<int, std::string> hashTable(7);
    
    // Insert some key-value pairs
    hashTable.insert(10, "Ten");
    hashTable.insert(22, "Twenty-Two");
    hashTable.insert(31, "Thirty-One");
    hashTable.insert(4, "Four");
    hashTable.insert(15, "Fifteen");
    hashTable.insert(28, "Twenty-Eight");
    hashTable.insert(17, "Seventeen");
    
    std::cout << "After insertions:\n";
    hashTable.display();
    
    // Search for values
    auto result = hashTable.search(22);
    if (result) {
        std::cout << "Found key 22: " << *result << "\n";
    }
    
    result = hashTable.search(99);
    if (!result) {
        std::cout << "Key 99 not found\n";
    }
    
    // Remove a key
    std::cout << "\nRemoving key 22...\n";
    hashTable.remove(22);
    hashTable.display();
    
    // Insert more to trigger rehashing
    hashTable.insert(33, "Thirty-Three");
    hashTable.insert(44, "Forty-Four");
    
    std::cout << "After more insertions (may trigger rehashing):\n";
    hashTable.display();
    
    return 0;
}
```