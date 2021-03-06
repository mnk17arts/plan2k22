---
layout: post
title: First Repeating Element 
summary:
tags:
    - hash
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/first-repeating-element4018/0/)  

Given an array `arr[]` of size `n`, find the first repeating element. The element should occurs more than once and the index of its first occurrence should be the smallest.

**Your Task:** 
You don't need to read input or print anything. Complete the function `firstRepeated()` which takes `arr` and `n` as input parameters and return the position of the first repeating element. If there is no such element, return `-1`.
The position you return should be according to `1`-based indexing. 


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
n = 7
arr[] = {1, 5, 3, 4, 3, 5, 6}
Output: 2
Explanation: 
5 is appearing twice and 
its first appearence is at index 2 
which is less than 3 whose first 
occuring index is 3.
```

**Example 2:**   
```
Input:
n = 4
arr[] = {1, 2, 3, 4}
Output: -1
Explanation: 
All elements appear only once so 
answer is -1.
```

### Constraints

+ `1 <= n <= 10^6`
+ `0 <= arr[i] <= 10^6` 

## Solutions

```cpp
class Solution{
    public:
    // Function to return the position of the first repeating element.
    int firstRepeated(int arr[], int n) {
        // code here
        unordered_map<int, int> m;
        for(int i=0; i<n; i++)
            m[arr[i]]++;
        for(int i=0; i<n; i++)
            if(m[arr[i]] > 1)
                return i+1;
            
        return -1;
    }
};
```

