---
layout: post
title: Minimum Swaps to Sort                   
summary:
tags:
    - graph
    - sorting
    - array
    - dfs
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/minimum-swaps/0/?track=DSASP-Graph&batchId=154)  

Given an array of `n` distinct elements. Find the minimum number of swaps required to sort the array in strictly increasing order. 

**Your Task:** 
You do not need to read input or print anything. Your task is to complete the function `minSwaps()` which takes the nums as input parameter and returns an integer denoting the minimum number of swaps required to sort the array. If the array is already sorted, return `0`. 




**Expected Time Complexity:** `O(nlogn)`           
**Expected Auxiliary Space:** `O(n)`


### Examples

**Example 1:**   
```
Input:
nums = {2, 8, 5, 4}
Output:
1
Explaination:
swap 8 with 4.
```

**Example 2:**   
```
Input:
nums = {10, 19, 6, 3, 5}
Output:
2
Explaination:
swap 10 with 3 and swap 19 with 5.
```

### Constraints

+ `1 ≤ n ≤ 10^5`
+ `1 ≤ nums[i] ≤ 10^6`

## Solutions

```cpp
class Solution
{
    public:
    void dfs(vector<int>&nums,bool vis[],int &cur,int i,vector<pair<int,int>>&v){
        vis[i]=1;
        cur++;
        if(vis[v[i].second]) return;
        dfs(nums,vis,cur,v[i].second,v);
    }
    //Function to find the minimum number of swaps required to sort the array. 
	int minSwaps(vector<int>&nums)
	{
	    // Code here
	    vector<pair<int,int>> v;
	    for(int i=0;i<nums.size();i++)
	        v.push_back({nums[i],i});
	    sort(v.begin(),v.end());
	    bool vis[v.size()]={0};
	    int res=0;
	    for(int i=0;i<v.size();i++)
	        if(!vis[i]){
	            int cur=-1;
	            dfs(nums,vis,cur,i,v);
	            res += cur;
	        }
	    return res;
	}
};
```

