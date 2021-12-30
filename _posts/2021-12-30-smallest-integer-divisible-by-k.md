---
layout: post
title: Smallest Integer Divisible by K
summary:
tags:
    - math
    - leetcode
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/smallest-integer-divisible-by-k)  

Given a positive integer `k`, you need to find the **length** of the **smallest** positive integer n such that n is divisible by `k`, and `n` only contains the digit `1`.

Return *the **length** of n. If there is no such `n`, return `-1`.*

**Note**: `n` may not fit in a 64-bit signed integer.


### Examples

**Example 1:**  
```
Input: k = 1
Output: 1
Explanation: The smallest answer is n = 1, which has length 1.
```

**Example 2:**  
```
Input: k = 2
Output: -1
Explanation: There is no such positive integer n divisible by 2.
```

**Example 3:**  
```
Input: k = 3
Output: 3
Explanation: The smallest answer is n = 111, which has length 3.
```

### Constraints
+ `1 <= k <= 10^5`

## Solutions

```cpp
class Solution {
public:
    int smallestRepunitDivByK(int K) {
        int remainder = 0;
        for (int length_N = 1; length_N <= K; length_N++) {
            remainder = (remainder * 10 + 1) % K;
            if (remainder == 0) {
                return length_N;
            }
        }
        return -1;        
    }
};
```

