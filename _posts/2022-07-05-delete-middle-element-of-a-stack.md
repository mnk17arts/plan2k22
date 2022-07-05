---
layout: post
title: Delete middle element of a stack         
summary:
tags:
    - stack
    - recursion
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/delete-middle-element-of-a-stack/0/?t)  

Given a stack with `push(), pop(), empty()` operations, delete the middle of the stack without using any additional data structure.
Middle: `ceil((size_of_stack+1)/2)` (1-based index)

**Your Task:** 
You don't need to read input or print anything. Complete the function `deleteMid()` which takes the stack and its size as input parameters and modifies the stack in-place.
**Note**: The output shows the stack from top to bottom.


**Expected Time Complexity:** `O(N)`
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input: 
Stack = {1, 2, 3, 4, 5}
Output:
ModifiedStack = {1, 2, 4, 5}
Explanation:
As the number of elements is 5 , 
hence the middle element will be the 3rd
element which is deleted
```


**Example 2:**   
```
Input: 
Stack = {1 2 3 4}
Output:
ModifiedStack = {1 3 4}
Explanation:
As the number of elements is 4 , 
hence the middle element will be the 2nd
element which is deleted
```


### Constraints

+ `2 ≤ size of stack ≤ 100`

## Solutions

```cpp
class Solution
{
    public:
    //Function to delete middle element of a stack.
    void del(stack<int>&s, int n, int c){
        if(c==n/2) { s.pop(); return; }
        int d = s.top();
        s.pop();
        del(s,n,c+1);
        s.push(d);
    }
    void deleteMid(stack<int>&s, int sizeOfStack)
    {
        // code here.. 
        del(s,sizeOfStack,0);
    }
};
```

