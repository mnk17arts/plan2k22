---
layout: post
title: Pairwise swap of nodes in LinkedList     
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/pairwise-swap-of-nodes-in-linkelist/0/?track=DSASP-LinkedList&batchId=154#)  

Given a linked list of N positive integers. You need to swap elements pairwise. Your task is to complete the function `pairwise_swap()`.  


**Your Task:** 
You don't have to worry about input and output, you just have to complete the function `pairwise_swap()`. The printing is done automatically by the driver code.   


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 7
value[] = {1,2,3,4,5,6,7}
Output: 2 1 4 3 6 5 7
Explanation:The linked list after swapping
becomes: 1 2 3 4 5 6 7 -> 2 1 4 3 6 5 7.
```

**Example 2:**   
```
Input:
N = 6
value[] = {1,2,3,4,5,6}
Output: 2 1 4 3 6 5
Explanation:The linked list after swapping
becomes: 1 2 3 4 5 6 -> 2 1 4 3 6 5.
```


### Constraints

+ `2 <= N <= 100`
+ `1 <= data <= 1000`

## Solutions

```cpp
class Solution{
    public:
    //Function to swap elements pairwise.
    struct Node* pairwise_swap(struct Node* head)
    {
        // your code here
        if(head==NULL || head->next==NULL) return head;
        Node* curr = head->next->next;
        Node* prev = head->next;
        prev->next = head;
        head->next = curr;
        head = prev;
        prev = head->next;
        while(curr != NULL && curr->next != NULL) {
            Node* temp = curr->next;
            curr->next = curr->next->next;
            temp->next = curr;
            curr = curr->next;
            prev->next = temp;
            prev = temp->next;
        }
        return head;
    }
};
```

