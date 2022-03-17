---
layout: post
title: Score of Parentheses
summary:
tags:
    - string
    - stack
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/score-of-parentheses)  

Given a balanced parentheses string `s`, return the **score** of the string.

The **score** of a balanced parentheses string is based on the following rule:

+ "`()`" has score 1.
+ `AB` has score `A + B`, where `A` and `B` are balanced parentheses strings.
+ `(A)` has score `2 * A`, where `A` is a balanced parentheses string.


### Examples

**Example 1:**   
```
Input: s = "()"
Output: 1
```

**Example 2:**   
```
Input: s = "(())"
Output: 2
```

**Example 3:**   
```
Input: s = "()()"
Output: 2
```

### Constraints

+ `2 <= s.length <= 50`
+ `s` consists of only '`(`' and '`)`'.
+ `s` is a balanced parentheses string.

## Solutions

```cpp
class Solution {
public:
    int scoreOfParentheses(string s) {
      stack<int> st;
        int i = 0;
        for(auto c : s)       {
            if(c == '(')           {
                st.push(i);
                i = 0;
            }
            else            {
                i = st.top() + max(i*2 ,1);
                st.pop();
            }
        }
        return i;
    }
};
```

