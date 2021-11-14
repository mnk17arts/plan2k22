---
layout: post
title: Iterator for Combination
description: 
summary:
tags:
    - array
    - string
    - backtracking
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/iterator-for-combination)  

Design the CombinationIterator class:

+ `CombinationIterator(string characters, int combinationLength)` Initializes the object with a string `characters` of **sorted distinct** lowercase English letters and a number `combinationLength` as arguments.
+ `next()` Returns the next combination of length `combinationLength` in **lexicographical order**.
+ `hasNext()` Returns `true` if and only if there exists a next combination.

### Examples

**Example 1:**    
```
Input
["CombinationIterator", "next", "hasNext", "next", "hasNext", "next", "hasNext"]
[["abc", 2], [], [], [], [], [], []]
Output
[null, "ab", true, "ac", true, "bc", false]

Explanation
CombinationIterator itr = new CombinationIterator("abc", 2);
itr.next();    // return "ab"
itr.hasNext(); // return True
itr.next();    // return "ac"
itr.hasNext(); // return True
itr.next();    // return "bc"
itr.hasNext(); // return False
```

### Constraints
+ `1 <= combinationLength <= characters.length <= 15`
+ All the characters of `characters` are **unique**.
+ At most `10^4` calls will be made to next and hasNext.
+ It's guaranteed that all calls of the function next are valid.

## Solutions

```cpp
class CombinationIterator {
public:
    vector<string> v;
    string s = "";
    int k, it=0 ;
    void bt(string c, int i){
      if(s.size() == k) {
        v.push_back(s);
        return;
      }
      for(int j=i; j<c.size(); j++){
        s.push_back(c[j]);
        bt(c, j+1);
        s.pop_back();
      }
    }
    CombinationIterator(string characters, int combinationLength) {
      k = combinationLength;
      bt(characters, 0);
    }
    
    string next() {
      return v[it++];
    }
    
    bool hasNext() {
        return it < v.size();
    }
};

/**
 * Your CombinationIterator object will be instantiated and called as such:
 * CombinationIterator* obj = new CombinationIterator(characters, combinationLength);
 * string param_1 = obj->next();
 * bool param_2 = obj->hasNext();
 */
```

