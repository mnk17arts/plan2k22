---
layout: post
title: Fractional Knapsack                   
summary:
tags:
    - greedy
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/fractional-knapsack-1587115620/0/?track=DSASP-Greedy&batchId=154#)  

Given weights and values of `N` items, we need to put these items in a knapsack of capacity `W` to get the maximum total value in the knapsack.
Note: Unlike `0/1` knapsack, you are allowed to break the item. 

**Your Task:** 
Complete the function `fractionalKnapsack()` that receives maximum capacity , array of structure/class and size n and returns a double value representing the maximum value in knapsack.
Note: The details of structure/class is defined in the comments above the given function.


**Expected Time Complexity:** `O(N * Log(N))`           
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
N = 3, W = 50
values[] = {60,100,120}
weight[] = {10,20,30}
Output:
240.00
Explanation:Total maximum value of item
we can have is 240.00 from the given
capacity of sack.
```

**Example 2:**   
```
Input:
N = 2, W = 50
values[] = {60,100}
weight[] = {10,20}
Output:
160.00
Explanation:
Total maximum value of item
we can have is 160.00 from the given
capacity of sack.
```

### Constraints

+ `1 ≤ N ≤ 10^5`
+ `1 ≤ W ≤ 10^5`

## Solutions

```cpp
/*
struct Item{
    int value;
    int weight;
};
*/


bool compare(Item &a, Item &b){
    double ra = (double)a.value/a.weight;
    double rb = (double)b.value/b.weight;
    return (ra>rb);
}

class Solution
{
    public:
    //Function to get the maximum total value in the knapsack.
    double fractionalKnapsack(int W, Item arr[], int n)
    {
        // Your code here
        sort(arr,arr+n,compare);
        double res=0;
        for(int i=0;i<n;i++){
            if(arr[i].weight <= W){
                res += arr[i].value;
                W -= arr[i].weight;
            }else{
                res += (W*((double)arr[i].value/arr[i].weight));
                break;
            }
        }
        return res;
    }
        
};
```

