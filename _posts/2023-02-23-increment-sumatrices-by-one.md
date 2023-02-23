---
layout: post
title: Increment Submatrices by One
summary:
tags:
  - leetcode
  - array
  - matrix
  - prefix-sum
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/increment-submatrices-by-one/description/)

You are given a positive integer n, indicating that we initially have an n x n 0-indexed integer matrix mat filled with zeroes.

You are also given a 2D integer array query. For each query[i] = [row1i, col1i, row2i, col2i], you should do the following operation:

+ Add 1 to every element in the submatrix with the top left corner (row1i, col1i) and the bottom right corner (row2i, col2i). That is, add 1 to mat[x][y] for all row1i <= x <= row2i and col1i <= y <= col2i.

Return the matrix mat after performing every query.

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2022/11/24/p2example11.png">
```
Input: n = 3, queries = [[1,1,2,2],[0,0,1,1]]
Output: [[1,1,0],[1,2,1],[0,1,1]]
Explanation: The diagram above shows the initial matrix, the matrix after the first query, and the matrix after the second query.
- In the first query, we add 1 to every element in the submatrix with the top left corner (1, 1) and bottom right corner (2, 2).
- In the second query, we add 1 to every element in the submatrix with the top left corner (0, 0) and bottom right corner (1, 1).
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2022/11/24/p2example22.png">
```
Input: n = 2, queries = [[0,0,1,1]]
Output: [[1,1],[1,1]]
Explanation: The diagram above shows the initial matrix and the matrix after the first query.
- In the first query we add 1 to every element in the matrix.
```

### Constraints

- `1 <= n <= 500`
- `1 <= query.length <= 10000`
- `0 <= row1i <= row2i < n`
- `0 <= col1i <= col2i < n`

## Solutions

```cpp

class Solution {
public:
    vector<vector<int>> rangeAddQueries(int n, vector<vector<int>>& queries) {
        vector<vector<int>> arr(n, vector<int> (n, 0));
        int r1, r2, c1, c2;
        for(auto &it: queries) {
            r1 = it[0], r2 = it[2], c1 = it[1], c2 = it[3];
            for(int i = r1; i <= r2; i++) {
                arr[i][c1] += 1;
                if((c2 + 1) >= n) {
                    if(i + 1 < n) {
                        arr[i + 1][0] -= 1; 
                    }
                    else {
                        continue;
                    }
                }
                else {
                    arr[i][c2 + 1] -= 1;
                }
            }
        }
        int count = 0;
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < n; j++) {
                count += arr[i][j];
                arr[i][j] = count;
            }
        }
        return arr;
    }
};

```
