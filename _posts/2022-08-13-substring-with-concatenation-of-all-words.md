---
layout: post
title: Substring with Concatenation of All Words
tags:
    - array
    - leetcode
    - hash
    - slidingwindow
    - cpp
    - hard
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)

You are given a string s and an array of strings words of the same length. Return all starting indices of substring(s) in s that is a concatenation of each word in words exactly once, in any order, and without any intervening characters.

You can return the answer in any order.

### Examples

**Example 1:**

```
Input: s = "barfoothefoobarman", words = ["foo","bar"]
Output: [0,9]
Explanation: Substrings starting at index 0 and 9 are "barfoo" and "foobar" respectively.
The output order does not matter, returning [9,0] is fine too.
```

**Example 2:**

```
Input: s = "wordgoodgoodgoodbestword", words = ["word","good","best","word"]
Output: []
```

**Example 3:**

```
Input: s = "barfoofoobarthefoobarman", words = ["bar","foo","the"]
Output: [6,9,12]
```



### Constraints
+ `1 <= s.length <= 10^4`
+ `1 <= words.length <= 5000`
+ `1 <= words[i].length <= 30`
+ `s` and `words[i]` contains only lowercase English letters.

## Solution
```cpp
class Solution {
public:

    bool helper(int ws, string s,unordered_map<string, int> mp) {
        for(int j=0;j<s.size();j+=ws){
            string ss = s.substr(j,ws);
            if(mp.find(ss)!=mp.end()&&mp[ss]!=0){
                mp[ss]--;
            }else return false;
        }
        return true;
    }
    vector<int> findSubstring(string s, vector<string>& words) {
        vector<int> res;
        unordered_map<string, int> mpw;
        int k,ws,as;
        k = words.size();
        ws = words[0].length();
        as = k*ws;
        if(as>s.size()) return res;
        for(auto i: words) mpw[i]++;
        for(int i=0;i<=s.length()-as;i++){
            if(helper(ws,s.substr(i,as),mpw)) res.push_back(i);
        }
        return res;
    }
};
```