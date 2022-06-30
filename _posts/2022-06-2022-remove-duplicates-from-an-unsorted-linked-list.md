---
layout: post
title: Remove duplicates from an unsorted linked list     
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/remove-duplicates-from-an-unsorted-linked-list/0/)  

Given an unsorted linked list of `N` nodes. The task is to remove duplicate elements from this unsorted Linked List. When a value appears in multiple nodes, the node which appeared first should be kept, all others duplicates are to be removed.

**Your Task:** 
You have to complete the method `removeDuplicates()` which takes `1` argument: the `head` of the linked list.  Your function should return a pointer to a linked list with no duplicate element.


**Expected Time Complexity:** `O(N)`    
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 4
value[] = {5,2,2,4}
Output: 5 2 4
Explanation:Given linked list elements are
5->2->2->4, in which 2 is repeated only.
So, we will delete the extra repeated
elements 2 from the linked list and the
resultant linked list will contain 5->2->4
```

**Example 2:**   
```
Input:
N = 5
value[] = {2,2,2,2,2}
Output: 2
Explanation:Given linked list elements are
2->2->2->2->2, in which 2 is repeated. So,
we will delete the extra repeated elements
2 from the linked list and the resultant
linked list will contain only 2.
```

### Constraints

+ `1 <= N <= 10^6`
+ `0 <= data <= 10^4`

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

    //Function to remove duplicates from unsorted linked list.
    Node * removeDuplicates( Node *head) 
    {
        // your code goes here
        unordered_set<int> s;
        Node* res = head;
        s.insert(head->data);
        while(head!=NULL && head->next!=NULL){
         if(s.find(head->next->data)!=s.end()){
             Node* temp = head->next;
             head->next = temp->next;
             delete temp;
         }else {
             s.insert(head->next->data);
             head = head->next;
         }
        }
        return res;
    }
};
```

