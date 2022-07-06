---
layout: post
title:  Maximum of minimum for every window size       
summary:
tags:
    - stack
    - geeksforgeeks
    - cpp
    - hard
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/maximum-of-minimum-for-every-window-size3453/0/?track=DSASP-Stack&batchId=154)  

Given an integer array. The task is to find the maximum of the minimum of every window size in the array.
**Note**: Window size varies from `1` to the size of the Array.


**Your Task:** 
The task is to complete the function `maxOfMin()` which takes the array `arr[]` and its size `N` as inputs and finds the maximum of minimum of every window size and returns an array containing the result. 

**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 7
arr[] = {10,20,30,50,10,70,30}
Output: 70 30 20 10 10 10 10 
Explanation: 
1.First element in output
indicates maximum of minimums of all
windows of size 1.
2.Minimums of windows of size 1 are {10},
 {20}, {30}, {50},{10}, {70} and {30}. 
 Maximum of these minimums is 70. 
3. Second element in output indicates
maximum of minimums of all windows of
size 2. 
4. Minimums of windows of size 2
are {10}, {20}, {30}, {10}, {10}, and
{30}.
5. Maximum of these minimums is 30 
Third element in output indicates
maximum of minimums of all windows of
size 3. 
6. Minimums of windows of size 3
are {10}, {20}, {10}, {10} and {10}.
7.Maximum of these minimums is 20. 
Similarly other elements of output are
computed.

```

**Example 2:**   
```
Input:
N = 3
arr[] = {10,20,30}
Output: 30 20 10
Explanation: First element in output
indicates maximum of minimums of all
windows of size 1.Minimums of windows
of size 1 are {10} , {20} , {30}.
Maximum of these minimums are 30 and
similarly other outputs can be computed
```


### Constraints

+ `1 <= N <= 10^5`
+ `1 <= arr[i] <= 10^6`

## Solutions

```cpp
class Solution{
    public:
    //Function to find maximum of minimums of every window size.
    vector <int> maxOfMin(int arr[], int n)
    {
        // Your code here
        stack<int> s;
        int ps[n];
        for(int i=0; i<n; i++){
            while(!s.empty() && arr[s.top()]>=arr[i]) s.pop();
            if(s.empty()) ps[i]=-1;
            else ps[i] = s.top();
            s.push(i);
        }
        while(!s.empty()) s.pop();
        int ns[n];
        for(int i=n-1; i>=0; i--){
            while(!s.empty() && arr[s.top()]>=arr[i]) s.pop();
            if(s.empty()) ns[i]=n;
            else ns[i]=s.top();
            s.push(i);
        }
        vector<int> res(n,-1);
        for(int i=0; i<n; i++){
            int len = ns[i] - ps[i] - 2;
            res[len] = max(res[len], arr[i]);
        }
        for(int i=n-2; i>=0; i--)
            res[i] = max(res[i], res[i+1]);
        return res;
    }
};
```

