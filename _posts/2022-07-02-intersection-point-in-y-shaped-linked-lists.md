---
layout: post
title: Intersection Point in Y Shapped Linked Lists     
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/intersection-point-in-y-shapped-linked-lists/0/?track=DSASP-LinkedList&batchId=154)  

Given two singly linked lists of size `N` and `M`, write a program to get the point where two linked lists intersect each other.


**Your Task:** 
You don't need to read input or print anything. The task is to complete the function `intersetPoint()` which takes the pointer to the head of linklist1(`head1`) and linklist2(`head2`) as input parameters and returns data value of a node where two linked lists intersect. If linked list do not merge at any point, then it should return `-1`.
**Challenge** : Try to solve the problem without using any extra space.


**Expected Time Complexity:** `O(N+M)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
LinkList1 = 3->6->9->common
LinkList2 = 10->common
common = 15->30->NULL
Output: 15
Explanation:
```
<img src="https://contribute.geeksforgeeks.org/wp-content/uploads/linked.jpg">


**Example 2:**   
```
Input: 
Linked List 1 = 4->1->common
Linked List 2 = 5->6->1->common
common = 8->4->5->NULL
Output: 8
Explanation: 

4              5
|              |
1              6
 \             /
  8   -----  1 
   |
   4
   |
  5
  |
  NULL  
```


### Constraints

+ `1 <= N+M <= 2*10^5`
+ `-1000 <= data <= 1000`

## Solutions

```cpp
class Solution{
    public:
    //Function to find intersection point in Y shaped Linked Lists.
    int intersectPoint(Node* head1, Node* head2)
    {
        Node* temp1 = head1;
        Node* temp2 = head2;
        int count1 = 0;
        int count2 = 0;
        while(temp1 != NULL) {
            temp1 = temp1->next;
            count1++;
        }
        while(temp2 != NULL) {
            temp2 = temp2->next;
            count2++;
        }
        temp1 = head1;
        temp2 = head2;
        if(count1 > count2) {
            int diff = count1 - count2;
            while(diff--) {
                temp1 = temp1->next;
            }
        } else {
            int diff = count2 - count1;
            while(diff--) {
                temp2 = temp2->next;
            }
        }
        while(temp1 != NULL && temp2 != NULL) {
            if(temp1 == temp2) {
                return temp1->data;
            }
            temp1 = temp1->next;
            temp2 = temp2->next;
        }
        return -1;
    }
};
```

