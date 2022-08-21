---
layout: post
title: Stamping The Sequence                       
summary:
tags:
    - leetcode
    - string
    - stack
    - greedy
    - queue
    - cpp
    - hard
minute: 15 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/stamping-the-sequence/)  

You are given two strings `stamp` and `target`. Initially, there is a string s of length `target.length` with all `s[i] == '?'`.

In one turn, you can place `stamp` over s and replace every letter in the `s` with the corresponding letter from `stamp`.

+ For example, if `stamp` = "`abc`" and `target` = "`abcba`", then `s` is "`?????`" initially. In one turn you can:
    - place `stamp` at index `0` of `s` to obtain "`abc??`",
    - place `stamp` at index `1` of `s` to obtain "`?abc?`", or
    - place `stamp` at index `2` of `s` to obtain "`??abc`".

Note that `stamp` must be fully contained in the boundaries of `s` in order to `stamp` (i.e., you cannot place `stamp` at index `3` of `s`).

We want to convert `s` to `target` using at most `10 * target.length` turns.

Return an array of the index of the left-most letter being stamped at each turn. If we cannot obtain `target` from s within `10 * target.length` turns, return an empty array.


### Examples


**Example 1:**   
```
Input: stamp = "abc", target = "ababc"
Output: [0,2]
Explanation: Initially s = "?????".
- Place stamp at index 0 to get "abc??".
- Place stamp at index 2 to get "ababc".
[1,0,2] would also be accepted as an answer, as well as some other answers.
```

**Example 2:**   
```
Input: stamp = "abca", target = "aabcaca"
Output: [3,0,1]
Explanation: Initially s = "???????".
- Place stamp at index 3 to get "???abca".
- Place stamp at index 0 to get "abcabca".
- Place stamp at index 1 to get "aabcaca".
```

### Constraints

+ `1 <= stamp.length <= target.length <= 1000`
+ `stamp and target consist of lowercase English letters.`

## Solutions

```cpp
class Solution {
public:
    bool isQ(string s){
        for(char c: s)
            if(c!='?')
                return false;
        return true;
    }
    
    bool isMatch(string a,string b){
        if(a.size()!=b.size()) return false;
        for(int i=0;i<a.size();i++)
            if(a[i]!=b[i]&&a[i]!='?'&&b[i]!='?')
                return false;
        return true;
    }
    
    vector<int> movesToStamp(string stamp, string target) {
        int n = target.size();
        int m = stamp.size();
        vector<int> res;
        bool flag = true;
        string str;
        while(flag){
            flag = false;
            for(int i=0;i<n-m+1;i++){
                str = target.substr(i,m);
                if(isQ(str)) continue;
                if(isMatch(str,stamp)){
                    flag = true;
                    res.push_back(i);
                    for(int j=0;j<m;j++) target[i+j]='?';
                }
            }
        }
        if(!isQ(target)) res.clear();
        if(res.size()>10*n) res.clear();
        reverse(res.begin(),res.end());
        return res;
    }
};
```

