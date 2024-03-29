---
layout: post
title: Minimum times A has to be repeated such that B is a substring of it                     
summary:
tags:
    - geeksforgeeks
    - searching
    - string
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/fda70097eb2895ecfff269849b6a8aace441947c/1)  

Given two strings A and B. Find minimum number of times A has to be repeated such that B is a Substring of it. If B can never be a substring then return -1.

**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function minRepeats() which takes 2 strings A, and B respectively and returns the minimum number of times A has to be repeated such that B is a substring of it. Return -1 if it's not possible


**Expected Time Complexity:** `O(|A|*|B|)`              
**Expected Auxiliary Space:** `O(|B|)` 



### Examples

**Example 1:**   
```
Input:
A = "abcd"
B = "cdabcdab"
Output:
3
Explanation:
Repeating A three times (abcdabcdabcd),
B is a substring of it. B is not a substring
of A when it is repeated less than 3 times.
```

**Example 2:**   
```
Input:
A = "ab"
B = "cab"
Output :
-1
Explanation:
No matter how many times we repeat A, we can't
get a string such that B is a substring of it.
```

### Constraints

+ `1 ≤ |A|, |B| ≤ 1000`
+ String `A` and `B` consists of lower case alphabets

## Solutions

```cpp

class Solution {
  public:
    int minRepeats(string A, string B) {
        // code here
        int count=1;
        string temp = A;
        while( A.length() < B.length() ) {
            A += temp;
            count++;
        }
        if( A.find(B) != string::npos ) {
            return count;
        }
        A += temp;
        count++;
        if( A.find(B) != string::npos ) {
            return count;
        }
        return -1;
    }
};

```

