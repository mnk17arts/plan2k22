---
layout: post
title: Diameter of a Binary Tree        
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/diameter-of-binary-tree/0/?track=DSASP-Tree&batchId=154#)  

The diameter of a tree (sometimes called the width) is the number of nodes on the longest path between two end nodes. The diagram below shows two trees each with diameter nine, the leaves that form the ends of the longest path are shaded (note that there is more than one path in each tree of length nine, but no path longer than nine nodes).   
<img src="https://contribute.geeksforgeeks.org/wp-content/uploads/diameter.jpg">


**Your Task:** 
You need to complete the function `diameter()` that takes root as parameter and returns the diameter.

**Expected Time Complexity:** `O(N)`     
**Expected Auxiliary Space:** `O(h)` , where h = height of tree  

### Examples

**Example 1:**   
```
Input:
       1
     /  \
    2    3
Output: 3
```


**Example 2:**   
```
Input:
         10
        /   \
      20    30
    /   \ 
   40   60
Output: 4
```


### Constraints

+ `1 <= Number of nodes <= 10^4`
+ `1 <= Data of a node <= 10^3`

## Solutions

```cpp
class Solution {
  public:
    // Function to return the diameter of a Binary Tree.
    int height(Node* root, int &res){
        if(!root) return 0;
        int lh = height(root->left, res);
        int rh = height(root->right, res);
        res = max(res, lh+rh+1);
        return max(lh,rh)+1;
    }
    int diameter(Node* root) {
        // Your code here
        int res=0;
        height(root, res);
        return res;
    }
};
```

