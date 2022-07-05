---
layout: post
title: Operations on Stack       
summary:
tags:
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/operations-on-stack/0/?track=DSASP-Stack&batchId=154)  

Given a stack of integers and `Q` queries. The task is to perform the operation on stack according to the query.

The queries can be of 4 types:

1. `i x`: (adds element `x` in the stack).

1. `r`: (removes the topmost element from the stack).

1. `h`: Prints the topmost element.

1. `f y`: (check if the element `y` is present or not in the stack). Print "Yes" if present, else "No".

**Your Task:** 
Your task is to complete functions `insert(), remove(), headOf_Stack()` which takes a stack as input parameter, and `find()` which takes a stack and value as input parameter, to insert, remove returning top element, and finding the element in stack respectively.


**Expected Time Complexity:**   
For find(): `O(N)`,
For others: `O(1)`. 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: 
Q = 6 
Queries = {(i, 2), (i, 4), (i, 3),
(i, 5), (h), (f, 8)}
Output: 
5
No
Explanation: 
Inserting 2, 4, 3, and 5 
onto the stack. Returning top element 
which is 5. Finding 8 will give No, 
as 8 is not in the stack.
```


**Example 2:**   
```
Input: 
Q = 4
Queries = {(i, 3), (i, 4), (r), (f, 3)}
Output: 
Yes
Explanation: 
Inserting 3 and 4 onto the 
stack. Finding 3 will give Yes as output 
because 3 is available in the stack.
```


### Constraints

+ `1 <= Q <= 1000`

## Solutions

```cpp
//Function to push an element into the stack.
void insert(stack<int> &s,int x)
{
    //Your code here
    s.push(x);
}

//Function to remove top element from stack.
void remove(stack<int> &s)
{
    s.pop();   
    //Your code here
}

//Function to print the top element of stack.
void headOf_Stack(stack<int> &s)
{
    int x=s.top();//Your code here
    cout<<x<<" "<<endl; 
}

//Function to search an element in the stack.
bool find(stack<int> s, int val)
{
    bool exists=false;
    
    //Your code here
    while(!s.empty()){
        if(s.top()==val) {exists = true; break;}
        s.pop();
    }
    
    if(exists==true){
        return true;
    }
    else{
        return false;
    }
}
```

