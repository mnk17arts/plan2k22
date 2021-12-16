---
layout: post
title: Maximum Repeating Substring
summary:
tags:
    - string
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/maximum-repeating-substring)  

For a string `sequence`, a string `word` is `k`-repeating if `word` concatenated `k` times is a substring of `sequence`. The `word`'s maximum `k`-repeating value is the highest value `k` where `word` is `k`-repeating in `sequence`. If `word` is not a substring of `sequence`, `word`'s maximum `k`-repeating value is 0.

Given strings `sequence` and `word`, return *the maximum `k`-repeating value of `word` in `sequence`*

### Examples

**Example 1:**  
```
Input: sequence = "ababc", word = "ab"
Output: 2
Explanation: "abab" is a substring in "ababc".
```

**Example 2:**  
```
Input: sequence = "ababc", word = "ba"
Output: 1
Explanation: "ba" is a substring in "ababc". "baba" is not a substring in "ababc".
```

**Example 3:**  
```
Input: sequence = "ababc", word = "ac"
Output: 0
Explanation: "ac" is not a substring in "ababc". 
```

### Constraints
+ `1 <= sequence.length <= 100`
+ `1 <= word.length <= 100`
+ `sequence `and `word` contains only lowercase English letters.

## Solutions

```cpp
class Solution {
public:
    int maxRepeating(string sequence, string word) {
      int res = 0, r = 0;
      int s= sequence.size(), w= word.size();
      for(int i=0; i<s-w+1; i++){
        if(sequence[i]==word[0]){
          int t=0;
          while(word[t%w] == sequence[i+t]) t++;
          r = t/w;
          res = max(res, r);
        }
      }
      return res;
    }
};
```

