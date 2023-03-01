---
layout: post
title: Update Queries
summary:
tags:
  - geeksforgeeks
  - array
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/a6528c893d4ab645ec6e0690c7982748385099c8/1)

You are given an array of n elements, initially all a[i] = 0. Q queries need to be performed. Each query contains three integers l, r, and x and you need to change all a[i] to (a[i] | x) for all l ≤ i ≤ r.

Return the array after executing Q queries.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function updateQuery() which takes the integer N,Q, and U a QX3 matrix containing the Q queries where U[i][0] is li, U[i][1] is ri andU[i][2] is xi.and it returns the final array a.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**

```
Input:
N=3, Q=2
U=[[1, 3, 1],
   [1, 3, 2]]

Output:
a[]={3,3,3}

Explanation:
Initially, all elements of the array are 0. After execution of the
first query, all elements become 1 and after execution of the
second query all elements become 3.
```

**Example 2:**

```
Input:
N=3, Q=2
U=[[1, 2, 1],
   [3, 3, 2]]

Output:
a[]={1,1,2}

Explanantion:
[0,0,0] => [1,1,0] => [1,1,2]
```

### Constraints

- `1 <= N <= 10^5`
- `1 <= Q <= 10^5`
- `1 <= l <= r <= N`
- `0 <= x <= 10^9`

## Solutions

```cpp

class Solution{
    public:
        vector<int> updateQuery(int n,int q,vector<vector<int>> &u)
        {
            // code here
            vector<int> res(n, 0);
            vector<vector<int>> pre(n, vector<int> (31, 0));
            for(int i = 0; i < q; i++) {
                int left = u[i][0] - 1;
                int right = u[i][1];
                int ele = u[i][2];
                for(int j = 0; j < 31; j++) {
                    if((1 << j) & ele) {
                        pre[left][j]++;
                        if(right < n) {
                            pre[right][j]--;
                        }
                    }
                }
            }
            for(int i = 0; i < n; i++) {
                for(int j = 0; j < 31; j++) {
                    pre[i][j] += pre[i-1][j];
                }
            }
            for(int i = 0; i < n; i++) {
                int cur_ele = 0;
                for(int j = 0; j < 31; j++) {
                    if(pre[i][j]) {
                        cur_ele |= (1 << j);
                    }
                }
                res[i] = cur_ele;
            }
            return res;
    }
};

```
