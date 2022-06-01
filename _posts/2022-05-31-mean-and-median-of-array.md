---
layout: post
title:  Mean And Median of Array 
summary:
tags:
    - array
    - math
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/mean-and-median-1587115620/1/)  

Given an array `a[ ]` of size `N`. The task is to find the `median` and `mean` of the array elements. Mean is average of the numbers and median is the element which is smaller than half of the elements and greater than remaining half.  If there are odd elements, the median is simply the middle element in the sorted array. If there are even elements, then the median is floor of average of two middle numbers in the sorted array. If mean is floating point number, then we need to print floor of it.


**Your Task:** 
You don't need to read input or print anything.. You just need to complete the following two function:   

`mean()`: It takes the array and its size `N` as parameters and returns the mean as an integer.   
`median()`: It takes the array and its size `N` as parameters and returns the median as an integer..

**Expected Time Complexity**: `O(Nlog(N))`.     
**Expected Auxiliary Space**: `O(1)`.


### Examples

**Example 1:**   
```
Input:
N = 5
a[] = {1, 2, 19, 28, 5}
Output: 11 5
Explanation: For array of 5 elements,
mean is (1 + 2 + 19  + 28  + 5)/5 = 11.
Median is 5 (middle element after 
sorting)
```

**Example 2:**   
```
Input:
N = 4
a[] = {2, 8, 3, 4}
Output: 4 3
Explanation: For array of 4 elements,
mean is floor((2 + 8 + 3 + 4)/4) = 4.
Median is floor((4 + 3)/2) = 3
```

### Constraints

+ `1 <= N <= 10^6`
+ `1 <= a[i] <= 10^6`

## Solutions

```cpp
class Solution
{
    public:
    //Function to find median of the array elements.
    int median(int A[],int N)
    {
        
        sort(A,A+N);
        if(N%2==1)
            return A[N/2];
        else
            return (A[N/2 -1] + A[N/2])/2;
        //your code here
        //If median is in fraction then convert it to integer and return
    }
    //Function to find mean of the array elements.
    int mean(int A[],int N)
    {
        //your code here
        int res = 0;
        for(int i=0; i<N; i++)
            res+=A[i];
        return res/N;
    }
};
```

