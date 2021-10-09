---
layout: post
title: Word Search II
description: 
summary: 
tags:
    - string
    - array
    - matrix
    - backtracking
    - trie
    - leetcode
    - cpp
    - hard
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/word-search-ii/)
Given an `m x n board` of characters and a list of strings `words`, return *all words on the board.*

Each word must be constructed from letters of sequentially adjacent cells, where **adjacent cells** are horizontally or vertically neighboring. The same letter cell may not be used more than once in a word.

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2020/11/07/search1.jpg" height="250">
```
Input: board = [["o","a","a","n"],["e","t","a","e"],["i","h","k","r"],["i","f","l","v"]], words = ["oath","pea","eat","rain"]
Output: ["eat","oath"]
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2020/11/07/search2.jpg" height="250">
```
Input: board = [["a","b"],["c","d"]], words = ["abcb"]
Output: []
```

### Constraints
+ `m == board.length`
+ `n == board[i].length`
+ `1 <= m, n <= 12`
+ `board[i][j]` is a lowercase English letter.
+ `1 <= words.length <= 3 * 10^4`
+ `1 <= words[i].length <= 10`
+ `words[i]` consists of lowercase English letters.
+ All the strings of `words` are unique.

## Solutions
```cpp
class Solution {
public:
  
    bool mnk(vector<vector<char>>& board, string word, int i, int j, int wi){
        
        if( wi == -1) return true;
        
        if( i >= board.size() || j >= board[0].size() || i<0 || j<0|| board[i][j] == '*' || board[i][j] != word[wi]  ) return false;
        
        char curr = board[i][j];
        board[i][j] = '*';
        
        bool ans = ( mnk(board,word,i,j-1,wi-1) || mnk(board,word,i,j+1,wi-1) || mnk(board,word,i-1,j,wi-1) || mnk(board,word,i+1,j,wi-1) );
      
        board[i][j] = curr;
      
        return ans;
        
    }
  
    vector<string> findWords(vector<vector<char>>& board, vector<string>& words) {
      
        vector<string> answer;
        bool yess;
      
        set<char> s;
        for(int i=0; i<words.size(); i++){
            char ch = words[i][words[i].length()-1]; 
            s.insert(ch);
        }
        
        map<char,vector<pair<int,int>>> mp;
        for(int i = 0; i < board.size(); i++){
            for(int j = 0; j < board[0].size(); j++){
                char ch = board[i][j];
                if(s.find(ch) != s.end()){
                    mp[ch].push_back({i,j}); 
                }
            }
        }
        
        for(int i=0 ; i < words.size(); i++){
            string st = words[i];
            char ch = st[st.length()-1];
            vector<pair<int,int>> v = mp[ch];
            for(int j=0; j<v.size(); j++){
                int x = v[j].first;
                int y = v[j].second;
                if(mnk(board, st, x, y, st.length()-1)){
                    answer.push_back(st);
                    break;
                }
            }
        }        

        return answer;
    }
};
```
