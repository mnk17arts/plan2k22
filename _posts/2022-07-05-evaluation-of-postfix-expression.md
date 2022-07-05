---
layout: post
title:  Evaluation of Postfix Expression          
summary:
tags:
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/evaluation-of-postfix-expression1735/0/?track=DSASP-Stack&batchId=154)  

Given string `S` representing a postfix expression, the task is to evaluate the expression and find the final value. Operators will only include the basic arithmetic operators like `*, /, +` and `-`.

**Your Task:** 
You do not need to read input or print anything. Complete the function `evaluatePostfixExpression()` that takes the string S denoting the expression as input parameter and returns the evaluated value.


**Expected Time Complexity:** `O(N)`
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input: S = "231*+9-"
Output: -4
Explanation:
After solving the given expression, 
we have -4 as result.
```


**Example 2:**   
```
Input: S = "123+*8-"
Output: -3
Explanation:
After solving the given postfix 
expression, we have -3 as result.
```


### Constraints

+ `1 ≤ |S| ≤ 10^5`
+ `0 ≤ |Si|≤ 9` (And given operators)

## Solutions

```cpp
class Solution {
    public:
    //Function to evaluate a postfix expression.
    int evaluatePostfix(string str)
    {
        // Your code here
        stack<int> s;
        for(char c: str){
            if(isdigit(c)) s.push(c-'0');
            else {
                int b = s.top(); s.pop();
                int a = s.top(); s.pop();
                switch(c){
                    case '+': s.push(a+b); break;
                    case '-': s.push(a-b); break;
                    case '*': s.push(a*b); break;
                    case '/': s.push(a/b); break;
                    default : break;
                }
            }
        }
        return s.top();
    }
};
```

