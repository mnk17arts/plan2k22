---
layout: post
title: Given a linked list of 0s, 1s and 2s, sort it.     
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

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/0/)  

Given a linked list of `N` nodes where nodes can contain values `0`s, `1`s, and `2`s only. The task is to segregate `0`s, `1`s, and `2`s linked list such that all zeros segregate to head side, `2`s at the end of the linked list, and `1`s in the mid of `0`s and `2`s.  


**Your Task:** 
The task is to complete the function `segregate()` which segregates the nodes in the linked list as asked in the problem statement and returns the head of the modified linked list. The printing is done automatically by the driver code. 


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 8
value[] = {1,2,2,1,2,0,2,2}
Output: 0 1 1 2 2 2 2 2
Explanation: All the 0s are segregated
to the left end of the linked list,
2s to the right end of the list, and
1s in between.
```

**Example 2:**   
```
Input:
N = 4
value[] = {2,2,0,1}
Output: 0 1 2 2
Explanation: After arranging all the
0s,1s and 2s in the given format,
the output will be 0 1 2 2.
```


### Constraints

+ `1 <= N <= 10^3`

## Solutions

```cpp
class Solution{
    public:
   //Function to sort a linked list of 0s, 1s and 2s.
    Node* segregate(Node *head) {
        
        // Add code here
        if(head==NULL || head->next==NULL) return head;
        Node* zeroH = new Node(0), *oneH = new Node(0), *twoH = new Node(0);
        Node* zero = zeroH, *one = oneH, *two = twoH;
        while(head){
            if(head->data == 0) { zero->next = head; zero = zero->next; }
            else if(head->data == 1) { one->next = head; one = one->next; }
            else { two->next = head; two = two->next; }
            head = head->next;
        }
        zero->next = (oneH->next) ? (oneH->next) : (twoH->next) ;
        one->next = twoH->next;
        two->next = NULL;
        head = zeroH->next;
        delete zeroH, oneH, twoH;
        return head;
    }
};
```

