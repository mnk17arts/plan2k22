---
layout: post
title: Find the Closest Element in BST           
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/find-the-closest-element-in-bst/0/?track=DSASP-BST&batchId=154#)  

Given a BST and an integer. Find the least absolute difference between any node value of the BST and the given integer.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `minDiff()` that takes the root of the BST and an integer K as its input and returns the minimum absolute difference between any node value of the BST and the integer K. 

**Expected Time Complexity:** `O(h)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
      8
    /   \
   1     9
    \     \
     4    10
    /
   3
K = 9
Output: 0
Explanation: K=9. The node that has
value nearest to K is 9. so the answer
is 0.
```   

**Example 2:**   
```
Input:
        10
      /   \
     2    11
   /  \ 
  1    5
      /  \
     3    6
      \
       4
K = 13
Output: 2
Explanation: K=13. The node that has
value nearest to K is 11. so the answer
is 2
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= data <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to find the least absolute difference between any node
	//value of the BST and the given integer.
    int findCeil(Node* root, int input) {
        if (!root) return -1;
        if(root->data==input) return input;
        if(root->data<input) return findCeil(root->right,input);
        int temp = findCeil(root->left,input);
        if(root->data < temp ) return root->data;
        return temp==-1? root->data : temp;
    }
    int floor(Node* root, int key) {
        // Your code goes here
        if(!root) return -1;
        if(root->data==key) return key;
        else if(root->data > key) return floor(root->left,key);
        int temp = floor(root->right,key);
        if(root->data > temp) return root->data;
        else return temp;
    }
    int minDiff(Node *root, int K)
    {
        //Your code here
        int c = abs(K - findCeil(root,K));
        int f = abs(K - floor(root,K));
        return min(c,f);
    }

};
```

