---
layout: post
title: Excel Sheet Column Number
summary:
tags:
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/excel-sheet-column-number)  

Given a string columnTitle that represents the column title as appear in an Excel sheet, return its corresponding column number.

For example:

```A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
...```

### Examples

**Example 1:**  
```
Input: columnTitle = "A"
Output: 1
```

**Example 2:**  
```
Input: columnTitle = "AB"
Output: 28
```

**Example 3:**  
```
Input: columnTitle = "ZY"
Output: 701
```

### Constraints

+ `1 <= columnTitle.length <= 7`
+ `columnTitle` consists only of uppercase English letters.
+ `columnTitle` is in the range `["A", "FXSHRXW"]`

## Solutions

```cpp
class Solution {
public:
    int titleToNumber(string columnTitle) {
      int res = 0;
      for(auto c: columnTitle)
        res = res*26 + (c-'A') + 1; 
      return res;
    }
};
```