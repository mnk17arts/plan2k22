---
layout: post
title:  Letter Combinations of a Phone Number
description: 
summary: 
tags:
    - string
    - backtracking
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
Given a string containing digits from `2-9` inclusive, return *all possible letter combinations that the number could represent. Return the answer in **any order**.*

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that `1` does not map to any letters.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png">

### Examples   
**Example 1:**  
```
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

**Example 2:**  
```
Input: digits = ""
Output: []
```

**Example 3:**  
```
Input: digits = "2"
Output: ["a","b","c"]
```

### Constraints
+ `0 <= digits.length <= 4`
+ `digits[i]` is a digit in the range `['2', '9']`

## Solutions

```cpp
class Solution {
public:
    map<char,string> mp={
        {'2', "abc"}, {'3', "def"}, {'4', "ghi"}, {'5', "jkl"}, {'6', "mno"}, {'7', "pqrs"}, {'8', "tuv"}, {'9', "wxyz"}
    };
    string temp;
    vector<string> res;
    void bc(string &d, int i){
        if( i==d.size() ){
            res.push_back(temp);
            return;
        }
        for(auto c: mp[d[i]]){
            temp.push_back(c);
            bc(d,i+1);
            temp.pop_back();
        }
    }
    vector<string> letterCombinations(string digits) {
        if(!digits.size()) return {};
        bc(digits,0);
        return res;
    }
};
```

