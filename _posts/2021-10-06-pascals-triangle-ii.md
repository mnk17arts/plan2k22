---
layout: post
title: Pascal's Triangle II
description: 
tags:
    - array
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/pascals-triangle-ii/)
Given an integer `rowIndex`, return the `rowIndexth` (**0-indexed**) row of the **Pascal's triangle**.

In **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:  
<img src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" width="200">

### Examples
**Example 1:**
```
Input: rowIndex = 3
Output: [1,3,3,1]
```

**Example 2:**
```
Input: rowIndex = 0
Output: [1]
```

**Example 3:**
```
Input: rowIndex = 1
Output: [1,1]
```
### Constraints
+ `0 <= rowIndex <= 33`

### Follow up: 
Could you optimize your algorithm to use only O(rowIndex) extra space?

## Solution
```cpp
class Solution {
public:
    vector<int> getRow(int numRows) {
        vector<vector<int>> mnk(numRows+1);
        int i=0,j;
        for(; i < numRows+1; i++){
            mnk[i].resize(i+1);
            mnk[i][0]=mnk[i][i]=1;
            j = 1;
            while(j<i){
                mnk[i][j]= mnk[i-1][j-1] + mnk[i-1][j];
                j++;
            }
        }
        return mnk[numRows];
    }
};
```
