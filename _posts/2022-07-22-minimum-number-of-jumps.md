---
layout: post
title: Minimum number of jumps                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/minimum-number-of-jumps4102/0/?track=DSASP-DP&batchId=154#)  

Given an array of integers where each element represents the max number of steps that can be made forward from that element. The task is to find the minimum number of jumps to reach the end of the array (starting from the first element). If an element is `0`, then cannot move through that element.

**Your Task:** 

Complete the function `minimumJump()` which takes an array and `N` (number of elements) as input parameters and returns the answer(if no answer possible return `-1`)


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 11
a[] = {1,3,5,8,9,2,6,7,6,8,9}
Output: 3
Explanation: First jump from 1st element,
and we jump to 2nd element with value 3.
Now, from here we jump to 5h element with
value 9. and from here we will jump to
last.
```

**Example 2:**   
```
Input:
N = 6
a[] = {1,4,3,2,6,7}
Output: 2
```

### Constraints

+ `1 <= N <= 10^5`
+ `1 <= a[i] <= 10^5`


## Solutions

```cpp
class Solution
{
    public:
    //Function to find minimum number of jumps to reach the end of the array.
    int minimumJumps(int arr[], int n){
        
        // your code here
        if(n==1) return 0;
        if(arr[0]==0) return -1;
        int steps = 1, 
            maxRange = arr[0],
            count = arr[0];
        for(int i=1;i<n;i++){
            if(i==n-1) return steps;
            maxRange = max(maxRange,i+arr[i]);
            count--;
            if(count==0){
                steps++;
                if(i>=maxRange) return -1;
                count = maxRange - i;
            }
            
        }
        return -1;
        
    }
};
```

