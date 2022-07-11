---
layout: post
title: Connect Nodes at Same Level          
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/connect-nodes-at-same-level/0/?#)  

Given a binary tree, connect the nodes that are at same level. You'll be given an addition nextRight pointer for the same.

Initially, all the nextRight pointers point to garbage values. Your function should set these pointers to point next right for each node.   
```
       10                   10 ------> NULL   
      / \                /      \    
     3   5       =>     3 ------> 5 --------> NULL   
    / \     \          /  \         \    
   4   1   2          4 --> 1 -----> 2 -------> NULL  
```


**Your Task:** 
You don't have to take input. Complete the function `connect()` that takes root as parameter and connects the nodes at same level. The printing is done by the driver code. First line of the output will be level order traversal and second line will be inorder travsersal

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
      10
    /   \
   20   30
  /  \
 40  60
Output:
10 20 30 40 60
40 20 60 10 30
Explanation:The connected tree is
         10 ----------> NULL
       /     \
     20 ------> 30 -------> NULL
  /    \
 40 ----> 60 ----------> NULL
```


**Example 2:**   
```
Input:
     3
   /  \
  1    2
Output:
3 1 2
1 3 2
Explanation:The connected tree is
        3 ------> NULL
     /    \
    1-----> 2 ------ NULL
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to connect nodes at same level.
    void connect(Node *root)
    {
       // Your Code Here
       queue<Node*> q;
       q.push(root);
       while(!q.empty()){
           int s = q.size();
           for(int i=0; i<s; i++){
               Node* t = q.front(); q.pop();
               if(i==s-1) t->nextRight = NULL;
               else { Node* t2=q.front(); t->nextRight=t2; }
               if(t->left) q.push(t->left);
               if(t->right) q.push(t->right);
           }
       }
    }  
};
```
