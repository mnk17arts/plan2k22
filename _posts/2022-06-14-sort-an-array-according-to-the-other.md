---
layout: post
title: Sort an array according to the other  
summary:
tags:
    - hash
    - searching
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/relative-sorting4323/0/)  

Given two integer arrays `A1[ ]` and `A2[ ]` of size `N` and `M` respectively. Sort the first array `A1[ ]` such that all the relative positions of the elements in the first array are the same as the elements in the second array `A2[ ]`.
See example for better understanding.
**Note:** If elements are repeated in the second array, consider their first occurance only.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `sortA1ByA2()` which takes the array `A1[ ]`, array `A2[ ] `and their respective size `N` and `M` as input parameters and returns the sorted array `A1[ ]` such that the relative positions of the elements in `A1[ ]` are same as the elements in `A2[ ]`. For the elements not present in `A2[ ]` but in `A1[ ]`, it appends them at the last in increasing order. 


**Expected Time Complexity:** `O(n * logn)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
N = 11 
M = 4
A1[] = {2, 1, 2, 5, 7, 1, 9, 3, 6, 8, 8}
A2[] = {2, 1, 8, 3}
Output: 
2 2 1 1 8 8 3 5 6 7 9
Explanation: Array elements of A1[] are
sorted according to A2[]. So 2 comes first
then 1 comes, then comes 8, then finally 3
comes, now we append remaining elements in
sorted order.
```

**Example 2:**   
```
Input:
N = 11 
M = 4
A1[] = {2, 1, 2, 5, 7, 1, 9, 3, 6, 8, 8}
A2[] = {99, 22, 444, 56}
Output: 
1 1 2 2 3 5 6 7 8 8 9
Explanation: No A1[] elements are in A2[]
so we cannot sort A1[] according to A2[].
Hence we sort the elements in non-decreasing 
order.
```

### Constraints

+ `1 <= n,m <= 10^6`
+ `1 ≤ A1[i], A2[i] ≤ 10^6`

## Solutions

```cpp
class Solution{
    public:
    // A1[] : the input array-1
    // N : size of the array A1[]
    // A2[] : the input array-2
    // M : size of the array A2[]
    
    //Function to sort an array according to the other array.
    vector<int> sortA1ByA2(vector<int> A1, int N, vector<int> A2, int M) 
    {
        //Your code here
        map<int, int> m;
        vector<int> v;
        for(int i=0; i<N; i++) m[A1[i]]++;
        for(int i=0; i<M; i++){
            int x = A2[i];
            if(m.find(x)!=m.end())
                for(int j = 0; j<m[x]; j++) v.push_back(x);
            m.erase(x);
        }
        for(auto i: m)
            for(int j=0; j<i.second; j++) v.push_back(i.first);
        return v;
    } 
};
```

