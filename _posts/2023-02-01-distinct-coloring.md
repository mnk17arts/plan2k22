---
layout: post
title: Distinct Coloring                     
summary:
tags:
    - geeksforgeeks
    - dynamic-programming
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/844b4fdcd988ac5461324d62d43f7892749a113c/1)  

There is a row of N houses, each house can be painted with one of the three colors: red, blue or green. The cost of painting each house with a certain color is different. You have to paint all the houses such that no two adjacent houses have the same color. Find the minimum cost to paint all houses.

The cost of painting each house in red, blue or green colour is given in the array r[], g[] and b[] respectively.

**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function distinctColoring() which takes the size N and the color arrays r[], g[], b[] as input parameters and returns the minimum cost of coloring such that the color of no two houses is same.



**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)` 



### Examples

**Example 1:**   
```
Input:
N = 3
r[] = {1, 1, 1}
g[] = {2, 2, 2}
b[] = {3, 3, 3}
Output: 4
Explanation: We can color the houses 
in RGR manner to incur minimum cost.
We could have obtained a cost of 3 if 
we coloured all houses red, but we 
cannot color adjacent houses with 
the same color.
```

**Example 2:**   
```
Input:
N = 3
r[] = {2, 1, 3}
g[] = {3, 2, 1}
b[] = {1, 3, 2} 
Output: 3
Explanation: We can color the houses
in BRG manner to incur minimum cost.
```

### Constraints

+ `1 <= N <= 5*10^4`
+ `1 <= r[i], g[i], b[i] <= 10^6`

## Solutions

```cpp

class Solution{   
public:
    long long int distinctColoring(int N, int r[], int g[], int b[]){
        // code here 
        long long int temp[3];
        temp[0] = r[0], temp[1] = g[0], temp[2] = b[0];
        for( int i=1; i<N; i++ ) {
            long long int tr = r[i] + min(temp[1], temp[2]);
            long long int tg = g[i] + min(temp[0], temp[2]);
            long long int tb = b[i] + min(temp[0], temp[1]);
            
            temp[0] = tr;
            temp[1] = tg;
            temp[2] = tb;
        }
        return min(temp[0], min(temp[1], temp[2]));
    }
};

```

