---
layout: post
title:  Design Add and Search Words Data Structure
summary:
tags:
    - string
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/design-add-and-search-words-data-structure)  

Design a data structure that supports adding new words and finding if a string matches any previously added string.

Implement the `WordDictionary `class:

+ `WordDictionary()` Initializes the object.
+ `void addWord(word) `Adds word to the data structure, it can be matched later.
+ `bool search(word)` Returns `true` if there is any string in the data structure that matches `word` or `false` otherwise. `word` may contain dots `'.'` where dots can be matched with any letter.


### Examples

**Example 1:**  
```
Input
["WordDictionary","addWord","addWord","addWord","search","search","search","search"]
[[],["bad"],["dad"],["mad"],["pad"],["bad"],[".ad"],["b.."]]
Output
[null,null,null,null,false,true,true,true]

Explanation
WordDictionary wordDictionary = new WordDictionary();
wordDictionary.addWord("bad");
wordDictionary.addWord("dad");
wordDictionary.addWord("mad");
wordDictionary.search("pad"); // return False
wordDictionary.search("bad"); // return True
wordDictionary.search(".ad"); // return True
wordDictionary.search("b.."); // return True
```

### Constraints

+ `1 <= word.length <= 500`
+ `word` in `addWord` consists lower-case English letters.
+ `word` in `search` consist of  `'.'` or lower-case English letters.
+ At most `50000` calls will be made to `addWord` and `search`.

## Solutions

```cpp
class WordDictionary {
  map<int ,vector<string>> wd;
  bool similar(string w1, string w2){
    for(int i=0; i<size(w1); i++){
      if(w2[i]=='.') continue;
      if(w1[i]!=w2[i]) return false;
    }
    return true;
  }
public:
    WordDictionary() {}
    
    void addWord(string word) {
      wd[size(word)].push_back(word);  
    }
    
    bool search(string word) {
        for(auto i: wd[size(word)]){
          if(similar(i, word)) return true;
        }
      return false;
    }
};

/**
 * Your WordDictionary object will be instantiated and called as such:
 * WordDictionary* obj = new WordDictionary();
 * obj->addWord(word);
 * bool param_2 = obj->search(word);
 */
```

