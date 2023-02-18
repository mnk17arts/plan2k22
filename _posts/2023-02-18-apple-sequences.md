---
layout: post
title: Apple Sequences
summary:
tags:
  - geeksforgeeks
  - 2pointers
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/38f100615d0b2efa755e7b07f905e0f8cd2fe5df/1)

There is a string of size n containing only 'A' and 'O'. 'A' stands for Apple, and 'O' stands for Orange. We have m number of spells, each spell allows us to convert an orange into an apple.

Find the longest sequence of apples you can make, given a string and the value of m

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function appleSequence() which takes the array in the form of a string, its size n, and an integer m as input parameters and returns the largest apple sequences after converting m oranges.



**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
N = 5
M = 1
arr[] = 'AAOAO'
Output: 4 
Explanation: Changing the orange at 
3rd position into an apple gives 
us the maximum possible answer.
```

**Example 2:**

```
Input:
N = 5
M = 1
arr = 'AOOAO'
Output: 2
Explanation: Changing any orange into 
an apple will give us a sequence 
of length 2.
```

### Constraints

- `1 <= m <= n <= 10^6`

## Solutions

```cpp

class Solution{
  public:
    int appleSequences(int n, int m, string arr){
        // code here 
        unordered_map<char, int> map;
        int l = 0, r = 0, res = 0;
        while(r < n) {
            map[arr[r++]]++;
            if(map['O'] <= m) {
                res = max(res, r - l);
            }
            else {
                map[arr[l++]]--;
            }
        }
        return res;
    }
};

```
