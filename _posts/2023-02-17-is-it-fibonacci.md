---
layout: post
title: Is it Fibonacci
summary:
tags:
  - geeksforgeeks
  - array
  - slidingwindow
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/202d95ecdeec659401edc63dd952b1d37b989ab8/1)

Geek just learned about Fibonacci numbers.

+ The Fibonacci Sequence is the series of numbers: 0, 1, 1, 2, 3, 5, 8, 13, ...
+ where the next number is found by adding up the two numbers before it.

He defines a new series called Geeky numbers. Here the next number is the sum of the K preceding numbers.

You are given an array of size K, GeekNum[ ], where the ith element of the array represents the ith Geeky number. Return its Nth term.

Note: This problem can be solved in O(N2) time complexity but the user has to solve this in O(N). The Constraints are less because there can be integer overflow in the terms.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function solve( ) which takes integer N, K, and an array GeekNum[] as input parameters and returns the Nth term of the Geeky series.



**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**

```
Input:
N = 6, K = 1
GeekNum[] = {4}
Output: 
4
Explanation: 
Terms are 4, 4, 4, 4, 4, 4
```

**Example 2:**

```
Input:
N = 5, K = 3
GeekNum[] = {0, 1, 2}
Output: 
6
Explanation: 
Terms are 0, 1, 2, 3, 6.
So the 5th term is 6
```

### Constraints

- `1 ≤ K < 30`
- `1 ≤ N ≤ 70`
- `0 ≤ GeekNum[i] ≤ 100`
- `K ≤ N`

## Solutions

```cpp

class Solution{
  public:
    long long solve(int N, int K, vector<long long> GeekNum) {
        // code here
        long long sum = 0;
        for(auto i: GeekNum) {
            sum += i;
        }
        for(int i = K; i < N; i++ ) {
            GeekNum.push_back(sum);
            sum -= GeekNum[i - K];
            sum += GeekNum[i];
        }
        return GeekNum[N-1];
    }
};

```
