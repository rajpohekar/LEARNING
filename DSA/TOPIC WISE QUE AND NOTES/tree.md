The height of a binary tree is the length of the longest path from the root to a leaf. We can find the height recursively. The height of an empty tree is -1. Otherwise, the height is 1 plus the maximum of the heights of the left and right subtrees. This utilizes a Depth-First Search (DFS) approach.

**Time Complexity:** `O(N)`, where `N` is the number of nodes in the tree. Each node is visited once.  
**Space Complexity:** `O(H)`, where `H` is the height of the tree. In the worst case (skewed tree), `H = N`, so space is `O(N)` due to the call stack. In the best case (balanced tree), `H = log(N)`, so space is `O(logN)`.

**Code Example:**

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

// Definition for a binary tree node.
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode() : val(0), left(nullptr), right(nullptr) {}
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
};

int height(TreeNode* root) {
    if (root == nullptr) {
        return -1;
    }
    return 1 + max(height(root->left), height(root->right));
}

int main() {
    // Example usage:
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->right = new TreeNode(3);
    root->left->left = new TreeNode(4);
    root->left->right = new TreeNode(5);

    cout << "Height of the binary tree: " << height(root) << endl; // Output: 2

    // Clean up memory
    delete root->left->right;
    delete root->left->left;
    delete root->right;
    delete root->left;
    delete root;

    return 0;
}
```

---

### Count Nodes

To count the number of nodes in a binary tree:

```cpp
int countNodes(TreeNode* root) {
    if (root == nullptr) return 0;
    return 1 + countNodes(root->left) + countNodes(root->right);
}
```

### Sum of Nodes

To find the sum of all node values in a binary tree:

```cpp
int sumNodes(TreeNode* root) {
    if (root == nullptr) return 0;
    return root->val + sumNodes(root->left) + sumNodes(root->right);
}
```