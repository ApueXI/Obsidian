---
Created: 2025-08-12T06:56
---
### ⚙️ C# (Max-Heap Heapify)

```C#
using System;
using System.Collections.Generic;
using System.Linq;

public class MaxHeapify<T> where T : IComparable<T>
{
    private List<T> heap;
    
    public MaxHeapify()
    {
        heap = new List<T>();
    }
    
    public MaxHeapify(T[] array)
    {
        heap = new List<T>(array);
        BuildMaxHeap();
    }
    
    // Index helper methods
    private int ParentIndex(int i) => (i - 1) / 2;
    private int LeftChildIndex(int i) => 2 * i + 1;
    private int RightChildIndex(int i) => 2 * i + 2;
    
    // Validation helper methods
    private bool HasParent(int i) => i > 0;
    private bool HasLeftChild(int i) => LeftChildIndex(i) < heap.Count;
    private bool HasRightChild(int i) => RightChildIndex(i) < heap.Count;
    
    private void Swap(int i, int j)
    {
        Console.WriteLine($"  Swapping {heap[i]} at index {i} with {heap[j]} at index {j}");
        T temp = heap[i];
        heap[i] = heap[j];
        heap[j] = temp;
    }
    
    /// <summary>
    /// Heapify downward from index i to maintain max heap property.
    /// Used after removing root or when building a heap.
    /// </summary>
    public void MaxHeapifyDown(int i)
    {
        Console.WriteLine($"Max heapifying down from index {i} (value: {heap[i]})");
        
        int largest = i;
        int left = LeftChildIndex(i);
        int right = RightChildIndex(i);
        
        // Find the largest among current node, left child, and right child
        if (left < heap.Count && heap[left].CompareTo(heap[largest]) > 0)
        {
            largest = left;
            Console.WriteLine($"  Left child {heap[left]} is larger than {heap[i]}");
        }
        
        if (right < heap.Count && heap[right].CompareTo(heap[largest]) > 0)
        {
            largest = right;
            Console.WriteLine($"  Right child {heap[right]} is larger than current largest");
        }
        
        // If largest is not the current node, swap and continue heapifying
        if (largest != i)
        {
            Swap(i, largest);
            MaxHeapifyDown(largest);
        }
        else
        {
            Console.WriteLine($"  Node at index {i} is in correct position");
        }
    }
    
    /// <summary>
    /// Heapify upward from index i to maintain max heap property.
    /// Used when inserting a new element.
    /// </summary>
    public void MaxHeapifyUp(int i)
    {
        Console.WriteLine($"Max heapifying up from index {i} (value: {heap[i]})");
        
        if (!HasParent(i))
        {
            Console.WriteLine("  Reached root, heapify up complete");
            return;
        }
        
        int parentIdx = ParentIndex(i);
        
        // If current node is larger than parent, swap and continue
        if (heap[i].CompareTo(heap[parentIdx]) > 0)
        {
            Console.WriteLine($"  {heap[i]} is larger than parent {heap[parentIdx]}");
            Swap(i, parentIdx);
            MaxHeapifyUp(parentIdx);
        }
        else
        {
            Console.WriteLine($"  Node at index {i} is in correct position relative to parent");
        }
    }
    
    /// <summary>
    /// Insert a new value into the max heap
    /// </summary>
    public void Insert(T value)
    {
        Console.WriteLine($"\nInserting {value} into heap");
        heap.Add(value);
        Console.WriteLine($"Added {value} at index {heap.Count - 1}");
        Console.WriteLine($"Heap before heapify up: [{string.Join(", ", heap)}]");
        
        // Heapify up to maintain max heap property
        MaxHeapifyUp(heap.Count - 1);
        Console.WriteLine($"Heap after insertion: [{string.Join(", ", heap)}]");
    }
    
    /// <summary>
    /// Remove and return the maximum element (root)
    /// </summary>
    public T ExtractMax()
    {
        if (heap.Count == 0)
            throw new InvalidOperationException("Cannot extract from empty heap");
        
        if (heap.Count == 1)
        {
            T result = heap[0];
            heap.RemoveAt(0);
            return result;
        }
        
        Console.WriteLine($"\nExtracting maximum: {heap[0]}");
        T maxValue = heap[0];
        
        // Move last element to root
        T lastElement = heap[heap.Count - 1];
        heap[0] = lastElement;
        heap.RemoveAt(heap.Count - 1);
        Console.WriteLine($"Moved last element {lastElement} to root");
        Console.WriteLine($"Heap before heapify down: [{string.Join(", ", heap)}]");
        
        // Heapify down to maintain max heap property
        if (heap.Count > 0)
            MaxHeapifyDown(0);
        
        Console.WriteLine($"Heap after extraction: [{string.Join(", ", heap)}]");
        return maxValue;
    }
    
    /// <summary>
    /// Build a max heap from an unordered array using heapify
    /// </summary>
    public void BuildMaxHeap()
    {
        Console.WriteLine($"\nBuilding max heap from array: [{string.Join(", ", heap)}]");
        
        // Start from the last non-leaf node
        int startIdx = heap.Count / 2 - 1;
        Console.WriteLine($"Starting from index {startIdx} (last non-leaf node)");
        
        for (int i = startIdx; i >= 0; i--)
        {
            Console.WriteLine($"\nMax heapifying subtree rooted at index {i}");
            MaxHeapifyDown(i);
        }
        
        Console.WriteLine($"Max heap built: [{string.Join(", ", heap)}]");
    }
    
    /// <summary>
    /// Return the maximum element without removing it
    /// </summary>
    public T Peek()
    {
        if (heap.Count == 0)
            throw new InvalidOperationException("Heap is empty");
        return heap[0];
    }
    
    public int Size => heap.Count;
    public bool IsEmpty => heap.Count == 0;
    
    /// <summary>
    /// Check if the current array satisfies max heap property
    /// </summary>
    public bool IsValidMaxHeap()
    {
        for (int i = 0; i < heap.Count; i++)
        {
            int left = LeftChildIndex(i);
            int right = RightChildIndex(i);
            
            // Check left child
            if (left < heap.Count && heap[i].CompareTo(heap[left]) < 0)
                return false;
            
            // Check right child
            if (right < heap.Count && heap[i].CompareTo(heap[right]) < 0)
                return false;
        }
        
        return true;
    }
    
    /// <summary>
    /// Print heap in tree structure
    /// </summary>
    public void PrintHeapStructure()
    {
        if (heap.Count == 0)
        {
            Console.WriteLine("Empty heap");
            return;
        }
        
        Console.WriteLine("\nHeap structure:");
        PrintHeapRecursive(0, 0);
    }
    
    private void PrintHeapRecursive(int index, int depth)
    {
        if (index >= heap.Count)
            return;
        
        // Print right subtree first (for better visualization)
        int right = RightChildIndex(index);
        if (right < heap.Count)
            PrintHeapRecursive(right, depth + 1);
        
        // Print current node
        Console.WriteLine(new string(' ', depth * 4) + $"└── {heap[index]} (idx: {index})");
        
        // Print left subtree
        int left = LeftChildIndex(index);
        if (left < heap.Count)
            PrintHeapRecursive(left, depth + 1);
    }
    
    public void PrintHeap()
    {
        Console.WriteLine($"Heap: [{string.Join(", ", heap)}]");
    }
    
    /// <summary>
    /// Perform heap sort returning elements in descending order
    /// </summary>
    public T[] HeapSort()
    {
        Console.WriteLine($"\nPerforming heap sort on: [{string.Join(", ", heap)}]");
        var originalHeap = new List<T>(heap);
        var sortedArray = new List<T>();
        
        while (!IsEmpty)
        {
            sortedArray.Add(ExtractMax());
        }
        
        // Restore original heap
        heap = originalHeap;
        BuildMaxHeap();
        
        return sortedArray.ToArray();
    }
    
    // Get heap array for external access
    public T[] GetHeap() => heap.ToArray();
    
    // Set heap manually (for demonstration purposes)
    public void SetHeap(T[] newHeap)
    {
        heap = new List<T>(newHeap);
    }
}
```

```C#
// Example program demonstrating max heapify operations
class Program
{
    static void Main()
    {
        Console.WriteLine("=" + new string('=', 59));
        Console.WriteLine("MAX HEAPIFY OPERATIONS DEMONSTRATION");
        Console.WriteLine("=" + new string('=', 59));
        
        // Demonstration 1: Building heap from array
        Console.WriteLine("\n1. BUILDING MAX HEAP FROM UNORDERED ARRAY");
        Console.WriteLine(new string('-', 50));
        int[] arr = {4, 1, 3, 2, 16, 9, 10, 14, 8, 7};
        Console.WriteLine($"Original array: [{string.Join(", ", arr)}]");
        
        var heap = new MaxHeapify<int>(arr);
        heap.PrintHeapStructure();
        Console.WriteLine($"Is valid max heap: {heap.IsValidMaxHeap()}");
        
        // Demonstration 2: Inserting elements
        Console.WriteLine("\n\n2. INSERTING ELEMENTS");
        Console.WriteLine(new string('-', 50));
        var heap2 = new MaxHeapify<int>();
        int[] elements = {5, 3, 8, 1, 6, 2, 7, 15, 12};
        
        foreach (int element in elements)
        {
            heap2.Insert(element);
            heap2.PrintHeapStructure();
            Console.WriteLine($"Is valid max heap: {heap2.IsValidMaxHeap()}");
            Console.WriteLine();
        }
        
        // Demonstration 3: Extracting maximum elements
        Console.WriteLine("\n\n3. EXTRACTING MAXIMUM ELEMENTS");
        Console.WriteLine(new string('-', 50));
        heap2.PrintHeap();
        
        var extractionResults = new List<int>();
        while (!heap2.IsEmpty)
        {
            int maxVal = heap2.ExtractMax();
            extractionResults.Add(maxVal);
            Console.WriteLine($"Extracted maximum: {maxVal}");
            if (!heap2.IsEmpty)
            {
                heap2.PrintHeapStructure();
                Console.WriteLine($"Is valid max heap: {heap2.IsValidMaxHeap()}");
            }
            Console.WriteLine();
        }
        
        Console.WriteLine($"Elements extracted in descending order: [{string.Join(", ", extractionResults)}]");
        
        // Demonstration 4: Step-by-step heapify down
        Console.WriteLine("\n\n4. DETAILED MAX HEAPIFY DOWN EXAMPLE");
        Console.WriteLine(new string('-', 50));
        var heap3 = new MaxHeapify<int>();
        int[] violatingHeap = {3, 16, 10, 14, 8, 9, 7}; // Root 3 is smaller than children
        heap3.SetHeap(violatingHeap);
        
        Console.WriteLine($"Heap with violation: [{string.Join(", ", violatingHeap)}]");
        Console.WriteLine($"Is valid max heap: {heap3.IsValidMaxHeap()}");
        
        heap3.PrintHeapStructure();
        Console.WriteLine("\nFixing with max heapify down from root:");
        heap3.MaxHeapifyDown(0);
        heap3.PrintHeapStructure();
        Console.WriteLine($"Is valid max heap: {heap3.IsValidMaxHeap()}");
        
        // Demonstration 5: Heap sort using max heapify
        Console.WriteLine("\n\n5. HEAP SORT USING MAX HEAPIFY");
        Console.WriteLine(new string('-', 50));
        int[] arrToSort = {64, 34, 25, 12, 22, 11, 90};
        Console.WriteLine($"Array to sort: [{string.Join(", ", arrToSort)}]");
        
        var heap4 = new MaxHeapify<int>(arrToSort);
        int[] sortedDesc = heap4.HeapSort();
        
        Console.WriteLine($"Sorted in descending order: [{string.Join(", ", sortedDesc)}]");
        Console.WriteLine($"Sorted in ascending order: [{string.Join(", ", sortedDesc.Reverse())}]");
        
        // Demonstration 6: Working with different data types
        Console.WriteLine("\n\n6. MAX HEAPIFY WITH DIFFERENT DATA TYPES");
        Console.WriteLine(new string('-', 50));
        
        // Character heap
        Console.WriteLine("Character Max Heap:");
        var charHeap = new MaxHeapify<char>();
        char[] chars = {'d', 'b', 'f', 'a', 'e', 'c', 'z', 'g'};
        
        foreach (char c in chars)
        {
            Console.WriteLine($"Inserting: {c}");
            charHeap.Insert(c);
        }
        
        Console.WriteLine("Final character heap:");
        charHeap.PrintHeap();
        charHeap.PrintHeapStructure();
        
        Console.WriteLine("\nExtracting characters in descending order:");
        while (!charHeap.IsEmpty)
        {
            Console.Write($"{charHeap.ExtractMax()} ");
        }
        Console.WriteLine();
        
        // Double heap
        Console.WriteLine("\nDouble Max Heap:");
        var doubleHeap = new MaxHeapify<double>();
        double[] doubles = {3.7, 1.2, 5.8, 2.1, 4.3, 0.9, 6.5};
        
        foreach (double d in doubles)
        {
            doubleHeap.Insert(d);
        }
        
        Console.WriteLine("Final double heap:");
        doubleHeap.PrintHeap();
        
        Console.WriteLine("Extracting in descending order:");
        while (!doubleHeap.IsEmpty)
        {
            Console.Write($"{doubleHeap.ExtractMax():F1} ");
        }
        Console.WriteLine();
        
        // Demonstration 7: Priority Queue Simulation
        Console.WriteLine("\n\n7. PRIORITY QUEUE SIMULATION (MAX PRIORITY)");
        Console.WriteLine(new string('-', 50));
        var priorityQueue = new MaxHeapify<int>();
        
        var tasks = new (string task, int priority)[]
        {
            ("Low Priority Task", 1),
            ("Medium Priority Task", 5),
            ("High Priority Task", 10),
            ("Critical Task", 15),
            ("Normal Task", 3),
            ("Urgent Task", 12)
        };
        
        Console.WriteLine("Adding tasks to priority queue:");
        foreach (var (task, priority) in tasks)
        {
            Console.WriteLine($"Adding: {task} (Priority: {priority})");
            priorityQueue.Insert(priority);
        }
        
        priorityQueue.PrintHeapStructure();
        
        Console.WriteLine("\nProcessing tasks by priority (highest first):");
        var sortedTasks = tasks.OrderByDescending(t => t.priority).ToArray();
        int taskIndex = 0;
        
        while (!priorityQueue.IsEmpty)
        {
            int maxPriority = priorityQueue.ExtractMax();
            if (taskIndex < sortedTasks.Length)
            {
                Console.WriteLine($"Processing: {sortedTasks[taskIndex].task} (Priority: {maxPriority})");
                taskIndex++;
            }
        }
        
        // Demonstration 8: Building heap vs inserting one by one
        Console.WriteLine("\n\n8. BUILDING HEAP VS INSERTING ONE BY ONE");
        Console.WriteLine(new string('-', 50));
        int[] testArray = {45, 23, 78, 12, 67, 34, 89, 56};
        
        // Method 1: Build heap from array (O(n))
        Console.WriteLine("Method 1: Build heap from array");
        var heapBuilt = new MaxHeapify<int>(testArray);
        Console.WriteLine($"Final heap: [{string.Join(", ", heapBuilt.GetHeap())}]");
        
        // Method 2: Insert one by one (O(n log n))
        Console.WriteLine("\nMethod 2: Insert elements one by one");
        var heapInserted = new MaxHeapify<int>();
        foreach (int element in testArray)
        {
            heapInserted.Insert(element);
        }
        Console.WriteLine($"Final heap: [{string.Join(", ", heapInserted.GetHeap())}]");
        
        Console.WriteLine($"\nBoth methods produce valid max heaps:");
        Console.WriteLine($"Built heap valid: {heapBuilt.IsValidMaxHeap()}");
        Console.WriteLine($"Inserted heap valid: {heapInserted.IsValidMaxHeap()}");
        
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

PQ Max Heap