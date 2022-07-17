---
layout: post
title: Activity Selection                   
summary:
tags:
    - greedy
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/activity-selection-1587115620/0/?track=DSASP-Greedy&batchId=154)  

Given `N` activities with their start and finish day given in array `start[ ]` and `end[ ]`. Select the maximum number of activities that can be performed by a single person, assuming that a person can only work on a single activity at a given day.
Note : Duration of the activity includes both starting and ending day. 

**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function `activityselection()` which takes array `start[ ]`, array `end[ ]` and integer `N` as input parameters and returns the maximum number of activities that can be done.


**Expected Time Complexity:** `O(N * Log(N))`           
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 2
start[] = {2, 1}
end[] = {2, 2}
Output: 
1
Explanation:
A person can perform only one of the
given activities.
```

**Example 2:**   
```
Input:
N = 4
start[] = {1, 3, 2, 5}
end[] = {2, 4, 3, 6}
Output: 
3
Explanation:
A person can perform activities 1, 2
and 4.
```

### Constraints

+ `1 ≤ N ≤ 2*10^5`
+ `1 ≤ start[i] ≤ end[i] ≤ 10^9`

## Solutions

```cpp
class Solution
{
    public:
    //Function to find the maximum number of activities that can
    //be performed by a single person.
    int activitySelection(vector<int> start, vector<int> end, int n) {
        // Your code here
        vector<pair<int,int>> v;
        for(int i  = 0 ; i < n;i++){
           v.push_back({end[i],start[i]});}
        sort(v.begin(),v.end());
        int ans = 1 ;
        int c = v[0].first;
        for(int i = 1 ; i < n;i++){
           if(v[i].second>c){
               ans++;
               c=v[i].first;
           }}
        return ans;
    }
};
```

