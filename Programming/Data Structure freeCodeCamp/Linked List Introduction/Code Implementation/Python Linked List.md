---
Created: 2025-08-12T06:46
---
### Python — LinkedList.py

```Python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class SinglyLinkedList:
    def __init__(self):
        self.head = None
        self.size = 0
    
    def __len__(self):
        return self.size
    
    def is_empty(self):
        return self.head is None
    
    def append(self, data):
        """Add element to the end of the list"""
        new_node = Node(data)
        if not self.head:
            self.head = new_node
        else:
            current = self.head
            while current.next:
                current = current.next
            current.next = new_node
        self.size += 1
    
    def prepend(self, data):
        """Add element to the beginning of the list"""
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node
        self.size += 1
    
    def insert(self, index, data):
        """Insert element at specific index"""
        if index < 0 or index > self.size:
            raise IndexError("Index out of range")
        
        if index == 0:
            self.prepend(data)
            return
        
        new_node = Node(data)
        current = self.head
        for i in range(index - 1):
            current = current.next
        
        new_node.next = current.next
        current.next = new_node
        self.size += 1
    
    def remove_first(self):
        """Remove and return the first element"""
        if not self.head:
            raise IndexError("List is empty")
        
        data = self.head.data
        self.head = self.head.next
        self.size -= 1
        return data
    
    def remove_last(self):
        """Remove and return the last element"""
        if not self.head:
            raise IndexError("List is empty")
        
        if not self.head.next:  # Only one element
            data = self.head.data
            self.head = None
            self.size -= 1
            return data
        
        # Find second to last node
        current = self.head
        while current.next.next:
            current = current.next
        
        data = current.next.data
        current.next = None
        self.size -= 1
        return data
    
    def remove_at(self, index):
        """Remove element at specific index"""
        if index < 0 or index >= self.size:
            raise IndexError("Index out of range")
        
        if index == 0:
            return self.remove_first()
        
        current = self.head
        for i in range(index - 1):
            current = current.next
        
        data = current.next.data
        current.next = current.next.next
        self.size -= 1
        return data
    
    def remove(self, data):
        """Remove first occurrence of data"""
        if not self.head:
            raise ValueError("List is empty")
        
        if self.head.data == data:
            self.remove_first()
            return
        
        current = self.head
        while current.next:
            if current.next.data == data:
                current.next = current.next.next
                self.size -= 1
                return
            current = current.next
        
        raise ValueError(f"Value {data} not found in list")
    
    def find(self, data):
        """Find index of first occurrence of data"""
        current = self.head
        index = 0
        while current:
            if current.data == data:
                return index
            current = current.next
            index += 1
        return -1
    
    def get(self, index):
        """Get element at specific index"""
        if index < 0 or index >= self.size:
            raise IndexError("Index out of range")
        
        current = self.head
        for i in range(index):
            current = current.next
        return current.data
    
    def __getitem__(self, index):
        """Support indexing with []"""
        return self.get(index)
    
    def __str__(self):
        """String representation of the list"""
        if not self.head:
            return "[]"
        
        result = []
        current = self.head
        while current:
            result.append(str(current.data))
            current = current.next
        
        return " -> ".join(result) + " -> None"
    
    def __repr__(self):
        return f"SinglyLinkedList({self.__str__()})"
    
    def to_list(self):
        """Convert to Python list"""
        result = []
        current = self.head
        while current:
            result.append(current.data)
            current = current.next
        return result

# Example usage
if __name__ == "__main__":
    ll = SinglyLinkedList()
    
    # Test append
    for i in range(5):
        ll.append(i * 10)
    print(f"After appending 0-40: {ll}")
    
    # Test prepend
    ll.prepend(-10)
    print(f"After prepending -10: {ll}")
    
    # Test insert
    ll.insert(2, 99)
    print(f"After inserting 99 at index 2: {ll}")
    
    # Test removal
    removed = ll.remove_first()
    print(f"Removed first element {removed}: {ll}")
    
    removed = ll.remove_last()
    print(f"Removed last element {removed}: {ll}")
    
    # Test find
    index = ll.find(20)
    print(f"Index of 20: {index}")
    
    # Test get
    value = ll.get(1)
    print(f"Element at index 1: {value}")
    
    print(f"List as array: {ll.to_list()}")
    print(f"Length: {len(ll)}")
```

### Python — DoublyLinkedList.py

```Python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

class DoublyLinkedList:
    def __init__(self):
        self.head = None
        self.tail = None
        self.size = 0
    
    def __len__(self):
        return self.size
    
    def is_empty(self):
        return self.head is None
    
    def append(self, data):
        """Add element to the end of the list"""
        new_node = Node(data)
        if not self.head:
            self.head = self.tail = new_node
        else:
            new_node.prev = self.tail
            self.tail.next = new_node
            self.tail = new_node
        self.size += 1
    
    def prepend(self, data):
        """Add element to the beginning of the list"""
        new_node = Node(data)
        if not self.head:
            self.head = self.tail = new_node
        else:
            new_node.next = self.head
            self.head.prev = new_node
            self.head = new_node
        self.size += 1
    
    def insert(self, index, data):
        """Insert element at specific index"""
        if index < 0 or index > self.size:
            raise IndexError("Index out of range")
        
        if index == 0:
            self.prepend(data)
            return
        
        if index == self.size:
            self.append(data)
            return
        
        new_node = Node(data)
        
        # Choose direction based on which is closer
        if index <= self.size // 2:
            # Traverse from head
            current = self.head
            for i in range(index):
                current = current.next
        else:
            # Traverse from tail
            current = self.tail
            for i in range(self.size - index - 1):
                current = current.prev
        
        # Insert before current
        new_node.next = current
        new_node.prev = current.prev
        current.prev.next = new_node
        current.prev = new_node
        self.size += 1
    
    def remove_first(self):
        """Remove and return the first element"""
        if not self.head:
            raise IndexError("List is empty")
        
        data = self.head.data
        if self.head == self.tail:  # Only one element
            self.head = self.tail = None
        else:
            self.head = self.head.next
            self.head.prev = None
        
        self.size -= 1
        return data
    
    def remove_last(self):
        """Remove and return the last element"""
        if not self.tail:
            raise IndexError("List is empty")
        
        data = self.tail.data
        if self.head == self.tail:  # Only one element
            self.head = self.tail = None
        else:
            self.tail = self.tail.prev
            self.tail.next = None
        
        self.size -= 1
        return data
    
    def remove_at(self, index):
        """Remove element at specific index"""
        if index < 0 or index >= self.size:
            raise IndexError("Index out of range")
        
        if index == 0:
            return self.remove_first()
        
        if index == self.size - 1:
            return self.remove_last()
        
        # Choose direction based on which is closer
        if index <= self.size // 2:
            current = self.head
            for i in range(index):
                current = current.next
        else:
            current = self.tail
            for i in range(self.size - index - 1):
                current = current.prev
        
        data = current.data
        current.prev.next = current.next
        current.next.prev = current.prev
        self.size -= 1
        return data
    
    def remove(self, data):
        """Remove first occurrence of data"""
        current = self.head
        while current:
            if current.data == data:
                if current == self.head:
                    self.remove_first()
                elif current == self.tail:
                    self.remove_last()
                else:
                    current.prev.next = current.next
                    current.next.prev = current.prev
                    self.size -= 1
                return
            current = current.next
        
        raise ValueError(f"Value {data} not found in list")
    
    def find(self, data):
        """Find index of first occurrence of data"""
        current = self.head
        index = 0
        while current:
            if current.data == data:
                return index
            current = current.next
            index += 1
        return -1
    
    def get(self, index):
        """Get element at specific index"""
        if index < 0 or index >= self.size:
            raise IndexError("Index out of range")
        
        # Choose direction based on which is closer
        if index <= self.size // 2:
            current = self.head
            for i in range(index):
                current = current.next
        else:
            current = self.tail
            for i in range(self.size - index - 1):
                current = current.prev
        
        return current.data
    
    def __getitem__(self, index):
        """Support indexing with []"""
        return self.get(index)
    
    def __str__(self):
        """String representation (forward)"""
        if not self.head:
            return "[]"
        
        result = []
        current = self.head
        while current:
            result.append(str(current.data))
            current = current.next
        
        return " <-> ".join(result)
    
    def str_reverse(self):
        """String representation (backward)"""
        if not self.tail:
            return "[]"
        
        result = []
        current = self.tail
        while current:
            result.append(str(current.data))
            current = current.prev
        
        return " <-> ".join(result)
    
    def to_list(self):
        """Convert to Python list"""
        result = []
        current = self.head
        while current:
            result.append(current.data)
            current = current.next
        return result
    
    def to_list_reverse(self):
        """Convert to Python list (reverse order)"""
        result = []
        current = self.tail
        while current:
            result.append(current.data)
            current = current.prev
        return result

# Example usage
if __name__ == "__main__":
    dll = DoublyLinkedList()
    
    # Test append
    for i in range(5):
        dll.append(i * 10)
    print(f"After appending 0-40: {dll}")
    
    # Test prepend
    dll.prepend(-10)
    print(f"After prepending -10: {dll}")
    
    # Test insert
    dll.insert(2, 99)
    print(f"After inserting 99 at index 2: {dll}")
    
    # Test removal
    removed = dll.remove_first()
    print(f"Removed first element {removed}: {dll}")
    
    removed = dll.remove_last()
    print(f"Removed last element {removed}: {dll}")
    
    # Test bidirectional traversal
    print(f"Forward: {dll}")
    print(f"Backward: {dll.str_reverse()}")
    
    # Test optimized access
    print(f"Element at index 1: {dll.get(1)}")
    print(f"Element at index {len(dll)-1}: {dll.get(len(dll)-1)}")
    
    print(f"List as array: {dll.to_list()}")
    print(f"List reversed: {dll.to_list_reverse()}")
    print(f"Length: {len(dll)}")
```