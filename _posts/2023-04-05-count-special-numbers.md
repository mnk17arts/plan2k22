---
layout: post
title: Count Special Numbers
summary:
tags:
  - geeksforgeeks
  - array
  - medium
  - cpp
  - medium
minute: 8+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/3d49e4cce2820a813da02d1587c2dd9c542ce769/1)

You are given an array arr[ ] of size N consisting of only positive integers. Your task is to find the count of special numbers in the array. A number is said to be a special number if it is divisible by at least 1 other element of the array.

**Your Task:**

You don't need to read input or print anything. Complete the function countSpecialNumbers() which takes the integer N and the array arr[ ] as the input parameters, and returns the count of special numbers in the array. 

**Expected Time Complexity:** `O(N*M)`, where `N` is the size of the array and `M` is the maximum element in the array.)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**

```
Input:
N = 3
arr[] = {2, 3, 6}
Output:
1
Explanation:
The number 6 is the only special number in the
array as it is divisible by the array elements 2 
and 3. Hence, the answer is 1 in this case.
```

**Example 2:**

```
Input:
N = 3
arr[] = {2, 3, 6}
Output:
1
Explanation:
The number 6 is the only special number in the
array as it is divisible by the array elements 2 
and 3. Hence, the answer is 1 in this case.
```

### Constraints

- `1 <= N ≤ 10^5`
- `1 <= arr[i] <= 10^6`

## Solutions

```cpp

class Solution {
  public:
    int countSpecialNumbers(int N, vector<int> arr) {
      map<int,int> m;
       int cnt=0;
       for(int i=0;i<N;i++) m[arr[i]]++;
       for(int i=0;i<N;i++){
           if(m[arr[i]]>0) {
               for(int j=0;j<N;j++){
                   if(j!=i and arr[i]%arr[j]==0) {
                       cnt+=m[arr[i]];
                       m.erase(arr[i]);
                       break;
                   }
               }
           }
       }
       return cnt;
    }
};

```
