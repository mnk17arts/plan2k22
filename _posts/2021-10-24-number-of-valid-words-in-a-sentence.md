---
layout: post
title:  Number of Valid Words in a Sentence
description: 
summary: 
tags:
    - string
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/number-of-valid-words-in-a-sentence/)  
A sentence consists of lowercase letters (`'a'` to `'z'`), digits (`'0'` to `'9'`), hyphens (`'-'`), punctuation marks (`'!'`, `'.'`, and `','`), and spaces (`' '`) only. Each sentence can be broken down into **one or more tokens** separated by one or more spaces `' '`.

A token is a valid word if:

+ It only contains lowercase letters, hyphens, and/or punctuation (**no** digits).
+ There is **at most** one hyphen `'-'`. If present, it should be surrounded by lowercase characters (`"a-b"` is valid, but `"-ab"` and `"ab-"` are not valid).
+ There is **at most** one punctuation mark. If present, it should be at the **end** of the token.

Examples of valid words include `"a-b."`, `"afad"`, `"ba-c"`, `"a!"`, and `"!"`.

Given a string `sentence`, return *the number of valid words in sentence.*
 
### Examples   
**Example 1:**  
```
Input: sentence = "cat and  dog"
Output: 3
Explanation: The valid words in the sentence are "cat", "and", and "dog".
```

**Example 2:**   
``` 
Input: sentence = "!this  1-s b8d!"
Output: 0
Explanation: There are no valid words in the sentence.
"!this" is invalid because it starts with a punctuation mark.
"1-s" and "b8d" are invalid because they contain digits.
```

**Example 3:**   
``` 
Input: sentence = "alice and  bob are playing stone-game10"
Output: 5
Explanation: The valid words in the sentence are "alice", "and", "bob", "are", and "playing".
"stone-game10" is invalid because it contains digits.
```

**Example 4:**   
``` 
Input: sentence = "he bought 2 pencils, 3 erasers, and 1  pencil-sharpener."
Output: 6
Explanation: The valid words in the sentence are "he", "bought", "pencils,", "erasers,", "and", and "pencil-sharpener.".
```

### Constraints
+ `1 <= sentence.length <= 1000`
+ `sentence` only contains lowercase English letters, digits, `' '`, `'-'`, `'!'`, `'.'`, and `','`.
+ There will be at least `1` token.


## Solutions

```cpp
typedef vector<string> VS;

#define FORI(i,n) for(int i=0; i<n; i++)

// splits a line into words at given char
VS split(string s,char c=' '){
    int ssi = 0;
    if(c == ' '){
        VS vs;
        string x;
        stringstream ss(s);
        while(ss >> x) vs.push_back(x); 
        return vs;
    }
    VS ret;
    FORI(i,s.size()){
        if(s[i]==c){
            ret.push_back(s.substr(ssi, i-ssi));
            ssi = i+1;
        }
    }
    ret.push_back(s.substr(ssi));
    return ret;
}

class Solution {
public:
    int countValidWords(string s) {
        VS vs= split(s,' ');
        int res=0;
        for(auto w: vs){
            bool yes = true;
            int _h = 0;
            FORI(i,w.size()){
                if(isdigit(w[i])) yes = false;
                else if(w[i] == '-'){
                    _h++;
                    if( i>=1 and i<w.size()-1 and islower(w[i-1]) and islower(w[i+1])){}
                    else yes = false;
                }
                else if(w[i]=='!' or w[i]=='.' or w[i]==','){
                    if(i!=w.size()-1) yes = false;
                }
            }
            if(_h >= 2) yes = false;
            if(yes) res++;
        }
        return res;
    }
};
```

