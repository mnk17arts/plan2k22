---
layout: post
title: Multiply two strings
summary:
tags:
  - geeksforgeeks
  - string
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/multiply-two-strings/1)

Given two numbers as strings s1 and s2. Calculate their Product.

Note: The numbers can be negative and You are not allowed to use any built-in function or convert the strings to integers.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function multiplyStrings() which takes two strings s1 and s2 as input and returns their product as a string.


**Expected Time Complexity:** `O(n1* n2)`  
**Expected Auxiliary Space:** `O(n1 + n2)` where n1 and n2 are the sizes of strings s1 and s2 respectively.

### Examples

**Example 1:**

```
Input:
s1 = "33"
s2 = "2"
Output:
66
```

**Example 2:**

```
Input:
s1 = "11"
s2 = "23"
Output:
253
```

### Constraints

- `1 ≤ length of s1 and s2 ≤ 1000`

## Solutions

```cpp

class Solution{
  public:
    /*You are required to complete below function */
    string multiply(string s, int n) {
        if(n == 0 || s=="" || s[0]=='0') {
            return "";
        }
        reverse(s.begin(), s.end());
        int carry = 0;
        for(auto &c: s) {
            int x = c - '0';
            int pro = x * n + carry;
            c = (pro % 10) + '0';
            carry = pro / 10;
        }
        if(carry) {
            s.push_back(carry + '0');
        }
        reverse(s.begin(), s.end());
        return s;
    }
    string add(string s1, string s2) {
        string temp = "";
        reverse(s1.begin(), s1.end());
        reverse(s2.begin(), s2.end());
        int carry = 0;
        int i = 0, j = 0;
        while(i < s1.length() && j < s2.length()) {
            int sum = (s1[i++] - '0') + (s2[j++] - '0') + carry;
            temp.push_back((sum % 10) + '0');
            carry = sum / 10;
        }
        while(i < s1.length()) {
            int sum = (s1[i++] - '0') + carry;
            temp.push_back((sum % 10) + '0');
            carry = sum / 10;            
        }
        while(j < s2.length()) {
            int sum = (s2[j++] - '0') + carry;
            temp.push_back((sum % 10) + '0');
            carry = sum / 10;            
        }
        if(carry) {
            temp.push_back(carry + '0');
        }
        reverse(temp.begin(), temp.end());
        return temp;
        
    }
    string multiplyStrings(string s1, string s2) {
       vector<string> temp;
       string zeros = "";
       int sign = 1;
       if(s1[0] == '-') {
           sign *= -1;
           s1 = s1.substr(1);
       }
       if(s2[0] == '-') {
           sign *= -1;
           s2 = s2.substr(1);
       }
       while(s1.length() > 1 && s1[0] == '0') {
           s1 = s1.substr(1);
       }
       while(s2.length() > 1 && s2[0] == '0') {
           s2 = s2.substr(1);
       }
       for(int i = s2.size()-1; i>=0; i--) {
           int n = s2[i] - '0';
           string cur = multiply(s1, n);
           if(cur != "") {
               cur += zeros;
           }
           temp.push_back(cur);
           zeros.push_back('0');
       }
       string res = temp[0];
       for(int i = 1; i < temp.size(); i++) {
           res = add(res, temp[i]);
       }
        if(res == "") {
            res = "0";
        }
        else if(sign == -1) {
            res = "-" + res;
        }
       return res;
    }
};

```
