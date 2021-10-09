---
layout: post
title: Flood Fill
description: 
summary: 
tags:
    - DFS
    - array
    - matrix
    - BFS
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/flood-fill/)
An image is represented by an `m x n` integer grid `image` where `image[i][j]` represents the pixel value of the image.

You are also given three integers `sr`, `sc`, and `newColor`. You should perform a **flood fill** on the image starting from the pixel `image[sr][sc]`.

To perform a **flood fill**, consider the starting pixel, plus any pixels connected **4-directionally** to the starting pixel of the same color as the starting pixel, plus any pixels connected **4-directionally** to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with `newColor`.

Return *the modified image after performing the flood fill.*



### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/06/01/flood1-grid.jpg" height="250">
```
Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, newColor = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
Explanation: From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.
```

**Example 2:**  
```
Input: image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, newColor = 2
Output: [[2,2,2],[2,2,2]]
```

### Constraints
+ `m == image.length`
+ `n == image[i].length`
+ `1 <= m, n <= 50`
+ `0 <= image[i][j], newColor < 2^16`
+ `0 <= sr < m`
+ `0 <= sc < n`

## Solutions
```cpp
class Solution {
public:

    void letsfill(vector<vector<int>>& image, int sr, int sc,int row,int col,int oldClr,int newClr){
    
        if(sr<0 || sc<0 || sr>=row || sc>=col || image[sr][sc] != oldClr) return;
        
        image[sr][sc] = newClr;
        letsfill(image,sr+1,sc,row,col,oldClr,newClr);
        letsfill(image,sr,sc-1,row,col,oldClr,newClr);
        letsfill(image,sr-1,sc,row,col,oldClr,newClr);
        letsfill(image,sr,sc+1,row,col,oldClr,newClr);
    }
    
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor) {
    
        if( newColor != image[sr][sc])
            letsfill(image,sr,sc,image.size(),image[0].size(),image[sr][sc],newColor);
            
        return image;
    }
};
```
