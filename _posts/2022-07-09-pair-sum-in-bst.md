---
layout: post
title: Pair Sum in BST              
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/pair-sum-in-bst/0/?track=DSASP-BST&batchId=154#)  

Given a BST and a number X. The task is to check if any pair exists in BST or not whose sum is equal to X.


**Your Task:** 
Just write your code for the boolean function `findPair()` to check if a pair with given sum `X` exists in BST or not. The function returns `true` or `false`. The printing is done by the driver's code. 


**Expected Time Complexity:** `O(h)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
      0
       \
        1
         \ 
          3
        /  \
       2    7
             \
              8
X = 6
Output: 0
Explanation: For the given input , there
exists no such pair whose sum is 6. 
```


**Example 2:**   
```
Input:
      8
    /   \
   3     9
  / \
 1   5
X = 4
Output: 1
Explanation: For the given input, there
exist a pair whose sum is, i.e, (3,1).
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= value of nodes <= 10^5`

## Solutions

```cpp
//Function to check if any pair exists in BST whose sum is equal to given value.
bool check(Node* root, int x, unordered_set<int> &s){
    if(!root) return false;
    if(s.count(x - root->data)) return true;
    s.insert(root->data);
    return check(root->left,x,s)||check(root->right,x,s);
}
bool findPair(Node* root, int X) 
{
    // Your code here
    unordered_set<int> s;
    return check(root,X,s);
}
```

