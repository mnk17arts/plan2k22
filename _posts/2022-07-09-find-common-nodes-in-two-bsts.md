---
layout: post
title: Find Common Nodes in two BSTs            
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/print-common-nodes-in-bst/0/?track=DSASP-BST&batchId=154)  

Given two Binary Search Trees. Find the nodes that are common in both of them, ie- find the intersection of the two BSTs.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `findCommon()` that takes roots of the two BSTs as input parameters and returns a list of integers containing the common nodes in sorted order.

**Expected Time Complexity:** `O(N1+N2)`      
**Expected Auxiliary Space:** `O(h1+h2)`  

### Examples

**Example 1:**   
```
Input:
BST1:
     10
    /  \
   2   11
  /  \
 1   3
BST2:
       2
     /  \
    1    3
Output: 1 2 3
```


**Example 2:**   
```
Input:
BST1:
                  5
               /     \
             1        10
           /   \      /
          0     4    7
                      \
                       9
BST2:
                10 
              /    \
             7     20
           /   \ 
          4     9
Output: 4 7 9 10
```


### Constraints

+ `1 <= Number of nodes <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to find the nodes that are common in both BST. 
    vector <int> findCommon(Node *root1, Node *root2)
    {
     //Your code here
     stack<Node*> s1, s2;
     Node* r1=root1, *r2=root2;
     vector<int> v;
     while((r1||!s1.empty())&&(r2||!s2.empty())){
         while(r1) { s1.push(r1); r1=r1->left; }
         while(r2) { s2.push(r2); r2=r2->left; }
         Node* t1=s1.top(), *t2=s2.top();
         if(t1->data==t2->data) { 
             v.push_back(t1->data); s1.pop(); s2.pop();
             r1=t1->right; r2=t2->right;
         }else if(t1->data > t2->data){
             s2.pop(); r2=t2->right;
         }else if(t1->data < t2->data){
             s1.pop(); r1=t1->right;
         }
     }
     return v;
        
    }
};
```

