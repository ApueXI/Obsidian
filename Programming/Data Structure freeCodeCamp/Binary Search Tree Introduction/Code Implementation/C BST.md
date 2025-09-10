---
Created: 2025-08-12T06:40
---
### ⚙️ C# — BST Implementation

```C#
using System;
using System.Collections.Generic;

public class TreeNode
{
    public int Val { get; set; }
    public TreeNode Left { get; set; }
    public TreeNode Right { get; set; }
    
    public TreeNode(int val = 0)
    {
        Val = val;
        Left = null;
        Right = null;
    }
}

public class BinarySearchTree
{
    private TreeNode root;
    private int size;
    
    public BinarySearchTree()
    {
        root = null;
        size = 0;
    }
    
    /// <summary>
    /// Insert a value into the BST
    /// </summary>
    public bool Insert(int val)
    {
        if (root == null)
        {
            root = new TreeNode(val);
            size++;
            return true;
        }
        
        return InsertRecursive(root, val);
    }
    
    private bool InsertRecursive(TreeNode node, int val)
    {
        if (val < node.Val)
        {
            if (node.Left == null)
            {
                node.Left = new TreeNode(val);
                size++;
                return true;
            }
            return InsertRecursive(node.Left, val);
        }
        else if (val > node.Val)
        {
            if (node.Right == null)
            {
                node.Right = new TreeNode(val);
                size++;
                return true;
            }
            return InsertRecursive(node.Right, val);
        }
        else
        {
            return false; // Value already exists
        }
    }
    
    /// <summary>
    /// Search for a value in the BST
    /// </summary>
    public bool Search(int val)
    {
        return SearchRecursive(root, val);
    }
    
    private bool SearchRecursive(TreeNode node, int val)
    {
        if (node == null)
            return false;
        
        if (val == node.Val)
            return true;
        else if (val < node.Val)
            return SearchRecursive(node.Left, val);
        else
            return SearchRecursive(node.Right, val);
    }
    
    /// <summary>
    /// Delete a value from the BST
    /// </summary>
    public bool Delete(int val)
    {
        var (newRoot, deleted) = DeleteRecursive(root, val);
        root = newRoot;
        if (deleted)
            size--;
        return deleted;
    }
    
    private (TreeNode, bool) DeleteRecursive(TreeNode node, int val)
    {
        if (node == null)
            return (null, false);
        
        if (val < node.Val)
        {
            var (newLeft, deleted) = DeleteRecursive(node.Left, val);
            node.Left = newLeft;
            return (node, deleted);
        }
        else if (val > node.Val)
        {
            var (newRight, deleted) = DeleteRecursive(node.Right, val);
            node.Right = newRight;
            return (node, deleted);
        }
        else
        {
            // Node to delete found
            if (node.Left == null)
                return (node.Right, true);
            else if (node.Right == null)
                return (node.Left, true);
            else
            {
                // Node has two children
                TreeNode minNode = FindMin(node.Right);
                node.Val = minNode.Val;
                var (newRight, _) = DeleteRecursive(node.Right, minNode.Val);
                node.Right = newRight;
                return (node, true);
            }
        }
    }
    
    private TreeNode FindMin(TreeNode node)
    {
        while (node.Left != null)
            node = node.Left;
        return node;
    }
    
    /// <summary>
    /// Find the minimum value in the BST
    /// </summary>
    public int? FindMinValue()
    {
        if (root == null)
            return null;
        return FindMin(root).Val;
    }
    
    /// <summary>
    /// Find the maximum value in the BST
    /// </summary>
    public int? FindMaxValue()
    {
        if (root == null)
            return null;
        
        TreeNode node = root;
        while (node.Right != null)
            node = node.Right;
        return node.Val;
    }
    
    /// <summary>
    /// Get the height of the BST
    /// </summary>
    public int Height()
    {
        return HeightRecursive(root);
    }
    
    private int HeightRecursive(TreeNode node)
    {
        if (node == null)
            return -1;
        
        int leftHeight = HeightRecursive(node.Left);
        int rightHeight = HeightRecursive(node.Right);
        return 1 + Math.Max(leftHeight, rightHeight);
    }
    
    /// <summary>
    /// Inorder traversal (sorted order)
    /// </summary>
    public List<int> Inorder()
    {
        List<int> result = new List<int>();
        InorderRecursive(root, result);
        return result;
    }
    
    private void InorderRecursive(TreeNode node, List<int> result)
    {
        if (node != null)
        {
            InorderRecursive(node.Left, result);
            result.Add(node.Val);
            InorderRecursive(node.Right, result);
        }
    }
    
    /// <summary>
    /// Preorder traversal
    /// </summary>
    public List<int> Preorder()
    {
        List<int> result = new List<int>();
        PreorderRecursive(root, result);
        return result;
    }
    
    private void PreorderRecursive(TreeNode node, List<int> result)
    {
        if (node != null)
        {
            result.Add(node.Val);
            PreorderRecursive(node.Left, result);
            PreorderRecursive(node.Right, result);
        }
    }
    
    /// <summary>
    /// Postorder traversal
    /// </summary>
    public List<int> Postorder()
    {
        List<int> result = new List<int>();
        PostorderRecursive(root, result);
        return result;
    }
    
    private void PostorderRecursive(TreeNode node, List<int> result)
    {
        if (node != null)
        {
            PostorderRecursive(node.Left, result);
            PostorderRecursive(node.Right, result);
            result.Add(node.Val);
        }
    }
    
    /// <summary>
    /// Check if the BST is empty
    /// </summary>
    public bool IsEmpty()
    {
        return root == null;
    }
    
    /// <summary>
    /// Get the number of nodes in the BST
    /// </summary>
    public int Size()
    {
        return size;
    }
}

// Example usage
class Program
{
    static void Main()
    {
        BinarySearchTree bst = new BinarySearchTree();
        
        // Insert values
        int[] values = {50, 30, 70, 20, 40, 60, 80};
        foreach (int val in values)
        {
            bst.Insert(val);
        }
        
        Console.WriteLine($"BST size: {bst.Size()}");
        Console.WriteLine($"Height: {bst.Height()}");
        Console.WriteLine($"Min value: {bst.FindMinValue()}");
        Console.WriteLine($"Max value: {bst.FindMaxValue()}");
        
        Console.WriteLine($"Search 40: {bst.Search(40)}");  // True
        Console.WriteLine($"Search 90: {bst.Search(90)}");  // False
        
        Console.WriteLine($"Inorder: [{string.Join(", ", bst.Inorder())}]");
        Console.WriteLine($"Preorder: [{string.Join(", ", bst.Preorder())}]");
        Console.WriteLine($"Postorder: [{string.Join(", ", bst.Postorder())}]");
        
        // Delete a node
        bst.Delete(30);
        Console.WriteLine($"After deleting 30: [{string.Join(", ", bst.Inorder())}]");
    }
}
```

### ⚙️ C# — Basic Binary Tree Node & Traversals

```C#
using System;

public class Node
{
    public int val;
    public Node left, right;

    public Node(int item)
    {
        val = item;
        left = right = null;
    }
}

public class BinaryTree
{
    public Node root;

    public BinaryTree(int rootVal)
    {
        root = new Node(rootVal);
    }

    public void Preorder(Node node)
    {
        if (node == null)
            return;
        Console.Write(node.val + " ");
        Preorder(node.left);
        Preorder(node.right);
    }

    public void Inorder(Node node)
    {
        if (node == null)
            return;
        Inorder(node.left);
        Console.Write(node.val + " ");
        Inorder(node.right);
    }

    public void Postorder(Node node)
    {
        if (node == null)
            return;
        Postorder(node.left);
        Postorder(node.right);
        Console.Write(node.val + " ");
    }
}

class Program
{
    static void Main()
    {
        BinaryTree tree = new BinaryTree(1);
        tree.root.left = new Node(2);
        tree.root.right = new Node(3);
        tree.root.left.left = new Node(4);
        tree.root.left.right = new Node(5);

        Console.WriteLine("Preorder traversal:");
        tree.Preorder(tree.root);
        Console.WriteLine("\nInorder traversal:");
        tree.Inorder(tree.root);
        Console.WriteLine("\nPostorder traversal:");
        tree.Postorder(tree.root);
    }
}
```