---
layout: post
title:  Surrounded Regions
description: 
summary: 
tags:
    - array
    - matrix
    - dfs
    - bfs
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/surrounded-regions/)  
Given an `m x n` matrix `board` containing `'X'` and `'O'`, capture all regions that are 4-directionally surrounded by `'X'`.

A region is captured by flipping all `'O'`s into `'X'`s in that surrounded region.
 
### Examples   
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/02/19/xogrid.jpg">
```
Input: board = [["X","X","X","X"],["X","O","O","X"],["X","X","O","X"],["X","O","X","X"]]
Output: [["X","X","X","X"],["X","X","X","X"],["X","X","X","X"],["X","O","X","X"]]
Explanation: Surrounded regions should not be on the border, which means that any 'O' on the border of the board are not flipped to 'X'. Any 'O' that is not on the border and it is not connected to an 'O' on the border will be flipped to 'X'. Two cells are connected if they are adjacent cells connected horizontally or vertically.
```

**Example 2:**   
``` 
Input: board = [["X"]]
Output: [["X"]]
```

### Constraints
+ `m == board.length`
+ `n == board[i].length`
+ `1 <= m, n <= 200`
+ `board[i][j] is 'X' or 'O'`


## Solutions

```cpp
class Solution {
public:
    void bt(vector<vector<char>>& board, int i, int j, int m, int n){
        if(i<0 or i>=m or j<0 or j>=n or board[i][j]!='O') return;
        board[i][j] = '$';
        bt(board,i-1,j,m,n) ;
        bt(board,i,j-1,m,n) ;
        bt(board,i+1,j,m,n) ;
        bt(board,i,j+1,m,n);
    }
    void solve(vector<vector<char>>& board) {
        int m=board.size();
        int n=board[0].size();
        if(m<3 or n<3) return;
        for(int i=0; i<m; i++){
            if(board[i][0] == 'O') bt(board,i,0,m,n);
            if(board[i][n-1] == 'O') bt(board,i,n-1,m,n);
        }
        for(int i=0; i<n; i++){
            if(board[0][i] == 'O') bt(board,0,i,m,n);
            if(board[m-1][i] == 'O') bt(board,m-1,i,m,n);
        }
        
        for(int i=0 ; i<m; i++)
            for(int j=0 ; j<n; j++){
                if(board[i][j] == 'O') board[i][j] = 'X';        
                if(board[i][j] == '$') board[i][j] = 'O';      
            }
    }
};
```

