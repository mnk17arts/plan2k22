---
layout: post
title: Permutation Sequence
summary:
tags:
    - leetcode
    - cpp
    - hard
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/permutation-sequence)  

The set `[1, 2, 3, ..., n]` contains a total of `n!` unique permutations.

By listing and labeling all of the permutations in order, we get the following sequence for `n = 3`:

1. `"123"`
2. `"132"`
2. `"213"`
2. `"231"`
2. `"312"`
2. `"321"`

Given `n` and `k`, return the `kth` permutation sequence.

### Examples

**Example 1:**   
```
Input: n = 3, k = 3
Output: "213"
```

**Example 2:**    
```
Input: n = 4, k = 9
Output: "2314"
```

**Example 3:**    
```
Input: n = 3, k = 1
Output: "123"
```

### Constraints
+ `1 <= n <= 9`
+ `1 <= k <= n!`

## Solutions

```cpp
class Solution {
public:
    string getPermutation(int n, int k) {
      int f[n+1];
      vector<int> a(n);
      f[0] = 1;
      int fc = 1;
      for( int i=1; i<=n; i++) {
        fc*=i;
        f[i] = fc;
        a[i-1] = i;
      } 
      k--;
      string res  = "";
      for(int i=1; i<n+1; i++){
        int id = k/f[n-i];
        res += to_string(a[id]);
        a.erase(a.begin()+id);
        k-=id*f[n-i];
      }
      return res;
    }
};
```

