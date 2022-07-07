---
layout: post
title: Check if subtree         
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/check-if-subtree/0/?t)  

Given two binary trees with head reference as `T` and `S` having at most `N` nodes. The task is to check if `S` is present as subtree in `T`.
A subtree of a tree `T1` is a tree `T2` consisting of a node in `T1` and all of its descendants in `T1`.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `isSubtree()` that takes root node of `S` and `T` as parameters and returns `1` if `S` is a subtree of `T` else `0`.

**Note**: The nodes can have the duplicate values.

**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`   

### Examples

**Example 1:**   
```
Input:
T:      1          S:   3
      /   \            /
     2     3          4
   /  \    /
  N    N  4
Output: 1 
Explanation: S is present in T
```

**Example 2:**   
```
Input:
T:      26         S:   26
       /   \           /  \
     10     N        10    N
   /    \           /  \
   20    30        20  30
  /  \            /  \
 40   60         40  60
Output: 1 
Explanation: 
S and T are both same. Hence, 
it can be said that S is a subtree 
of T.
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^4`

## Solutions

```cpp
class Solution
{
  public:
    bool check(Node* T, Node* S){
        if(!T && !S) return true;
        if(!T || !S) return false;
        if(T->data != S->data) return false;
        return check(T->left,S->left) && check(T->right,S->right);
        
    }
    //Function to check if S is a subtree of tree T.
    bool isSubTree(Node* T, Node* S) 
    {
        // Your code here
        if(!T) return false;
        if(T->data==S->data) if(check(T,S)) return true;
        return isSubTree(T->left,S) || isSubTree(T->right,S);
        
    }
};
```

