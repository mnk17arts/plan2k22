---
layout: post
title: Binary Tree to CDLL        
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/binary-tree-to-cdll/0/)  

Given a Binary Tree of `N` edges. The task is to convert this to a Circular Doubly Linked List(CDLL) in-place. The left and right pointers in nodes are to be used as previous and next pointers respectively in converted CDLL. The order of nodes in CDLL must be same as Inorder of the given Binary Tree. The first node of Inorder traversal (left most node in BT) must be head node of the CDLL.


**Your Task:** 
You don't have to take input. Complete the function `bTreeToCList()` that takes root as a parameter and returns the head of the list. The printing is done by the driver code.

**Expected Time Complexity:** `O(N)`   
**Expected Auxiliary Space:** `O(h)` , where h = height of tree  

### Examples

**Example 1:**   
```
Input:
      1
    /   \
   3     2
Output:
3 1 2 
2 1 3
Explanation: After converting tree to CDLL
when CDLL is is traversed from head to
tail and then tail to head, elements
are displayed as in the output.
```

**Example 2:**   
```
Input:
     10
   /    \
  20    30
 /  \
40  60
Output:
40 20 60 10 30 
30 10 60 20 40
Explanation:After converting tree to CDLL,
when CDLL is is traversed from head to
tail and then tail to head, elements
are displayed as in the output.
```


### Constraints

+ `1 <= Number of nodes <= 10^3`
+ `0 <= Data of a node <= 10^4`

## Solutions

```cpp
class Solution {
  public:
    //Function to convert binary tree into circular doubly linked list.
    Node* prev = NULL;
    Node * bToDLL(Node *root)
    {
        // your code here
        if(!root) return NULL;
        Node* head = bToDLL(root->left);
        if(!prev) { head = root; }
        else {
           root->left = prev;
           prev->right = root;
            
        }
        prev = root;
        bToDLL(root->right);
        return head;
    }
    Node *bTreeToCList(Node *root)
    {
    //add code here.
        Node* head = bToDLL(root);
        Node* temp = head;
        while(temp->right) temp = temp->right;
        temp->right = head;
        head->left = temp;
        return head;
    }
};
```

