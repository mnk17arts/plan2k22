---
layout: post
title: Reordered Power of 2                       
summary:
tags:
    - leetcode
    - sorting
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/reordered-power-of-2/)  

You are given an integer n. We reorder the digits in any order (including the original order) such that the leading digit is not zero.

Return true if and only if we can do this so that the resulting number is a power of two.


### Examples



**Example 1:**   
```
Input: n = 1
Output: true
```


**Example 2:**   
```
Input: n = 10
Output: false
```

### Constraints

+ `1 <= n <= 10^9`

## Solutions

```cpp
class Solution {
public:
    bool reorderedPowerOf2(int n) {
        string s = to_string(n);
        sort(begin(s),end(s));
        vector<string> v;
        for(int i=0;i<=30;i++){
            int p = pow(2,i);
            string x = to_string(p);
            sort(begin(x),end(x));
            v.push_back(x);
        }
            
        for(auto i: v)
            if(i==s) return true;
        return false;
    }
};
```

