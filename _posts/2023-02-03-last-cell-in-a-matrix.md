---
layout: post
title: Last cell in a Matrix                     
summary:
tags:
    - geeksforgeeks
    - matrix
    - cpp
    - easy
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/2e068e2342b9c9f40cfda1ed8e8119542d748fd8/1) 

Given a binary matrix of dimensions  with R rows and C columns. Start from cell(0, 0), moving in the right direction. Perform the following operations: 

+ If the value of matrix[i][j] is 0, then traverse in the same direction and check the next value.
+ If the value of matrix[i][j] is 1, then update matrix[i][j] to 0 and change the current direction clockwise. ie - up, right, down, or left directions change to right, down, left, and up respectively.

Find the index of the cell where you will be forced to exit the matrix while performing the given traversal. 

**Your Task:** 

You don't need to read input or print anything. Complete the function endPoints() which take a 2D matrix[][] , an integer R and an integer C as input parameters and returns the index of the last cell before exiting the matrix. 



**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(1)` 



### Examples

**Example 1:**   
```
Input:
matrix[][] = [[0,1],
              [1,0]]
R=2
C=2

Output: (1,1)
Explanation:
```
<img src="https://media.geeksforgeeks.org/img-practice/endpoint1-1622886995.jpg">
<img src="https://media.geeksforgeeks.org/img-practice/endpoint2-1622887085.jpg">
<img src="https://media.geeksforgeeks.org/img-practice/endpoint3-1622887174.jpg">

**Example 2:**   
```
Input: 
matrix[][] = [[0, 1, 1, 1, 0], [1, 0, 1, 0, 1],[1, 1, 1, 0, 0]]
R=3
C=5

Output: (2,0)
Explanation: We will leave the grid after visiting the index (2,0).
```

### Constraints

+ `1<= R,C<=1000`
+ `0<= matrix[i][j] <=1`

## Solutions

```cpp

class Solution{
    public:
    pair<int,int> endPoints(vector<vector<int>> matrix, int R, int C){
        //code here
        pair<int ,int> dir[] = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
        int cdir = 0;
        int r = 0 , c = 0;
        while(true) {
            if(matrix[r][c] == 1) {
                cdir++;
                matrix[r][c] = 0;
            }
            cdir %= 4;
            int nextR = r + dir[cdir].first;
            int nextC = c + dir[cdir].second;
            if(nextR < 0 || nextC < 0 || nextR >= R || nextC >= C) break;
            r = nextR;
            c = nextC;
        }
        return {r, c};
    }
};

```
