---
layout: post
title: Make Binary Tree From Linked List         
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/make-binary-tree/0/?)  

Given a Linked List Representation of Complete Binary Tree. The task is to construct the Binary tree.
Note : The complete binary tree is represented as a linked list in a way where if root node is stored at position `i`, its left, and right children are stored at position `2*i+1`, `2*i+2` respectively.

<img src="http://d1hyf4ir1gqw6c.cloudfront.net/wp-content/uploads/LinkedListToBST.png">

**Your Task:** 
The task is to complete the function `convert()` which takes head of linked list and root of the tree as the reference. The driver code prints the level order.

**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`   

### Examples

**Example 1:**   
```
Input:
N = 5
K = 1->2->3->4->5
Output: 1 2 3 4 5
Explanation: The tree would look like
      1
    /   \
   2     3
 /  \
4   5
Now, the level order traversal of
the above tree is 1 2 3 4 5.
```

**Example 2:**   
```
Input:
N = 5
K = 5->4->3->2->1
Output: 5 4 3 2 1
Explanation: The tree would look like
     5
   /  \
  4    3
 / \
2    1
Now, the level order traversal of
the above tree is 5 4 3 2 1..
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^5`

## Solutions

```cpp
//Function to make binary tree from linked list.
TreeNode *bt(vector<int> &v, int i){
    if(i>=v.size()) return NULL;
    TreeNode* root = new TreeNode(v[i]);
    root->left = bt(v,2*i+1);
    root->right = bt(v,2*i+2);
    return root;
}
void convert(Node *head, TreeNode *&root) {
    // Your code here
    vector<int> v;
    Node* temp = head;
    while(temp) { v.push_back(temp->data); temp=temp->next; }
    root = bt(v,0);
}
```

