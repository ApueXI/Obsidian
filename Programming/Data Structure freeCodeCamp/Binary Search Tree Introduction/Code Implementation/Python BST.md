---
Created: 2025-08-12T06:40
---
### 🐍 Python — BST Implementation

```Python
class TreeNode:
    def __init__(self, val=0):
        self.val = val
        self.left = None
        self.right = None

class BinarySearchTree:
    def __init__(self):
        self.root = None
        self.size = 0
    
    def insert(self, val):
        """Insert a value into the BST"""
        if self.root is None:
            self.root = TreeNode(val)
            self.size += 1
            return True
        
        return self._insert_recursive(self.root, val)
    
    def _insert_recursive(self, node, val):
        if val < node.val:
            if node.left is None:
                node.left = TreeNode(val)
                self.size += 1
                return True
            return self._insert_recursive(node.left, val)
        elif val > node.val:
            if node.right is None:
                node.right = TreeNode(val)
                self.size += 1
                return True
            return self._insert_recursive(node.right, val)
        else:
            return False  # Value already exists
    
    def search(self, val):
        """Search for a value in the BST"""
        return self._search_recursive(self.root, val)
    
    def _search_recursive(self, node, val):
        if node is None:
            return False
        
        if val == node.val:
            return True
        elif val < node.val:
            return self._search_recursive(node.left, val)
        else:
            return self._search_recursive(node.right, val)
    
    def delete(self, val):
        """Delete a value from the BST"""
        self.root, deleted = self._delete_recursive(self.root, val)
        if deleted:
            self.size -= 1
        return deleted
    
    def _delete_recursive(self, node, val):
        if node is None:
            return None, False
        
        if val < node.val:
            node.left, deleted = self._delete_recursive(node.left, val)
            return node, deleted
        elif val > node.val:
            node.right, deleted = self._delete_recursive(node.right, val)
            return node, deleted
        else:
            # Node to delete found
            if node.left is None:
                return node.right, True
            elif node.right is None:
                return node.left, True
            else:
                # Node has two children
                min_node = self._find_min(node.right)
                node.val = min_node.val
                node.right, _ = self._delete_recursive(node.right, min_node.val)
                return node, True
    
    def _find_min(self, node):
        """Find the minimum value node in a subtree"""
        while node.left is not None:
            node = node.left
        return node
    
    def find_min(self):
        """Find the minimum value in the BST"""
        if self.root is None:
            return None
        return self._find_min(self.root).val
    
    def find_max(self):
        """Find the maximum value in the BST"""
        if self.root is None:
            return None
        
        node = self.root
        while node.right is not None:
            node = node.right
        return node.val
    
    def height(self):
        """Get the height of the BST"""
        return self._height_recursive(self.root)
    
    def _height_recursive(self, node):
        if node is None:
            return -1
        
        left_height = self._height_recursive(node.left)
        right_height = self._height_recursive(node.right)
        return 1 + max(left_height, right_height)
    
    def inorder(self):
        """Inorder traversal (sorted order)"""
        result = []
        self._inorder_recursive(self.root, result)
        return result
    
    def _inorder_recursive(self, node, result):
        if node is not None:
            self._inorder_recursive(node.left, result)
            result.append(node.val)
            self._inorder_recursive(node.right, result)
    
    def preorder(self):
        """Preorder traversal"""
        result = []
        self._preorder_recursive(self.root, result)
        return result
    
    def _preorder_recursive(self, node, result):
        if node is not None:
            result.append(node.val)
            self._preorder_recursive(node.left, result)
            self._preorder_recursive(node.right, result)
    
    def postorder(self):
        """Postorder traversal"""
        result = []
        self._postorder_recursive(self.root, result)
        return result
    
    def _postorder_recursive(self, node, result):
        if node is not None:
            self._postorder_recursive(node.left, result)
            self._postorder_recursive(node.right, result)
            result.append(node.val)
    
    def is_empty(self):
        """Check if the BST is empty"""
        return self.root is None
    
    def get_size(self):
        """Get the number of nodes in the BST"""
        return self.size

# Example usage
if __name__ == "__main__":
    bst = BinarySearchTree()
    
    # Insert values
    values = [50, 30, 70, 20, 40, 60, 80]
    for val in values:
        bst.insert(val)
    
    print(f"BST size: {bst.get_size()}")
    print(f"Height: {bst.height()}")
    print(f"Min value: {bst.find_min()}")
    print(f"Max value: {bst.find_max()}")
    
    print(f"Search 40: {bst.search(40)}")  # True
    print(f"Search 90: {bst.search(90)}")  # False
    
    print(f"Inorder: {bst.inorder()}")      # Sorted order
    print(f"Preorder: {bst.preorder()}")
    print(f"Postorder: {bst.postorder()}")
    
    # Delete a node
    bst.delete(30)
    print(f"After deleting 30: {bst.inorder()}")
```

### 🐍 Python — Basic Binary Tree Node & Traversals

```Python
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key

class BinaryTree:
    def __init__(self, root_val):
        self.root = Node(root_val)

    def preorder(self, node):
        if node:
            print(node.val, end=' ')
            self.preorder(node.left)
            self.preorder(node.right)

    def inorder(self, node):
        if node:
            self.inorder(node.left)
            print(node.val, end=' ')
            self.inorder(node.right)

    def postorder(self, node):
        if node:
            self.postorder(node.left)
            self.postorder(node.right)
            print(node.val, end=' ')

# Example usage:
if __name__ == "__main__":
    tree = BinaryTree(1)
    tree.root.left = Node(2)
    tree.root.right = Node(3)
    tree.root.left.left = Node(4)
    tree.root.left.right = Node(5)

    print("Preorder traversal:")
    tree.preorder(tree.root)
    print("\nInorder traversal:")
    tree.inorder(tree.root)
    print("\nPostorder traversal:")
    tree.postorder(tree.root)
```