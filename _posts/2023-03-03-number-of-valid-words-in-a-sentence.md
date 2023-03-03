---
layout: post
title: Number of Valid Words in a Sentence
summary:
tags:
  - string
  - leetcode
  - cpp
  - easy
minute: 8+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/number-of-valid-words-in-a-sentence/)

A sentence consists of lowercase letters (`'a'` to `'z'`), digits (`'0'` to `'9'`), hyphens (`'-'`), punctuation marks (`'!'`, `'.'`, and `','`), and spaces (`' '`) only. Each sentence can be broken down into **one or more tokens** separated by one or more spaces `' '`.

A token is a valid word if:

- It only contains lowercase letters, hyphens, and/or punctuation (**no** digits).
- There is **at most** one hyphen `'-'`. If present, it should be surrounded by lowercase characters (`"a-b"` is valid, but `"-ab"` and `"ab-"` are not valid).
- There is **at most** one punctuation mark. If present, it should be at the **end** of the token.

Examples of valid words include `"a-b."`, `"afad"`, `"ba-c"`, `"a!"`, and `"!"`.

Given a string `sentence`, return _the number of valid words in sentence._

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

- `1 <= sentence.length <= 1000`
- `sentence` only contains lowercase English letters, digits, `' '`, `'-'`, `'!'`, `'.'`, and `','`.
- There will be at least `1` token.

## Solutions

```cpp

class Solution {
    bool validToken(string str) {
        int n = str.length();
        int hypen = 0;
        for(int i = 0; i < n; i++) {
            if(isdigit(str[i])) {
                return false;
            }
            if(isalpha(str[i])) {
                continue;
            }
            if(str[i] == '-') {
                if(++hypen > 1) {
                    return false;
                }
                if(i - 1 < 0 || !isalpha(str[i - 1]) || i + 1 >= n || !isalpha(str[i + 1]) ) {
                    return false;
                }
            }
            else if(i != n - 1) {
                return false;
            }
        }
        return true;
    }
public:
    int countValidWords(string sentence) {
        int res = 0;
        string word;
        stringstream ss(sentence);
        while(ss >> word) {
            res += validToken(word);
        }
        return res;
    }
};

```
