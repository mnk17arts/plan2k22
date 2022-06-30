---
layout: post
title: Merge two sorted linked lists     
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/merge-two-sorted-linked-lists/0/?)  

Given two sorted linked lists consisting of `N` and `M` nodes respectively. The task is to merge both of the list (in-place) and return head of the merged list.

**Your Task:** 
The task is to complete the function `sortedMerge()` which takes references to the heads of two linked lists as the arguments and returns the head of merged linked list.


**Expected Time Complexity:** `O(N+M)`    
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 4, M = 3 
valueN[] = {5,10,15,40}
valueM[] = {2,3,20}
Output: 2 3 5 10 15 20 40
Explanation: After merging the two linked
lists, we have merged list as 2, 3, 5,
10, 15, 20, 40.
```

**Example 2:**   
```
Input:
N = 2, M = 2
valueN[] = {1,1}
valueM[] = {2,4}
Output:1 1 2 4
Explanation: After merging the given two
linked list , we have 1, 1, 2, 4 as
output.
```

### Constraints

+ `1 <= N,M <= 10^4`
+ `1 <= data <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    /*
    struct Node {
    int data;
    struct Node *next;
    Node(int x) {
        data = x;
        next = NULL;
    }
    };
    */

    //Function to merge two sorted linked list.
    Node* sortedMerge(Node* head1, Node* head2)  
    {  
        // code here
        Node* head, *tail;
        if(head1->data <= head2->data) {
            head = tail = head1; head1 = head1->next;
        }else { head = tail = head2; head2 = head2->next; }
        while(head1!=NULL && head2!=NULL){
            if(head1->data <= head2->data){
                tail->next = head1;
                tail = head1;
                head1 = head1->next;
            }else {
                tail->next = head2;
                tail = head2;
                head2 = head2->next;
            }
        }
        if(head1==NULL) tail->next = head2;
        else tail->next = head1;
        return head;
    }  
};
```

