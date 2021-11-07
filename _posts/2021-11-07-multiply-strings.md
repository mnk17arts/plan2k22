---
layout: post
title: Multiply Strings
description: 
summary:
tags:
    - string
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/multiply-strings/)
Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`, also represented as a string.

**Note:** You must not use any built-in BigInteger library or convert the inputs to integer directly.

### Examples

**Example 1:**    
```
Input: num1 = "2", num2 = "3"
Output: "6"
```

**Example 2:**   
```
Input: num1 = "123", num2 = "456"
Output: "56088"
```

### Constraints
+ `1 <= num1.length, num2.length <= 200`
+ `num1` and `num2` consist of digits only.
+ Both `num1` and `num2` do not contain any leading zero, except the number `0` itself.

## Solutions

```cpp
class Solution {
public:
    string multiply(string num1, string num2) {
      if(num1 == "0" or num2 == "0") return "0";
      int n1 = num1.size();
      int n2 = num2.size();
      int n = n1+n2;
      string res(n, '0');
      
      reverse(num1.begin(), num1.end());      
      reverse(num2.begin(), num2.end());

      for(int i=0; i<n2; i++){
        int d2 = num2[i]-'0';
        for(int j=0; j<n1; j++){
          int d1 = num1[j]-'0';
          int id = i+j;
          int c = res[id]-'0';
          int a = d1*d2 + c;
          res[id] = (a%10)+'0';
          res[id+1] += (a/10);
        }
      }
      
      if(res.back() == '0'){
        res.pop_back();
      }
      reverse(res.begin(),res.end());
      return res; 
    }
};
```

