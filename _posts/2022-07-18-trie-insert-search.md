---
layout: post
title: Trie | (Insert and Search)                    
summary:
tags:
    - trie
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/trie-insert-and-search0651/0/?track=DSASP-Trie&batchId=154#)  

Trie is an efficient information retrieval data structure. Use this data structure to store Strings and search strings. Your task is to use TRIE data structure and search the given string `A`. If found print `1` else `0`

**Your Task:** 

Complete `insert` and `search` function and return `true` if key is present in the formed trie else `false` in the search function. (In case of true, `1` is printed and false, `0` is printed by the driver's code.


**Expected Time Complexity:** `O(M+|search|)`              
**Expected Auxiliary Space:** `O(M)`
`M` = sum of the length of all strings which is present in the `key[]` 

`|search|` denotes the length of the string search.


### Examples

**Example 1:**   
```
Input:
N = 8
key[] = {the,a,there,answer,any,by,
         bye,their}
search = the
Output: 1
Explanation: the is present in the given
string "the a there answer any by bye
their" 
```

**Example 2:**
```
Input:
N = 8
key[] = {the,a,there,answer,any,by,
         bye,their}
search = geeks
Output: 0
Explanation: geeks is not present in the
given string "the a there answer any by
bye their"
```

### Constraints

+ `1 ≤ N <= 10^4`
+ `1 <= |input strings|, |A| <= 100`

## Solutions

```cpp
//Function to insert string into TRIE.
void insert(struct TrieNode *root, string key)
{
    // code here
    TrieNode* cur = root;
    for(int i=0;i<key.length();i++){
        int id = key[i]-'a';
        if(cur->children[id]==NULL)
            cur->children[id] = getNode();
        cur = cur->children[id];
    }
    cur->isLeaf = true;
}

//Function to use TRIE data structure and search the given string.
bool search(struct TrieNode *root, string key) 
{
    // code here
    int id = key[0]-'a';
    if(root->children[id]==NULL) return false;
    if(key.length() == 1)
        return root->children[id]->isLeaf;
    return search(root->children[id],key.substr(1));
}
```

