---
layout: post
title: Find the maximum GCD of the siblings of a Binary Tree                       
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/6eb51dc638ee1b936f38d1ab4b2f7062d4425463/1)  

Given a binary tree. The task is to find the maximum GCD of the siblings of this tree. You have to return the value of the node whose two immediate children has the maximum gcd.
If there are multiple such nodes, return the node which has the maximum value.

Siblings: Nodes with the same parent are called siblings.

GCD (Greatest Common Divisor) of two positive integers is the largest positive integer that divides both numbers without a remainder.

Note:
Return 0 if input tree is empty i.e level of tree is -1.
Consider those nodes which have a sibling.
Return 0 if no such pair of siblings found.
 

**Your Task:** 

You don't need to take input. Just complete the function maxGCD() that takes the root node as a parameter and returns the value of the node whose two immediate children has the maximum gcd.


**Expected Time Complexity:** `O(n)`              
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
              4
            /   \
           5     2
                /  \
               3    1
              /  \
             6   12

Output: 3
Explanation: For the above tree, the maximum
GCD for the siblings is formed for nodes 6 and 12
for the children of node 3.
```

**Example 2:**   
```
Input: 
            1
          /   \
        3      5
      /  \    /  \
     6    9  4    8

Output: 5
Explanation: For the above tree, the maximum
GCD for the siblings is formed for nodes 4 and 8
for the children of node 5.
```

### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= Data of a node  <= 10^5`


## Solutions

```cpp
/*
struct Node
{
    int data;
    struct Node* left;
    struct Node* right;
    
    Node(int x){
        data = x;
        left = right = NULL;
    }
};
 */


class Solution
{
public:
    int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);  
    }
    int mGcd = 0;
    int res = 0;
    void helper(Node* root){
        if(!root) return; 
        int cGcd=0;
        if(root->left&&root->right)
            cGcd = gcd(root->left->data, root->right->data);
        if(mGcd && cGcd == mGcd) { res = max(res, root->data); } 
        if(cGcd > mGcd) { res = root->data; mGcd = cGcd; }
        helper(root->left);
        helper(root->right);
    }
    int maxGCD( Node* root)
    {
        //code here
        helper(root);
        return res;
        
    }
};

```

