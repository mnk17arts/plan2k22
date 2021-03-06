---
layout: post
title: Get min at pop         
summary:
tags:
    - stack
    - recursion
    - geeksforgeeks
    - cpp
    - easy
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/get-min-at-pop/0/?t#)  

Now, we'll try to solve a famous stack problem.
You are given an array A of size N. You need to first push the elements of the array into a stack and then print minimum in the stack at each pop.

**Your Task:** 
Since this is a function problem, you don't need to take any input. Just complete the provided functions `_push()` and `_getMinAtPop()`. The `_push()` function takes an array as parameter, you need to push all elements of this array onto a stack and return the stack. The `_getMinAtPop()` accepts a stack as a parameter which is returned by `_push()` function and prints minimum in the stack at each pop separated by spaces.


**Expected Time Complexity:** `O(N)`
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 5
A = {1 2 3 4 5}
Output: 
1 1 1 1 1
Explanation: 
After pushing elements to the stack, 
the stack will be "top -> 5, 4, 3, 2, 1". 
Now, start popping elements from the stack
popping 5: min in the stack is 1.popped 5
popping 4: min in the stack is 1. popped 4
popping 3: min in the stack is 1. popped 3
popping 2: min in the stack is 1. popped 2
popping 1: min in the stack is 1. popped 1
```


**Example 2:**   
```
Input: 
N = 7
A = {1 6 43 1 2 0 5}
Output: 
0 0 1 1 1 1 1
Explanation: 
After pushing the elements to the stack, 
the stack will be 5->0->2->1->43->6->1. 
Now, poping the elements from the stack:
popping 5: min in the stack is 0. popped 5
popping 0: min in the stack is 0. popped 0
popping 2: min in the stack is 1. popped 2
popping 1: min in the stack is 1. popped 1
popping 43: min in the stack is 1. 
            popped 43
popping 6: min in the stack is 1. popped 6
popping 1: min in the stack is 1. popped 1.
```


### Constraints

+ `1 <= Ai <= 107`

## Solutions

```cpp
int cmin;
//Function to push all the elements into the stack.
stack<int> _push(int arr[],int n)
{
   // your code here
   stack<int> s;
   if(n==0) return s;
   s.push(arr[0]);
   cmin = arr[0];
   for(int i=1; i<n; i++){
       if(arr[i] < cmin){
           s.push( (2*arr[i]) - cmin );
           cmin = arr[i];
       }
       else s.push(arr[i]);
   }
   return s;
}

//Function to print minimum value in stack each time while popping.
void _getMinAtPop(stack<int>s)
{
    // your code here
    while(!s.empty()){
        if(s.top() < cmin) { cout << cmin << " "; cmin = (2*cmin) - s.top(); }
        else { cout << cmin << " "; }
        s.pop();
    }
}
```

