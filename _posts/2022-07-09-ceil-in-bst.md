---
layout: post
title: Ceil in BST              
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/implementing-ceil-in-bst/0/?t)  

Given a BST and a number X, find Ceil of X.
Note: Ceil(X) is a number that is either equal to X or is immediately greater than X.


**Your Task:** 
You don't need to read input or print anything. Just complete the function `findCeil()` to implement ceil in BST which returns the ceil of `X` in the given BST. 


**Expected Time Complexity:** `O(h)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
     10
    /  \
   5    11
  / \ 
 4   7
      \
       8
X = 6
Output: 7
Explanation: We find 7 in BST, so ceil
of 6 is 7.
```


**Example 2:**   
```
Input:
      5
    /   \
   1     7
    \
     2 
      \
       3
X = 3
Output: 3
Explanation: We find 3 in BST, so ceil
of 3 is 3.
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= Value of Node <= 10^5`

## Solutions

```cpp
// Function to return the ceil of given number in BST.
int findCeil(Node* root, int input) {
    if (!root) return -1;
    if(root->data==input) return input;
    if(root->data<input) return findCeil(root->right,input);
    int temp = findCeil(root->left,input);
    if(root->data < temp ) return root->data;
    return temp==-1? root->data : temp;
    
    // Your code here
}
```

