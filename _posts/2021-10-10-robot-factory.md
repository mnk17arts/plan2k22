---
layout: post
title: Robot Factory
description: 
summary: 
tags:
    - bitmasks
    - DFS
    - codeforces
    - cpp
    - medium
minute: 9 min
---

## Problem Statement - [*link*](https://codeforces.com/problemset/problem/1600/J)
You have received data from a Bubble bot. You know your task is to make factory facilities, but before you even start, you need to know how big the factory is and how many rooms it has. When you look at the data you see that you have the dimensions of the construction, which is in rectangle shape: `N x M`.

Then in the next `N` lines you have `M` numbers. These numbers represent factory tiles and they can go from `0` to `15`. Each of these numbers should be looked in its binary form. Because from each number you know on which side the tile has walls. For example number `10` in it's binary form is `1010`, which means that it has a wall from the **North** side, it doesn't have a wall from the **East**, it has a wall on the **South** side and it doesn't have a wall on the **West** side. So it goes North, East, South, West.

It is guaranteed that the construction always has walls on it's edges. The input will be correct.

Your task is to print the size of the rooms from biggest to smallest.

### Input 
The first line has two numbers which are `N` and `M`, the size of the construction.  
Next `N x M` numbers represent each tile of construction.

### Output  
Once you finish processing the data your output consists of one line sorted from biggest to smallest room sizes.

### Examples
**Example 1:**  
<img src="https://user-images.githubusercontent.com/71878747/136700498-7218158e-373e-43c5-a32c-b8e5e8adee6c.JPG" height="300">
```
Input: 
4 5
9 14 11 12 13
5 15 11 6 7
5 9 14 9 14
3 2 14 3 14
Output: 
9 4 4 2 1 
```

### Constraints
+ `1 <= n <= 1000`
+ `1 <= m <= 1000`

## Solution
```cpp
#include<bits/stdc++.h>

using namespace std;

int n,m,i,j,c;
vector<vector<int>> nxm(1001,vector<int>(1001));
vector<vector<bool>> yess(1001,vector<bool>(1001,false));
int X[4] = {0, 1, 0, -1};
int Y[4] = {-1, 0, 1, 0};

void bt(int x,int y){
    if(x<0 || x>=n || y<0 || y>=m || yess[x][y]) return;
    yess[x][y] = true;
    c++;
    for(int k=0; k < 4; k++)
        if((nxm[x][y]&1<<k) == 0)
            bt(x+X[k], y+Y[k]);
}

void solution(){
    cin>>n>>m ;
    for(i=0; i<n; i++){
        for(j=0; j<m; j++){
            cin>>nxm[i][j];            
        }
    }
    vector<int> rooms;
    for(i=0;i<n;i++)
        for(j=0;j<m;j++)
            if(!yess[i][j]){
                c=0;
                bt(i,j);
                rooms.push_back(c);
            }
    sort(rooms.begin(),rooms.end());
    for(i=rooms.size()-1;i>=0;i--)
        cout<<rooms[i]<<" ";
    cout<<endl;
}

int main(){
    ios_base::sync_with_stdio(0), cin.tie(0);
    int t = 1;
    while(t--) solution();
    return 0;
}
```
