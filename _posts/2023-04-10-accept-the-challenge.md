---
layout: post
title: Accept the challenge
summary:
tags:
  - geeksforgeeks
  - array
  - math
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-97/problems/)

Geekina gave Geek a challenge, she asked Geek to choose any positive number (say x) and perform the operation at least twice - 

Add x to your current score and double the value of x.

The challenge here is you must perform the above operation at least twice and after performing the above operation your score should be exactly k.

Could you help Geek by giving him largest x to start with or return -1 if such x does not exist?

Note: Initially the score is 0

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function acceptTheChallenge() which takes k as input parameter and returns the optimal x.

### Examples

**Example 1:**

```
Input: 
7

Output:
1

Explanation:
Geek will choose x = 1 and do the following operations - 
Add 1 to score and double x. Therefore x = 2 and Score = 1
Now add 2 to score and double x. Therefore x = 4 and Score = 3
Now add 4 to the score and double x. Therefore x = 8 and Score = 7. 
```

**Example 2:**

```
Input:
8

Output:
-1

Explanation:
It can be shown that there does not exist any x that can help Geek to have a score of exactly 8.
```

### Constraints

- `3 ≤ k ≤ 10^9`

## Solutions

```cpp


class Solution {
  public:
    long long acceptTheChallenge(int n) {
        // code here
        if (n <= 2 || (n & (n - 1)) == 1) {
            return -1;
        }
        long long x = n / 2;
        while (x > 0) {
            long long score = x;
            long long temp = x;
            while (score < n) {
                temp *= 2;
                score += temp;
            }
            if (score == n) {
                return x;
            }
            x--;
        }
        return -1; 
    }
};


```
