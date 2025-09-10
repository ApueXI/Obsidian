---
Created: 2025-08-12T06:56
---
### 🐍 Python (Max-Heap Heapify)

```Python
class MaxHeapify:
    """Complete Max Heap implementation with detailed heapify operations"""
    
    def __init__(self, arr: Optional[List[int]] = None):
        if arr is None:
            self.heap = []
        else:
            self.heap = arr.copy()
            self.build_max_heap()
    
    def parent_index(self, i: int) -> int:
        """Get parent index of node at index i"""
        return (i - 1) // 2
    
    def left_child_index(self, i: int) -> int:
        """Get left child index of node at index i"""
        return 2 * i + 1
    
    def right_child_index(self, i: int) -> int:
        """Get right child index of node at index i"""
        return 2 * i + 2
    
    def has_parent(self, i: int) -> bool:
        """Check if node at index i has a parent"""
        return i > 0
    
    def has_left_child(self, i: int) -> bool:
        """Check if node at index i has a left child"""
        return self.left_child_index(i) < len(self.heap)
    
    def has_right_child(self, i: int) -> bool:
        """Check if node at index i has a right child"""
        return self.right_child_index(i) < len(self.heap)
    
    def swap(self, i: int, j: int) -> None:
        """Swap elements at indices i and j"""
        print(f"  Swapping {self.heap[i]} at index {i} with {self.heap[j]} at index {j}")
        self.heap[i], self.heap[j] = self.heap[j], self.heap[i]
    
    def max_heapify_down(self, i: int) -> None:
        """
        Heapify downward from index i to maintain max heap property.
        This is used after removing the root or when building a heap.
        """
        print(f"Max heapifying down from index {i} (value: {self.heap[i]})")
        
        largest = i
        left = self.left_child_index(i)
        right = self.right_child_index(i)
        
        # Find the largest among current node, left child, and right child
        if left < len(self.heap) and self.heap[left] > self.heap[largest]:
            largest = left
            print(f"  Left child {self.heap[left]} is larger than {self.heap[i]}")
        
        if right < len(self.heap) and self.heap[right] > self.heap[largest]:
            largest = right
            print(f"  Right child {self.heap[right]} is larger than current largest")
        
        # If largest is not the current node, swap and continue heapifying
        if largest != i:
            self.swap(i, largest)
            self.max_heapify_down(largest)
        else:
            print(f"  Node at index {i} is in correct position")
    
    def max_heapify_up(self, i: int) -> None:
        """
        Heapify upward from index i to maintain max heap property.
        This is used when inserting a new element.
        """
        print(f"Max heapifying up from index {i} (value: {self.heap[i]})")
        
        if not self.has_parent(i):
            print("  Reached root, heapify up complete")
            return
        
        parent_idx = self.parent_index(i)
        
        # If current node is larger than parent, swap and continue
        if self.heap[i] > self.heap[parent_idx]:
            print(f"  {self.heap[i]} is larger than parent {self.heap[parent_idx]}")
            self.swap(i, parent_idx)
            self.max_heapify_up(parent_idx)
        else:
            print(f"  Node at index {i} is in correct position relative to parent")
    
    def insert(self, value: int) -> None:
        """Insert a new value into the max heap"""
        print(f"\nInserting {value} into heap")
        self.heap.append(value)
        print(f"Added {value} at index {len(self.heap) - 1}")
        print(f"Heap before heapify up: {self.heap}")
        
        # Heapify up to maintain max heap property
        self.max_heapify_up(len(self.heap) - 1)
        print(f"Heap after insertion: {self.heap}")
    
    def extract_max(self) -> int:
        """Remove and return the maximum element (root)"""
        if len(self.heap) == 0:
            raise IndexError("Cannot extract from empty heap")
        
        if len(self.heap) == 1:
            return self.heap.pop()
        
        print(f"\nExtracting maximum: {self.heap[0]}")
        max_value = self.heap[0]
        
        # Move last element to root
        last_element = self.heap.pop()
        self.heap[0] = last_element
        print(f"Moved last element {last_element} to root")
        print(f"Heap before heapify down: {self.heap}")
        
        # Heapify down to maintain max heap property
        if len(self.heap) > 0:
            self.max_heapify_down(0)
        
        print(f"Heap after extraction: {self.heap}")
        return max_value
    
    def build_max_heap(self) -> None:
        """
        Build a max heap from an unordered array using heapify.
        Start from the last non-leaf node and heapify down.
        """
        print(f"\nBuilding max heap from array: {self.heap}")
        
        # Start from the last non-leaf node
        # Last non-leaf node is at index (n/2 - 1)
        start_idx = len(self.heap) // 2 - 1
        print(f"Starting from index {start_idx} (last non-leaf node)")
        
        for i in range(start_idx, -1, -1):
            print(f"\nMax heapifying subtree rooted at index {i}")
            self.max_heapify_down(i)
        
        print(f"Max heap built: {self.heap}")
    
    def peek(self) -> int:
        """Return the maximum element without removing it"""
        if len(self.heap) == 0:
            raise IndexError("Heap is empty")
        return self.heap[0]
    
    def size(self) -> int:
        """Return the size of the heap"""
        return len(self.heap)
    
    def is_empty(self) -> bool:
        """Check if heap is empty"""
        return len(self.heap) == 0
    
    def is_valid_max_heap(self) -> bool:
        """Check if the current array satisfies max heap property"""
        for i in range(len(self.heap)):
            left = self.left_child_index(i)
            right = self.right_child_index(i)
            
            # Check left child
            if left < len(self.heap) and self.heap[i] < self.heap[left]:
                return False
            
            # Check right child
            if right < len(self.heap) and self.heap[i] < self.heap[right]:
                return False
        
        return True
    
    def print_heap_structure(self) -> None:
        """Print heap in tree structure"""
        if not self.heap:
            print("Empty heap")
            return
        
        print("\nHeap structure:")
        self._print_heap_recursive(0, 0)
    
    def _print_heap_recursive(self, index: int, depth: int) -> None:
        """Helper method to print heap structure recursively"""
        if index >= len(self.heap):
            return
        
        # Print right subtree first (for better visualization)
        right = self.right_child_index(index)
        if right < len(self.heap):
            self._print_heap_recursive(right, depth + 1)
        
        # Print current node
        print("  " * depth + f"└── {self.heap[index]} (idx: {index})")
        
        # Print left subtree
        left = self.left_child_index(index)
        if left < len(self.heap):
            self._print_heap_recursive(left, depth + 1)
    
    def heap_sort(self) -> List[int]:
        """
        Perform heap sort on the current heap.
        Returns sorted array in descending order (largest first).
        """
        print(f"\nPerforming heap sort on: {self.heap}")
        original_heap = self.heap.copy()
        sorted_array = []
        
        while not self.is_empty():
            max_val = self.extract_max()
            sorted_array.append(max_val)
        
        # Restore original heap
        self.heap = original_heap
        self.build_max_heap()
        
        return sorted_array
```

```Python

# Example usage and demonstrations
if __name__ == "__main__":
    print("=" * 60)
    print("MAX HEAPIFY OPERATIONS DEMONSTRATION")
    print("=" * 60)
    
    # Demonstration 1: Building heap from array
    print("\n1. BUILDING MAX HEAP FROM UNORDERED ARRAY")
    print("-" * 50)
    arr = [4, 1, 3, 2, 16, 9, 10, 14, 8, 7]
    print(f"Original array: {arr}")
    
    heap = MaxHeapify(arr)
    heap.print_heap_structure()
    print(f"Is valid max heap: {heap.is_valid_max_heap()}")
    
    # Demonstration 2: Inserting elements
    print("\n\n2. INSERTING ELEMENTS")
    print("-" * 50)
    heap2 = MaxHeapify()
    elements = [5, 3, 8, 1, 6, 2, 7, 15, 12]
    
    for element in elements:
        heap2.insert(element)
        heap2.print_heap_structure()
        print(f"Is valid max heap: {heap2.is_valid_max_heap()}")
        print()
    
    # Demonstration 3: Extracting maximum elements
    print("\n\n3. EXTRACTING MAXIMUM ELEMENTS")
    print("-" * 50)
    print("Starting heap:", heap2.heap)
    
    extraction_results = []
    while not heap2.is_empty():
        max_val = heap2.extract_max()
        extraction_results.append(max_val)
        print(f"Extracted maximum: {max_val}")
        if not heap2.is_empty():
            heap2.print_heap_structure()
            print(f"Is valid max heap: {heap2.is_valid_max_heap()}")
        print()
    
    print(f"Elements extracted in descending order: {extraction_results}")
    
    # Demonstration 4: Step-by-step heapify down
    print("\n\n4. DETAILED MAX HEAPIFY DOWN EXAMPLE")
    print("-" * 50)
    # Create a heap that violates max heap property at root
    heap3 = MaxHeapify()
    heap3.heap = [3, 16, 10, 14, 8, 9, 7]  # Root 3 is smaller than children
    print(f"Heap with violation: {heap3.heap}")
    print(f"Is valid max heap: {heap3.is_valid_max_heap()}")
    
    heap3.print_heap_structure()
    print("\nFixing with max heapify down from root:")
    heap3.max_heapify_down(0)
    heap3.print_heap_structure()
    print(f"Is valid max heap: {heap3.is_valid_max_heap()}")
    
    # Demonstration 5: Heap sort using max heapify
    print("\n\n5. HEAP SORT USING MAX HEAPIFY")
    print("-" * 50)
    arr_to_sort = [64, 34, 25, 12, 22, 11, 90]
    print(f"Array to sort: {arr_to_sort}")
    
    heap4 = MaxHeapify(arr_to_sort)
    sorted_desc = heap4.heap_sort()
    
    print(f"Sorted in descending order: {sorted_desc}")
    print(f"Sorted in ascending order: {sorted_desc[::-1]}")
    
    # Demonstration 6: Priority queue simulation
    print("\n\n6. PRIORITY QUEUE SIMULATION (MAX PRIORITY)")
    print("-" * 50)
    priority_queue = MaxHeapify()
    
    # Simulate tasks with priorities
    tasks = [
        ("Low Priority Task", 1),
        ("Medium Priority Task", 5),
        ("High Priority Task", 10),
        ("Critical Task", 15),
        ("Normal Task", 3),
        ("Urgent Task", 12)
    ]
    
    print("Adding tasks to priority queue:")
    for task, priority in tasks:
        print(f"Adding: {task} (Priority: {priority})")
        priority_queue.insert(priority)
    
    priority_queue.print_heap_structure()
    
    print("\nProcessing tasks by priority (highest first):")
    task_index = 0
    original_tasks = sorted(tasks, key=lambda x: x[1], reverse=True)
    
    while not priority_queue.is_empty():
        max_priority = priority_queue.extract_max()
        # Find task with this priority
        for task, priority in tasks:
            if priority == max_priority:
                print(f"Processing: {task} (Priority: {priority})")
                break
        
    # Demonstration 7: Building heap vs inserting one by one
    print("\n\n7. BUILDING HEAP VS INSERTING ONE BY ONE")
    print("-" * 50)
    test_array = [45, 23, 78, 12, 67, 34, 89, 56]
    
    # Method 1: Build heap from array (O(n))
    print("Method 1: Build heap from array")
    heap_built = MaxHeapify(test_array)
    print("Final heap:", heap_built.heap)
    
    # Method 2: Insert one by one (O(n log n))
    print("\nMethod 2: Insert elements one by one")
    heap_inserted = MaxHeapify()
    for element in test_array:
        heap_inserted.insert(element)
    print("Final heap:", heap_inserted.heap)
    
    print(f"\nBoth methods produce valid max heaps:")
    print(f"Built heap valid: {heap_built.is_valid_max_heap()}")
    print(f"Inserted heap valid: {heap_inserted.is_valid_max_heap()}")
```