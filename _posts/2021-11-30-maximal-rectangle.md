---
layout: post
title: Maximal Rectangle
summary:
tags:
    - array
    - matrix
    - dynamic-programming
    - stack
    - leetcode
    - cpp
    - hard
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/maximal-rectangle)  

Given a `rows x cols` binary `matrix` filled with `0`'s and `1`'s, find the largest rectangle containing only `1`'s and return *its area.*

### Examples

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2020/09/14/maximal.jpg">
```
Input: matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
Output: 6
Explanation: The maximal rectangle is shown in the above picture.
```

**Example 2:**    
```
Input: matrix = []
Output: 0
```

**Example 3:**    
```
Input: matrix = [["0"]]
Output: 0
```

**Example 4:**    
```
Input: matrix = [["1"]]
Output: 1
```

**Example 5:**    
```
Input: matrix = [["0","0"]]
Output: 0
```

### Constraints
+ `rows == matrix.length`
+ `cols == matrix[i].length`
+ `0 <= row, cols <= 200`
+ `matrix[i][j] is '0' or '1'.`

## Solutions

```cpp
class Solution {
public:
  int rec(vector<int>& c){
    int res = 0;
    int n = c.size();
    stack<int> s;
    s.push(-1);
    int l=0,r=0;
    for(int i=0; i<n+1; i++){
      int v = (i==n ? 0 : c[i] ) ;
      while(s.top()!=-1 and c[s.top()]>=v){
        r = i;
        int h = c[s.top()];
        s.pop();
        l = s.top();
        res = max(res, h*(r-l-1));
      }
      s.push(i);
    }
    return res;
  }
    int maximalRectangle(vector<vector<char>>& matrix) {
      int res = 0;
      int r = matrix.size();
      if(r == 0) return 0;
      int c = matrix[0].size();
      vector<int> tc(c);
      for(int i=0; i<c; i++){
        tc[i] = matrix[0][i]-'0';
      }
      res = max(res, rec(tc));
      for(int i=1; i<r; i++){
        for(int j=0; j<c; j++){
          if(matrix[i][j]=='1') tc[j]++;
          else tc[j] = 0;
        }
        res = max(res, rec(tc));
      }
      return res;
    }
};
```

