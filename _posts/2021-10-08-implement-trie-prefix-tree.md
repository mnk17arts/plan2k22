---
layout: post
title: Implement Trie (Prefix Tree)
description: 
summary: 
tags:
    - trie
    - leetcode
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/implement-trie-prefix-tree/)
A `trie` (pronounced as "try") or **prefix tree** is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class: 

+ `Trie()` Initializes the trie object.
+ `void insert(String word)` Inserts the string `word` into the trie.
+ `boolean search(String word)` Returns `true` if the string `word` is in the `trie` (i.e., was inserted before), and `false` otherwise.
+ `boolean startsWith(String prefix)` Returns `true` if there is a previously inserted string `word` that has the prefix `prefix`, and `false` otherwise.
 

### Examples
**Example 1:**  
```
Input
["Trie", "insert", "search", "search", "startsWith", "insert", "search"]
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]
Output
[null, null, true, false, true, null, true]

Explanation
Trie trie = new Trie();
trie.insert("apple");
trie.search("apple");   // return True
trie.search("app");     // return False
trie.startsWith("app"); // return True
trie.insert("app");
trie.search("app");     // return True
```

### Constraints
+ `1 <= word.length, prefix.length <= 2000`
+ `word` and `prefix` consist only of lowercase English letters.
+ At most `3 * 10^4` calls **in total** will be made to `insert`, `search`, and `startsWith`.

## Solutions
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Trie {
public:
    set<string> trieData;
    Trie() {
    
    }
    
    void insert(string word) {
        
        trieData.insert(word);
        
    }
    
    bool search(string word) {
        
        if(trieData.find(word)!=trieData.end()) return true;
        
        return false;
    }
    
    bool startsWith(string prefix) {
        
        for(set<string>::iterator it = trieData.begin(); it != trieData.end(); it++ ){
            
            int i=0,j=0;
            
            while(i<prefix.size()){
                
                if((*it)[i]==prefix[i]) j++;
                
                else break;
                
                if(j==prefix.size()) return true;
                
                i++;
            }
        }
        return false;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */
```
