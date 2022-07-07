---
layout: post
title:  Determine if Two Trees are Identical          
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/determine-if-two-trees-are-identical/0/?track=DSASP-Tree&batchId=154)  

Given two binary trees, the task is to find if both of them are identical or not. 



**Your Task:** 
Since this is a functional problem you don't have to worry about input, you just have to complete the function `isIdentical()` that takes two roots as parameters and returns true or false. The printing is done by the driver code.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(height of the tree)`  

### Examples

**Example 1:**   
```
Input:
    1       1
  /  \     /  \
 2    3   3    2
Output: No
Explanation: There are two trees both
having 3 nodes and 2 edges, but both
trees are not identical.
```


**Example 2:**   
```
Input:
     1          1
   /   \      /   \
  2     3    2     3
Output: Yes
Explanation: There are two trees both
having 3 nodes and 2 edges, both trees
are identical having the root as 1,
left child of 1 is 2 and right child
of 1 is 3.
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= Data of a node <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to check if two trees are identical.
    bool isIdentical(Node *r1, Node *r2)
    {
        //Your Code here
        if(r1 == NULL || r2 == NULL)  return(r1 == r2);
        return(r1 -> data == r2 -> data)
        && isIdentical(r1 -> left, r2 -> left)
        && isIdentical(r1 -> right, r2 -> right);
    }
};
```

