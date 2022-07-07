---
layout: post
title: Binary Tree to DLL        
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - hard
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/binary-tree-to-dll/0/?t)  

Given a Binary Tree (BT), convert it to a Doubly Linked List(DLL) In-Place. The left and right pointers in nodes are to be used as previous and next pointers respectively in converted DLL. The order of nodes in DLL must be same as Inorder of the given Binary Tree. The first node of Inorder traversal (leftmost node in BT) must be the head node of the DLL.

<img src="http://www.geeksforgeeks.org/wp-content/uploads/TreeToList.png">

**Your Task:** 
You don't have to take input. Complete the function `bToDLL()` that takes root node of the tree as a parameter and returns the head of DLL . The driver code prints the DLL both ways

**Expected Time Complexity:** `O(N)`    
**Expected Auxiliary Space:** `O(h)` , where h = height of tree  

### Examples

**Example 1:**   
```
Input:
      1
    /  \
   3    2
Output:
3 1 2 
2 1 3 
Explanation: DLL would be 3<=>1<=>2
```

**Example 2:**   
```
Input:
       10
      /   \
     20   30
   /   \
  40   60
Output:
40 20 60 10 30 
30 10 60 20 40
Explanation:  DLL would be 
40<=>20<=>60<=>10<=>30.
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^5`

## Solutions

```cpp
class Solution {
  public:
    //Function to convert binary tree into doubly linked list.
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
};
```

