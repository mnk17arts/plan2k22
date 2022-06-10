---
layout: post
title: Three way partitioning
summary:
tags:
    - array
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/three-way-partitioning/0/#)  

Given an array of size n and a range `[a, b]`. The task is to partition the array around the range such that array is divided into three parts.
1) All elements smaller than `a` come first.
2) All elements in range `a` to `b` come next.
3) All elements greater than `b` appear in the end.
The individual elements of three sets can appear in any order. You are required to return the modified array.

**Your Task:** 
You dont need to read input or print anything. The task is to complete the function `threeWayPartition()` which takes the `array[]`, `a` and `b` as input parameters and modifies the array in-place according to the given conditions.
**Note**: The generated output is `1` if you modify the given array successfully. 

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: 
n = 5
A[] = {1, 2, 3, 3, 4}
[a, b] = [1, 2]
Output: 1
Explanation: One possible arrangement is:
{1, 2, 3, 3, 4}. If you return a valid
arrangement, output will be 1.
```

**Example 2:**   
```
Input: 
n = 3 
A[] = {1, 2, 3}
[a, b] = [1, 3]
Output: 1
Explanation: One possible arrangement 
is: {1, 2, 3}. If you return a valid
arrangement, output will be 1. 
```

### Constraints

+ `1 <= n <= 10^6`
+ `1 <= arr[i] = 10^6` 

## Solutions

```cpp
class Solution{
    public:
    //Function to partition the array around the range such 
    //that array is divided into three parts.
    void threeWayPartition(vector<int>& arr,int a, int b) {
        // code here 
        int low = 0, mid = 0, high = arr.size()-1;
        while(mid <= high){
            if (arr[mid] < a)  swap(arr[low++],arr[mid++]);
            else if (arr[mid] >= a && arr[mid] <= b) mid++;
            else swap(arr[mid], arr[high--]);
        }
    }
};
```

