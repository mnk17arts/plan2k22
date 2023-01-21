---
layout: post
title: Restore IP Addresses                       
summary:
tags:
    - leetcode
    - array
    - backtracking
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/restore-ip-addresses/description/)  

A valid IP address consists of exactly four integers separated by single dots. Each integer is between 0 and 255 (inclusive) and cannot have leading zeros.

+ For example, "`0.1.2.201`" and "`192.168.1.1`" are valid IP addresses, but "`0.011.255.245`", "`192.168.1.312`" and "`192.168@1.1`" are invalid IP addresses.

Given a string s containing only digits, return all possible valid IP addresses that can be formed by inserting dots into s. You are not allowed to reorder or remove any digits in s. You may return the valid IP addresses in any order.

### Examples


**Example 1:**   
```
Input: s = "25525511135"
Output: ["255.255.11.135","255.255.111.35"]
```


**Example 2:**   
```
Input: s = "0000"
Output: ["0.0.0.0"]
```

**Example 3:**   
```
Input: s = "101023"
Output: ["1.0.10.23","1.0.102.3","10.1.0.23","10.10.2.3","101.0.2.3"]
```


### Constraints

+ `1 <= s.length <= 20`
+ `s` consists of digits only.

## Solutions

```cpp

class Solution {
public:
    bool isValid(string str) {
        int n = str.length();
        if(n==0 || n>3) return false;
        if(n>1 && str.at(0)=='0') return false;
        if(stoi(str)>255) return false;
        return true;
    }
    void helper(string &s, string temp, int id, int cur, vector<string> &res) {
        int n = s.length();
        if(cur==3) {
            if(isValid(s.substr(id))) {
                res.push_back(temp + s.substr(id));
            }
            return ;     
        }
        for(int i=id; i<n; i++) {
            if(isValid(s.substr(id, i-id+1))) {
                temp.push_back(s.at(i));
                temp.push_back('.');
                helper(s,temp,i+1,cur+1,res);
                temp.pop_back();
            }
        }

    }
    vector<string> restoreIpAddresses(string s) {
        vector<string> res;
        if(s.length()>12 or s.length()<4) return res;
        string temp;
        int cur = 0;
        helper(s, temp, 0, cur, res);
        return res;
    }
};

```

