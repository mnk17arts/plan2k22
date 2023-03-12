---
layout: post
title: Make array beautiful
summary:
tags:
  - geeksforgeeks
  - array
  - math
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-93/problems/#)

Given an array A of size N, make the array beautiful in minimum number of operations.
A beautiful array has all the elements divisible by 3.
In one operation you can take any two elements from the array, remove them and append their sum at the end of array. If it is not possible to make array beautiful return -1.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function minimumOperations() which takes n and A as input parameters and returns the number of pairs that have sum K.


### Examples

**Example 1:**

```
Input :
7 
1 4 7 10 13 2 5

Output :
4

Explaination :
Operation 1 :- Remove 1 and 2 and Append 3. Array becomes [4 7 10 13 5 3]
Operation 2 :- Remove 4 and 5 and Append 9. Array becomes [7 10 13 3 9]
Operation 3 :- Remove 7 and 13 and Append 20. Array becomes [10 3 9 20]
Operation 4 :- Remove 10 and 20 and Append 30. Array becomes [3 9 30]
Now array has all the elements divisible by 3 so it is beautiful.
```

**Example 2:**

```
Input :
5
1 4 7 10 13

Output :
-1

Explaination :
It is not possible to make it divisible by 3 by any kind of operations.
```

### Constraints

- `1 <= N <= 10^5`
- `1 <= a[i] <= 10^5`

## Solutions

```cpp

class Solution {
  public:
    int minimumOperations(int n, vector<int> &a) {
        // code here
        // 1 4 7 10 13 2 5
        // 1 1 1 1 1 2 2
        int one = 0, two = 0;        
        for(auto &num: a) {
            num %= 3; 
            if(num == 1) {
                one++;
            }
            else if(num == 2) {
                two++;
            }
        }
        int tot_sum = one + 2 * two;
        if(tot_sum % 3 != 0) {
            return -1;
        }
        int res = 0;
        if(two < one) {
            res += two;
            one -= two;
            two = 0;
        }
        else if(two > one) {
            res += one;
            two -= one;
            one = 0;
        }
        else {
            res += one;
            one = 0;
            two = 0;
        }
        
        if(one != 0) {
            res += (one / 3)*2;
            one = 0;
        }
        if(two != 0) {
            res += (two / 3)*2;
            two = 0;
        }
        return res;
    }
};

```
