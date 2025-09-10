---
Created: 2025-08-12T06:56
---
### 🖥️ C++ (Max-Heap Heapify)

```C++
\#include <iostream>
\#include <vector>
\#include <stdexcept>
\#include <string>
\#include <algorithm>
\#include <iomanip>

template<typename T>
class MaxHeapify {
private:
    std::vector<T> heap;
    
    // Index helper methods
    int parentIndex(int i) { return (i - 1) / 2; }
    int leftChildIndex(int i) { return 2 * i + 1; }
    int rightChildIndex(int i) { return 2 * i + 2; }
    
    // Validation helper methods
    bool hasParent(int i) { return i > 0; }
    bool hasLeftChild(int i) { return leftChildIndex(i) < heap.size(); }
    bool hasRightChild(int i) { return rightChildIndex(i) < heap.size(); }
    
    void swap(int i, int j) {
        std::cout << "  Swapping " << heap[i] << " at index " << i 
                  << " with " << heap[j] << " at index " << j << std::endl;
        T temp = heap[i];
        heap[i] = heap[j];
        heap[j] = temp;
    }
    
    void printHeapRecursive(int index, int depth) {
        if (index >= heap.size())
            return;
        
        // Print right subtree first (for better visualization)
        int right = rightChildIndex(index);
        if (right < heap.size())
            printHeapRecursive(right, depth + 1);
        
        // Print current node
        for (int i = 0; i < depth; i++) std::cout << "    ";
        std::cout << "└── " << heap[index] << " (idx: " << index << ")" << std::endl;
        
        // Print left subtree
        int left = leftChildIndex(index);
        if (left < heap.size())
            printHeapRecursive(left, depth + 1);
    }
    
```

```C++

// Helper function to print array
template<typename T>
void printArray(const std::vector<T>& arr, const std::string& label) {
    std::cout << label << ": [";
    for (size_t i = 0; i < arr.size(); i++) {
        std::cout << arr[i];
        if (i < arr.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
}
```

```C++
public:
    MaxHeapify() {}
    
    MaxHeapify(const std::vector<T>& array) {
        heap = array;
        buildMaxHeap();
    }
    
    /**
     * Max heapify downward from index i to maintain max heap property.
     * Used after removing root or when building a heap.
     */
    void maxHeapifyDown(int i) {
        std::cout << "Max heapifying down from index " << i << " (value: " << heap[i] << ")" << std::endl;
        
        int largest = i;
        int left = leftChildIndex(i);
        int right = rightChildIndex(i);
        
        // Find the largest among current node, left child, and right child
        if (left < heap.size() && heap[left] > heap[largest]) {
            largest = left;
            std::cout << "  Left child " << heap[left] << " is larger than " << heap[i] << std::endl;
        }
        
        if (right < heap.size() && heap[right] > heap[largest]) {
            largest = right;
            std::cout << "  Right child " << heap[right] << " is larger than current largest" << std::endl;
        }
        
        // If largest is not the current node, swap and continue heapifying
        if (largest != i) {
            swap(i, largest);
            maxHeapifyDown(largest);
        } else {
            std::cout << "  Node at index " << i << " is in correct position" << std::endl;
        }
    }
    
    /**
     * Max heapify upward from index i to maintain max heap property.
     * Used when inserting a new element.
     */
    void maxHeapifyUp(int i) {
        std::cout << "Max heapifying up from index " << i << " (value: " << heap[i] << ")" << std::endl;
        
        if (!hasParent(i)) {
            std::cout << "  Reached root, heapify up complete" << std::endl;
            return;
        }
        
        int parentIdx = parentIndex(i);
        
        // If current node is larger than parent, swap and continue
        if (heap[i] > heap[parentIdx]) {
            std::cout << "  " << heap[i] << " is larger than parent " << heap[parentIdx] << std::endl;
            swap(i, parentIdx);
            maxHeapifyUp(parentIdx);
        } else {
            std::cout << "  Node at index " << i << " is in correct position relative to parent" << std::endl;
        }
    }
    
    /**
     * Insert a new value into the max heap
     */
    void insert(T value) {
        std::cout << "\nInserting " << value << " into heap" << std::endl;
        heap.push_back(value);
        std::cout << "Added " << value << " at index " << (heap.size() - 1) << std::endl;
        std::cout << "Heap before heapify up: ";
        printHeap();
        
        // Heapify up to maintain max heap property
        maxHeapifyUp(heap.size() - 1);
        std::cout << "Heap after insertion: ";
        printHeap();
    }
    
    /**
     * Remove and return the maximum element (root)
     */
    T extractMax() {
        if (heap.empty())
            throw std::runtime_error("Cannot extract from empty heap");
        
        if (heap.size() == 1) {
            T result = heap[0];
            heap.pop_back();
            return result;
        }
        
        std::cout << "\nExtracting maximum: " << heap[0] << std::endl;
        T maxValue = heap[0];
        
        // Move last element to root
        T lastElement = heap.back();
        heap[0] = lastElement;
        heap.pop_back();
        std::cout << "Moved last element " << lastElement << " to root" << std::endl;
        std::cout << "Heap before heapify down: ";
        printHeap();
        
        // Heapify down to maintain max heap property
        if (!heap.empty())
            maxHeapifyDown(0);
        
        std::cout << "Heap after extraction: ";
        printHeap();
        return maxValue;
    }
    
    /**
     * Build a max heap from an unordered array using heapify
     */
    void buildMaxHeap() {
        std::cout << "\nBuilding max heap from array: ";
        printHeap();
        
        // Start from the last non-leaf node
        int startIdx = heap.size() / 2 - 1;
        std::cout << "Starting from index " << startIdx << " (last non-leaf node)" << std::endl;
        
        for (int i = startIdx; i >= 0; i--) {
            std::cout << "\nMax heapifying subtree rooted at index " << i << std::endl;
            maxHeapifyDown(i);
        }
        
        std::cout << "Max heap built: ";
        printHeap();
    }
    
    /**
     * Return the maximum element without removing it
     */
    T peek() const {
        if (heap.empty())
            throw std::runtime_error("Heap is empty");
        return heap[0];
    }
    
    size_t size() const { return heap.size(); }
    bool isEmpty() const { return heap.empty(); }
    
    /**
     * Check if the current array satisfies max heap property
     */
    bool isValidMaxHeap() const {
        for (size_t i = 0; i < heap.size(); i++) {
            size_t left = leftChildIndex(i);
            size_t right = rightChildIndex(i);
            
            // Check left child
            if (left < heap.size() && heap[i] < heap[left])
                return false;
            
            // Check right child
            if (right < heap.size() && heap[i] < heap[right])
                return false;
        }
        return true;
    }
    
    /**
     * Print heap in tree structure
     */
    void printHeapStructure() const {
        if (heap.empty()) {
            std::cout << "Empty heap" << std::endl;
            return;
        }
        
        std::cout << "\nHeap structure:" << std::endl;
        const_cast<MaxHeapify<T>*>(this)->printHeapRecursive(0, 0);
    }
    
    void printHeap() const {
        std::cout << "[";
        for (size_t i = 0; i < heap.size(); i++) {
            std::cout << heap[i];
            if (i < heap.size() - 1) std::cout << ", ";
        }
        std::cout << "]" << std::endl;
    }
    
    /**
     * Perform heap sort returning elements in descending order
     */
    std::vector<T> heapSort() {
        std::cout << "\nPerforming heap sort on: ";
        printHeap();
        
        std::vector<T> originalHeap = heap;
        std::vector<T> sortedArray;
        
        while (!isEmpty()) {
            sortedArray.push_back(extractMax());
        }
        
        // Restore original heap
        heap = originalHeap;
        buildMaxHeap();
        
        return sortedArray;
    }
    
    // Get heap array for external access
    const std::vector<T>& getHeap() const { return heap; }
    
    // Set heap manually (for demonstration purposes)
    void setHeap(const std::vector<T>& newHeap) { heap = newHeap; }
};

```

```C++
int main() {
    std::cout << std::string(60, '=') << std::endl;
    std::cout << "MAX HEAPIFY OPERATIONS DEMONSTRATION" << std::endl;
    std::cout << std::string(60, '=') << std::endl;
    
    // Demonstration 1: Building heap from array
    std::cout << "\n1. BUILDING MAX HEAP FROM UNORDERED ARRAY" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    std::vector<int> arr = {4, 1, 3, 2, 16, 9, 10, 14, 8, 7};
    printArray(arr, "Original array");
    
    MaxHeapify<int> heap(arr);
    heap.printHeapStructure();
    std::cout << "Is valid max heap: " << (heap.isValidMaxHeap() ? "true" : "false") << std::endl;
    
    // Demonstration 2: Inserting elements
    std::cout << "\n\n2. INSERTING ELEMENTS" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    MaxHeapify<int> heap2;
    std::vector<int> elements = {5, 3, 8, 1, 6, 2, 7, 15, 12};
    
    for (int element : elements) {
        heap2.insert(element);
        heap2.printHeapStructure();
        std::cout << "Is valid max heap: " << (heap2.isValidMaxHeap() ? "true" : "false") << std::endl;
        std::cout << std::endl;
    }
    
    // Demonstration 3: Extracting maximum elements
    std::cout << "\n\n3. EXTRACTING MAXIMUM ELEMENTS" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    std::cout << "Starting heap: ";
    heap2.printHeap();
    
    std::vector<int> extractionResults;
    while (!heap2.isEmpty()) {
        int maxVal = heap2.extractMax();
        extractionResults.push_back(maxVal);
        std::cout << "Extracted maximum: " << maxVal << std::endl;
        if (!heap2.isEmpty()) {
            heap2.printHeapStructure();
            std::cout << "Is valid max heap: " << (heap2.isValidMaxHeap() ? "true" : "false") << std::endl;
        }
        std::cout << std::endl;
    }
    
    printArray(extractionResults, "Elements extracted in descending order");
    
    // Demonstration 4: Step-by-step heapify down
    std::cout << "\n\n4. DETAILED MAX HEAPIFY DOWN EXAMPLE" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    // Create a heap that violates max heap property at root
    MaxHeapify<int> heap3;
    std::vector<int> violatingHeap = {3, 16, 10, 14, 8, 9, 7}; // Root 3 is smaller than children
    heap3.setHeap(violatingHeap);
    
    printArray(violatingHeap, "Heap with violation");
    std::cout << "Is valid max heap: " << (heap3.isValidMaxHeap() ? "true" : "false") << std::endl;
    
    heap3.printHeapStructure();
    std::cout << "\nFixing with max heapify down from root:" << std::endl;
    heap3.maxHeapifyDown(0);
    heap3.printHeapStructure();
    std::cout << "Is valid max heap: " << (heap3.isValidMaxHeap() ? "true" : "false") << std::endl;
    
    // Demonstration 5: Heap sort using max heapify
    std::cout << "\n\n5. HEAP SORT USING MAX HEAPIFY" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    std::vector<int> arrToSort = {64, 34, 25, 12, 22, 11, 90};
    printArray(arrToSort, "Array to sort");
    
    MaxHeapify<int> heap4(arrToSort);
    std::vector<int> sortedDesc = heap4.heapSort();
    
    printArray(sortedDesc, "Sorted in descending order");
    
    // Reverse for ascending order
    std::vector<int> sortedAsc = sortedDesc;
    std::reverse(sortedAsc.begin(), sortedAsc.end());
    printArray(sortedAsc, "Sorted in ascending order");
    
    // Demonstration 6: Working with different data types
    std::cout << "\n\n6. MAX HEAPIFY WITH DIFFERENT DATA TYPES" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    
    // Character heap
    std::cout << "Character Max Heap:" << std::endl;
    MaxHeapify<char> charHeap;
    std::vector<char> chars = {'d', 'b', 'f', 'a', 'e', 'c', 'z', 'g'};
    
    for (char c : chars) {
        std::cout << "Inserting: " << c << std::endl;
        charHeap.insert(c);
    }
    
    std::cout << "Final character heap: ";
    charHeap.printHeap();
    charHeap.printHeapStructure();
    
    std::cout << "\nExtracting characters in descending order: ";
    while (!charHeap.isEmpty()) {
        std::cout << charHeap.extractMax() << " ";
    }
    std::cout << std::endl;
    
    // Double heap
    std::cout << "\nDouble Max Heap:" << std::endl;
    MaxHeapify<double> doubleHeap;
    std::vector<double> doubles = {3.7, 1.2, 5.8, 2.1, 4.3, 0.9, 6.5};
    
    for (double d : doubles) {
        doubleHeap.insert(d);
    }
    
    std::cout << "Final double heap: ";
    doubleHeap.printHeap();
    
    std::cout << "Extracting in descending order: ";
    while (!doubleHeap.isEmpty()) {
        std::cout << std::fixed << std::setprecision(1) << doubleHeap.extractMax() << " ";
    }
    std::cout << std::endl;
    
    // Demonstration 7: Priority Queue Simulation
    std::cout << "\n\n7. PRIORITY QUEUE SIMULATION (MAX PRIORITY)" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    MaxHeapify<int> priorityQueue;
    
    struct Task {
        std::string name;
        int priority;
    };
    
    std::vector<Task> tasks = {
        {"Low Priority Task", 1},
        {"Medium Priority Task", 5},
        {"High Priority Task", 10},
        {"Critical Task", 15},
        {"Normal Task", 3},
        {"Urgent Task", 12}
    };
    
    std::cout << "Adding tasks to priority queue:" << std::endl;
    for (const auto& task : tasks) {
        std::cout << "Adding: " << task.name << " (Priority: " << task.priority << ")" << std::endl;
        priorityQueue.insert(task.priority);
    }
    
    priorityQueue.printHeapStructure();
    
    std::cout << "\nProcessing tasks by priority (highest first):" << std::endl;
    
    // Sort tasks by priority for display
    std::sort(tasks.begin(), tasks.end(), [](const Task& a, const Task& b) {
        return a.priority > b.priority;
    });
    
    size_t taskIndex = 0;
    while (!priorityQueue.isEmpty()) {
        int maxPriority = priorityQueue.extractMax();
        if (taskIndex < tasks.size()) {
            std::cout << "Processing: " << tasks[taskIndex].name << " (Priority: " << maxPriority << ")" << std::endl;
            taskIndex++;
        }
    }
    
    // Demonstration 8: Building heap vs inserting one by one
    std::cout << "\n\n8. BUILDING HEAP VS INSERTING ONE BY ONE" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    std::vector<int> testArray = {45, 23, 78, 12, 67, 34, 89, 56};
    
    // Method 1: Build heap from array (O(n))
    std::cout << "Method 1: Build heap from array" << std::endl;
    MaxHeapify<int> heapBuilt(testArray);
    printArray(heapBuilt.getHeap(), "Final heap");
    
    // Method 2: Insert one by one (O(n log n))
    std::cout << "\nMethod 2: Insert elements one by one" << std::endl;
    MaxHeapify<int> heapInserted;
    for (int element : testArray) {
        heapInserted.insert(element);
    }
    printArray(heapInserted.getHeap(), "Final heap");
    
    std::cout << "\nBoth methods produce valid max heaps:" << std::endl;
    std::cout << "Built heap valid: " << (heapBuilt.isValidMaxHeap() ? "true" : "false") << std::endl;
    std::cout << "Inserted heap valid: " << (heapInserted.isValidMaxHeap() ? "true" : "false") << std::endl;
    
    // Demonstration 9: Performance comparison visualization
    std::cout << "\n\n9. HEAP OPERATIONS PERFORMANCE SUMMARY" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    std::cout << "Operation           | Time Complexity | Space Complexity" << std::endl;
    std::cout << std::string(50, '-') << std::endl;
    std::cout << "Max Heapify Down    | O(log n)        | O(1)" << std::endl;
    std::cout << "Max Heapify Up      | O(log n)        | O(1)" << std::endl;
    std::cout << "Insert              | O(log n)        | O(1)" << std::endl;
    std::cout << "Extract Max         | O(log n)        | O(1)" << std::endl;
    std::cout << "Peek                | O(1)            | O(1)" << std::endl;
    std::cout << "Build Max Heap      | O(n)            | O(1)" << std::endl;
    std::cout << "Heap Sort           | O(n log n)      | O(1)" << std::endl;
    
    return 0;
}
```