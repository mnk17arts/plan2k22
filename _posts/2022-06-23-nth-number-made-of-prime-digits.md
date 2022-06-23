---
layout: post
title: Nth number made of prime digits   
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/nth-number-made-of-prime-digits4319/0/?)  

Given a number '`N`'. The task is to find the `N`th number whose each digit is a prime number i.e `2, 3, 5, 7`. In other words you have to find nth number of this sequence : `2, 3, 5, 7, 22, 23 ,..` and so on.

**Your Task:** 
Complete `primeDigits` function and return the `n`th number of the given sequence made of prime digits.


**Expected Time Complexity:** `O(|S|)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 10
Output: 33
Explanation:10th number in the sequence of
numbers whose each digit is prime is 33.
```

**Example 2:**   
```
Input:
N = 21
Output: 222
Explanation:21st number in the sequence of
numbers whose each digit is prime is 222.
```

### Constraints

+ `1 <= N <= 100`

## Solutions

```cpp
class Solution{
    public:
    //Function to find nth number made of only prime digits.
    int primeDigits(int n)
    {
        //code here
        string s = "2357";
        int count = 0;
        int num = 0;
        while( count <= n ){
            int temp = num;
            while(s.find(temp%10 + '0')!=-1) temp/=10;
            if(temp==0) count++;
            num++;
        }
        return --num;
    }
};
```

