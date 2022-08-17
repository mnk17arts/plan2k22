---
layout: post
title: Valid Sudoku                       
summary:
tags:
    - leetcode
    - array
    - hash
    - cpp
    - medium
minute: 9 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/valid-sudoku/)  

Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

1. Each row must contain the digits `1-9` without repetition.
1. Each column must contain the digits `1-9` without repetition.
1. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

Note:

+ A Sudoku board (partially filled) could be valid but is not necessarily solvable.
+ Only the filled cells need to be validated according to the mentioned rules.


### Examples

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png">

**Example 1:**   
```
Input: board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: true
```

**Example 2:**   
```
Input: board = 
[["8","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: false
Explanation: Same as Example 1, except with the 5 in the top left corner being modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.
```

### Constraints

+ `board.length == 9`
+ `board[i].length == 9`
+ `board[i][j]` contains digits `0-9` or `.`.


## Solutions

```cpp
class Solution {
public:
    bool isSafe(vector<vector<char>>& board,int i,int j,char c){
        for(int k=0;k<9;k++){
            if(board[i][k]==c) return false;
            if(board[k][j]==c) return false;
            if(board[3*(i/3)+k/3][3*(j/3)+k%3]==c) return false;
        }
        return true;
    }
    bool isValidSudoku(vector<vector<char>>& board) {
        for(int i=0;i<9;i++){
            for(int j=0;j<9;j++){
                if(board[i][j]=='.') continue;
                char c = board[i][j];
                board[i][j] = '.';
                if(!isSafe(board,i,j,c))
                    return false;
                board[i][j] = c;
            }
        }
        return true;
    }
};
```

