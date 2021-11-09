---
layout: post
title: Number of Valid Words for Each Puzzle
description: 
summary:
tags:
    - dynamic-programming
    - tree 
    - binary-tree
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/number-of-valid-words-for-each-puzzle)  
With respect to a given puzzle `string`, a `word` is valid if both the following conditions are satisfied:
+ `word` contains the first letter of `puzzle`.
+ For each letter in `word`, that letter is in `puzzle`.
   + For example, if the `puzzle` is `"abcdefg"`, then valid words are `"faced"`, `"cabbage"`, and `"baggage"`, while
   + invalid words are `"beefed"` (does not include `'a'`) and `"based"` (includes `'s'` which is not in the puzzle).

Return *an array `answer`, where `answer[i]` is the number of words in the given word list words that is valid with respect to the puzzle `puzzles[i]`.*

### Examples

**Example 1:**    
```
Input: words = ["aaaa","asas","able","ability","actt","actor","access"], puzzles = ["aboveyz","abrodyz","abslute","absoryz","actresz","gaswxyz"]
Output: [1,1,3,2,4,0]
Explanation: 
1 valid word for "aboveyz" : "aaaa" 
1 valid word for "abrodyz" : "aaaa"
3 valid words for "abslute" : "aaaa", "asas", "able"
2 valid words for "absoryz" : "aaaa", "asas"
4 valid words for "actresz" : "aaaa", "asas", "actt", "access"
There are no valid words for "gaswxyz" cause none of the words in the list contains letter 'g'.
```

**Example 2:**   
```
Input: words = ["apple","pleas","please"], puzzles = ["aelwxyz","aelpxyz","aelpsxy","saelpxy","xaelpsy"]
Output: [0,1,3,2,0]
```

### Constraints
+ `1 <= words.length <= 105`
+ `4 <= words[i].length <= 50`
+ `1 <= puzzles.length <= 104`
+ `puzzles[i].length == 7`
+ `words[i]` and `puzzles[i]` consist of lowercase English letters.
+ Each `puzzles[i]` does not contain repeated characters.

## Solutions

```cpp
class Solution {
public:
vector<int> findNumOfValidWords(vector<string>& words, vector<string>& puzzles) {
        map<char,vector<int>> mp;
        for(int i=0;i<26;i++)
        {
            char ch = (char)('a'+i);
            mp[ch]={};
        }
        for(string word:words)
        {
            int wmask=0;
            for(char c:word)
            {
                int bit = c-'a';
                wmask = wmask | (1 << bit);
            }
            set<char> s;
            for(char c:word)
            {
                auto pos = s.find(c);
                if(pos!=s.end())
                {
                    continue;
                }
                s.insert(c);
                mp[c].push_back(wmask);
            }
        }
        vector<int> ans;
        for(string puzzle:puzzles)
        {
            int pmask=0;
            for(char c:puzzle)
            {
                int bit = c-'a';
                pmask = pmask | (1 << bit);
            }
            
            char ch = puzzle[0];
            vector<int> v=mp[ch];
            int count=0;
            for(int temp:v)
            {
                if((pmask & temp)==temp)
                {
                    count++;
                }
            }
            ans.push_back(count);
            // count=0;
        }
        return ans;
    }
};
```

