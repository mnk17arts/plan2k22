---
layout: post
title: Parenthesis Checker   
summary:
tags:
    - string
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/parenthesis-checker2744/1#)  

Given an expression string x. Examine whether the pairs and the orders of `“{“,”}”,”(“,”)”,”[“,”]”` are correct in exp.
For example, the function should return '`true`' for exp = `“[()]{}{[()()]()}”` and '`false`' for exp = `“[(])”`.

**Your Task:** 
This is a function problem. You only need to complete the function `ispar()` that takes a string as a parameter and returns a boolean value `true` if brackets are balanced else returns `false`. The printing is done automatically by the driver code.


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
{([])}
Output: 
true
Explanation: 
{ ( [ ] ) }. Same colored brackets can form 
balaced pairs, with 0 number of 
unbalanced bracket.
```

**Example 2:**   
```
Input: 
()
Output: 
true
Explanation: 
(). Same bracket can form balanced pairs, 
and here only 1 type of bracket is 
present and in balanced way.
```

**Example 3:**   
```
Input: 
([]
Output: 
false
Explanation: 
([]. Here square bracket is balanced but 
the small bracket is not balanced and 
Hence , the output will be unbalanced.
```

### Constraints

+ `1 <= N <= 32000`

## Solutions

```cpp
class Solution{
    public:
    //Function to check if brackets are balanced or not.
    bool ispar(string x)
    {
        // Your code here
        stack<char> s;
        int n=x.size();
        for(int i=0;i<n;i++)
            if(x[i]=='(' || x[i]=='{' || x[i]=='[')
                s.push(x[i]);
            else if( !s.empty() && ((x[i]==')'&&s.top()=='(')
                     || (x[i]=='}'&&s.top()=='{') 
                     || (x[i]==']'&&s.top()=='[')))
                         s.pop();
            else return false;
        if(s.size()==0) return true;
        return false;                     
    }
};
```

