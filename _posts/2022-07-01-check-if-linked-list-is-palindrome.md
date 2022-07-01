---
layout: post
title: Check if Linked List is Palindrome     
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/check-if-linked-list-is-pallindrome/0/?)  

Given a singly linked list of size `N` of integers. The task is to check if the given linked list is palindrome or not.  


**Your Task:** 
The task is to complete the function `isPalindrome()` which takes head as reference as the only parameter and returns `true` or `false` if linked list is palindrome or not respectively.   


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 3
value[] = {1,2,1}
Output: 1
Explanation: The given linked list is
1 2 1 , which is a palindrome and
Hence, the output is 1.
```

**Example 2:**   
```
Input:
N = 4
value[] = {1,2,3,4}
Output: 0
Explanation: The given linked list
is 1 2 3 4 , which is not a palindrome
and Hence, the output is 0.
```


### Constraints

+ `1 <= N <= 10000`

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

