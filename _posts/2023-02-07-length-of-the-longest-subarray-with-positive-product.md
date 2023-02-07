---
layout: post
title: Length of the longest subarray with positive product
summary:
tags:
    - geeksforgeeks
    - dynamic-programming
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/4dfa8ba14d4c94f4d7637b6b5246782412f3aeb8/1) 

Given an array arr[] consisting of n integers, find the length of the longest subarray with positive (non zero) product.

**Your Task:** 

Your Task: This is a function problem. You don't need to take any input, as it is already accomplished by the driver code. You just need to complete the function maxLength() that takes array arr[], and an integer n as parameters and return the length of the longest subarray where the product of all of its element is positive. 



**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`  



### Examples

**Example 1:**   
```
Input:
arr[] ={0, 1, -2, -3, -4} 
Output:
3
Explanation: 
The longest subarray with positive product is: 
{1, -2, -3}.Therefore, the required length is 3.
```

**Example 2:** 
```
Input:
arr[]={-1, -2, 0, 1, 2}
Output:
2
Explanation:
The longest subarray with positive products 
are: {-1, -2}, {1, 2}. Therefore, the required 
length is 2.
```

### Constraints

+ `1 <= n < 10^5`
+ `-10^9<=arr[i]<=10^9`

## Solutions

```cpp

class Solution{
    public:
    // Function to return the length of the
    //longest subarray with ppositive product
    int maxLength(vector<int> &arr,int n){
        //code here
        int res = 0, neg = 0,si = 0, ei = 0, fn = 0;
        while( ei < n) {
            if(arr[ei] == 0) {
                si = ei + 1;
                neg = 0;
                ei++;
                continue;
            }
            if (arr[ei] < 0) {
                neg++;
                if(neg == 1) {
                    fn = ei;
                }
            }
            if(neg % 2 == 0) {
                res = max(res, ei - si + 1);
            }
            else {
                res = max(res, ei - fn);
            }
            ei++;              
        }
        return res;
    }
};

```
