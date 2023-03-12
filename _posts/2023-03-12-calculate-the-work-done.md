---
layout: post
title: Calculate the work done
summary:
tags:
  - geeksforgeeks
  - array
  - hash
  - queue
  - cpp
  - easy
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-93/problems/#)

Geek has a conveyor belt which has a capacity of cap. Initially conveyor belt is empty. There is an arr which has N items to be processed which may not be distinct. Whenever new item comes he checks if the same item already exists on conveyor belt, if it exists he keeps it as it is and if it is not there he has to do 1 amount of work. If while doing work the conveyor belt is not full he just puts it at front and if it was full he removes the last item from the belt and puts the new item in front. Calculate the total amount of work Geek has to do.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function workDone() which takes n, cap and arr as input parameters and returns the amount of work done by Geek.


### Examples

**Example 1:**

```
Input :
5 3
1 2 3 1 4

Output :
4

Explaination :
1,2,3 are not present so 3 amounts of work is done. 1 is present on conveyor belt so 0 amount of work required.When 4 comes conveyor belt is full, he removes the last element i.e. 1 and puts 4 there so 1 amount of work done.
```

**Example 2:**

```
Input :
5 4
1 1 1 1 1

Output :
1

Explaination :
Initially 1 is not present so 1 amount of work done. Later on no work is required as 1 is already present.
```

### Constraints

- `1 <= N <= 10^5`
- `1 <= cap <= 10^3`
- `1 <= arr[i] <= 10^4`

## Solutions

```cpp

class Solution {
  public:
    int workDone(int n, vector<int> &a, int cap) {
        // code here
        unordered_set<int> items;
        deque<int> cb;
        int res = 0;
        for (int i = 0; i < n; i++) {
            if (items.count(a[i]) == 0) {
                res++;
                if (cb.size() == cap) {
                    int lastItem = cb.back();
                    items.erase(lastItem);
                    cb.pop_back();
                }
                cb.push_front(a[i]);
                items.insert(a[i]);
            }
        }
        return res;
    }
};

```
