---
layout: post
title: Merge Sort on Doubly Linked List     
summary:
tags:
    - linkedlist
    - merge-sort
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/merge-sort-on-doubly-linked-list/0/?track=DSASP-LinkedList&batchId=154#)  

Given Pointer/Reference to the head of a doubly linked list of `N` nodes, the task is to Sort the given doubly linked list using Merge Sort in both non-decreasing and non-increasing order. 


**Your Task:** 
The task is to complete the function `sortDoubly()` which sorts the doubly linked list. The printing is done automatically by the driver code. 


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 8
value[] = {7,3,5,2,6,4,1,8}
Output:
1 2 3 4 5 6 7 8
8 7 6 5 4 3 2 1
Explanation: After sorting the given
linked list in both ways, resultant
matrix will be as given in the first
two line of output, where first line
is the output for non-decreasing
order and next line is for non-
increasing order.
```

**Example 2:**   
```
Input:
N = 5
value[] = {9,15,0,-1,0}
Output:
-1 0 0 9 15
15 9 0 0 -1
Explanation: After sorting the given
linked list in both ways, the
resultant list will be -1 0 0 9 15
in non-decreasing order and 
15 9 0 0 -1 in non-increasing order.
```


### Constraints

+ `1 <= N <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    Node* merge(Node* head1, Node* head2) {
        if (head1 == NULL) return head2;
        if (head2 == NULL) return head1;
        Node* head = new Node(0);
        Node* temp = head;
        while(head1 && head2){
            if(head1->data <= head2->data) { temp->next = head1; head1->prev = temp; temp = head1; head1=head1->next; }
            else { temp->next = head2; head2->prev = temp; temp = head2; head2=head2->next; }
        }
        if(head1) {temp->next = head1; head1->prev=temp;}
        if(head2) {temp->next = head2; head2->prev=temp;}
        Node* res = head->next;
        res->prev = NULL;
        delete head;
        return res;
    }
    //Function to sort the given doubly linked list using Merge Sort.
    struct Node *sortDoubly(struct Node *head)
    {
        // Your code here
        if (head == NULL || head->next == NULL) return head;
        Node* slow = head, *fast = head->next;
        while (fast != NULL && fast->next != NULL) {
            slow = slow->next;
            fast = fast->next->next;
        }
        
        Node* left = head;
        Node* right = slow->next;
        slow->next = NULL;
        left = sortDoubly(left);
        right = sortDoubly(right);
        return merge(left, right);
    }
};
```

