---
layout: post
title: Maximum path sum from any node           
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/maximum-path-sum-from-any-node/0/?#)  

Given a binary tree, the task is to find the maximum path sum. The path may start and end at any node in the tree.


**Your Task:** 
You don't need to take input or print anything. Your task is to complete the function findMaxSum() that takes root as input and returns max sum between any two nodes in the given Binary Tree.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
     10
   /    \
  2      5
          \
          -2
Output: 17
Explanation: Path in the given tree goes
like 2 , 10 , 5 which gives the max sum
as 17.
```


**Example 2:**   
```
Input:
     10
    /  \
   2   -25
  / \  /  \
 20 1  3  4
Output: 32
Explanation: Path in the given tree goes
like 10 , 2 , 20 which gives the max
sum as 32.
```


### Constraints

+ `1 <= Number of nodes <= 10^3`
+ `1 <= |data| <= 10^4`

## Solutions

```cpp
class Solution {
  public:
    int findMax(Node* root, int &res){
        if(!root) return 0;
        int ls = max(0, findMax(root->left, res));
        int rs = max(0, findMax(root->right, res));
        res = max(res, ls+rs+root->data);
        return max(ls,rs)+root->data;
    }
    //Function to return maximum path sum from any node in a tree.
    int findMaxSum(Node* root)
    {
        // Your code goes here
        int res = INT_MIN;
        findMax(root, res);
        return res;
    }
};
```

