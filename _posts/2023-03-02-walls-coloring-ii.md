---
layout: post
title: Walls Coloring II
summary:
tags:
  - geeksforgeeks
  - array
  - dynamic-programming
  - cpp
  - hard
minute: 15+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/9dacc32ad062be6e2ba8f6c41aad0b2b2376397d/1)

There is a row of N walls in Geeksland. The king of Geeksland ordered Alexa to color all the walls on the occasion of New Year. Alexa can color each wall with one of the K colors. The cost associated with coloring each wall with a particular color is represented by a 2D costs array of size N \* K. For example, costs[0][0] is the cost of coloring wall 0 with color 0; costs[1][2] is the cost of coloring wall 1 with color 2, and so on... Find the minimum cost to color all the walls such that no two adjacent walls have the same color.

Note: If you are not able to paint all the walls, then you should return -1.

**Your Task:**

Your task is to complete the function minCost() which takes a 2D integer matrix costs as the only argument and returns an integer, representing the minimum cost to paint all the walls. If you are not able to paint all the walls, then you should return -1

**Expected Time Complexity:** `O(N*K)`  
**Expected Auxiliary Space:** `O(N*K)`

### Examples

**Example 1:**

```
Input:
N = 4, K = 3
costs[][] = [[1, 5, 7],
             [5, 8, 4],
             [3, 2, 9],
             [1, 2, 4]]

Output:
8
Explanation:
Paint wall 0 with color 0. Cost = 1
Paint wall 1 with color 2. Cost = 4
Paint wall 2 with color 1. Cost = 2
Paint wall 3 with color 0. Cost = 1
Total Cost = 1 + 4 + 2 + 1 = 8
```

**Example 2:**

```
Input:
N = 5, K = 1
costs[][] = [[5],
             [4],
             [9],
             [2],
             [1]]
Output:
-1
Explanation:
It is not possible to color all the walls under the given conditions.
```

### Constraints

- `0 <= N <= 1000`
- `0 <= K <= 1000`
- `1 <= costs[i][j] <= 100000`

## Solutions

```cpp

class Solution{
    public:
    int minCost(vector<vector<int>> &costs) {
        // write your code here
        int MAX = 1e9;
        int n = costs.size(), k = costs[0].size();
        int prevMinCost = 0, prevMinCost2 = 0, prevClr = -1;
        for(int i = 0; i < n; i++) {
            int curMinCost = MAX, curMinCost2 = MAX, curClr = -1;
            for(int j = 0; j < k; j++) {
                int curCost = costs[i][j];
                if(i == 0) {
                    if(curCost != 0 && curCost < curMinCost) {
                        curMinCost2 = curMinCost;
                        curMinCost = curCost;
                        curClr = j;
                    }
                    else if(curCost != 0 && curCost < curMinCost2) {
                        curMinCost2 = curCost;
                    }
                }
                else {
                    if(j != prevClr) {
                        curCost += prevMinCost;
                    }
                    else {
                        curCost += prevMinCost2;
                    }
                    if(curCost != 0 && curCost < curMinCost) {
                        curMinCost2 = curMinCost;
                        curMinCost = curCost;
                        curClr = j;
                    }
                    else if(curCost !=0 && curCost < curMinCost2) {
                        curMinCost2 = curCost;
                    }
                }
            }
            prevMinCost = curMinCost;
            prevMinCost2 = curMinCost2;
            prevClr = curClr;
        }
        if(prevMinCost == MAX) {
            return -1;
        }
        return prevMinCost;
    }
};

```
