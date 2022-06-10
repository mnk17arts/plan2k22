---
layout: post
title: Counting Sort
summary:
tags:
    - sorting
    - counting-sort
    - algorithm
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/counting-sort/0/#)  

Given a string `arr` consisting of lowercase english letters, arrange all its letters in lexicographical order using Counting Sort.

**Your Task:** 
This is a function problem. You only need to complete the function `countSort()` that takes string `arr` as a parameter and returns the sorted string. The printing is done by the driver code.

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
N = 5
S = "edsab"
Output:
abdes
Explanation: 
In lexicographical order, string will be 
abdes.
```

**Example 2:**   
```
Input:
N = 13
S = "geeksforgeeks"
Output:
eeeefggkkorss
Explanation:
In lexicographical order, string will be 
eeeefggkkorss.
```

### Constraints

+ `1 <= n <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Function to arrange all letters of a string in lexicographical 
    //order using Counting Sort.
    string countSort(string arr){
        // code here
        int n = arr.size();
        int count[26] = {0} ;
        for(int i=0; i<n; i++){
            count[arr[i]-'a']++ ;
        }
        for(int i=1; i<26; i++){
            count[i] += count[i-1] ;
        }
        vector<char> res(n);
        for(int i=0; i<n; i++){
            res[--count[arr[i]-'a']] = arr[i];
        }
        for(int i=0; i<n; i++){
            arr[i] = res[i];
        }
        return arr;
    }
};
```

