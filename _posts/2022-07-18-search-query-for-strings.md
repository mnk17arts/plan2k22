---
layout: post
title: Search Query for Strings                      
summary:
tags:
    - trie
    - strings
    - geeksforgeeks
    - cpp
    - easy
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/search-query-for-strings5049/0/?tr)  

Trie is an efficient information retrieval data structure. Use this data structure to store strings and search strings. In this problem, you are given an array of strings (consisting of lowercase characters) `arr[]` of size `N`. Also, you will be given some queries `Q` and for each query a string is given and your task is to check if the given string is in the string array or not.

Note: Each word in the array of string can be of size `10^3`.



**Your Task:** 

Complete `insert` and `search`, return `true` if the given string is present in the TRIE, else `false` in search function.  `1` is printed by the driver's code if the value returned is true, `0` otherwise.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`



### Examples

**Example 1:**   
```
Input:
N = 8, Q = 3
words[] = {the,a,there,answer,any,by,bye
their}
Queries[] = {the,an,any}
Output:
1
0
1
Explanation: After inserting words in the
array,all the words will be stored. Now
searching for the will result in 1
(present), an will resultin 0(not present)
and any will result in 1 (present).
```

### Constraints

+ `1 ≤ N <= 1000`
+ `1 ≤ Q <= 1000`


## Solutions

```cpp

//Function to insert string into TRIE.
void insert(struct TrieNode *root, string key)
{
    // code here
    struct TrieNode *cur = root;
    for(int i=0;i<key.length();i++){
        int id = key[i]-'a';
        if(cur->children[id]==NULL) 
            cur->children[id] = getNode();
        cur = cur->children[id];
    }
    cur->isEndOfWord = true;
}

//Function to use TRIE data structure and search the given string.
bool search(struct TrieNode *root, string key) 
{
    // code here
    struct TrieNode *cur = root;
    for(int i=0;i<key.length();i++){
        int id = key[i]-'a';
        if(cur->children[id]==NULL)
            return false;
        cur = cur->children[id];
    }
    return cur->isEndOfWord;
}

```

