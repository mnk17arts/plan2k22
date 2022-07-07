---
layout: post
title: Vertical Width of a Binary Tree        
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/vertical-width-of-a-binary-tree/0/?)  

Given a Binary Tree of `N` nodes. Find the vertical width of the tree.


**Your Task:** 
You don't have to read input or print anything. Your task is to complete the function `verticalWidth()` which takes root as the only parameter, and returns the vertical width of the binary tree.

**Expected Time Complexity:** `O(N)`     
**Expected Auxiliary Space:** `O(h)` , where h = height of tree  

### Examples

**Example 1:**   
```
Input:
          1
       /    \
      2      3
     / \    / \
    4   5  6   7
            \   \
             8   9
Output: 6
Explanation: The width of a binary tree is
the number of vertical paths in that tree.
```
<img src="https://cdncontribute.geeksforgeeks.org/wp-content/uploads/tree2-8.png">   

```
The above tree contains 6 vertical lines.
```

**Example 2:**   
```
Input:
      1
    /  \
   2    3
Output: 3
```


### Constraints

+ `1 <= Number of nodes <= 10^5`

## Solutions

```cpp
void indexes(Node* root, unordered_set<int> &us, int i){
    if(!root) return;
    us.insert(i);
    indexes(root->left, us, i-1);
    indexes(root->right, us, i+1);
}

//Function to find the vertical width of a Binary Tree.
int verticalWidth(Node* root)
{
    // Code here
    unordered_set<int> us;
    indexes(root, us, 0);
    return us.size();
}
```

