---
layout: post
title: Add two numbers represented by linked lists    
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/add-two-numbers-represented-by-linked-lists/0/?track=DSASP-LinkedList&batchId=154#)  

Given two numbers represented by two linked lists of size `N` and `M`. The task is to return a sum list.

> The sum list is a linked list representation of the addition of two input numbers from the last.  


**Your Task:** 
The task is to complete the function `addTwoLists()` which has node reference of both the linked lists and returns the head of the sum list.   


**Expected Time Complexity:** `O(N+M)` 
**Expected Auxiliary Space:** `O(max(N,M))`

### Examples

**Example 1:**   
```
Input:
N = 2
valueN[] = {4,5}
M = 3
valueM[] = {3,4,5}
Output: 3 9 0  
Explanation: For the given two linked
list (4 5) and (3 4 5), after adding
the two linked list resultant linked
list will be (3 9 0).
```

**Example 2:**   
```
Input:
N = 2
valueN[] = {6,3}
M = 1
valueM[] = {7}
Output: 7 0
Explanation: For the given two linked
list (6 3) and (7), after adding the
two linked list resultant linked list
will be (7 0).
```


### Constraints

+ `1 <= N,M <= 5000`

## Solutions

```cpp
class Solution{
    public:
    // reverse linked list
    Node* reverse(Node* head) {
        if(head == NULL || head->next == NULL) return head;
        Node* prev = NULL;
        Node* curr = head;
        Node* next = head->next;
        while(next != NULL) {
            curr->next = prev;
            prev = curr;
            curr = next;
            next = next->next;
        }
        curr->next = prev;
        return curr;
    }
    
    //Function to add two numbers represented by linked list.
    struct Node* addTwoLists(struct Node* head1, struct Node* head2)
    {   head1 = reverse(head1);
        head2 = reverse(head2); 
        Node* head = NULL;
        Node* curr = NULL;
        int carry = 0;
        while(head1 != NULL || head2 != NULL) {
            int sum = 0;
            if(head1 != NULL) {
                sum += head1->data;
                head1 = head1->next;
            }
            if(head2 != NULL) {
                sum += head2->data;
                head2 = head2->next;
            }
            sum += carry;
            if(sum >= 10) {
                sum -= 10;
                carry = 1;
            } else {
                carry = 0;
            }
            if(head == NULL) {
                head = new Node(sum);
                curr = head;
            } else {
                curr->next = new Node(sum);
                curr = curr->next;
            }
        }
        if(carry > 0) {
            curr->next = new Node(carry);
        }
        return reverse(head);
    }
};
```

