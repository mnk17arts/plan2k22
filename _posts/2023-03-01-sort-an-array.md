---
layout: post
title: Sort an Array
summary:
tags:
  - leetcode
  - array
  - heap
  - sorting
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/sort-an-array/description/)

Given an array of integers nums, sort the array in ascending order and return it.

You must solve the problem without using any built-in functions in O(nlog(n)) time complexity and with the smallest space complexity possible.


### Examples

**Example 1:**  


```
Input: nums = [5,2,3,1]
Output: [1,2,3,5]
Explanation: After sorting the array, the positions of some numbers are not changed (for example, 2 and 3), while the positions of other numbers are changed (for example, 1 and 5).
```

**Example 2:**  


```
Input: nums = [5,1,1,2,0,0]
Output: [0,0,1,1,2,5]
Explanation: Note that the values of nums are not necessairly unique.
```


### Constraints

- `1 <= nums.length <= 5 * 10^4`
- `-5 * 10^4 <= nums[i] <= 5 * 10^4`


## Solutions

```cpp

class Solution {
    void heapify(int[] nums, int n, int i) {
        int parent = i, left = 2 * i + 1, right = 2 * i + 2;
        if(left < n && nums[left] > nums[parent]) {
            parent = left;
        }
        if(right < n && nums[right] > nums[parent]) {
            parent = right; 
        }
        if(parent != i) {
            int temp = nums[i];
            nums[i] = nums[parent];
            nums[parent] = temp;
            heapify(nums, n, parent);
        }
    }
    void heapSort(int[] nums) {
        int n = nums.length;
        for(int i = n / 2 - 1; i >= 0; i--) {
            heapify(nums, n, i);
        }
        for(int i = n - 1; i >= 0; i--) {
            int temp = nums[0];
            nums[0] = nums[i];
            nums[i] = temp;
            heapify(nums, i, 0);
        }
    }
    public int[] sortArray(int[] nums) {
        heapSort(nums);
        return nums;
    }
}

```
