---
layout: post
title: Largest number with given sum                   
summary:
tags:
    - greedy
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/largest-number-with-given-sum-1587115620/0/?track=DSASP-Greedy&batchId=154)  

Geek lost the password of his super locker. He remembers the number of digits `N` as well as the sum `S` of all the digits of his password. He know that his password is the largest number of `N` digits that can be made with given sum `S`. As he is busy doing his homework, help him retrieving his password. 

**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function `largestNumber()` which takes `2` integers `N` and `S` as input parameters and returns the password in the form of string, else return "`-1`" in the form of string.


**Expected Time Complexity:** `O(N)`           
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
N = 5, S = 12
Output:
93000
Explanation:
Sum of elements is 12. Largest possible 
5 digit number is 93000 with sum 12.
```

**Example 2:**   
```
Input:
N = 3, S = 29
Output:
-1
Explanation:
There is no such three digit number 
whose sum is 29.
```

### Constraints

+ `1 ≤ N ≤ 10^4`
+ `1 ≤ S ≤ 9*10^4`

## Solutions

```cpp
class Solution
{
    public:
    //Function to return the largest possible number of n digits
    //with sum equal to given sum.
    string largestNumber(int n, int sum) {
        // Your code here
        if(n*9 < sum) return "-1";
        string res="";
        for(int j=9;j>0;j--){
            while(sum >= j){
                res += ('0'+j);
                sum -= j;
            }
        }
        for(int i=res.size();i<n;i++) res += '0';
        return res;
    }
};
```

