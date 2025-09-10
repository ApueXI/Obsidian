---
Created: 2025-08-12T06:40
---
### 🖥️ C++ — BST Implementation

```C++
\#include <iostream>
\#include <vector>
\#include <algorithm>

struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
    
    TreeNode(int v = 0) : val(v), left(nullptr), right(nullptr) {}
};

class BinarySearchTree {
private:
    TreeNode* root;
    int size;
    
    bool insertRecursive(TreeNode* node, int val) {
        if (val < node->val) {
            if (node->left == nullptr) {
                node->left = new TreeNode(val);
                size++;
                return true;
            }
            return insertRecursive(node->left, val);
        }
        else if (val > node->val) {
            if (node->right == nullptr) {
                node->right = new TreeNode(val);
                size++;
                return true;
            }
            return insertRecursive(node->right, val);
        }
        else {
            return false; // Value already exists
        }
    }
    
    bool searchRecursive(TreeNode* node, int val) const {
        if (node == nullptr)
            return false;
        
        if (val == node->val)
            return true;
        else if (val < node->val)
            return searchRecursive(node->left, val);
        else
            return searchRecursive(node->right, val);
    }
    
    std::pair<TreeNode*, bool> deleteRecursive(TreeNode* node, int val) {
        if (node == nullptr)
            return {nullptr, false};
        
        if (val < node->val) {
            auto [newLeft, deleted] = deleteRecursive(node->left, val);
            node->left = newLeft;
            return {node, deleted};
        }
        else if (val > node->val) {
            auto [newRight, deleted] = deleteRecursive(node->right, val);
            node->right = newRight;
            return {node, deleted};
        }
        else {
            // Node to delete found
            if (node->left == nullptr) {
                TreeNode* temp = node->right;
                delete node;
                return {temp, true};
            }
            else if (node->right == nullptr) {
                TreeNode* temp = node->left;
                delete node;
                return {temp, true};
            }
            else {
                // Node has two children
                TreeNode* minNode = findMin(node->right);
                node->val = minNode->val;
                auto [newRight, _] = deleteRecursive(node->right, minNode->val);
                node->right = newRight;
                return {node, true};
            }
        }
    }
    
    TreeNode* findMin(TreeNode* node) const {
        while (node->left != nullptr)
            node = node->left;
        return node;
    }
    
    int heightRecursive(TreeNode* node) const {
        if (node == nullptr)
            return -1;
        
        int leftHeight = heightRecursive(node->left);
        int rightHeight = heightRecursive(node->right);
        return 1 + std::max(leftHeight, rightHeight);
    }
    
    void inorderRecursive(TreeNode* node, std::vector<int>& result) const {
        if (node != nullptr) {
            inorderRecursive(node->left, result);
            result.push_back(node->val);
            inorderRecursive(node->right, result);
        }
    }
    
    void preorderRecursive(TreeNode* node, std::vector<int>& result) const {
        if (node != nullptr) {
            result.push_back(node->val);
            preorderRecursive(node->left, result);
            preorderRecursive(node->right, result);
        }
    }
    
    void postorderRecursive(TreeNode* node, std::vector<int>& result) const {
        if (node != nullptr) {
            postorderRecursive(node->left, result);
            postorderRecursive(node->right, result);
            result.push_back(node->val);
        }
    }
    
    void destroyTree(TreeNode* node) {
        if (node != nullptr) {
            destroyTree(node->left);
            destroyTree(node->right);
            delete node;
        }
    }

public:
    /**
     * Constructor
     */
    BinarySearchTree() : root(nullptr), size(0) {}
    
    /**
     * Destructor
     */
    ~BinarySearchTree() {
        destroyTree(root);
    }
    
    /**
     * Copy constructor
     */
    BinarySearchTree(const BinarySearchTree& other) : root(nullptr), size(0) {
        std::vector<int> values = other.inorder();
        for (int val : values) {
            insert(val);
        }
    }
    
    /**
     * Assignment operator
     */
    BinarySearchTree& operator=(const BinarySearchTree& other) {
        if (this != &other) {
            destroyTree(root);
            root = nullptr;
            size = 0;
            
            std::vector<int> values = other.inorder();
            for (int val : values) {
                insert(val);
            }
        }
        return *this;
    }
    
    /**
     * Insert a value into the BST
     */
    bool insert(int val) {
        if (root == nullptr) {
            root = new TreeNode(val);
            size++;
            return true;
        }
        
        return insertRecursive(root, val);
    }
    
    /**
     * Search for a value in the BST
     */
    bool search(int val) const {
        return searchRecursive(root, val);
    }
    
    /**
     * Delete a value from the BST
     */
    bool remove(int val) {
        auto [newRoot, deleted] = deleteRecursive(root, val);
        root = newRoot;
        if (deleted)
            size--;
        return deleted;
    }
    
    /**
     * Find the minimum value in the BST
     */
    bool findMinValue(int& minVal) const {
        if (root == nullptr)
            return false;
        
        minVal = findMin(root)->val;
        return true;
    }
    
    /**
     * Find the maximum value in the BST
     */
    bool findMaxValue(int& maxVal) const {
        if (root == nullptr)
            return false;
        
        TreeNode* node = root;
        while (node->right != nullptr)
            node = node->right;
        
        maxVal = node->val;
        return true;
    }
    
    /**
     * Get the height of the BST
     */
    int height() const {
        return heightRecursive(root);
    }
    
    /**
     * Inorder traversal (sorted order)
     */
    std::vector<int> inorder() const {
        std::vector<int> result;
        inorderRecursive(root, result);
        return result;
    }
    
    /**
     * Preorder traversal
     */
    std::vector<int> preorder() const {
        std::vector<int> result;
        preorderRecursive(root, result);
        return result;
    }
    
    /**
     * Postorder traversal
     */
    std::vector<int> postorder() const {
        std::vector<int> result;
        postorderRecursive(root, result);
        return result;
    }
    
    /**
     * Check if the BST is empty
     */
    bool isEmpty() const {
        return root == nullptr;
    }
    
    /**
     * Get the number of nodes in the BST
     */
    int getSize() const {
        return size;
    }
};

// Example usage
int main() {
    BinarySearchTree bst;
    
    // Insert values
    std::vector<int> values = {50, 30, 70, 20, 40, 60, 80};
    for (int val : values) {
        bst.insert(val);
    }
    
    std::cout << "BST size: " << bst.getSize() << std::endl;
    std::cout << "Height: " << bst.height() << std::endl;
    
    int minVal, maxVal;
    if (bst.findMinValue(minVal))
        std::cout << "Min value: " << minVal << std::endl;
    if (bst.findMaxValue(maxVal))
        std::cout << "Max value: " << maxVal << std::endl;
    
    std::cout << "Search 40: " << std::boolalpha << bst.search(40) << std::endl;  // true
    std::cout << "Search 90: " << std::boolalpha << bst.search(90) << std::endl;  // false
    
    // Print traversals
    auto inorderResult = bst.inorder();
    std::cout << "Inorder: ";
    for (int val : inorderResult) {
        std::cout << val << " ";
    }
    std::cout << std::endl;
    
    auto preorderResult = bst.preorder();
    std::cout << "Preorder: ";
    for (int val : preorderResult) {
        std::cout << val << " ";
    }
    std::cout << std::endl;
    
    auto postorderResult = bst.postorder();
    std::cout << "Postorder: ";
    for (int val : postorderResult) {
        std::cout << val << " ";
    }
    std::cout << std::endl;
    
    // Delete a node
    bst.remove(30);
    auto afterDelete = bst.inorder();
    std::cout << "After deleting 30: ";
    for (int val : afterDelete) {
        std::cout << val << " ";
    }
    std::cout << std::endl;
    
    return 0;
}
```

### 🖥️ C++ — Basic Binary Tree Node & Traversals

```C++
\#include <iostream>
using namespace std;

struct Node {
    int val;
    Node* left;
    Node* right;

    Node(int value) {
        val = value;
        left = right = nullptr;
    }
};

class BinaryTree {
public:
    Node* root;

    BinaryTree(int rootVal) {
        root = new Node(rootVal);
    }

    void preorder(Node* node) {
        if (node == nullptr)
            return;
        cout << node->val << " ";
        preorder(node->left);
        preorder(node->right);
    }

    void inorder(Node* node) {
        if (node == nullptr)
            return;
        inorder(node->left);
        cout << node->val << " ";
        inorder(node->right);
    }

    void postorder(Node* node) {
        if (node == nullptr)
            return;
        postorder(node->left);
        postorder(node->right);
        cout << node->val << " ";
    }
};

int main() {
    BinaryTree tree(1);
    tree.root->left = new Node(2);
    tree.root->right = new Node(3);
    tree.root->left->left = new Node(4);
    tree.root->left->right = new Node(5);

    cout << "Preorder traversal:" << endl;
    tree.preorder(tree.root);
    cout << "\nInorder traversal:" << endl;
    tree.inorder(tree.root);
    cout << "\nPostorder traversal:" << endl;
    tree.postorder(tree.root);
    cout << endl;

    return 0;
}
```