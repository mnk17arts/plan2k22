---
layout: post
title: Swap Kth nodes from ends 
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/swap-kth-node-from-beginning-and-kth-node-from-end-in-a-singly-linked-list/0/#)  

Given a singly linked list of size `N`, and an integer `K`. You need to swap the `K`th node from the beginning and `K`th node from the end of the linked list. Swap the nodes through the links. Do not change the content of the nodes.

**Your Task:** 
You do not need to read input or print anything. The task is to complete the function `swapkthnode()`, which has takes head of link list, `N` and `K` as input parameters and returns the new head.
The generated output will be `1` if you are able to complete your task. 


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 4,  K = 1
value[] = {1,2,3,4}
Output: 1
Explanation: Here K = 1, hence after
swapping the 1st node from the beginning
and end thenew list will be 4 2 3 1.
```

**Example 2:**   
```
Input:
N = 5,  K = 7
value[] = {1,2,3,4,5}
Output: 1
Explanation: K > N. Swapping is invalid. 
Return the head node as it is.
```


### Constraints

+ `1 <= N <= 10^3`
+ `1 <= K <= N`

## Solutions

```cpp
class Solution{
    public:
    //Function to swap Kth node from beginning and end in a linked list.
    Node *swapkthnode(Node* head, int num, int K)
    {
        // Your Code here
        if(head==NULL || K>num || num==1 || (num%2==1 && K==(num+1)/2)) return head;
        if(num==2) { Node* t=head->next; head->next=NULL; t->next=head; return t; }
        Node* start = head, *startP = NULL;
        for(int i=1; i<K; i++){ startP = start; start=start->next; }
        Node* end = head, *endP = NULL;
        for(int i=1; i<num-K+1; i++){ endP = end; end=end->next; }
        if(startP!=NULL) { startP->next = end; }
        if(endP!=NULL) { endP->next = start; }
        Node *temp = start->next;
        start->next = end->next;
        end->next = temp;
        if(K==1) head = end;
        if(K==num) head = start;
        return head;
        
    }
};
```

