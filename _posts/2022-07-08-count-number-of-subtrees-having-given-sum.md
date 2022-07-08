---
layout: post
title: Count Number of SubTrees having given Sum           
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-number-of-subtrees-having-given-sum/0/?tr#)  

Given a binary tree and an integer `X`. Your task is to complete the function `countSubtreesWithSumX()` that returns the count of the number of subtress having total node’s data sum equal to the value `X`.
Example: For the tree given below:            
```
              5
            /    \
        -10     3
        /    \    /  \
      9     8  -4 7

Subtree with sum 7:
             -10
            /      \
          9        8

and one node 7.
```

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `countSubtreesWithSumX()` which takes the root node and an integer `X` as inputs and returns the number of subtrees of the given Binary Tree having sum exactly equal to `X`.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
    1
  /  \
 2    3
X = 5
Output: 0
Explanation: No subtree has sum equal
to 5.
```


**Example 2:**   
```
Input:
       5
    /    \
  -10     3
 /   \   /  \
 9   8 -4    7
X = 7
Output: 2
Explanation: Subtrees with sum 7 are
[9, 8, -10] and [7] (refer the example
in the problem description).
```


### Constraints

+ `1 <= Number of nodes <= 10^3`
+ `-10^3 <= Node value <= 10^3`

## Solutions

```cpp
class Solution {
  public:
    int nitish(Node* root, int x, int &res){
        if(!root) return 0;
        int l = nitish(root->left,x,res);
        int r = nitish(root->right,x,res);
        if(l+r+root->data == x) res++;
        return l+r+root->data;
    }
    //Function to count number of subtrees having sum equal to given sum.
    int countSubtreesWithSumX(Node* root, int X)
    {
        // Code here
        int res = 0;
        nitish(root, X, res);
        return res;
    }
};
```

