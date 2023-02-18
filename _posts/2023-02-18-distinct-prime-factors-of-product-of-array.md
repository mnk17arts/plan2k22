---
layout: post
title: Distinct Prime Factors of Product of Array
summary:
tags:
  - leetcode
  - array
  - hash
  - math
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/distinct-prime-factors-of-product-of-array/)

Given an array of positive integers nums, return the number of distinct prime factors in the product of the elements of nums.

Note that:

+ A number greater than 1 is called prime if it is divisible by only 1 and itself.
+ An integer val1 is a factor of another integer val2 if val2 / val1 is an integer.

### Examples

**Example 1:**
```
Input: nums = [2,4,3,7,10,6]
Output: 4
Explanation:
The product of all the elements in nums is: 2 * 4 * 3 * 7 * 10 * 6 = 10080 = 2^5 * 3^2 * 5 * 7.
There are 4 distinct prime factors so we return 4.
```

**Example 2:**
```
Input: nums = [2,4,8,16]
Output: 1
Explanation:
The product of all the elements in nums is: 2 * 4 * 8 * 16 = 1024 = 2^10.
There is 1 distinct prime factor so we return 1.
```

### Constraints

- `1 <= nums.length <= 10^4`
- `2 <= nums[i] <= 1000`

## Solutions

```cpp

class Solution {
public:
    int distinctPrimeFactors(vector<int>& nums) {
        int pa[11] = {2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31};
        unordered_set<int> set;
        for(int n: nums) {
            for(int p: pa) {
                if(n % p == 0) {
                    set.insert(p);
                    while(n % p == 0) {
                        n /= p;
                    }
                }
            }
            if(n != 1) {
                set.insert(n);
            }
        }
        return set.size();
    }
};

```
