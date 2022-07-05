---
layout: post
title: Infix to Postfix        
summary:
tags:
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/infix-to-postfix-1587115620/0/?track=DSASP-Stack&batchId=154)  

Given an infix expression in the form of string `str`. Convert this infix expression to postfix expression.

+ Infix expression: The expression of the form `a op b`. When an operator is in-between every pair of operands.
+ Postfix expression: The expression of the form `a b op`. When an operator is followed for every pair of operands.

Note: The order of precedence is: `^` greater than `*` equals to `/` greater than `+` equals to `-`

**Your Task:** 
This is a function problem. You only need to complete the function `infixToPostfix()` that takes a string(Infix Expression) as a parameter and returns a string(postfix expression). The printing is done automatically by the driver code.


**Expected Time Complexity:** `O(N)`
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input: str = "a+b*(c^d-e)^(f+g*h)-i"
Output: abcd^e-fgh*+^*+i-
Explanation:
After converting the infix expression 
into postfix expression, the resultant 
expression will be abcd^e-fgh*+^*+i-
```


**Example 2:**   
```
Input: str = "A*(B+C)/D"
Output: ABC+*D/
Explanation:
After converting the infix expression 
into postfix expression, the resultant 
expression will be ABC+*D/
```


### Constraints

+ `1 <= |str| <= 100000`

## Solutions

```cpp
class Solution
{
    public:
   int prec(char c){
        if(c=='^') return 3;
        else if(c=='*' || c=='/') return 2;
        else if(c=='+' || c=='-') return 1;
        return -1;
    }
    // Function to convert an infix expression to a postfix expression.
    string infixToPostfix(string str) {
        // Your code here
        string res = "";
        stack<char> s;
        for(char c: str){
            if(c=='(') s.push(c);
            else if(c==')'){
                while(s.top()!='('){
                    res += s.top();
                    s.pop();
                }
                s.pop();
            }else if(isalpha(c) or isdigit(c)){
                res+=c;
            }else {
                while(!s.empty() && prec(c) <= prec(s.top()) ){
                    if(c=='^' && s.top()=='^') break;
                    res += s.top();
                    s.pop();
                }
                s.push(c);
            }
        }
        
        while(!s.empty()) { res+=s.top(); s.pop(); }
        
        return res;
    }
};
```

