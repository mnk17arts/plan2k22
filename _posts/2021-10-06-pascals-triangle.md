---
layout: post
title: Pascal's Triangle
description: 
tags:
    - array
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/pascals-triangle/)
Given an integer `numRows`, return the first numRows of **Pascal's triangle.**

In **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:  
<img src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" width="200">

### Examples
**Example 1:**
```
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

**Example 2:**
```
Input: numRows = 1
Output: [[1]]
```

### Constraints
+ `1 <= numRows <= 30`

## Solution
```cpp
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> mnk(numRows);
        int i=0,j;
        for(; i < numRows; i++){
            mnk[i].resize(i+1);
            mnk[i][0]=mnk[i][i]=1;
            j = 1;
            while(j<i){
                mnk[i][j]= mnk[i-1][j-1] + mnk[i-1][j];
                j++;
            }
        }
        return mnk;
    }
};
```
