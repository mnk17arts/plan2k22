---
layout: post
title: Detect Loop in linked list  
summary:
tags:
    - linkedlist
    - 2pointers
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/detect-loop-in-linked-list/0/?track=DSASP-LinkedList&batchId=154)  

Given a linked list of `N` nodes. The task is to check if the linked list has a loop. Linked list can contain self loop.

**Your Task:** 
The task is to complete the function `detectloop()` which contains reference to the head as only argument. This function should return `true` if linked list contains loop, else return `false`.


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 3
value[] = {1,3,4}
x(position at which tail is connected) = 2
Output: True
Explanation: In above test case N = 3.
The linked list with nodes N = 3 is
given. Then value of x=2 is given which
means last node is connected with xth
node of linked list. Therefore, there
exists a loop.
```

**Example 2:**   
```
Input:
N = 4
value[] = {1,8,3,4}
x = 0
Output: False
Explanation: For N = 4 ,x = 0 means
then lastNode->next = NULL, then
the Linked list does not contains
any loop.
```


### Constraints

+ `1 <= N <= 10^4`
+ `1 <= data <= 10^3`

## Solutions

```cpp
class Solution{
    public:
    //Function to check if the linked list has a loop.
    bool detectLoop(Node* head)
    {
        // your code here
        if(head==NULL) return false;
        Node* fast=head, *slow=head;
        while(fast!=NULL && fast->next!=NULL){
            slow = slow->next;
            fast = fast->next->next;
            if(slow==fast) return true;
        }
        return false;
    }
};
```

