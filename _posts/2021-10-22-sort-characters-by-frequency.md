---
layout: post
title:  Sort Characters By Frequency
description: 
summary: 
tags:
    - string
    - sorting
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/sort-characters-by-frequency/)
Given a string `s`, sort it in decreasing order based on the frequency of the characters. The frequency of a character is the number of times it appears in the string.

Return *the sorted string*. If there are multiple answers, return *any of them.*
 
### Examples   
**Example 1:**  
```
Input: s = "tree"
Output: "eert"
Explanation: 'e' appears twice while 'r' and 't' both appear once.
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.
```

**Example 2:**  
```
Input: s = "cccaaa"
Output: "aaaccc"
Explanation: Both 'c' and 'a' appear three times, so both "cccaaa" and "aaaccc" are valid answers.
Note that "cacaca" is incorrect, as the same characters must be together.
```

**Example 3:**  
```
Input: s = "Aabb"
Output: "bbAa"
Explanation: "bbaA" is also a valid answer, but "Aabb" is incorrect.
Note that 'A' and 'a' are treated as two different characters.
```

### Constraints
+ `1 <= s.length <= 5 * 10^5`
+ `s` consists of uppercase and lowercase English letters and digits.


## Solutions

```cpp
class Solution {
public:

    string frequencySort(string s) {
        
        map<char,int> mp;
        int k=0;
        multimap<int, char, greater<int>> mp2;
        
        for(auto c: s) mp[c]++;
        for(auto i: mp) mp2.insert({i.second,i.first});
        for(auto i=mp2.begin(); i!=mp2.end(); i++)
            for(auto j=0; j<i->first; j++){
                s[k++] = i->second;
            }
                
        return s;
    }
};
```

