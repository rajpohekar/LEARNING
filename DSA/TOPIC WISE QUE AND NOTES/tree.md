Top 10 Tree Interview Problems

# Height/Maximum Depth of Binary Tree: Find the maximum distance from root to leaf.

# Check if Two Trees are Identical: Validate structural and value equivalence of two trees.

# Mirror/Symmetric Tree: Determine if a tree is a mirror image or symmetric about its center.

Check/Validate a Binary Search Tree (BST): Confirm if a tree meets BST properties (ordering rules).

Inorder Successor in BST: Find the next node in inorder traversal for a given node.

Lowest Common Ancestor (LCA): Given two nodes, find their lowest shared ancestor in the tree.

# Diameter of Binary Tree: Compute the longest path between any two nodes in the tree.

# Level Order Traversal (BFS): Traverse nodes level-by-level, often used to solve serialization or structure problems.

Construct Binary Tree from Traversals: Build a tree given inorder and preorder/postorder traversals.

Maximum Path Sum: Find the path (root to leaf or any node to any node) with the maximum sum.

Additional Problem 

# 🌳 Step 1: Binary Tree Node Structure

In C++, a node of a binary tree can be represented like this:

```cpp
#include <iostream>
using namespace std;

// Definition of a tree node
struct Node {
    int data;
    Node* left;
    Node* right;

    // Constructor
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
```

---

# 🌲 Step 2: Basic Traversals (DFS)

```cpp
// Preorder: Root -> Left -> Right
void preorder(Node* root) {
    if (root == nullptr) return;
    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}

// Inorder: Left -> Root -> Right
void inorder(Node* root) {
    if (root == nullptr) return;
    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

// Postorder: Left -> Right -> Root
void postorder(Node* root) {
    if (root == nullptr) return;
    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}
```

---

# 🌿 Step 3: BFS (Level Order)

We use a **queue** for this.

```cpp
#include <queue>

void levelOrder(Node* root) {
    if (root == nullptr) return;
    queue<Node*> q;
    q.push(root);

    while (!q.empty()) {
        Node* curr = q.front();
        q.pop();
        cout << curr->data << " ";

        if (curr->left) q.push(curr->left);
        if (curr->right) q.push(curr->right);
    }
}
```

---

# 🌴 Step 4: Example Usage

```cpp
int main() {
    // Create nodes manually
    Node* root = new Node(1);
    root->left = new Node(2);
    root->right = new Node(3);
    root->left->left = new Node(4);
    root->left->right = new Node(5);

    cout << "Preorder: ";
    preorder(root);
    cout << "\nInorder: ";
    inorder(root);
    cout << "\nPostorder: ";
    postorder(root);
    cout << "\nLevel Order: ";
    levelOrder(root);

    return 0;
}
```

---

✅ Output for this tree:

```
       1
      / \
     2   3
    / \
   4   5
```

```
Preorder: 1 2 4 5 3
Inorder: 4 2 5 1 3
Postorder: 4 5 2 3 1
Level Order: 1 2 3 4 5
```

---

Would you like me to next explain **Binary Search Tree (BST) implementation** (insert, search, delete) since that’s heavily asked in interviews?


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


Perfect! Let’s analyze your **`isIdentical` function** in C++ step by step.

---

## ✅ Code

```cpp
struct Node {
    int data;
    Node* left;
    Node* right;
    Node(int val) : data(val), left(NULL), right(NULL) {}
};

bool isIdentical(Node* p, Node* q) {
    if (p == q) return true;   // base case: both NULL or same pointer
    if (!p || !q) return false; // one is NULL, other is not
    return (p->data == q->data) &&
           isIdentical(p->left, q->left) &&
           isIdentical(p->right, q->right);
}
```

---

## 🧮 Time Complexity

* Let **n** = number of nodes in tree `p` (or `q` if identical, same size).
* Each node is visited **exactly once**.
* At each node, comparison of `data` and recursive calls → **O(1)** work.

**⏱ Time Complexity = O(n)**

* Worst case: trees are identical → all nodes are visited.
* Best case: trees differ at root → O(1) (early exit).

---

## 📦 Space Complexity

* Space is due to **recursion stack** (DFS).
* In a binary tree, recursion depth = **height of tree = h**.
* Worst case (skewed tree): h = n → O(n)
* Best case (balanced tree): h ≈ log₂n → O(log n)

**📌 Space Complexity = O(h)**

---

### 🔹 Summary Table

| Parameter | Complexity       |
| --------- | ---------------- |
| Time      | O(n)             |
| Space     | O(h) (recursion) |

---

If you want, I can also show the **iterative approach using queues** with **O(n) time** but **O(n) space**, which is useful for interviews too.

Do you want me to show that?






Great question 👍 The **diameter of a binary tree** is a very popular interview problem. Let’s go step by step.

---

## **Definition**

The **diameter** (a.k.a. width) of a binary tree is the **length of the longest path** between any two nodes in the tree.

* This path **may or may not pass through the root**.
* The length is measured as the **number of edges** (sometimes number of nodes, but usually edges).

---

## **Approach 1: Brute Force (O(n²))**

**Logic:**

1. For each node, compute:

   * Height of left subtree
   * Height of right subtree
   * Diameter passing through this node = `leftHeight + rightHeight`
2. The overall diameter = `max(diameter of left subtree, diameter of right subtree, leftHeight + rightHeight)`

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
    Node(int val){ data=val; left=right=nullptr; }
};

// Height of a tree
int height(Node* root){
    if(!root) return 0;
    return 1 + max(height(root->left), height(root->right));
}

// Brute Force Diameter
int diameter(Node* root){
    if(!root) return 0;
    
    int leftHeight = height(root->left);
    int rightHeight = height(root->right);

    int leftDiameter = diameter(root->left);
    int rightDiameter = diameter(root->right);

    return max({leftHeight + rightHeight, leftDiameter, rightDiameter});
}
```

* **Time Complexity:** O(n²) (height recomputed for every node).
* **Space Complexity:** O(h) recursion stack (O(n) worst).

---

## **Approach 2: Optimized (O(n))**

**Logic:**

* Instead of recalculating heights, compute **height and diameter together** in one DFS.
* Use a helper function that returns height while updating diameter.

```cpp
int diameterUtil(Node* root, int &diam){
    if(!root) return 0;

    int lh = diameterUtil(root->left, diam);
    int rh = diameterUtil(root->right, diam);

    // Update diameter if path through root is larger
    diam = max(diam, lh + rh);

    // Return height
    return 1 + max(lh, rh);
}

int diameter(Node* root){
    int diam = 0;
    diameterUtil(root, diam);
    return diam;
}
```

* **Time Complexity:** O(n) (each node visited once).
* **Space Complexity:** O(h) recursion stack.

---

## **Example**

For tree:

```
       1
      / \
     2   3
    / \
   4   5
```

* Path with maximum length = 4 → 2 → 1 → 3 (length = 3 edges).
* Diameter = 3.

---

✅ **Key Notes for Interviews**

* Clarify whether diameter means **nodes count** or **edges count**.
* Optimized approach is expected in interviews.
* Similar to **height problem**, just add an extra tracking variable.

---

Do you want me to also explain this using a **dry run on a sample tree (step-by-step height & diameter updates)**? That’s usually what interviewers ask.
