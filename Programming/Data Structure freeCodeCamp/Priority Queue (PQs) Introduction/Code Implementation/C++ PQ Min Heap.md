---
Created: 2025-08-12T06:50
---
### C++ — PriorityQueue.cpp

```C++
\#include <iostream>
\#include <vector>
\#include <queue>
\#include <stdexcept>
\#include <string>
\#include <utility>

// Priority item structure for custom priority queue
template<typename T>
struct PriorityItem {
    T item;
    double priority;
    int insertionOrder;
    
    PriorityItem(T i, double p, int order) : item(i), priority(p), insertionOrder(order) {}
    
    // For min-heap behavior (lower priority number = higher actual priority)
    bool operator>(const PriorityItem& other) const {
        if (priority != other.priority)
            return priority > other.priority;
        return insertionOrder > other.insertionOrder; // Maintain insertion order for ties
    }
};

// Priority Queue using STL priority_queue (min-heap)
template<typename T>
class PriorityQueueMinHeap {
private:
    std::priority_queue<PriorityItem<T>, std::vector<PriorityItem<T>>, std::greater<PriorityItem<T>>> pq;
    int insertionCounter;
```

```C++
public:
    MinHeap() {}
    
    void insert(T key) {
        heap.push_back(key);
        heapifyUp(heap.size() - 1);
    }
    
    T extractMin() {
        if (heap.empty())
            throw std::runtime_error("Heap is empty");
        
        if (heap.size() == 1) {
            T result = heap[0];
            heap.pop_back();
            return result;
        }
        
        T root = heap[0];
        heap[0] = heap.back();
        heap.pop_back();
        heapifyDown(0);
        return root;
    }
    
    T peek() const {
        if (heap.empty())
            throw std::runtime_error("Heap is empty");
        return heap[0];
    }
    
    size_t size() const {
        return heap.size();
    }
    
    bool isEmpty() const {
        return heap.empty();
    }
    
    void buildHeap(const std::vector<T>& arr) {
        heap = arr;
        for (int i = heap.size() / 2 - 1; i >= 0; i--) {
            heapifyDown(i);
        }
    }
    
    void printHeap() const {
        std::cout << "Heap: [";
        for (size_t i = 0; i < heap.size(); i++) {
            std::cout << heap[i];
            if (i < heap.size() - 1) std::cout << ", ";
        }
        std::cout << "]" << std::endl;
    }
};
```

```C++
public:
    PriorityQueueMinHeap() : insertionCounter(0) {}
    
    void push(T item, double priority) {
        pq.push(PriorityItem<T>(item, priority, insertionCounter++));
    }
    
    T pop() {
        if (isEmpty())
            throw std::runtime_error("Priority queue is empty");
        
        T item = pq.top().item;
        pq.pop();
        return item;
    }
    
    T peek() const {
        if (isEmpty())
            throw std::runtime_error("Priority queue is empty");
        
        return pq.top().item;
    }
    
    std::pair<T, double> peekWithPriority() const {
        if (isEmpty())
            throw std::runtime_error("Priority queue is empty");
        
        const auto& top = pq.top();
        return std::make_pair(top.item, top.priority);
    }
    
    bool isEmpty() const {
        return pq.empty();
    }
    
    size_t size() const {
        return pq.size();
    }
};
```

```C++

// Manual Min Heap implementation
template<typename T>
class MinHeap {
private:
    std::vector<T> heap;
    
    int parent(int i) { return (i - 1) / 2; }
    int leftChild(int i) { return 2 * i + 1; }
    int rightChild(int i) { return 2 * i + 2; }
    
    void swap(int i, int j) {
        T temp = heap[i];
        heap[i] = heap[j];
        heap[j] = temp;
    }
    
    void heapifyUp(int i) {
        while (i != 0 && heap[parent(i)] > heap[i]) {
            swap(i, parent(i));
            i = parent(i);
        }
    }
    
    void heapifyDown(int i) {
        int smallest = i;
        int left = leftChild(i);
        int right = rightChild(i);
        
        if (left < heap.size() && heap[left] < heap[smallest])
            smallest = left;
        
        if (right < heap.size() && heap[right] < heap[smallest])
            smallest = right;
        
        if (smallest != i) {
            swap(i, smallest);
            heapifyDown(smallest);
        }
    }
    
```

  

```C++
int main() {
    std::cout << "=== Priority Queue with Min Heap ===" << std::endl;
    PriorityQueueMinHeap<std::string> pq;
    
    // Insert items with priorities (lower number = higher priority)
    std::vector<std::pair<std::string, double>> items = {
        {"Task A", 3.0},
        {"Task B", 1.0},  // Highest priority
        {"Task C", 5.0},
        {"Task D", 2.0},
        {"Task E", 1.5}
    };
    
    std::cout << "Inserting items:" << std::endl;
    for (const auto& item : items) {
        pq.push(item.first, item.second);
        std::cout << "  " << item.first << " with priority " << item.second << std::endl;
    }
    
    std::cout << "\nPriority Queue size: " << pq.size() << std::endl;
    std::cout << "Items in order of priority:" << std::endl;
    
    while (!pq.isEmpty()) {
        auto itemWithPriority = pq.peekWithPriority();
        std::string removedItem = pq.pop();
        std::cout << "  " << removedItem << " (priority: " << itemWithPriority.second << ")" << std::endl;
    }
    
    std::cout << "\n=== Manual Min Heap Implementation ===" << std::endl;
    MinHeap<double> minHeap;
    
    // Insert priorities
    std::vector<double> priorities = {10, 20, 15, 30, 40, 5, 25};
    std::cout << "Inserting priorities: [";
    for (size_t i = 0; i < priorities.size(); i++) {
        std::cout << priorities[i];
        if (i < priorities.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    for (double p : priorities) {
        minHeap.insert(p);
    }
    
    minHeap.printHeap();
    std::cout << "Min element: " << minHeap.peek() << std::endl;
    
    std::cout << "\nExtracting elements in ascending order:" << std::endl;
    while (!minHeap.isEmpty()) {
        std::cout << "Extracted: " << minHeap.extractMin() << std::endl;
    }
    
    // Build heap from array
    std::cout << "\n=== Build Heap from Array ===" << std::endl;
    std::vector<double> arr = {50, 30, 70, 20, 40, 60, 80};
    std::cout << "Building heap from array: [";
    for (size_t i = 0; i < arr.size(); i++) {
        std::cout << arr[i];
        if (i < arr.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    minHeap.buildHeap(arr);
    minHeap.printHeap();
    
    // Demonstrate with integer min heap
    std::cout << "\n=== Integer Min Heap Example ===" << std::endl;
    MinHeap<int> intHeap;
    std::vector<int> intValues = {64, 34, 25, 12, 22, 11, 90};
    
    std::cout << "Inserting integers: [";
    for (size_t i = 0; i < intValues.size(); i++) {
        std::cout << intValues[i];
        if (i < intValues.size() - 1) std::cout << ", ";
        intHeap.insert(intValues[i]);
    }
    std::cout << "]" << std::endl;
    
    intHeap.printHeap();
    std::cout << "Extracting in sorted order: ";
    while (!intHeap.isEmpty()) {
        std::cout << intHeap.extractMin();
        if (!intHeap.isEmpty()) std::cout << " < ";
    }
    std::cout << std::endl;
    
    return 0;
}
```