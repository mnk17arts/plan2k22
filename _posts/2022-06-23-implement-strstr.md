---
layout: post
title: Implement strstr    
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/implement-strstr/0/?track=DSASP-Strings&batchId=154#)  

Your task is to implement the function `strstr`. The function takes two strings as arguments (`s,x`) and  locates the occurrence of the string `x` in the string `s`. The function returns and integer denoting the first occurrence of the string `x` in `s` (`0` based indexing).

**Note**: You are not allowed to use inbuilt function.


**Your Task:** 
You don't have to take any input. Just complete the `strstr()` function which takes two strings `str`, `target` as an input parameter. The function returns `-1` if no match if found else it returns an integer denoting the first occurrence of the `x` in the string `s`.


**Expected Time Complexity:** `O(|s|*|x|)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
s = GeeksForGeeks, x = Fr
Output: -1
Explanation: Fr is not present in the
string GeeksForGeeks as substring.
```

**Example 2:**   
```
Input:
s = GeeksForGeeks, x = For
Output: 5
Explanation: For is present as substring
in GeeksForGeeks from index 5 (0 based
indexing).
```

### Constraints

+ `1 <= |S|, |X| <= 100`

## Solutions

```cpp
class Solution{
    public:
    //Function to locate the occurrence of the string x in the string s.
    int strstr(string s, string x)
    {
        //Your code here
        int n = s.size(), m = x.size();
        for(int i=0; i<n; i++){
            if(s[i] == x[0]) {
                int j = 1;
                for(; j<m; j++)
                    if(s[i+j]!=x[j]) break;
                if(j==m) return i;
            }
        }
        return -1;
    }
};
```

