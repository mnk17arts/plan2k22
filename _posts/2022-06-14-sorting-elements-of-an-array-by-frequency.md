---
layout: post
title: Sorting Elements of an Array by Frequency  
summary:
tags:
    - hash
    - array
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/sorting-elements-of-an-array-by-frequency-1587115621/0/)  

Given an array of integers, sort the array according to frequency of elements. That is elements that have higher frequency come first. If frequencies of two elements are same, then smaller number comes first.


**Your Task:** 
You only need to complete the function `sortByFreq` that takes `arr`, and `n` as parameters and returns the sorted array.


**Expected Time Complexity:** `O(n * logn)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
N = 5
A[] = {5,5,4,6,4}
Output: 4 4 5 5 6
Explanation: The highest frequency here is
2. Both 5 and 4 have that frequency. Now
since the frequencies are same then 
smallerelement comes first. So 4 4 comes 
firstthen comes 5 5. Finally comes 6.
The output is 4 4 5 5 6.
```

**Example 2:**   
```
Input:
N = 5
A[] = {9,9,9,2,5}
Output: 9 9 9 2 5
Explanation: The highest frequency here is
3. The element 9 has the highest frequency
So 9 9 9 comes first. Now both 2 and 5
have same frequency. So we print smaller
element first.
The output is 9 9 9 2 5.
```

### Constraints

+ `1 <= n <= 10^5`
+ `1 ≤ arr[i] ≤ 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Complete this function
    //Function to sort the array according to frequency of elements.
    static bool myFunc(pair<int, int> &a, pair<int, int> &b){
        if(a.second != b.second)
            return a.second > b.second;
        return a.first < b.first;
    }
    vector<int> sortByFreq(int arr[],int n)
    {
        //Your code here
        unordered_map<int, int> m;
        
        for(int i=0; i<n; i++) m[arr[i]]++;
        vector<pair<int, int>> p;
        for(auto i: m)
            p.push_back(make_pair(i.first, i.second));
        sort(p.begin(), p.begin() + m.size(), myFunc);
        vector<int> v;
        for(int i=0; i<m.size(); i++)
            for(int j=0; j<p[i].second; j++)
                v.push_back(p[i].first);
        return v;
    }
};
```

