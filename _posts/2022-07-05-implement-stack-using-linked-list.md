---
layout: post
title: Implement Stack using Linked List      
summary:
tags:
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/implement-stack-using-linked-list/0/?)  

Let's give it a try! You have a linked list and you have to implement the functionalities push and pop of stack using this given linked list. Your task is to use the class as shown in the comments in the code editor and complete the functions `push()` and `pop()` to implement a stack.


**Your Task:** 
You are required to complete two methods `push()` and `pop()`. The `push()` method takes one argument, an integer '`x`' to be pushed into the stack and `pop()` which returns an integer present at the top and popped out from the stack. If the stack is empty then return `-1` from the `pop()` method.


**Expected Time Complexity:** `O(1)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: 
push(2)
push(3)
pop()
push(4) 
pop()
Output: 3, 4
Explanation: 
push(2)    the stack will be {2}
push(3)    the stack will be {2 3}
pop()      poped element will be 3,
           the stack will be {2}
push(4)    the stack will be {2 4}
pop()      poped element will be 4
```


**Example 2:**   
```
Input: 
pop()
push(4)
push(5)
pop()
Output: -1, 5
```


### Constraints

+ `1 <= Q,x <= 100`

## Solutions

```cpp
//Function to push an integer into the stack.
void MyStack ::push(int x) 
{
    // Your Code
    StackNode *temp = new StackNode(x);
    temp->next = top;
    top = temp;
}

//Function to remove an item from top of the stack.
int MyStack ::pop() 
{
    // Your Code
    if(top==NULL) return -1;
    int data = top->data;
    StackNode* temp = top;
    top = top->next;
    delete temp;
    return data;
}
```

