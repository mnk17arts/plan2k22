---
layout: post
title: Guess Number Higher or Lower
description: 
summary: 
tags:
    - binary-search
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/guess-number-higher-or-lower/)
We are playing the Guess Game. The game is as follows:

I pick a number from `1` to `n`. You have to guess which number I picked.

Every time you guess wrong, I will tell you whether the number I picked is higher or lower than your guess.

You call a pre-defined API `int guess(int num)`, which returns 3 possible results:

+ `-1`: The number I picked is lower than your guess (i.e. `pick < num`).
+ `1`: The number I picked is higher than your guess (i.e. `pick > num`).
+ `0`: The number I picked is equal to your guess (i.e. `pick == num`).
Return *the number that I picked.*

### Examples
**Example 1:**  
```
Input: n = 10, pick = 6
Output: 6
```

**Example 2:**  
```
Input: n = 1, pick = 1
Output: 1
```

**Example 3:**  
```
Input: n = 2, pick = 1
Output: 1
```

**Example 4:**  
```
Input: n = 2, pick = 2
Output: 2
```

### Constraints
+ `1 <= n <= 2^31 - 1`
+ `1 <= pick <= n`

## Solutions
```cpp

/** 
 * Forward declaration of guess API.
 * @param  num   your guess
 * @return 	     -1 if num is lower than the guess number
 *			      1 if num is higher than the guess number
 *               otherwise return 0
 * int guess(int num);
 */

class Solution {
public:
    int guessNumber(int n) {
        int l=1,r=n;
        while(l<=r) {
            int t = l+(r-l)/2;
            if(guess(t)==0) return t;
            if(guess(t)<0) r=t-1;
            else l=t+1;
        }
        return 0;
    }
};
```
