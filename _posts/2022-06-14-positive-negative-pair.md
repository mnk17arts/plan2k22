---
layout: post
title: Positive Negative Pair  
summary:
tags:
    - hash
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/positive-negative-pair5209/0/#)  

Given an array of distinct integers, find all the pairs having both negative and positive values of a number in the array.



**Your Task:** 
You do not need to read input or print anything. Complete the function `findPairs()` which takes the array `A[]` and the size of the array, `n`, as input parameters and returns a list of integers denoting the pairs. The pair that appears first(i.e. second element of the pair appears first) in `A[]` should appear first in the returning list and within the pair, the negative integer should appear before the positive integer. Return an empty integer list if no such pair exists.


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
n = 8
arr[] = {1,3,6,-2,-1,-3,2,7}
Output: -1 1 -3 3 -2 2
Explanation: 1, 3 and 2 are present 
pairwise positive and negative. 6 and 
7 have no pair.
```

**Example 2:**   
```
Input:
n = 3
arr[] = {3,2,1}
Output: 0
Explanation: No such pair exists so the 
output is 0.
```

### Constraints

+ `1 <= n <= 10^6`
+ `-10^6 <= arr[i] <= 10^6`

## Solutions

```cpp
class Solution{
    public:
    //Function to return list containing all the pairs having both
    //negative and positive values of a number in the array.
    vector <int> findPairs(int arr[], int n) 
    {
        // code here
        
        unordered_map<int, int> m;
        vector<int> v;
        for(int i=0; i<n; i++){
            if(arr[i]==0) continue;
            m[arr[i]] = 1;
            if(m.find(-1*arr[i]) != m.end()){
                v.push_back(-1*abs(arr[i]));
                v.push_back(abs(arr[i]));
                m.erase(arr[i]);
            }
        }

        return v;
    }
};
```

