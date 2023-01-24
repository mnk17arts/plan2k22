---
layout: post
title: Next Greater Element                       
summary:
tags:
    - geeksforgeeks
    - array
    - stack
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/214734e358208c1c6811d9b237b518f6b3c3c094/1)  

Given an array arr[ ] of size n having distinct elements, the task is to find the next greater element for each element of the array in order of their appearance in the array.

Next greater element of an element in the array is the nearest element on the right which is greater than the current element.

If there does not exist next greater of current element, then next greater element for current element is -1. For example, next greater of the last element is always -1
 

**Your Task:** 

This is a function problem. You only need to complete the function nextLargerElement() that takes list of integers arr[ ] and n as input parameters and returns list of integers of length N denoting the next greater elements for all the corresponding elements in the input array.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)` 



### Examples

**Example 1:**   
```
Input: 
n = 4, arr[] = [1 3 2 4]
Output:
3 4 4 -1
Explanation:
In the array, the next larger element 
to 1 is 3, 3 is 4, 2 is 4 and for 4? 
since it doesn't exist, it is -1.

```

**Example 2:**   
```
Input: 
n = 5, arr[] = [6 8 0 1 3]
Output:
8 -1 1 3 -1
Explanation:
In the array, the next larger element to 
6 is 8, for 8 there is no larger elements 
hence it is -1, for 0 it is 1, for 1 it 
is 3 and then for 3 there is no larger 
element on right and hence -1.
```

### Constraints

+ `1 <= N <= 10^4`
+ `1 <= K <= N`
+ `1 <= arr[i] <= 10^5`

## Solutions

```cpp

class Solution {
  public:
    vector<long long> nextLargerElement(vector<long long> &arr, int n){
        // Your code here
        vector<long long> result(n,-1);
        stack<long long> next;
        next.push(arr.at(n-1));
        for(int i=n-1; i>=0; i-- ) {
            if(next.top() > arr.at(i)) {
                result.at(i) = next.top();
            }
            else {
                while(!next.empty() && next.top()<=arr.at(i)) {
                    next.pop();
                }
                if(next.empty()) {
                    result.at(i) = -1;
                }
                else {
                    result.at(i) = next.top();
                }
            }
            next.push(arr.at(i));
        }
        return result;
    }
};

```

