---
layout: post
title: Avoid Fire
summary:
tags:
  - geeksforgeeks
  - array
  - bfs
  - queue
  - cpp
  - hard
minute: 15+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-92/problems#)

You are given a 2D array arr with n rows and m columns. If arr[i][j] is 0, that means the block is empty, and if arr[i][j] is 1, then the block is burning in fire. Initially, you are at point (x,y). In one second you can go left, right, up, or down and the fire also spreads accordingly. Your task is to determine if it is possible to reach the point (n-1,m-1) safely.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function avoidFire() which takes 4 integers and a 2D array arr as input parameters and returns the if it is possible to reach safely.

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**

```
Input:
n = 4
m = 4
x = 2
y = 2
arr = [[0,0,0,1],[0,0,0,0],[0,0,0,0],[1,0,0,0]]
Output:
1
Explanation:
You can follow the path (2,2) -> (2,3) -> (3,3)
```

**Example 2:**

```
Input:
n = 3
m = 3
x = 0
y = 0
arr = [[0,0,1],[1,0,0],[1,0,1]]
Output:
0
Explanation:
You can't reach safely at (1,2).
```

### Constraints

- `1 <= n,m <= 500`
- `0 <= x < n`
- `0 <= y < m`
- `arr[i][j]` can be either 0 or 1

## Solutions

```cpp

class Solution{
  public:
    bool avoidFire(int n, int m, int x, int y, vector<vector<int>> &arr) {
        // code here
        if(x == n - 1 && y == m -1) {
            return true;
        }
        if(arr[x][y] == 1) {
            return false;
        }
        int res = false;
        queue<pair<int, int>> q;
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < m; j++) {
                if(arr[i][j] == 1) {
                    q.push({i, j});
                }
            }
        }
        int secs = 1;
        while(q.size()) {
            int qs = q.size();
            while(qs--) {
                auto xy = q.front();
                q.pop();
                int xi = xy.first;
                int yi = xy.second;
                if(xi - 1 >= 0 && arr[xi - 1][yi] == 0) {
                    q.push({xi - 1, yi});
                    arr[xi - 1][yi] = arr[xi][yi] + 1;
                }
                if(xi + 1 < n && arr[xi + 1][yi] == 0) {
                    q.push({xi + 1, yi});
                    arr[xi + 1][yi] = arr[xi][yi] + 1; 
                }
                if(yi - 1 >= 0 && arr[xi][yi - 1] == 0) {
                    q.push({xi, yi - 1});
                    arr[xi][yi - 1] = arr[xi][yi] + 1;
                }
                if(yi + 1 < m && arr[xi][yi + 1] == 0) {
                    q.push({xi, yi + 1});
                    arr[xi][yi + 1] = arr[xi][yi] + 1;
                }
            }
        }
        q.push({x, y});
        while(q.size()) {
            int qs = q.size();
            while(qs--) {
                auto xy = q.front(); q.pop();
                int xi = xy.first, yi = xy.second;
                if(xi == n - 1 && yi == m - 1) {
                    return true;
                }
                if(xi - 1 >= 0 && arr[xi - 1][yi] > secs + 1) {
                    q.push({xi - 1, yi});
                }
                if(xi + 1 < n && arr[xi + 1][yi] > secs + 1) {
                    q.push({xi + 1, yi});
                }
                if(yi - 1 >= 0 && arr[xi][yi - 1] > secs + 1) {
                    q.push({xi, yi - 1});
                }
                if(yi + 1 < m && arr[xi][yi + 1] > secs + 1) {
                    q.push({xi, yi + 1});
                }
            }
            secs++;
        }
        return false;
    }
};
};

```
