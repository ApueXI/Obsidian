---
Created: 2025-08-12T08:45
---
## ==Separate Chaining Code Implementation==

```C++
\#include <iostream>
\#include <vector>
\#include <string>
\#include <functional>
\#include <stdexcept>

template<typename K, typename V>
class HashNode {
public:
    K key;
    V value;
    HashNode* next;
    
    HashNode(K k, V v) : key(k), value(v), next(nullptr) {}
};

template<typename K, typename V>
class HashTable {
private:
    std::vector<HashNode<K, V>*> table;
    int capacity;
    int size;
    
    int hash(K key) {
        std::hash<K> hasher;
        return hasher(key) % capacity;
    }

public:
    HashTable(int cap = 10) : capacity(cap), size(0) {
        table.resize(capacity, nullptr);
    }
    
    ~HashTable() {
        clear();
    }
    
    void insert(K key, V value) {
        int index = hash(key);
        
        if (table[index] == nullptr) {
            // No collision
            table[index] = new HashNode<K, V>(key, value);
            size++;
        } else {
            // Handle collision with chaining
            HashNode<K, V>* current = table[index];
            
            while (current != nullptr) {
                if (current->key == key) {
                    // Key already exists, update value
                    current->value = value;
                    return;
                }
                if (current->next == nullptr)
                    break;
                current = current->next;
            }
            
            // Add new node at the end of the chain
            current->next = new HashNode<K, V>(key, value);
            size++;
        }
    }
    
    V get(K key) {
        int index = hash(key);
        HashNode<K, V>* current = table[index];
        
        while (current != nullptr) {
            if (current->key == key) {
                return current->value;
            }
            current = current->next;
        }
        
        throw std::runtime_error("Key not found");
    }
    
    bool remove(K key) {
        int index = hash(key);
        HashNode<K, V>* current = table[index];
        
        if (current == nullptr)
            return false;
        
        // If first node contains the key
        if (current->key == key) {
            table[index] = current->next;
            delete current;
            size--;
            return true;
        }
        
        // Search in the chain
        while (current->next != nullptr) {
            if (current->next->key == key) {
                HashNode<K, V>* nodeToDelete = current->next;
                current->next = current->next->next;
                delete nodeToDelete;
                size--;
                return true;
            }
            current = current->next;
        }
        
        return false;
    }
    
    void display() {
        for (int i = 0; i < capacity; i++) {
            std::cout << "Bucket " << i << ": ";
            HashNode<K, V>* current = table[i];
            
            if (current == nullptr) {
                std::cout << "Empty" << std::endl;
            } else {
                bool first = true;
                while (current != nullptr) {
                    if (!first) std::cout << " -> ";
                    std::cout << "(" << current->key << ": " << current->value << ")";
                    current = current->next;
                    first = false;
                }
                std::cout << std::endl;
            }
        }
    }
    
    void clear() {
        for (int i = 0; i < capacity; i++) {
            HashNode<K, V>* current = table[i];
            while (current != nullptr) {
                HashNode<K, V>* next = current->next;
                delete current;
                current = next;
            }
            table[i] = nullptr;
        }
        size = 0;
    }
    
    int getSize() const { return size; }
    int getCapacity() const { return capacity; }
};

// Example usage
int main() {
    HashTable<std::string, int> ht(7);
    
    // Insert some key-value pairs
    ht.insert("apple", 5);
    ht.insert("banana", 3);
    ht.insert("orange", 8);
    ht.insert("grape", 2);
    ht.insert("kiwi", 4);
    ht.insert("mango", 6);
    
    std::cout << "Hash Table Contents:" << std::endl;
    ht.display();
    
    std::cout << "\nSize: " << ht.getSize() << std::endl;
    
    // Test retrieval
    try {
        std::cout << "apple: " << ht.get("apple") << std::endl;
        std::cout << "grape: " << ht.get("grape") << std::endl;
    } catch (const std::runtime_error& e) {
        std::cout << e.what() << std::endl;
    }
    
    // Test deletion
    if (ht.remove("banana")) {
        std::cout << "\nAfter deleting 'banana':" << std::endl;
        ht.display();
    }
    
    return 0;
}
```

## Separating Chaining HT Code Implementation

```C++
\#include <iostream>
\#include <vector>
\#include <string>
using namespace std;

struct Node {
    string key;
    int value;
    Node* next;
    Node(string k, int v) : key(k), value(v), next(nullptr) {}
};

class HashTable {
private:
    vector<Node*> buckets;
    int size;

    int hashFunction(const string& key) {
        int hash = 0;
        for (char ch : key) {
            hash = (hash * 31 + ch) % size;
        }
        return hash;
    }

public:
    HashTable(int s = 10) : size(s) {
        buckets.resize(size, nullptr);
    }

    void insert(const string& key, int value) {
        int index = hashFunction(key);
        Node* head = buckets[index];

        // Update value if key exists
        Node* current = head;
        while (current != nullptr) {
            if (current->key == key) {
                current->value = value;
                return;
            }
            current = current->next;
        }

        // Insert at head
        Node* newNode = new Node(key, value);
        newNode->next = head;
        buckets[index] = newNode;
    }

    int* search(const string& key) {
        int index = hashFunction(key);
        Node* current = buckets[index];

        while (current != nullptr) {
            if (current->key == key)
                return &(current->value);
            current = current->next;
        }
        return nullptr;
    }

    bool remove(const string& key) {
        int index = hashFunction(key);
        Node* current = buckets[index];
        Node* prev = nullptr;

        while (current != nullptr) {
            if (current->key == key) {
                if (prev != nullptr)
                    prev->next = current->next;
                else
                    buckets[index] = current->next;
                delete current;
                return true;
            }
            prev = current;
            current = current->next;
        }
        return false;
    }

    ~HashTable() {
        for (int i = 0; i < size; i++) {
            Node* current = buckets[i];
            while (current != nullptr) {
                Node* temp = current;
                current = current->next;
                delete temp;
            }
        }
    }
};
```