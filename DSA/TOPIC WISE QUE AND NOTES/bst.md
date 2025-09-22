Perfect 👌 Let’s go through the **Binary Search Tree (BST)** basics step by step, with **insert, search, and delete operations in C++**.

---

# **Binary Search Tree (BST)**

A **BST** is a binary tree with these properties:

1. Left child < Root
2. Right child > Root
3. Both left and right subtrees are also BSTs

---

## **Node Structure**

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
```

---

## **1️⃣ Insert in BST**

**Logic:**

* If tree is empty, new node becomes root.
* If value < root → go left.
* If value > root → go right.
* Recursively insert in correct position.

```cpp
Node* insert(Node* root, int val) {
    if (root == nullptr) return new Node(val);

    if (val < root->data)
        root->left = insert(root->left, val);
    else if (val > root->data)
        root->right = insert(root->right, val);

    return root;
}
```

---

## **2️⃣ Search in BST**

**Logic:**

* If root is null → not found.
* If val == root → found.
* If val < root → search in left.
* Else search in right.

```cpp
bool search(Node* root, int key) {
    if (root == nullptr) return false;
    if (root->data == key) return true;

    if (key < root->data)
        return search(root->left, key);
    else
        return search(root->right, key);
}
```

---

## **3️⃣ Delete in BST**

**Cases:**

1. **Node is leaf** → just delete it.
2. **Node has one child** → replace node with child.
3. **Node has two children** → find inorder successor (min in right subtree), replace node value, and delete successor.

```cpp
Node* findMin(Node* root) {
    while (root->left != nullptr) root = root->left;
    return root;
}

Node* deleteNode(Node* root, int key) {
    if (root == nullptr) return root;

    if (key < root->data)
        root->left = deleteNode(root->left, key);
    else if (key > root->data)
        root->right = deleteNode(root->right, key);
    else {
        // Case 1 & 2: Node with 0 or 1 child
        if (root->left == nullptr) {
            Node* temp = root->right;
            delete root;
            return temp;
        } else if (root->right == nullptr) {
            Node* temp = root->left;
            delete root;
            return temp;
        }

        // Case 3: Node with 2 children
        Node* temp = findMin(root->right);
        root->data = temp->data;
        root->right = deleteNode(root->right, temp->data);
    }
    return root;
}
```

---

## **4️⃣ Inorder Traversal (for testing)**

```cpp
void inorder(Node* root) {
    if (root == nullptr) return;
    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}
```

---

## **5️⃣ Main Function Example**

```cpp
int main() {
    Node* root = nullptr;

    // Insert
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 20);
    insert(root, 40);
    insert(root, 70);
    insert(root, 60);
    insert(root, 80);

    cout << "Inorder traversal: ";
    inorder(root);
    cout << "\n";

    // Search
    cout << "Search 40: " << (search(root, 40) ? "Found" : "Not Found") << "\n";

    // Delete
    root = deleteNode(root, 20);
    cout << "After deleting 20: ";
    inorder(root);
    cout << "\n";

    root = deleteNode(root, 30);
    cout << "After deleting 30: ";
    inorder(root);
    cout << "\n";

    root = deleteNode(root, 50);
    cout << "After deleting 50: ";
    inorder(root);
    cout << "\n";

    return 0;
}
```

---

## ✅ **Complexities**

| Operation | Average  | Worst (Skewed Tree) |
| --------- | -------- | ------------------- |
| Insert    | O(log n) | O(n)                |
| Search    | O(log n) | O(n)                |
| Delete    | O(log n) | O(n)                |

👉 Balanced BSTs (like AVL, Red-Black Tree) guarantee O(log n).

---

Do you want me to also show a **dry run example of insert → delete → inorder traversal** so you can see how the tree changes step by step?
