---
Created: 2025-08-12T06:50
---
### Python — PriorityQueue.py

```Python
from typing import List, Optional

class MinHeapify:
    """Complete Min Heap implementation with detailed heapify operations"""
    
    def __init__(self, arr: Optional[List[int]] = None):
        if arr is None:
            self.heap = []
        else:
            self.heap = arr.copy()
            self.build_min_heap()
    
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
    
    def min_heapify_down(self, i: int) -> None:
        """
        Heapify downward from index i to maintain min heap property.
        This is used after removing the root or when building a heap.
        """
        print(f"Heapifying down from index {i} (value: {self.heap[i]})")
        
        smallest = i
        left = self.left_child_index(i)
        right = self.right_child_index(i)
        
        # Find the smallest among current node, left child, and right child
        if left < len(self.heap) and self.heap[left] < self.heap[smallest]:
            smallest = left
            print(f"  Left child {self.heap[left]} is smaller than {self.heap[i]}")
        
        if right < len(self.heap) and self.heap[right] < self.heap[smallest]:
            smallest = right
            print(f"  Right child {self.heap[right]} is smaller than current smallest")
        
        # If smallest is not the current node, swap and continue heapifying
        if smallest != i:
            self.swap(i, smallest)
            self.min_heapify_down(smallest)
        else:
            print(f"  Node at index {i} is in correct position")
    
    def min_heapify_up(self, i: int) -> None:
        """
        Heapify upward from index i to maintain min heap property.
        This is used when inserting a new element.
        """
        print(f"Heapifying up from index {i} (value: {self.heap[i]})")
        
        if not self.has_parent(i):
            print("  Reached root, heapify up complete")
            return
        
        parent_idx = self.parent_index(i)
        
        # If current node is smaller than parent, swap and continue
        if self.heap[i] < self.heap[parent_idx]:
            print(f"  {self.heap[i]} is smaller than parent {self.heap[parent_idx]}")
            self.swap(i, parent_idx)
            self.min_heapify_up(parent_idx)
        else:
            print(f"  Node at index {i} is in correct position relative to parent")
    
    def insert(self, value: int) -> None:
        """Insert a new value into the min heap"""
        print(f"\nInserting {value} into heap")
        self.heap.append(value)
        print(f"Added {value} at index {len(self.heap) - 1}")
        print(f"Heap before heapify up: {self.heap}")
        
        # Heapify up to maintain min heap property
        self.min_heapify_up(len(self.heap) - 1)
        print(f"Heap after insertion: {self.heap}")
    
    def extract_min(self) -> int:
        """Remove and return the minimum element (root)"""
        if len(self.heap) == 0:
            raise IndexError("Cannot extract from empty heap")
        
        if len(self.heap) == 1:
            return self.heap.pop()
        
        print(f"\nExtracting minimum: {self.heap[0]}")
        min_value = self.heap[0]
        
        # Move last element to root
        last_element = self.heap.pop()
        self.heap[0] = last_element
        print(f"Moved last element {last_element} to root")
        print(f"Heap before heapify down: {self.heap}")
        
        # Heapify down to maintain min heap property
        if len(self.heap) > 0:
            self.min_heapify_down(0)
        
        print(f"Heap after extraction: {self.heap}")
        return min_value
    
    def build_min_heap(self) -> None:
        """
        Build a min heap from an unordered array using heapify.
        Start from the last non-leaf node and heapify down.
        """
        print(f"\nBuilding min heap from array: {self.heap}")
        
        # Start from the last non-leaf node
        # Last non-leaf node is at index (n/2 - 1)
        start_idx = len(self.heap) // 2 - 1
        print(f"Starting from index {start_idx} (last non-leaf node)")
        
        for i in range(start_idx, -1, -1):
            print(f"\nHeapifying subtree rooted at index {i}")
            self.min_heapify_down(i)
        
        print(f"Min heap built: {self.heap}")
    
    def peek(self) -> int:
        """Return the minimum element without removing it"""
        if len(self.heap) == 0:
            raise IndexError("Heap is empty")
        return self.heap[0]
    
    def size(self) -> int:
        """Return the size of the heap"""
        return len(self.heap)
    
    def is_empty(self) -> bool:
        """Check if heap is empty"""
        return len(self.heap) == 0
    
    def is_valid_min_heap(self) -> bool:
        """Check if the current array satisfies min heap property"""
        for i in range(len(self.heap)):
            left = self.left_child_index(i)
            right = self.right_child_index(i)
            
            # Check left child
            if left < len(self.heap) and self.heap[i] > self.heap[left]:
                return False
            
            # Check right child
            if right < len(self.heap) and self.heap[i] > self.heap[right]:
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
```

```Python
from typing import List, Optional

# Example usage and demonstrations
if __name__ == "__main__":
    print("=" * 60)
    print("MIN HEAPIFY OPERATIONS DEMONSTRATION")
    print("=" * 60)
    
    # Demonstration 1: Building heap from array
    print("\n1. BUILDING MIN HEAP FROM UNORDERED ARRAY")
    print("-" * 50)
    arr = [4, 1, 3, 2, 16, 9, 10, 14, 8, 7]
    print(f"Original array: {arr}")
    
    heap = MinHeapify(arr)
    heap.print_heap_structure()
    print(f"Is valid min heap: {heap.is_valid_min_heap()}")
    
    # Demonstration 2: Inserting elements
    print("\n\n2. INSERTING ELEMENTS")
    print("-" * 50)
    heap2 = MinHeapify()
    elements = [5, 3, 8, 1, 6, 2, 7]
    
    for element in elements:
        heap2.insert(element)
        heap2.print_heap_structure()
        print(f"Is valid min heap: {heap2.is_valid_min_heap()}")
        print()
    
    # Demonstration 3: Extracting minimum elements
    print("\n\n3. EXTRACTING MINIMUM ELEMENTS")
    print("-" * 50)
    print("Starting heap:", heap2.heap)
    
    while not heap2.is_empty():
        min_val = heap2.extract_min()
        print(f"Extracted minimum: {min_val}")
        if not heap2.is_empty():
            heap2.print_heap_structure()
            print(f"Is valid min heap: {heap2.is_valid_min_heap()}")
        print()
    
    # Demonstration 4: Step-by-step heapify down
    print("\n\n4. DETAILED HEAPIFY DOWN EXAMPLE")
    print("-" * 50)
    # Create a heap that violates min heap property at root
    heap3 = MinHeapify()
    heap3.heap = [10, 2, 3, 4, 5, 6, 7]  # Root 10 is larger than children
    print(f"Heap with violation: {heap3.heap}")
    print(f"Is valid min heap: {heap3.is_valid_min_heap()}")
    
    heap3.print_heap_structure()
    print("\nFixing with heapify down from root:")
    heap3.min_heapify_down(0)
    heap3.print_heap_structure()
    print(f"Is valid min heap: {heap3.is_valid_min_heap()}")
    
    # Demonstration 5: Heap sort using min heapify
    print("\n\n5. HEAP SORT USING MIN HEAPIFY")
    print("-" * 50)
    arr_to_sort = [64, 34, 25, 12, 22, 11, 90]
    print(f"Array to sort: {arr_to_sort}")
    
    heap4 = MinHeapify(arr_to_sort)
    sorted_array = []
    
    while not heap4.is_empty():
        sorted_array.append(heap4.extract_min())
    
    print(f"Sorted array: {sorted_array}")
```