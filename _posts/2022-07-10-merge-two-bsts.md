---
layout: post
title:  Merge two BST 's            
summary:
tags:
    - tree
    - bst
    - stack
    - geeksforgeeks
    - cpp
    - hard
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/merge-two-bst-s/0/?track=DSASP-BST&batchId=154)  

Given two BSTs, return elements of both BSTs in sorted form.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `merge()` which takes roots of both the BSTs as its input and returns an array of integers denoting the node values of both the BSTs in a sorted order.



**Expected Time Complexity:** `O(M+N)` where `M` and `N` are the sizes if the two BSTs.          
**Expected Auxiliary Space:** `O(Height of BST1 + Height of BST2)` 


### Examples

**Example 1:**   
```
Input:
BST1:
       5
     /   \
    3     6
   / \
  2   4  
BST2:
        2
      /   \
     1     3
            \
             7
            /
           6
Output: 1 2 2 3 3 4 5 6 6 7
Explanation: 
After merging and sorting the
two BST we get 1 2 2 3 3 4 5 6 6 7.
```


**Example 2:**   
```
Input:
BST1:
       12
     /   
    9
   / \    
  6   11
BST2:
      8
    /  \
   5    10
  /
 2
Output: 2 5 6 8 9 10 11 12
Explanation: 
After merging and sorting the
two BST we get 2 5 6 8 9 10 11 12.
```


### Constraints

+ `1 <= N <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to return a list of integers denoting the node 
    //values of both the BST in a sorted order.
    void helper(Node* root, stack<Node*> &s){
        while(root){
            s.push(root); root = root->left;
        }
    }
    vector<int> merge(Node *root1, Node *root2)
    {
       //Your code here
       stack<Node*> s1,s2;
       vector<int> res;
       helper(root1,s1);
       helper(root2,s2);
       while(!s1.empty()&&!s2.empty()){
           Node* c1=s1.top(), *c2=s2.top();
           if(c1->data == c2->data){
               s1.pop(); s2.pop();
               res.push_back(c1->data);
               res.push_back(c2->data);
               if(c1->right) helper(c1->right,s1);
               if(c2->right) helper(c2->right,s2);
           }else if(c1->data < c2->data){
               s1.pop();
               res.push_back(c1->data);
               if(c1->right) helper(c1->right,s1);
           }else {
               s2.pop();
               res.push_back(c2->data);
               if(c2->right) helper(c2->right,s2);
           }
       }
       while(!s1.empty()){
            Node* c1=s1.top(); s1.pop();
            res.push_back(c1->data);
            if(c1->right) helper(c1->right,s1);          
       }
       while(!s2.empty()){
            Node* c2=s2.top(); s2.pop();
            res.push_back(c2->data);
            if(c2->right) helper(c2->right,s2);          
       }
       return res;
    }
};
```

