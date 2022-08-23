---
layout: post
title: Maximum Number of Points with Cost                       
summary:
tags:
    - leetcode
    - array
    - dynamic-programming
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/maximum-number-of-points-with-cost/)  

You are given an `m x n` integer matrix points (0-indexed). Starting with 0 points, you want to maximize the number of points you can get from the matrix.

To gain points, you must pick one cell in each row. Picking the cell at coordinates (r, c) will add points[r][c] to your score.

However, you will lose points if you pick a cell too far from the cell that you picked in the previous row. For every two adjacent rows r and r + 1 (where 0 <= r < m - 1), picking cells at coordinates (r, c1) and (r + 1, c2) will subtract abs(c1 - c2) from your score.

Return the maximum number of points you can achieve.

abs(x) is defined as:

+ x for x >= 0.
+ -x for x < 0.


### Examples

<img src="https://assets.leetcode.com/uploads/2021/07/12/screenshot-2021-07-12-at-13-40-26-diagram-drawio-diagrams-net.png">

**Example 1:**   
```
Input: points = [[1,2,3],[1,5,1],[3,1,1]]
Output: 9
Explanation:
The blue cells denote the optimal cells to pick, which have coordinates (0, 2), (1, 1), and (2, 0).
You add 3 + 5 + 3 = 11 to your score.
However, you must subtract abs(2 - 1) + abs(1 - 0) = 2 from your score.
Your final score is 11 - 2 = 9.
```

<img src="https://assets.leetcode.com/uploads/2021/07/12/screenshot-2021-07-12-at-13-42-14-diagram-drawio-diagrams-net.png">

**Example 2:**   
```
Input: points = [[1,5],[2,3],[4,2]]
Output: 11
Explanation:
The blue cells denote the optimal cells to pick, which have coordinates (0, 1), (1, 1), and (2, 0).
You add 5 + 3 + 4 = 12 to your score.
However, you must subtract abs(1 - 1) + abs(1 - 0) = 1 from your score.
Your final score is 12 - 1 = 11.
```


### Constraints

+ `m == points.length`
+ `n == points[r].length`
+ `1<= m,n <=10^5`
+ `0<= points[r][c] <=10^5`
+ `1<= m*n <=10^5`

## Solutions

```cpp
class Solution {
public:
    long long maxPoints(vector<vector<int>>& p) {
        int n = (int)p.size() , m = (int)p[0].size();
        vector<vector<int64_t>>points; 
        for(auto temp : p){
            vector<int64_t>lost;
            for(auto r : temp){
                int64_t x = (int64_t)r;
                lost.push_back(x);
            }
            points.push_back(lost);
        }
       
        int64_t ans = (int64_t)-1;
        for(int i = 1 ; i<n; i++){
            vector<int64_t>left(m,(int64_t)0),right(m,(int64_t)0);
            int64_t mx = 0ll;
            for(int j = 0 ; j<m; j++){
                left[j] = max(mx-(int64_t)1,(int64_t)points[i-1][j]);
                mx = left[j];
            }
            mx = 0;
            for(int j = m-1 ; j>=0; j--){
                right[j] = max(mx-(int64_t)1,(int64_t)points[i-1][j]);
                mx = right[j];
            }
            for(int j = 0 ; j<m; j++){
                points[i][j] = max(left[j],right[j]) + (int64_t)points[i][j];
            }
        }
        for(int i = 0 ; i<m; i++){
            ans = max((int64_t)points[n-1][i],ans);
        }  
        return ans;
    }
};
```

