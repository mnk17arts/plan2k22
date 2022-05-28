---
layout: post
title:  Count total set bits
summary:
tags:
    - bit-manipulation
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-total-set-bits-1587115620/1)  

You are given a number `N`. Find the total count of set bits for all numbers from `1` to `N`(both inclusive).

**Your Task:** 
The task is to complete the function `countSetBits()` that takes `n` as a parameter and returns *the count of all bits.*

**Expected Time Complexity**: `O(log N)`      
**Expected Auxiliary Space**: `O(1)`.


### Examples

**Example 1:**   
```
Input: N = 4
Output: 5
Explanation:
For numbers from 1 to 4.
For 1: 0 0 1 = 1 set bits
For 2: 0 1 0 = 1 set bits
For 3: 0 1 1 = 2 set bits
For 4: 1 0 0 = 1 set bits
Therefore, the total set bits is 5.
```

**Example 2:**   
```
Input: N = 17
Output: 35
Explanation: From numbers 1 to 17(both inclusive), 
the total number of set bits is 35.
```

### Constraints

+ `1 <= N <= 10^8`

## Solutions

```cpp
class Solution
{
    public:
    // n: input to count the number of set bits
    //Function to return sum of count of set bits in the integers from 1 to n.
    int countSetBits(int n)
    {
        // Your logic here
        n++;
        int count = n/2; // setbits in 0th place
        int powOf2 = 2;
        while(powOf2 <= n){
            int tpairs = n/powOf2; // total pairs
            count += powOf2*(tpairs/2); // setbits in pairs
            count += (tpairs&1) ? (n%powOf2) : 0; // setbits in last pair
            powOf2 <<= 1;
        }
        return count;
    }
};
```

