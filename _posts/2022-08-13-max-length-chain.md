---
layout: post
title: Max length chain                       
summary:
tags:
    - dynamic-programming
    - greedy
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/max-length-chain/1)  

You are given N pairs of numbers. In every pair, the first number is always smaller than the second number. A pair (c, d) can follow another pair (a, b) if b < c. Chain of pairs can be formed in this fashion. You have to find the longest chain which can be formed from the given set of pairs

**Your Task:** 

You don't need to read input or print anything. Your task is to Complete the function `maxChainLen()` which takes a structure `p[]` denoting the pairs and `n` as the number of pairs and returns the length of the longest chain formed.


**Expected Time Complexity:** `O(NlogN)`              
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
N = 5
P[] = {5  24 , 39 60 , 15 28 , 27 40 , 50 90}
Output: 3
Explanation: The given pairs are [ [5, 24], [39, 60],
[15, 28], [27, 40], [50, 90] ],the longest chain that
can be formed is of length 3, and the chain is
[[5, 24], [27, 40], [50, 90]]
```

**Example 2:**   
```
Input:
N = 2
P[] = {5 10 , 1 11}
Output: 1
Explanation:The max length chain possible is only of
length one.
```

### Constraints

+ `1 <= N <= 10^5`


## Solutions

```cpp
/*
The structure to use is as follows
struct val{
	int first;
	int second;
};*/

bool myCmp(val const &a, val const &b){
    return a.second < b.second;
}

class Solution{
public:
    /*You are required to complete this method*/
    int maxChainLen(struct val p[],int n){
        //Your code here
        sort(p,p+n, myCmp);
        int ans=0, cur = INT_MIN;
        for(int i=0;i<n;i++){
            if(cur < p[i].first) { 
                ans++;
                cur = p[i].second;
            }
        }
        return ans;
    }
};
```

