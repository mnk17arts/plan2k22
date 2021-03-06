---
layout: post
title: Sequential Digits
summary:
tags:
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/sequential-digits)  

An integer has sequential digits if and only if each digit in the number is one more than the previous digit.

Return a sorted list of all the integers in the range `[low, high]` inclusive that have sequential digits.


### Examples

**Example 1:**   
```
Input: low = 100, high = 300
Output: [123,234]
```

**Example 2:**   
```
Input: low = 1000, high = 13000
Output: [1234,2345,3456,4567,5678,6789,12345]
```

### Constraints

+ `10 <= low <= high <= 10^9`

## Solutions

```cpp
class Solution {
public:
    vector<int> ans;
    
    void dfs(int low, int high, int i, int num){
        
        if (num >= low and num <= high)
            ans.push_back(num);
        if (num > high or i>9) 
            return;
        dfs(low, high, i+1, num*10 + i);
    }
    
    vector<int> sequentialDigits(int low, int high) {
        for(int i=1; i<=9; i++)
            dfs(low, high, i, 0);
        sort(ans.begin(), ans.end());
        return ans;
    }
};
```

