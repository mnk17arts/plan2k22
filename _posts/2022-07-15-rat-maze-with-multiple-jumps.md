---
layout: post
title: Rat Maze With Multiple Jumps                    
summary:
tags:
    - backtracking
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/rat-maze-with-multiple-jumps-1587115621/0/?track=DSASP-Backtracking&batchId=154#)  

A Maze is given as `N*N` matrix of blocks where source block is the upper left most block i.e., `maze[0][0]` and destination block is lower rightmost block i.e., `maze[N-1][N-1]`. Find if it is possible for the rat to reach from the source block to the destination block. The number of steps rat can jump from `(i, j)` is represented by `maze[i][j]`.

Note:
If multiple solutions exist, the shortest earliest hop will be accepted. For the same hop distance at any point, forward will be preferred over downward.
In the maze matrix, `0` means the block is the dead end and non-zero number means the block can be used in the path from source to destination. The non-zero value of `mat[i][j]` indicates number of maximum jumps rat can make from cell `mat[i][j]`.

 

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `solve()` which takes the Maze and its dimensions `N` as inputs and prints the valid path if it exists. If it does not exist, print `-1`
Note: In the valid path, for each block, if you are visiting the block then you should print `1` for it else `0`. 


**Expected Time Complexity:** `O(N^N)`             
**Expected Auxiliary Space:** `O(N)`  if we don't consider the solution matrix for this.



### Examples

**Example 1:**   
```
Input:
N = 4
maze[][] = {{2,1,0,0},{3,0,0,1},
{0,1,0,1},{0,0,0,1}}
Output:
1 0 0 0
1 0 0 1
0 0 0 1
0 0 0 1
Explanation: Rat started with m[0][0] and
can jump up to 2 steps right/down. First
check m[0][1] as it is 1, next check
m[0][2], this won't lead to the solution.
Then check m[1][0], as this is 3(non-zero)
so we can make 3 jumps to reach m[1][3].
From m[1][3] we can move downwards taking
1 jump each time to reach destination at
m[3][3]. 
```

**Example 2:**   
```
Input:
N = 4
maze[][] = {{2,1,0,0}{2,0,0,1},
{0,1,0,1},{0,0,0,1}}
Output: -1
Explanation: As no path exists, so -1.
```

### Constraints

+ `2 <= n <= 50`
+ `0 <= maze[i][j] <= 20`


## Solutions

```cpp
vector<vector<int>> sol;

void printSol(){
    for(auto i: sol){
        for(auto j: i)
            cout << j << " ";  
        cout<<endl;
    }
}

bool isSafe(int r,int c,vector<int> maze[],int n){
    return (r<n&&c<n&&maze[r][c]);
}

bool solveRec(int r,int c,vector<int> maze[],int n){
    if(r==n-1&&c==n-1) { sol[r][c]=1; return true; }
    if(isSafe(r,c,maze,n)){
        sol[r][c]=1;
        for(int i=0;i<maze[r][c];i++)
            if(solveRec(r,c+1+i,maze,n)||solveRec(r+1+i,c,maze,n))
                return true;
        sol[r][c]=0;
    }
    return false;
}


//Function to find the minimum number of Hops required for the rat to 
//reach from the source block to the destination block. 
void solve(int N, vector<int> maze[]) 
{
    // write code here
    sol = vector<vector<int>>(N,vector<int>(N,0));
    if(solveRec(0,0,maze,N))
        printSol();
    else cout<<-1<<endl;
}
```

