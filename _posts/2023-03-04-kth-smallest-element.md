---
layout: post
title: Kth smallest element
summary:
tags:
  - geeksforgeeks
  - array
  - binary-search
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/kth-smallest-element5635/1)

Given an array arr[] and an integer K where K is smaller than size of array, the task is to find the Kth smallest element in the given array. It is given that all array elements are distinct.

Note :-  l and r denotes the starting and ending index of the array.

**Your Task:**

You don't have to read input or print anything. Your task is to complete the function kthSmallest() which takes the array arr[], integers l and r denoting the starting and ending index of the array and an integer K as input and returns the Kth smallest element.

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(logn)`

### Examples

**Example 1:**

```
Input:
N = 6
arr[] = 7 10 4 3 20 15
K = 3
Output : 7
Explanation :
3rd smallest element in the given 
array is 7.
```

**Example 2:**

```
Input:
N = 5
arr[] = 7 10 4 20 15
K = 4
Output : 15
Explanation :
4th smallest element in the given 
array is 15.
```

### Constraints

- `1 ≤ N  <= 10^5`
- `1 ≤ arr[i] ≤ 10^5`
- `1 ≤ K ≤ N`

## Solutions

```cpp

class Solution{
    int util(int arr[], int mid, int n) {
        int ck = 0;
        for(int i = 0; i < n; i++) {
            if(arr[i] <= mid) {
                ck++;
            }
        }
        return ck;
    }
    public:
    // arr : given array
    // l : starting index of the array i.e 0
    // r : ending index of the array i.e size-1
    // k : find kth smallest element and return using this function
    int kthSmallest(int arr[], int l, int r, int k) {
        //code here
        int n = r + 1;
        l = *min_element(arr, arr + n);
        r = *max_element(arr, arr + n);
        while(l <= r) {
            int mid = l + (r - l) / 2;
            int ck = util(arr, mid, n);
            if(ck < k) {
                l = mid + 1;
            }
            else {
                int cck = util(arr, mid - 1, n);
                if(cck < k) {
                    return mid;
                }
                else {
                    r = mid - 1;
                } 
            }
        }
        return arr[0];
    }
};

```
