---
layout: post
title: Count More than n/k Occurences 
summary:
tags:
    - array
    - searching
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-element-occurences/1/)  

Given an array `arr[]` of size `N` and an element `k`. The task is to find all elements in array that appear more than n/k times.

**Your Task:** 
The task is to complete the function `countOccurence()` which returns `count` of elements with more than `n/k` times appearance.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 8
arr[] = {3,1,2,2,1,2,3,3}
k = 4
Output: 2
Explanation: In the given array, 3 and
 2 are the only elements that appears 
more than n/k times.
```

**Example 2:**   
```
Example 2:

Input:
N = 4
arr[] = {2,3,3,2}
k = 3
Output: 2
Explanation: In the given array, 3 and 2 
are the only elements that appears more 
than n/k times. So the count of elements 
are 2.
```

### Constraints

+ `1 <= N <= 10^4`
+ `1 <= arrr[i] = 10^6` 
+ `1 <= k <= N`

## Solutions

```cpp
class Solution{
    public:
    //Function to find all elements in array that appear more than n/k times.
    int countOccurence(int arr[], int n, int k) {
        int count = 0;
        unordered_map<int, int> m;
        for(int i=0; i<n; i++) {
            m[arr[i]]++;
        }
        for(auto it = m.begin(); it != m.end(); it++) {
            if(it->second > n/k)
                count++;
        }
        return count;
    }
};
```

