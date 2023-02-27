---
layout: post
title: Count Artifacts That Can Be Extracted
summary:
tags:
  - leetcode
  - array
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/count-artifacts-that-can-be-extracted/description/)

There is an n x n 0-indexed grid with some artifacts buried in it. You are given the integer n and a 0-indexed 2D integer array artifacts describing the positions of the rectangular artifacts where artifacts[i] = [r1i, c1i, r2i, c2i] denotes that the ith artifact is buried in the subgrid where:

+ (r1i, c1i) is the coordinate of the top-left cell of the ith artifact and
+ (r2i, c2i) is the coordinate of the bottom-right cell of the ith artifact.

You will excavate some cells of the grid and remove all the mud from them. If the cell has a part of an artifact buried underneath, it will be uncovered. If all the parts of an artifact are uncovered, you can extract it.

Given a 0-indexed 2D integer array dig where dig[i] = [ri, ci] indicates that you will excavate the cell (ri, ci), return the number of artifacts that you can extract.

The test cases are generated such that:

+ No two artifacts overlap.
+ Each artifact only covers at most 4 cells.
+ The entries of dig are unique.


### Examples

**Example 1:**  

<img src="https://assets.leetcode.com/uploads/2019/09/16/untitled-diagram.jpg">

```
Input: n = 2, artifacts = [[0,0,0,0],[0,1,1,1]], dig = [[0,0],[0,1]]
Output: 1
Explanation: 
The different colors represent different artifacts. Excavated cells are labeled with a 'D' in the grid.
There is 1 artifact that can be extracted, namely the red artifact.
The blue artifact has one part in cell (1,1) which remains uncovered, so we cannot extract it.
Thus, we return 1. 
```

**Example 2:**  

<img src="https://assets.leetcode.com/uploads/2019/09/16/untitled-diagram-1.jpg">

```
Input: n = 2, artifacts = [[0,0,0,0],[0,1,1,1]], dig = [[0,0],[0,1],[1,1]]
Output: 2
Explanation: Both the red and blue artifacts have all parts uncovered (labeled with a 'D') and can be extracted, so we return 2. 
```


### Constraints

- `1 <= n <= 1000`
- `1 <= artifacts.length, dig.length <= min(n^2, 10^5)`
- `artifacts[i].length == 4`
- `dig[i].length == 2`
- `0 <= r1i <= r2i < n`
- `0 <= c1i <= c2i < n`
- `0 <= ri < n`
- `0 <= ci < n`
- `All the elements of artifacts are unique.`
- `All the elements of dig are unique.`
- `The elements of dig are distinct from the elements of artifacts.`
- `The elements of dig are in the range [0, n - 1].`


## Solutions

```cpp

class Solution {
    bool isValid(int r1, int c1, int r2, int c2, vector<vector<bool>>& yard, int n) {
        for(int i = r1; i <= r2; i++) {
            for(int j = c1; j <= c2; j++) {
                if(yard[i][j] == false) {
                    return false;
                }
            }
        }
        return true;
    }
public:
    int digArtifacts(int n, vector<vector<int>>& artifacts, vector<vector<int>>& dig) {
        vector<vector<bool>> yard(n, vector<bool>(n, false));
        for(auto &d: dig) {
            yard[d[0]][d[1]] = true;
        }
        int res = 0;
        for(auto &a: artifacts) {
            if(isValid(a[0], a[1], a[2], a[3], yard, n)) {
                res++;
            }
        }
        return res;
    }
};

```
