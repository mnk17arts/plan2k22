---
layout: post
title: Optimal Array
summary:
tags:
  - geeksforgeeks
  - array
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/d4aeef538e6dd3280dda5f8ed7964727fdc7075f/1)

You are given a sorted array a of length n. For each i(0<=i<=n-1), you have to make all the elements of the array from index 0 till i equal, using minimum number of operations. In one operation you either increase or decrease the array element by 1.

You have to return a list which contains the minimum number of operations for each i, to accomplish the above task.

Note:
1. 0-based indexing.
1. For each index, you need to consider the same array which was given to you at the start.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function optimalArray() which takes N(length of array) and  an array A as input and returns an array of size N  with optimal answer for each index i.


**Expected Time Complexity:** `O(N)`   
**Expected Auxiliary Space:** `O(1)`   


### Examples

**Example 1:**


```
Input:
N=4
A=[1,6,9,12]

Output:
0 5 8 14

Explanation:
For i=0, We do not need to perform any 
operation, our array will be [1]->[1].
And minimum number of operations
will be 0.

For i=1, We can choose to convert all 
the elements from 0<=j<=i to 4, our 
array will become [1,6]->[4,4]. And 
minimum number of operations will be 
|1-4|+|6-4|=5.

For i=2, We can choose to convert all 
the elements from 0<=j<=i to 6, our 
array will become [1,6,9]->[6,6,6] and 
the minimum number of operations will 
be |1-6|+|6-6|+|9-6|=8.

Similarly, for i=3, we can choose to 
convert all the elements to 8, 
[1,6,9,12]->[8,8,8,8], and the 
minimum number of operations will be 14.
```

**Example 2:**

```
Input:
N=7
A=[1,1,1,7,7,10,19]

Output:
0 0 0 6 12 21 33

Explanation:
Possible operations could be:
[1]->[1]
[1,1]->[1,1]
[1,1,1]->[1,1,1]
[1,1,1,7]->[1,1,1,1]
[1,1,1,7,7]->[1,1,1,1,1]
[1,1,1,7,7,10]->[5,5,5,5,5,5]
[1,1,1,7,7,10,19]->[7,7,7,7,7,7,7]
```

### Constraints

- `1 <= N <= 10^6`
- `-10^5 <= A[i] <= 10^5`
- Sum of N over all testcases will not exceed `10^6`

## Solutions

```cpp

class Solution{
public:
    vector<int> optimalArray(int n,vector<int> &a){
        // Code here 
        int j = 0;
        int median = a[j];
        int sum = 0;
        vector<int> ret;
        for(int i=0;i<n;i++,j+=(i%2==0)){
            sum += a[i]-a[j];
            ret.push_back(sum);
        }
        return ret;
    }
};

```
