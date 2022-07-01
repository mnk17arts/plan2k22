---
layout: post
title: Rotate a Linked List    
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/rotate-a-linked-list/0/?)  

Given a singly linked list of size N. The task is to left-shift the linked list by k nodes, where k is a given positive integer smaller than or equal to length of the linked list.  


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `rotate()` which takes a head reference as the first argument and k as the second argument, and returns the head of the rotated linked list.


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 5
value[] = {2, 4, 7, 8, 9}
k = 3
Output: 8 9 2 4 7
Explanation:
Rotate 1: 4 -> 7 -> 8 -> 9 -> 2
Rotate 2: 7 -> 8 -> 9 -> 2 -> 4
Rotate 3: 8 -> 9 -> 2 -> 4 -> 7
```

**Example 2:**   
```
Input:
N = 8
value[] = {1, 2, 3, 4, 5, 6, 7, 8}
k = 4
Output: 5 6 7 8 1 2 3 4
```


### Constraints

+ `1 <= N <= 10^4`

## Solutions

```cpp
class Solution{
    public:
    //Function to rotate a linked list.
    Node* rotate(Node* head, int k)
    {
        // Your code here
        Node* two = head;
        for(int i=1;i<k;i++) head=head->next;
        if(head->next==NULL) return two;
        Node* one = head->next;
        head->next = NULL;
        head = one;
        while(one->next!=NULL) one=one->next;
        one->next = two;
        return head;
    }
};
```

