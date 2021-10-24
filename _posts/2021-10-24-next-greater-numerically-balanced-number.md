---
layout: post
title:  Next Greater Numerically Balanced Number
description: 
summary: 
tags:
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/next-greater-numerically-balanced-number/)  
An integer `x` is **numerically balanced** if for every digit `d` in the number `x`, there are **exactly** `d` occurrences of that digit in `x`.

Given an integer `n`, return *the **smallest numerically balanced** number **strictly greater** than `n`.*
 
### Examples   
**Example 1:**  
```
Input: n = 1
Output: 22
Explanation: 
22 is numerically balanced since:
- The digit 2 occurs 2 times. 
It is also the smallest numerically balanced number strictly greater than 1.
```

**Example 2:**   
``` 
Input: n = 1000
Output: 1333
Explanation: 
1333 is numerically balanced since:
- The digit 1 occurs 1 time.
- The digit 3 occurs 3 times. 
It is also the smallest numerically balanced number strictly greater than 1000.
Note that 1022 cannot be the answer because 0 appeared more than 0 times.
```

**Example 3:**   
``` 
Input: n = 3000
Output: 3133
Explanation: 
3133 is numerically balanced since:
- The digit 1 occurs 1 time.
- The digit 3 occurs 3 times.
It is also the smallest numerically balanced number strictly greater than 3000.
```

### Constraints
+ `0 <= n <= 10^6`


## Solutions

```cpp
class Solution {
public:
    bool bt(int n){
        int d[10]={},x=n;
        while(x){d[x%10]++;x/=10;}
        for(int i=0;i<10;i++){if(d[i] and d[i]!=i) return false;}
        return true;
    }
    int nextBeautifulNumber(int n) {
        for(n++;!bt(n);n++);
        return n;
    }
};
```

