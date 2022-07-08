---
layout: post
title: Maximum sum of Non-adjacent nodes             
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/maximum-sum-of-non-adjacent-nodes/0/?#)  

Given a binary tree with a value associated with each node, we need to choose a subset of these nodes such that sum of chosen nodes is maximum under a constraint that no two chosen node in subset should be directly connected that is, if we have taken a node in our sum then we can’t take its any children or parents in consideration and vice versa.

<img src="http://cdncontribute.geeksforgeeks.org/wp-content/uploads/nodeSubsetWithMaxSum.png">


**Your Task:** 
You don't need to read input or print anything. You just have to complete function `getMaxSum()` which accepts root node of the tree as parameter and returns the maximum sum as described.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
     11
    /  \
   1    2
Output: 11
Explanation: The maximum sum is sum of
node 11.
```


**Example 2:**   
```
Input:
        1
      /   \
     2     3
    /     /  \
   4     5    6
Output: 16
Explanation: The maximum sum is sum of
nodes 1 4 5 6 , i.e 16. These nodes are
non adjacent.
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= value of node <= 10^5`

## Solutions

```cpp
class Solution{
  public:
    pair<int, int> nitish(Node* root){
        if(!root) return {0,0};
        pair<int,int> p1 = nitish(root->left);
        pair<int,int> p2 = nitish(root->right);
        int inc = p1.second + p2.second + root->data;
        int ninc = max(p1.first,p1.second) + max(p2.first,p2.second);
        return {inc,ninc};
        
    }
    //Function to return the maximum sum of non-adjacent nodes.
    int getMaxSum(Node *root) 
    {
        // Add your code here
        pair<int, int> res = nitish(root);
        return max(res.first,res.second);
    }
};
```

