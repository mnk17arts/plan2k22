---
layout: post
title: Steps by Knight                   
summary:
tags:
    - graph
    - bfs
    - queue
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/steps-by-knight5927/0/?track=DSASP-Graph&batchId=154#)  

Given a square chessboard, the initial position of Knight and position of a target. Find out the minimum steps a Knight will take to reach the target position.

Note:
The initial and the target position coordinates of Knight have been given according to 1-base indexing.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `minStepToReachTarget()` which takes the initial position of Knight (`KnightPos`), the target position of Knight (`TargetPos`), and the size of the chessboard (`N`) as input parameters and returns the minimum number of steps required by the knight to reach from its current position to the given target position or return `-1` if its not possible. 




**Expected Time Complexity:** `O(N^2)`           
**Expected Auxiliary Space:** `O(N^2)`


### Examples

**Example 1:**   
```
Input:
N=6
knightPos[ ] = {4, 5}
targetPos[ ] = {1, 1}
Output:
3
Explanation:
```

<img src="https://media.geeksforgeeks.org/wp-content/uploads/KnightChess.jpg">

```
Knight takes 3 step to reach from 
(4, 5) to (1, 1):
(4, 5) -> (5, 3) -> (3, 2) -> (1, 1).
```

### Constraints

+ `1 <= N <= 1000`
+ `1 <= Knight_pos(X, Y), Targer_pos(X, Y) <= N`

## Solutions

```cpp
class Solution
{
    public:
    //Function to find out minimum steps Knight needs to reach target position.
	int minStepToReachTarget(vector<int>&KnightPos,vector<int>&TargetPos,int N)
	{
	    // Code here
	    vector<vector<int>> vis(N,vector<int>(N,0));
        int d[9] = { 1,-2,-1,-2,1,2,-1,2,1 };
        queue<pair<int,int>> q;
        q.push({KnightPos[0]-1,KnightPos[1]-1});
        int res = 0;
        vis[KnightPos[0]-1][KnightPos[1]-1]=1;
        while(!q.empty()){
            int size = q.size();
            while(size--){
                int x = q.front().first;
                int y = q.front().second;
                q.pop();
                if(x==TargetPos[0]-1&&y==TargetPos[1]-1) return res;
                for(int i=0;i<8;i++){
                    int xi=x+d[i];
                    int yi=y+d[i+1];
                    if(xi<0||xi>=N||yi<0||yi>=N||vis[xi][yi]) continue;
                    q.push({xi,yi});
                    vis[xi][yi]=1;
                }
            }
            res++;
        }
        return -1;
	}
};
```

