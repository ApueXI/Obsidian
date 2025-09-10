---
Created: 2025-08-12T06:50
---
### C# — PriorityQueue.cs

```C#
using System;
using System.Collections.Generic;
using System.Linq;

// Priority Queue item structure
public class PriorityItem<T> : IComparable<PriorityItem<T>>
{
    public T Item { get; set; }
    public double Priority { get; set; }
    public int InsertionOrder { get; set; }
    
    public PriorityItem(T item, double priority, int insertionOrder)
    {
        Item = item;
        Priority = priority;
        InsertionOrder = insertionOrder;
    }
    
    public int CompareTo(PriorityItem<T> other)
    {
        if (other == null) return 1;
        
        // Compare by priority first (lower number = higher priority)
        int priorityComparison = Priority.CompareTo(other.Priority);
        if (priorityComparison != 0)
            return priorityComparison;
        
        // If priorities are equal, compare by insertion order for stability
        return InsertionOrder.CompareTo(other.InsertionOrder);
    }
}
```

```C#

// Priority Queue using Min Heap
public class PriorityQueueMinHeap<T>
{
    private MinHeap<PriorityItem<T>> heap;
    private int insertionCounter;
    
    public PriorityQueueMinHeap()
    {
        heap = new MinHeap<PriorityItem<T>>();
        insertionCounter = 0;
    }
    
    public void Push(T item, double priority)
    {
        var priorityItem = new PriorityItem<T>(item, priority, insertionCounter++);
        heap.Insert(priorityItem);
    }
    
    public T Pop()
    {
        if (IsEmpty)
            throw new InvalidOperationException("Priority queue is empty");
        
        return heap.ExtractMin().Item;
    }
    
    public T Peek()
    {
        if (IsEmpty)
            throw new InvalidOperationException("Priority queue is empty");
        
        return heap.Peek().Item;
    }
    
    public (T Item, double Priority) PeekWithPriority()
    {
        if (IsEmpty)
            throw new InvalidOperationException("Priority queue is empty");
        
        var priorityItem = heap.Peek();
        return (priorityItem.Item, priorityItem.Priority);
    }
    
    public bool IsEmpty => heap.IsEmpty;
    public int Size => heap.Size;
}
```

```C#

// Manual Min Heap implementation
public class MinHeap<T> where T : IComparable<T>
{
    private List<T> heap;
    
    public MinHeap()
    {
        heap = new List<T>();
    }
    
    private int Parent(int i) => (i - 1) / 2;
    private int LeftChild(int i) => 2 * i + 1;
    private int RightChild(int i) => 2 * i + 2;
    
    private void Swap(int i, int j)
    {
        T temp = heap[i];
        heap[i] = heap[j];
        heap[j] = temp;
    }
    
    public void Insert(T key)
    {
        heap.Add(key);
        HeapifyUp(heap.Count - 1);
    }
    
    private void HeapifyUp(int i)
    {
        while (i != 0 && heap[Parent(i)].CompareTo(heap[i]) > 0)
        {
            Swap(i, Parent(i));
            i = Parent(i);
        }
    }
    
    public T ExtractMin()
    {
        if (heap.Count == 0)
            throw new InvalidOperationException("Heap is empty");
        
        if (heap.Count == 1)
        {
            T result = heap[0];
            heap.RemoveAt(0);
            return result;
        }
        
        T root = heap[0];
        heap[0] = heap[heap.Count - 1];
        heap.RemoveAt(heap.Count - 1);
        HeapifyDown(0);
        return root;
    }
    
    private void HeapifyDown(int i)
    {
        int smallest = i;
        int left = LeftChild(i);
        int right = RightChild(i);
        
        if (left < heap.Count && heap[left].CompareTo(heap[smallest]) < 0)
            smallest = left;
        
        if (right < heap.Count && heap[right].CompareTo(heap[smallest]) < 0)
            smallest = right;
        
        if (smallest != i)
        {
            Swap(i, smallest);
            HeapifyDown(smallest);
        }
    }
    
    public T Peek()
    {
        if (heap.Count == 0)
            throw new InvalidOperationException("Heap is empty");
        return heap[0];
    }
    
    public int Size => heap.Count;
    public bool IsEmpty => heap.Count == 0;
    
    public void PrintHeap()
    {
        Console.WriteLine($"Heap: [{string.Join(", ", heap)}]");
    }
    
    public void BuildHeap(T[] arr)
    {
        heap = new List<T>(arr);
        for (int i = heap.Count / 2 - 1; i >= 0; i--)
        {
            HeapifyDown(i);
        }
    }
}
```

```C#

// Example usage
class Program
{
    static void Main()
    {
        Console.WriteLine("=== Priority Queue with Min Heap ===");
        var pq = new PriorityQueueMinHeap<string>();
        
        // Insert items with priorities (lower number = higher priority)
        var items = new[]
        {
            ("Task A", 3.0),
            ("Task B", 1.0),  // Highest priority
            ("Task C", 5.0),
            ("Task D", 2.0),
            ("Task E", 1.5)
        };
        
        Console.WriteLine("Inserting items:");
        foreach (var (item, priority) in items)
        {
            pq.Push(item, priority);
            Console.WriteLine($"  {item} with priority {priority}");
        }
        
        Console.WriteLine($"\nPriority Queue size: {pq.Size}");
        Console.WriteLine("Items in order of priority:");
        
        while (!pq.IsEmpty)
        {
            var (item, priority) = pq.PeekWithPriority();
            var removedItem = pq.Pop();
            Console.WriteLine($"  {removedItem} (priority: {priority})");
        }
        
        Console.WriteLine("\n=== Manual Min Heap Implementation ===");
        var minHeap = new MinHeap<double>();
        
        // Insert priorities
        double[] priorities = {10, 20, 15, 30, 40, 5, 25};
        Console.WriteLine($"Inserting priorities: [{string.Join(", ", priorities)}]");
        foreach (double p in priorities)
        {
            minHeap.Insert(p);
        }
        
        minHeap.PrintHeap();
        Console.WriteLine($"Min element: {minHeap.Peek()}");
        
        Console.WriteLine("\nExtracting elements in ascending order:");
        while (!minHeap.IsEmpty)
        {
            Console.WriteLine($"Extracted: {minHeap.ExtractMin()}");
        }
        
        // Build heap from array
        Console.WriteLine("\n=== Build Heap from Array ===");
        double[] arr = {50, 30, 70, 20, 40, 60, 80};
        Console.WriteLine($"Building heap from array: [{string.Join(", ", arr)}]");
        minHeap.BuildHeap(arr);
        minHeap.PrintHeap();
        
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```