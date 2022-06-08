---
layout: post
title: Allocate minimum number of pages 
summary:
tags:
    - divide-conquer
    - searching
    - geeksforgeeks
    - cpp
    - hard
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1#)  

You are given `N` number of books. Every `i`th book has `Ai` number of pages.

You have to allocate contiguous books to `M` number of students. There can be many ways or permutations to do so. In each permutation, one of the `M` students will be allocated the maximum number of pages. Out of all these permutations, the task is to find that particular permutation in which the maximum number of pages allocated to a student is the minimum of those in all the other permutations and print this minimum value.

Each book will be allocated to exactly one student. Each student has to be allocated at least one book.

**Note:** Return `-1` if a valid assignment is not possible, and allotment should be in contiguous order (see the explanation for better understanding).

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `findPages()` which takes `2` Integers `N`, and `m` and an array `A[]` of length `N` as input and returns the expected answer.

**Expected Time Complexity:** `O(NlogN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 4
A[] = {12,34,67,90}
M = 2
Output:113
Explanation:Allocation can be done in 
following ways:{12} and {34, 67, 90} 
Maximum Pages = 191{12, 34} and {67, 90} 
Maximum Pages = 157{12, 34, 67} and {90} 
Maximum Pages =113. Therefore, the minimum 
of these cases is 113, which is selected 
as the output.
```

**Example 2:**   
```
Input:
N = 3
A[] = {15,17,20}
M = 2
Output:32
Explanation: Allocation is done as
{15,17} and {20}
```

### Constraints

+ `1 <= N <= 10^5`
+ `1 <= arrr[i] = 10^6` 
+ `1 <= M <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    bool isPossible(int arr[], int n, int m, int mid){
       int studentCount=1;
       int pageSum=0;
       
       for(int i=0; i<n; i++){
           if(pageSum + arr[i] <= mid){
               pageSum+=arr[i];
           }
           else{
               studentCount++;
               if(studentCount>m or arr[i]>mid){
                   return false;
               }
               pageSum= arr[i];
           }
       }
       return true;
   }
   //Function to find minimum number of pages.
   int findPages(int arr[], int n, int m) 
   {
       int start=0, ans =-1;
       int sum=0;
       for(int i=0; i<n; i++){
           sum= sum+arr[i];
       }
       int end= sum;
       int mid= (start+end)/2;
       
       while(start<=end){
           if(isPossible(arr, n, m, mid)){
               ans= mid;
               end= mid-1;
           }
           else{
               start= mid+1;
           }
           mid= (start+end)/2;
       }
       return ans;
   }
};
```

