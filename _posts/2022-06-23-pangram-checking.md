---
layout: post
title: Pangram Checking  
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/pangram-checking-1587115620/0/?)  

Given a string check if it is Pangram or not. A pangram is a sentence containing every letter in the English Alphabet.

**Your Task:** 
You need to complete the function `checkPangram()` that takes a string as a parameter and returns `true` if the string is a pangram, else it returns `false`.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(Number of distinct characters)`

### Examples

**Example 1:**   
```
Input:
S = Bawds jog, flick quartz, vex nymph
Output: 1
Explantion: In the given input, there
are all the letters of the English
alphabet. Hence, the output is 1.
```

**Example 2:**   
```
Input:
S = sdfs
Output: 0
Explantion: In the given input, there
aren't all the letters present in the
English alphabet. Hence, the output
is 0.
```

### Constraints

+ `1 <= length of the string <= 10^4`

## Solutions

```cpp
class Solution{
    public:
    //Function to check if a string is Pangram or not.
    bool checkPangram (string &str) {
        // your code here
        unordered_set<char> us;
        for(int i=0; i<str.size(); i++){
            if(isalpha(str[i]))
                us.insert(tolower(str[i]));
        }
        return us.size()==26;
    }
};
```

