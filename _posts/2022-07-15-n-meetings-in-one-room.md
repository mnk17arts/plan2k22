---
layout: post
title: N meetings in one room                   
summary:
tags:
    - greedy
    - geeksforgeeks
    - cpp
    - easy
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/0/?track=DSASP-Greedy&batchId=154#)  

There is one meeting room in a firm. There are `N` meetings in the form of (`start[i], end[i]`) where `start[i]` is start time of meeting `i` and `end[i]` is finish time of meeting `i`.
What is the maximum number of meetings that can be accommodated in the meeting room when only one meeting can be held in the meeting room at a particular time?

Note: Start time of one chosen meeting can't be equal to the end time of the other chosen meeting. 

**Your Task:** 
You don't need to read inputs or print anything. Complete the function `maxMeetings()` that takes two arrays `start[]` and `end[]` along with their size `N` as input parameters and returns the maximum number of meetings that can be held in the meeting room.


**Expected Time Complexity:** `O(N * Log(N))`           
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 6
start[] = {1,3,0,5,8,5}
end[] =  {2,4,6,7,9,9}
Output: 
4
Explanation:
Maximum four meetings can be held with
given start and end timings.
The meetings are - (1, 2),(3, 4), (5,7) and (8,9)
```

**Example 2:**   
```
Input:
N = 3
start[] = {10, 12, 20}
end[] = {20, 25, 30}
Output: 
1
Explanation:
Only one meetings can be held
with given start and end timings.
```

### Constraints

+ `1 ≤ N ≤ 10^5`
+ `1 ≤ start[i] ≤ end[i] ≤ 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to find the maximum number of meetings that can
    //be performed in a meeting room.
    int maxMeetings(int start[], int end[], int n) {
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

