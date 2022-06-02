---
layout: post
title: Square root of a number
summary:
tags:
    - searching
    - binary-search
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/square-root/1)  

Given an integer `x`, find the square root of `x`. If `x` is not a perfect square, then return `floor(√x)`.

**Your Task:** 
You don't need to read input or print anything. The task is to complete the function `floorSqrt()` which takes x as the input parameter and return its square root.
**Note:** Try Solving the question without using sqrt Function.

**Expected Time Complexity:** `O(logN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
x = 5
Output: 2
Explanation: Since, 5 is not a perfect 
square, floor of square_root of 5 is 2.
```

**Example 2:**   
```
Input:
x = 4
Output: 2
Explanation: Since, 4 is a perfect 
square, so its square root is 2.
```

### Constraints

+ `1 <= x <= 10^7`

## Solutions

```cpp
class Solution{
    public:
    long long int floorSqrt(long long int x) 
    {
        // Your code goes here 
        long long low=1;
        long long high=x;
        int res;
        while(low<=high){
        
        long long mid=(high+low)/2;
        
        long long msqrt=mid*mid;
        if(x==msqrt) return mid;
        
        if(msqrt>x){
            high=mid-1;
        }
        else{
            res=mid;
            low=mid+1;
        }
        }
        return res;
    }
};
```

