---
layout: post
title: Median of Two sorted arrays 
summary:
tags:
    - array
    - divide-conquer
    - searching
    - geeksforgeeks
    - cpp
    - hard
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/median-of-two-sorted-arrays1618/1/)  

Given two sorted arrays of sizes `N` and `M` respectively. The task is to find the median of the two arrays when they get merged.
If there are even number of elements in the resulting array, find the floor of the average of two medians.

**Your Task:** 
You do not need to read input or print anything. Complete `findMedian()` function which takes the two arrays and n and m as input parameters and returns their median. If there are total even elements, return floor of average of middle two elements.


**Expected Time Complexity:** `O(log(max(m,n)))`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 5, M = 6 
arr[] = {1,2,3,4,5}
brr[] = {3,4,5,6,7,8}
Output: 4
Explanation: After merging two arrays, 
elements will be as 1 2 3 3 4 4 5 5 6 7 8
So, median is 4.
```

**Example 2:**   
```
Input:
N = 2, M = 3 
arr[] = {1,2}
brr[] = {2,3,4}
Output: 2
Explanation: After merging two arrays, 
elements will be as 1 2 2 3 4. So, 
median is 2.
```

### Constraints

+ `1 <= N,M <= 10^6`
+ `1 <= arr[i], brr[i] = 10^7` 

## Solutions

```cpp
class Solution{
    public:
    //Function to find the median of the two arrays when they get merged.
    int findMedian(int arr[], int n, int brr[], int m)
    {
        if( n > m) return findMedian(brr, m, arr, n);
        int left = 0, right = n;
        while(left <= right){
            int i1 = left + (right-left)/2 ;
            int i2 = (n + m + 1)/2 - i1;
            int max1 = (i1 == 0) ? INT_MIN : arr[i1-1];
            int max2 = (i2 == 0) ? INT_MIN : brr[i2-1];
            int min1 = (i1 == n) ? INT_MAX : arr[i1];
            int min2 = (i2 == m) ? INT_MAX : brr[i2];
            if(max2 <= min1 && max1 <= min2){
                if((n+m) % 2 == 0)
                    return ((double)min(min1, min2) + max(max1, max2)) / 2.0;
                else
                    return max(max1, max2);
            }
            else if(max1 > min2) right = i1 - 1;
            else left = i1 + 1;
        }
        return -1;
    }
};
```

