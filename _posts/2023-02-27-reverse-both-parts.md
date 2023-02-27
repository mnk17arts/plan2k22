---
layout: post
title: Reverse both parts
summary:
tags:
  - geeksforgeeks
  - linkedlist
  - cpp
  - easy
minute: 8+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/bae68b4d6a2a77fb6bd459cf7447240919ebfbf5/1)

Given a linked list and a number k. You have to reverse first part of linked list with k nodes and the second part with n-k nodes.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function reverse() which takes head node of the linked list and a integer k as input parameters and returns head node of the linked list after reversing both parts. 


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`   


### Examples

**Example 1:**

```
Input: 1 -> 2 -> 3 -> 4 -> 5
k = 2
Output: 2 -> 1 -> 5 -> 4 -> 3
Explanation: As k = 2 , so the first part 2
nodes: 1 -> 2 and the second part with 3 nodes:
3 -> 4 -> 5. Now after reversing the first part: 
2 -> 1 and the second part: 5 -> 4 -> 3.
So the output is: 2 -> 1 -> 5 -> 4 -> 3
```

**Example 2:**

```
Input: 1 -> 2 -> 4 -> 3
k = 3
Output: 4 -> 2 -> 1 -> 3
Explanation: As k = 3 , so the first part 
3 nodes: 4 -> 2 -> 1 and the second part
with 1 nodes: 3. Now after reversing the 
first part: 1 -> 2 -> 4 and the 
second part: 3. So the output is: 1 -> 2 -> 4 -> 3
```


### Constraints

- `1 <= Number of queries <= 100`
- `1 <= values of the stack <= 100`

## Solutions

```cpp

/*
Definition for singly Link List Node
struct Node
{
    int data;
    struct Node *next;

    Node(int x)
    {
        data = x;
        next = NULL;
    }
};
*/


class Solution {
public:
   
    Node *reverse(Node *head, int k) {
        Node *cur = head, *prev  =NULL, *nxt;
        int cnt = 0;
        while(cur && cnt < k) {
            nxt = cur->next;
            cur->next = prev;
            prev = cur;
            cur = nxt;
            cnt++;
        }
        if(nxt != NULL)  {
            head->next = reverse(nxt, INT_MAX);
        }
        return prev;
    }
};

```
