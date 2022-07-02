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

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/add-two-numbers-represented-by-linked-list/0/?#)  

Given two numbers represented by two linked lists, write a function that returns Sum list. The sum list is linked list representation of addition of two input numbers. 


**Your Task:** 
The task is to complete the function `addSameSize()` `addCarryToRemaining()`. 


### Examples

**Example 1:**   
```
Input:
S1 = 3, S2 = 3
ValueS1 = {2,3,4}
ValueS2 = {3,4,5}
Output: 5 7 9
Explanation: After adding the 2 numbers
the resultant number is 5 7 9.
```

**Example 2:**   
```
Input:
S1 = 1, S2 = 2
ValueS1 = {9}
ValueS2 = {8,7}
Output: 9 6
Explanation: Add 9 and 7 we get 16.
1 is carry here and is added to 8.
So the answer is 9 6
```


### Constraints

+ `1 <= N,M <= 100`

## Solutions

```cpp
class Solution{
    public:
    //Function which adds two linked lists of same size.
    //Function which adds two linked lists of same size represented by head1  
    //and head2 and returns head of the resultant linked list. Carry
    //is propagated while returning from the recursion
    Node* addSameSize(Node* head1, Node* head2, int* carry) 
    { 
        // Your code here
        if(!head1 && !head2) { *carry = 0; return NULL; }
        Node* temp = addSameSize(head1->next,head2->next,carry);
        int sum = head1->data + head2->data;
        sum += *carry;
        head1->data = sum%10;
        *carry = sum/10;
        return head1;
    } 


    //This function is called after the smaller list is added to the sublist of 
    //bigger list of same size. Once the right sublist is added, the carry
    //must be added to left side of larger list to get the final result.
    void addCarryToRemaining(Node* head1, Node* curr, int* carry, Node** result) 
    { 
        // Your code here
        if(head1==curr) return;
        addCarryToRemaining(head1->next,curr,carry,result);
        int sum = head1->data + *carry;
        *carry = sum/10;
        head1->data = sum%10;
        curr = head1;
        *result = head1;
    }
};
```

