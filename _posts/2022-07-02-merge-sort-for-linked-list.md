---
layout: post
title: Merge Sort for Linked List     
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

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/sort-a-linked-list/0/?)  

Given Pointer/Reference to the head of the linked list, the task is to Sort the given linked list using Merge Sort.
Note: If the length of linked list is odd, then the extra node should go in the first list while splitting.  


**Your Task:** 
The task is to complete the function `mergeSort()` and return the node which can be used to print the sorted linked list.  


**Expected Time Complexity:** `O(N*Log(N))` 
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 5
value[]  = {3,5,2,4,1}
Output: 1 2 3 4 5
Explanation: After sorting the given
linked list, the resultant matrix
will be 1->2->3->4->5.
```

**Example 2:**   
```
Input:
N = 3
value[]  = {9,15,0}
Output: 0 9 15
Explanation: After sorting the given
linked list , resultant will be
0->9->15.
```


### Constraints

+ `1 <= T <= 100`
+ `1 <= N <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    Node *reverse(Node *head) {
        if(head==NULL || head->next==NULL) return head;
        Node *prev = NULL;
        Node *curr = head;
        Node *next;
        while (curr != NULL) {
            next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
    
    // check if the given linked list is palindrome or not
    bool isPalindrome(Node* head) {
        if(head == NULL || head->next==NULL) return true;
        Node* slow = head, *fast = head;
        while(fast->next != NULL && fast->next->next != NULL) {
            slow = slow->next;
            fast = fast->next->next;
        }
        Node* rev = reverse(slow->next);
        slow = head;
        while(rev != NULL) {
            if(rev->data != slow->data) {
                return false;
            }
            rev = rev->next;
            slow = slow->next;
        }
        return true;
    }
};
```

