---
layout: post
title: Concatenated Words                       
summary:
tags:
    - leetcode
    - array
    - string
    - dynamic-programming
    - trie
    - dfs
    - cpp
    - hard
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/concatenated-words/description/)  

Given an array of strings words (without duplicates), return all the concatenated words in the given list of words.

A concatenated word is defined as a string that is comprised entirely of at least two shorter words in the given array.

### Examples


**Example 1:**   
```
Input: words = ["cat","cats","catsdogcats","dog","dogcatsdog","hippopotamuses","rat","ratcatdogcat"]
Output: ["catsdogcats","dogcatsdog","ratcatdogcat"]
Explanation: "catsdogcats" can be concatenated by "cats", "dog" and "cats"; 
"dogcatsdog" can be concatenated by "dog", "cats" and "dog"; 
"ratcatdogcat" can be concatenated by "rat", "cat", "dog" and "cat".
```


**Example 2:**   
```
Input: words = ["cat","dog","catdog"]
Output: ["catdog"]
```


### Constraints

+ `1 <= words.length <= 10^4`
+ `1 <= words[i].length <= 30`
+ `words[i]` consists of only lowercase English letters.
+ `0 <= sum(words[i].length) <= 10^5`
+ All the strings of `words` are unique.

## Solutions

```cpp
class Solution {
public:
    vector<string> findAllConcatenatedWordsInADict(vector<string>& words) {
        vector<string> res;
        unordered_set<string> dict(words.begin(), words.end());
        for(auto w : words) {
            if(w.empty())
                continue;
            vector<int> dp(w.size() + 1, 0);
            dp[0] = 1;
            for(int i = 1 ; i <= w.size() ;  i++) {
                for(int j = 0 ; j < i ; j++) {
                    if(i - j < w.size() && dp[j] == 1 && dict.find(w.substr(j, i - j)) != dict.end()) {
                        dp[i] = 1;
                        break;
                    }
                }
            }
            if(dp[w.size()])
                res.push_back(w);
        }
        return res;
    }
};
```

