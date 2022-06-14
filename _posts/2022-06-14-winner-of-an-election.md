---
layout: post
title: Winner of an election  
summary:
tags:
    - hash
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/winner-of-an-election-where-votes-are-represented-as-candidate-names-1587115621/0/)  

Given an array of names (consisting of lowercase characters) of candidates in an election. A candidate name in array represents a vote casted to the candidate. Print the name of candidate that received Max votes. If there is tie, print lexicographically smaller name.

**Your Task:** 
You only need to complete the function `winner()` that takes an array of strings `arr`, and `n` as parameters and returns the name of the candiate with maximum votes and the number of votes the candidate got as an array of size `2`.


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
n = 13
Votes[] = {john,johnny,jackie,johnny,john 
jackie,jamie,jamie,john,johnny,jamie,
johnny,john}
Output: john 4
Explanation: john has 4 votes casted for 
him, but so does johny. john is 
lexicographically smaller, so we print 
john and the votes he received.
```

**Example 2:**   
```
Input:
n = 3
Votes[] = {andy,blake,clark}
Output: andy 1
Explanation: All the candidates get 1 
votes each. We print andy as it is 
lexicographically smaller.
```

### Constraints

+ `1 <= n <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Function to return the name of candidate that received maximum votes.
    vector<string> winner(string arr[],int n)
    {
        // Your code here
        // Return the string containing the name and an integer
        // representing the number of votes the winning candidate got
        string s = "";
        int mx = 0;
        unordered_map<string, int> m;
        for(int i=0; i<n; i++){
            m[arr[i]]++;
            if(m[arr[i]] > mx){
                mx = m[arr[i]];
                s = arr[i];
            }
            else if(m[arr[i]] == mx){
                if(s > arr[i])
                s = arr[i];
            }
        }
        vector<string> res;
        res.push_back(s);
        res.push_back(to_string(mx));
        return res;
    }
};
```

