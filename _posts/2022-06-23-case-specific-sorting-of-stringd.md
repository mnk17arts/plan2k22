---
layout: post
title: Case-specific Sorting of Strings    
summary:
tags:
    - string
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/case-specific-sorting-of-strings4845/0/?#)  

Given a string `S` consisting of uppercase and lowercase characters. The task is to sort uppercase and lowercase letters separately such that if the `i`th place in the original string had an Uppercase character then it should not have a lowercase character after being sorted and vice versa.

**Your Task:** 
You only need to complete the function `caseSort` that returns sorted string.


**Expected Time Complexity:** `O(N*Log(N))`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 12
S = defRTSersUXI
Output: deeIRSfrsTUX
Explanation: Sorted form of given string
with the same case of character as that
in original string is deeIRSfrsTUX
```

**Example 2:**   
```
Input:
N = 6
S = srbDKi
Output: birDKs
Explanation: Sorted form of given string
with the same case of character will
result in output as birDKs.
```

### Constraints

+ `1 ≤ N ≤ 10^3`

## Solutions

```cpp
class Solution{
    public:
    //Function to perform case-specific sorting of strings.
    string caseSort(string str, int n)
    {
        // your code here
        int ca[n] = {0};
        string lc = "", uc = "";
        for(int i=0; i<n; i++)
            if('A' <= str[i] && str[i] <= 'Z'){
                ca[i] = 1;
                uc += str[i];
            }else lc += str[i];
        sort(uc.begin(),uc.end());
        sort(lc.begin(),lc.end());
        int l=0, u=0;
        for(int i=0; i<n; i++)
            if(ca[i]) str[i]=uc[u++];
            else str[i]=lc[l++];
        return str;
    }
};
```

