---
layout: post
title: Frogs and Jumps
summary:
tags:
  - geeksforgeeks
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/5551749efa02ae36b6fdb3034a7810e84bd4c1a4/1)

N frogs are positioned at one end of the pond. All frogs want to reach the other end of the pond as soon as possible. The pond has some leaves arranged in a straight line. Each frog has the strength to jump exactly K leaves. For example, a frog having strength 2 will visit the leaves 2, 4, 6, ... etc. while crossing the pond.

Given the strength of each frog and the number of leaves, your task is to find the number of leaves that not be visited by any of the frogs when all frogs have reached the other end of the pond.

**Your Task:**

Complete the function unvisitedLeaves() which takes the integers N, leaves and the array frogs as the input parameters, and returns the number of unvisited leaves.

**Expected Time Complexity:** `O(N*log(leaves))`  
**Expected Auxiliary Space:** `O(leaves)`

### Examples

**Example 1:**

```
Input:
N = 3
leaves = 4
frogs[] = {3, 2, 4}
Output: 1
Explanation:
Leaf 1 will not be visited by any frog.
```

**Example 2:**

```
Input:
N = 3
leaves = 6
frogs[] = {1, 3, 5}
Output: 0
Explanation:
First frog will visit all the leaves so no
leaf is left unvisited.
```

### Constraints

- `1 ≤ N, leaves, frogs[i] ≤ 10^5`

## Solutions

```cpp

class Solution {
  public:
    int unvisitedLeaves(int N, int leaves, int frogs[]) {
        // Code here
        vector<bool> arr(leaves + 1, 0);
        for(int i = 0; i < N; i++) {
            if(arr[frogs[i]] == 0){
                for(int j = frogs[i]; j < arr.size(); j += frogs[i]) {
                    arr[j] = 1;
                }
            }
        }
        int count = 0;
        for(int i = 1; i < arr.size(); i++) {
            if(arr[i] == 0) {
                count++;
            }
        }
        return count;

    }
};

```
