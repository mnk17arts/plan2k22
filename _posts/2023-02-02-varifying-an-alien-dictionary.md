---
layout: post
title: Verifying an Alien Dictionary                       
summary:
tags:
    - leetcode
    - string
    - hash
    - array
    - cpp
    - easy
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/verifying-an-alien-dictionary/description/)  

In an alien language, surprisingly, they also use English lowercase letters, but possibly in a different order. The order of the alphabet is some permutation of lowercase letters.

Given a sequence of words written in the alien language, and the order of the alphabet, return true if and only if the given words are sorted lexicographically in this alien language.

### Examples


**Example 1:**   
```
Input: words = ["hello","leetcode"], order = "hlabcdefgijkmnopqrstuvwxyz"
Output: true
Explanation: As 'h' comes before 'l' in this language, then the sequence is sorted.
```

**Example 2:**   
```
Input: words = ["word","world","row"], order = "worldabcefghijkmnpqstuvxyz"
Output: false
Explanation: As 'd' comes after 'l' in this language, then words[0] > words[1], hence the sequence is unsorted.
```

**Example 3:**   
```
Input: words = ["apple","app"], order = "abcdefghijklmnopqrstuvwxyz"
Output: false
Explanation: The first three characters "app" match, and the second string is shorter (in size.) According to lexicographical rules "apple" > "app", because 'l' > '∅', where '∅' is defined as the blank character which is less than any other character 
```

### Constraints

+ `11 <= words.length <= 100`
+ `s1 <= words[i].length <= 20`
+ `order.length == 26`
+ All characters in `words[i]` and order are English lowercase letters.

## Solutions

```cpp

class Solution {
public:
    int abc[26];
    bool isInvalid(string s1, string s2) {
        int i=0;
        while(i<s1.length() && i<s2.length()) {
            if(s1[i]==s2[i]) {
                i++;
            }
            else if(abc[s1[i]-'a'] > abc[s2[i]-'a']) {
                return true;
            }
            else {
                return false;
            }
        } 
        if( s1.length() > s2.length() ) {
            return true;
        }
        return false;
    }
    bool isAlienSorted(vector<string>& words, string order) {
        for(int i=0; i<order.length(); i++) {
            abc[order[i]-'a'] = i;
        }
        for(int i=0; i<words.size()-1; i++) {
            if(isInvalid(words[i], words[i+1])) {
                return false;
            }
        }
        return true;
    }
};

```

