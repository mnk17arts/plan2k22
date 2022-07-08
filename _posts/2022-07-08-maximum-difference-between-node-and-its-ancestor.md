---
layout: post
title: Maximum difference between node and its ancestor           
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/maximum-difference-between-node-and-its-ancestor/0/?tr)  

Given a Binary Tree, you need to find the maximum value which you can get by subtracting the value of node B from the value of node A, where A and B are two nodes of the binary tree and A is an ancestor of B. 


**Your Task:** 
The task is to complete the function maxDiff() which finds the maximum difference between the node and its ancestor.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
      1
    /    \
   2      3
           \
            7
Output: -1
Explanation:The maximum difference we can
get is -1, which is between 1 and 2.
```


**Example 2:**   
```
Input:
    5
 /    \
2      1
Output: 4
Explanation:The maximum difference we can
get is 4, which is bewteen 5 and 1.
```


### Constraints

+ `2 <= Number of nodes <= 10^4`
+ `1 <= |data| <= 10^4`

## Solutions

```cpp
class Solution {
  public:
    //Function to return the maximum difference between any node and its ancestor.
    int nitish(Node* root, int &res){
        if(!root) return INT_MAX;
        if(!root->left&&!root->right)return root->data;
        int l = nitish(root->left, res);
        int r = nitish(root->right, res);
        int minv = min(l,r);
        res = max(res, root->data-minv);
        return min(minv, root->data);
    }
    int maxDiff(Node* root)
    {
        // Your code here 
        int res = INT_MIN;
        nitish(root, res);
        return res;
    }
};
```

