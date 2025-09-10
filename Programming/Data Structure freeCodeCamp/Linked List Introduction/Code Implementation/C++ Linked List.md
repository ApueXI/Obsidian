---
Created: 2025-08-12T06:46
---
### C++ — LinkedList.cpp

```C++
\#include <iostream>
\#include <stdexcept>
\#include <vector>

template<typename T>
class Node {
public:
    T data;
    Node* next;
    
    Node(const T& value) : data(value), next(nullptr) {}
};

template<typename T>
class SinglyLinkedList {
private:
    Node<T>* head;
    size_t size;

public:
    SinglyLinkedList() : head(nullptr), size(0) {}
    
    // Copy constructor
    SinglyLinkedList(const SinglyLinkedList& other) : head(nullptr), size(0) {
        Node<T>* current = other.head;
        while (current != nullptr) {
            append(current->data);
            current = current->next;
        }
    }
    
    // Assignment operator
    SinglyLinkedList& operator=(const SinglyLinkedList& other) {
        if (this != &other) {
            clear();
            Node<T>* current = other.head;
            while (current != nullptr) {
                append(current->data);
                current = current->next;
            }
        }
        return *this;
    }
    
    // Destructor
    ~SinglyLinkedList() {
        clear();
    }
    
    void clear() {
        while (head != nullptr) {
            Node<T>* temp = head;
            head = head->next;
            delete temp;
        }
        size = 0;
    }
    
    size_t getSize() const { return size; }
    bool isEmpty() const { return head == nullptr; }
    
    void append(const T& data) {
        Node<T>* newNode = new Node<T>(data);
        if (head == nullptr) {
            head = newNode;
        } else {
            Node<T>* current = head;
            while (current->next != nullptr) {
                current = current->next;
            }
            current->next = newNode;
        }
        size++;
    }
    
    void prepend(const T& data) {
        Node<T>* newNode = new Node<T>(data);
        newNode->next = head;
        head = newNode;
        size++;
    }
    
    void insert(size_t index, const T& data) {
        if (index > size) {
            throw std::out_of_range("Index out of range");
        }
        
        if (index == 0) {
            prepend(data);
            return;
        }
        
        Node<T>* newNode = new Node<T>(data);
        Node<T>* current = head;
        for (size_t i = 0; i < index - 1; i++) {
            current = current->next;
        }
        
        newNode->next = current->next;
        current->next = newNode;
        size++;
    }
    
    T removeFirst() {
        if (head == nullptr) {
            throw std::runtime_error("List is empty");
        }
        
        Node<T>* temp = head;
        T data = head->data;
        head = head->next;
        delete temp;
        size--;
        return data;
    }
    
    T removeLast() {
        if (head == nullptr) {
            throw std::runtime_error("List is empty");
        }
        
        if (head->next == nullptr) { // Only one element
            T data = head->data;
            delete head;
            head = nullptr;
            size--;
            return data;
        }
        
        // Find second to last node
        Node<T>* current = head;
        while (current->next->next != nullptr) {
            current = current->next;
        }
        
        Node<T>* temp = current->next;
        T data = temp->data;
        current->next = nullptr;
        delete temp;
        size--;
        return data;
    }
    
    T removeAt(size_t index) {
        if (index >= size) {
            throw std::out_of_range("Index out of range");
        }
        
        if (index == 0) {
            return removeFirst();
        }
        
        Node<T>* current = head;
        for (size_t i = 0; i < index - 1; i++) {
            current = current->next;
        }
        
        Node<T>* temp = current->next;
        T data = temp->data;
        current->next = temp->next;
        delete temp;
        size--;
        return data;
    }
    
    bool remove(const T& data) {
        if (head == nullptr) {
            return false;
        }
        
        if (head->data == data) {
            removeFirst();
            return true;
        }
        
        Node<T>* current = head;
        while (current->next != nullptr) {
            if (current->next->data == data) {
                Node<T>* temp = current->next;
                current->next = temp->next;
                delete temp;
                size--;
                return true;
            }
            current = current->next;
        }
        
        return false;
    }
    
    int indexOf(const T& data) const {
        Node<T>* current = head;
        int index = 0;
        while (current != nullptr) {
            if (current->data == data) {
                return index;
            }
            current = current->next;
            index++;
        }
        return -1;
    }
    
    T get(size_t index) const {
        if (index >= size) {
            throw std::out_of_range("Index out of range");
        }
        
        Node<T>* current = head;
        for (size_t i = 0; i < index; i++) {
            current = current->next;
        }
        return current->data;
    }
    
    T operator[](size_t index) const {
        return get(index);
    }
    
    bool contains(const T& data) const {
        return indexOf(data) != -1;
    }
    
    std::vector<T> toVector() const {
        std::vector<T> result;
        Node<T>* current = head;
        while (current != nullptr) {
            result.push_back(current->data);
            current = current->next;
        }
        return result;
    }
    
    void print() const {
        if (head == nullptr) {
            std::cout << "[]" << std::endl;
            return;
        }
        
        Node<T>* current = head;
        while (current != nullptr) {
            std::cout << current->data;
            if (current->next != nullptr) {
                std::cout << " -> ";
            }
            current = current->next;
        }
        std::cout << " -> nullptr" << std::endl;
    }
};

int main() {
    SinglyLinkedList<int> ll;
    
    // Test append
    for (int i = 0; i < 5; i++) {
        ll.append(i * 10);
    }
    std::cout << "After appending 0-40: ";
    ll.print();
    
    // Test prepend
    ll.prepend(-10);
    std::cout << "After prepending -10: ";
    ll.print();
    
    // Test insert
    ll.insert(2, 99);
    std::cout << "After inserting 99 at index 2: ";
    ll.print();
    
    // Test removal
    int removed = ll.removeFirst();
    std::cout << "Removed first element " << removed << ": ";
    ll.print();
    
    removed = ll.removeLast();
    std::cout << "Removed last element " << removed << ": ";
    ll.print();
    
    // Test find
    int index = ll.indexOf(20);
    std::cout << "Index of 20: " << index << std::endl;
    
    // Test get
    int value = ll.get(1);
    std::cout << "Element at index 1: " << value << std::endl;
    
    // Print as vector
    auto vec = ll.toVector();
    std::cout << "List as vector: [";
    for (size_t i = 0; i < vec.size(); i++) {
        std::cout << vec[i];
        if (i < vec.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    std::cout << "Length: " << ll.getSize() << std::endl;
    
    return 0;
}
```

### C++ — DoublyLinkedList.cpp

```C++
\#include <iostream>
\#include <stdexcept>
\#include <vector>

template<typename T>
class Node {
public:
    T data;
    Node* next;
    Node* prev;
    
    Node(const T& value) : data(value), next(nullptr), prev(nullptr) {}
};

template<typename T>
class DoublyLinkedList {
private:
    Node<T>* head;
    Node<T>* tail;
    size_t size;

public:
    DoublyLinkedList() : head(nullptr), tail(nullptr), size(0) {}
    
    // Copy constructor
    DoublyLinkedList(const DoublyLinkedList& other) : head(nullptr), tail(nullptr), size(0) {
        Node<T>* current = other.head;
        while (current != nullptr) {
            append(current->data);
            current = current->next;
        }
    }
    
    // Assignment operator
    DoublyLinkedList& operator=(const DoublyLinkedList& other) {
        if (this != &other) {
            clear();
            Node<T>* current = other.head;
            while (current != nullptr) {
                append(current->data);
                current = current->next;
            }
        }
        return *this;
    }
    
    // Destructor
    ~DoublyLinkedList() {
        clear();
    }
    
    void clear() {
        while (head != nullptr) {
            Node<T>* temp = head;
            head = head->next;
            delete temp;
        }
        head = tail = nullptr;
        size = 0;
    }
    
    size_t getSize() const { return size; }
    bool isEmpty() const { return head == nullptr; }
    
    void append(const T& data) {
        Node<T>* newNode = new Node<T>(data);
        if (head == nullptr) {
            head = tail = newNode;
        } else {
            newNode->prev = tail;
            tail->next = newNode;
            tail = newNode;
        }
        size++;
    }
    
    void prepend(const T& data) {
        Node<T>* newNode = new Node<T>(data);
        if (head == nullptr) {
            head = tail = newNode;
        } else {
            newNode->next = head;
            head->prev = newNode;
            head = newNode;
        }
        size++;
    }
    
    void insert(size_t index, const T& data) {
        if (index > size) {
            throw std::out_of_range("Index out of range");
        }
        
        if (index == 0) {
            prepend(data);
            return;
        }
        
        if (index == size) {
            append(data);
            return;
        }
        
        Node<T>* newNode = new Node<T>(data);
        Node<T>* current;
        
        // Choose direction based on which is closer
        if (index <= size / 2) {
            // Traverse from head
            current = head;
            for (size_t i = 0; i < index; i++) {
                current = current->next;
            }
        } else {
            // Traverse from tail
            current = tail;
            for (size_t i = 0; i < size - index - 1; i++) {
                current = current->prev;
            }
        }
        
        // Insert before current
        newNode->next = current;
        newNode->prev = current->prev;
        current->prev->next = newNode;
        current->prev = newNode;
        size++;
    }
    
    T removeFirst() {
        if (head == nullptr) {
            throw std::runtime_error("List is empty");
        }
        
        Node<T>* temp = head;
        T data = head->data;
        
        if (head == tail) { // Only one element
            head = tail = nullptr;
        } else {
            head = head->next;
            head->prev = nullptr;
        }
        
        delete temp;
        size--;
        return data;
    }
    
    T removeLast() {
        if (tail == nullptr) {
            throw std::runtime_error("List is empty");
        }
        
        Node<T>* temp = tail;
        T data = tail->data;
        
        if (head == tail) { // Only one element
            head = tail = nullptr;
        } else {
            tail = tail->prev;
            tail->next = nullptr;
        }
        
        delete temp;
        size--;
        return data;
    }
    
    T removeAt(size_t index) {
        if (index >= size) {
            throw std::out_of_range("Index out of range");
        }
        
        if (index == 0) {
            return removeFirst();
        }
        
        if (index == size - 1) {
            return removeLast();
        }
        
        Node<T>* current;
        
        // Choose direction based on which is closer
        if (index <= size / 2) {
            current = head;
            for (size_t i = 0; i < index; i++) {
                current = current->next;
            }
        } else {
            current = tail;
            for (size_t i = 0; i < size - index - 1; i++) {
                current = current->prev;
            }
        }
        
        T data = current->data;
        current->prev->next = current->next;
        current->next->prev = current->prev;
        delete current;
        size--;
        return data;
    }
    
    bool remove(const T& data) {
        Node<T>* current = head;
        while (current != nullptr) {
            if (current->data == data) {
                if (current == head) {
                    removeFirst();
                } else if (current == tail) {
                    removeLast();
                } else {
                    current->prev->next = current->next;
                    current->next->prev = current->prev;
                    delete current;
                    size--;
                }
                return true;
            }
            current = current->next;
        }
        return false;
    }
    
    int indexOf(const T& data) const {
        Node<T>* current = head;
        int index = 0;
        while (current != nullptr) {
            if (current->data == data) {
                return index;
            }
            current = current->next;
            index++;
        }
        return -1;
    }
    
    T get(size_t index) const {
        if (index >= size) {
            throw std::out_of_range("Index out of range");
        }
        
        Node<T>* current;
        
        // Choose direction based on which is closer
        if (index <= size / 2) {
            current = head;
            for (size_t i = 0; i < index; i++) {
                current = current->next;
            }
        } else {
            current = tail;
            for (size_t i = 0; i < size - index - 1; i++) {
                current = current->prev;
            }
        }
        
        return current->data;
    }
    
    T operator[](size_t index) const {
        return get(index);
    }
    
    bool contains(const T& data) const {
        return indexOf(data) != -1;
    }
    
    std::vector<T> toVector() const {
        std::vector<T> result;
        Node<T>* current = head;
        while (current != nullptr) {
            result.push_back(current->data);
            current = current->next;
        }
        return result;
    }
    
    std::vector<T> toVectorReverse() const {
        std::vector<T> result;
        Node<T>* current = tail;
        while (current != nullptr) {
            result.push_back(current->data);
            current = current->prev;
        }
        return result;
    }
    
    void print() const {
        printForward();
    }
    
    void printForward() const {
        if (head == nullptr) {
            std::cout << "[]" << std::endl;
            return;
        }
        
        Node<T>* current = head;
        while (current != nullptr) {
            std::cout << current->data;
            if (current->next != nullptr) {
                std::cout << " <-> ";
            }
            current = current->next;
        }
        std::cout << std::endl;
    }
    
    void printBackward() const {
        if (tail == nullptr) {
            std::cout << "[]" << std::endl;
            return;
        }
        
        Node<T>* current = tail;
        while (current != nullptr) {
            std::cout << current->data;
            if (current->prev != nullptr) {
                std::cout << " <-> ";
            }
            current = current->prev;
        }
        std::cout << std::endl;
    }
};

int main() {
    DoublyLinkedList<int> dll;
    
    // Test append
    for (int i = 0; i < 5; i++) {
        dll.append(i * 10);
    }
    std::cout << "After appending 0-40: ";
    dll.print();
    
    // Test prepend
    dll.prepend(-10);
    std::cout << "After prepending -10: ";
    dll.print();
    
    // Test insert
    dll.insert(2, 99);
    std::cout << "After inserting 99 at index 2: ";
    dll.print();
    
    // Test removal
    int removed = dll.removeFirst();
    std::cout << "Removed first element " << removed << ": ";
    dll.print();
    
    removed = dll.removeLast();
    std::cout << "Removed last element " << removed << ": ";
    dll.print();
    
    // Test bidirectional traversal
    std::cout << "Forward: ";
    dll.printForward();
    std::cout << "Backward: ";
    dll.printBackward();
    
    // Test optimized access
    std::cout << "Element at index 1: " << dll.get(1) << std::endl;
    std::cout << "Element at index " << (dll.getSize() - 1) << ": " << dll.get(dll.getSize() - 1) << std::endl;
    
    // Print as vectors
    auto vec = dll.toVector();
    std::cout << "List as vector: [";
    for (size_t i = 0; i < vec.size(); i++) {
        std::cout << vec[i];
        if (i < vec.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    auto vecReverse = dll.toVectorReverse();
    std::cout << "List reversed: [";
    for (size_t i = 0; i < vecReverse.size(); i++) {
        std::cout << vecReverse[i];
        if (i < vecReverse.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    std::cout << "Length: " << dll.getSize() << std::endl;
    
    return 0;
}
```