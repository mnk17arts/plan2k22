---
layout: post
title: Merge Strings Alternately
summary:
tags:
  - leetcode
  - string
  - 2pointers
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/merge-strings-alternately/description/)

You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.


### Examples

**Example 1:**  

```
Input: word1 = "abc", word2 = "pqr"
Output: "apbqcr"
Explanation: The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r
```

**Example 2:**  

```
Input: word1 = "ab", word2 = "pqrs"
Output: "apbqrs"
Explanation: Notice that as word2 is longer, "rs" is appended to the end.
word1:  a   b 
word2:    p   q   r   s
merged: a p b q   r   s
```

**Example 3:**  

```
Input: word1 = "abcd", word2 = "pq"
Output: "apbqcd"
Explanation: Notice that as word1 is longer, "cd" is appended to the end.
word1:  a   b   c   d
word2:    p   q 
merged: a p b q c   d
```

### Constraints

- `1 <= word1.length, word2.length <= 100`
- `word1 and word2 consist of lowercase English letters.`


## Solutions

```cpp

class Solution {
public:
    string mergeAlternately(string word1, string word2) {
        int i=0;
        int j=0;
        string finals="";
        while(i<word1.length()&&j<word2.length()){
            finals+=word1[i];
            finals+=word2[j];
            i++;
            j++;
        }
        for(int m=i;m<word1.length();m++){
            finals+=word1[m];
        }
        for(int m=j;m<word2.length();m++){
            finals+=word2[m];
        }
        return finals;
    }
};

```
