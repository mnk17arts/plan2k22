---
layout: post
title: Shortest XY distance in Grid
summary:
tags:
  - geeksforgeeks
  - matrix
  - bfs
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/7366ce450d84b55391fc787a681c4d60de359e72/1)

Give a N\*M grid of characters 'O', 'X', and 'Y'. Find the minimum Manhattan distance between a X and a Y.

Manhattan Distance :
`| row_index_x - row_index_y | + | column_index_x - column_index_y |`

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function shortestXYDist() which takes two integers N, and M and an 2D list of size N\*M as input and returns the shortest Manhattan Distance between a X and a Y.

**Expected Time Complexity:** `O(N*M)`  
**Expected Auxiliary Space:** `O(N*M)`

### Examples

**Example 1:**

```
Input:
N = 4, M = 4
grid  = [[X, O, O, O]
         [O, Y, O, Y]
         [X, X, O, O]
         [O, Y, O, O]]
Output:
1
Explanation:
[[X, O, O, O]
[O, Y, O, Y]
[X, X, O, O]
[O, Y, O, O]]
The shortest X-Y distance in the grid is 1.
One possible such X and Y are marked in bold
in the above grid.
```

**Example 2:**

```
Input:
N = 3, M = 3
grid = [[X, X, O]
        [O, O, Y]
        [Y, O, O]]
Output :
2
Explanation:
[[X, X, O]
 [O, O, Y]
 [Y, O, O]]
The shortest X-Y distance in the grid is 2.
One possible such X and Y are marked in bold
in the above grid.
```

### Constraints

- `1 <= N, M <= 10^5`
- There is at least one X and one Y in the grid.

## Solutions

```cpp

class Solution {
  public:
    int shortestXYDist(vector<vector<char>> grid, int N, int M) {
        queue<pair<int, int>> q;
        for(int i = 0; i < N; i++) {
            for(int j = 0; j < M; j++) {
                if(grid[i][j] == 'X')
                    q.push({i, j});
            }
        }
        vector<int> dirs = {-1, 0, 1, 0, -1};
        int dis = 0;
        bool flag = 1;
        while(!q.empty() && flag) {
            int size = q.size();
            dis++;
            while(size-- && flag) {
                int x = q.front().first;
                int y = q.front().second;
                q.pop();
                for(int i = 0; i < 4; i++) {
                    int newx = x + dirs[i];
                    int newy = y + dirs[i + 1];
                    if(newx >= 0 && newy >= 0 && newx < N && newy < M) {
                        if(grid[newx][newy] == 'Y') {
                            flag = 0;
                            break;
                        }
                        else if(grid[newx][newy] == 'O') {
                            q.push({newx, newy});
                            grid[newx][newy] = 'X';
                        }
                    }
                }
            }
        }
        return dis;
    }
};

```
