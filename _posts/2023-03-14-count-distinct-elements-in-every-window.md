---
layout: post
title: Count distinct elements in every window
summary:
tags:
  - geeksforgeeks
  - array
  - slidingwindow
  - hash
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/count-distinct-elements-in-every-window/1?page=3&curated[]=1&sortBy=submissions)

Given an array of integers and a number K. Find the count of distinct elements in every window of size K in the array.

**Your Task:**

Your task is to complete the function countDistinct() which takes the array A[], the size of the array(N) and the window size(K) as inputs and returns an array containing the count of distinct elements in every contiguous window of size K in the array A[]. 

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)` 

### Examples

**Example 1:**

```
Input:
N = 7, K = 4
A[] = {1,2,1,3,4,2,3}
Output: 3 4 4 3
Explanation: Window 1 of size k = 4 is
1 2 1 3. Number of distinct elements in
this window are 3. 
Window 2 of size k = 4 is 2 1 3 4. Number
of distinct elements in this window are 4.
Window 3 of size k = 4 is 1 3 4 2. Number
of distinct elements in this window are 4.
Window 4 of size k = 4 is 3 4 2 3. Number
of distinct elements in this window are 3.
```

**Example 2:**

```
Input:
N = 3, K = 2
A[] = {4,1,1}
Output: 2 1
```

### Constraints

- `1 <= K <= N <= 10^5`
- `1 <= A[i] <= 10^5`

## Solutions

```cpp

class Solution {
  public:
    vector <int> countDistinct (int A[], int n, int k) {
        //code here.
        unordered_map<int, int> mp;
        for(int i = 0; i < k; i++) {
            mp[A[i]]++;
        }
        int j = k;
        vector<int> ans;
        while(j < n) {
            ans.push_back(mp.size());
            if(mp[A[j-k]] > 1) {
                mp[A[j-k]]--;
            }
            else {
                mp.erase(A[j-k]);
            }
            mp[A[j]]++;
            j++;
        }
        ans.push_back(mp.size());
        return ans;
    }
};

```
