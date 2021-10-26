---
layout: post
title:  Combination Sum II
description: 
summary: 
tags:
    - array
    - backtracking
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/combination-sum-ii/)
Given a collection of candidate numbers (`candidates`) and a target number (`target`), find all unique combinations in `candidates` where the candidate numbers sum to `target`.

Each number in `candidates` may only be used **once** in the combination.

**Note**: The solution set must not contain duplicate combinations.
 
### Examples   
**Example 1:**  
```
Input: candidates = [10,1,2,7,6,1,5], target = 8
Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
```

**Example 2:**  
```
Input: candidates = [2,5,2,1,2], target = 5
Output: 
[
[1,2,2],
[5]
]
```

### Constraints
+ `1 <= candidates.length <= 100`
+ `1 <= candidates[i] <= 50`
+ `1 <= target <= 30`

## Solutions

```cpp
class Solution {
public:
    vector<vector<int>> res;
    vector<int> sub;
    void bc(vector<int>& c, int t, int i){
        if(t == 0) {
            res.push_back(sub);
            return;
        }
        for(int j=i; j<c.size(); j++){
            if(j>i and c[j]==c[j-1]) continue;
            if(t-c[j]<0) break;
            sub.push_back(c[j]);
            bc(c,t-c[j],j+1);
            sub.pop_back();
        }
    }
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        sort(candidates.begin(), candidates.end());
        bc(candidates, target, 0);
        return res;
    }
};
```

