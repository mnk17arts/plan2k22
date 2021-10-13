---
layout: post
title: Letter Case Permutation
description: 
summary: 
tags:
    - string
    - recursion
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/letter-case-permutation/)
Given a string `s`, we can transform every letter individually to be lowercase or uppercase to create another string.

Return *a list of all possible strings we could create. You can return the output in **any order**.*
 

### Examples

**Example 1:**  
```
Input: s = "a1b2"
Output: ["a1b2","a1B2","A1b2","A1B2"]
```

**Example 2:**  
```
Input: s = "3z4"
Output: ["3z4","3Z4"]
```

**Example 3:**  
```
Input: s = "12345"
Output: ["12345"]
```

**Example 4:**  
```
Input: s = "0"
Output: ["0"]
```

### Constraints
+ `s` will be a string with length between `1 and 12`.
+ `s` will consist only of letters or digits.


## Solutions

```cpp

class Solution {
public:
    vector<string> ans;
    
    void recurse(int i, string &s){
        if(i == s.size()){
            ans.push_back(s);
            return ;
        }
        for(int j=i; j<s.size(); j++){
            if(s[j] >= '0' && s[j]<='9'){
                continue;                
            }
            else if(s[j] >='a' && s[j]<='z'){
                s[j] = (s[j] - 'a') + 'A';
                recurse(j+1,s);
                s[j] = (s[j] - 'A') + 'a';
            }else{
                s[j] = (s[j] - 'A') + 'a';
                recurse(j+1,s);
                s[j] = (s[j] - 'a') + 'A';
            }            
        }

        ans.push_back(s);
        return;
    }
    
    vector<string> letterCasePermutation(string s) {
        
        recurse(0,s);
        return ans;
    
    }
};

```
