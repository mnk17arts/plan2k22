---
layout: post
title: Word Search
description: 
summary: 
tags:
    - array
    - matrix
    - leetcode
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/word-search/)
Given an `m x n` grid of characters `board` and a string `word`, return `true` *if `word` exists in the grid*.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2020/11/04/word2.jpg" width="200">  
```
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
Output: true
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2020/11/04/word-1.jpg" width="200">  
```
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "SEE"
Output: true
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2020/10/15/word3.jpg" width="200">  
```
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
Output: false
```
### Constraints
+ `m == board.length`
+ `n = board[i].length`
+ `1 <= m, n <= 6`
+ `1 <= word.length <= 15`
+ `board` and `word` consists of only lowercase and uppercase English letters.

**Follow up**: Could you use search pruning to make your solution faster with a larger `board`?

## Solutions
```cpp
class Solution {
public:
    bool mnk(vector<vector<char>>& board, string word, int i, int j, int wi){
        
        if( wi == word.length()) return true;
        
        if( i >= board.size() || j >= board[0].size() || i<0 || j<0|| board[i][j] == '*' || board[i][j] != word[wi]  ) return false;
        
        char curr = board[i][j];
        board[i][j] = '*';
        
        bool ans = ( mnk(board,word,i,j-1,wi+1) || mnk(board,word,i,j+1,wi+1) || mnk(board,word,i-1,j,wi+1) || mnk(board,word,i+1,j,wi+1) );
        board[i][j] = curr;
        return ans;
        
    }
    
    bool exist(vector<vector<char>>& board, string word) {
        
        
        for(int i=0;i<board.size();i++){
            
            for(int j=0;j<board[0].size();j++){
                
                if(board[i][j] == word[0]){
                    
                    if(mnk(board, word, i, j, 0))
                        return true;
                }
            }
        }
        return false;
    }
};
```
