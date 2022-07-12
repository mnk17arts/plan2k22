---
layout: post
title: Merge k Sorted Arrays                
summary:
tags:
    - heap
    - sorting
    - priority-queue
    - queue
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/merge-k-sorted-arrays/0/?track=DSASP-Heap&batchId=154)  

Given `K` sorted arrays arranged in the form of a matrix of size `K*K`. The task is to merge them into one sorted array.

**Your Task:** 
You do not need to read input or print anything. Your task is to complete `mergeKArrays()` function which takes 2 arguments, an `arr[K][K]` 2D Matrix containing `K` sorted arrays and an integer K denoting the number of sorted arrays, as input and returns the merged sorted array ( as a pointer to the merged sorted arrays in cpp, as an ArrayList in java, and list in python)



**Expected Time Complexity:** `O(K^2 * LogK)`           
**Expected Auxiliary Space:** `O(K)`


### Examples

**Example 1:**   
```
Input:
K = 3
arr[][] = [[1,2,3],[4,5,6],[7,8,9]]
Output: 1 2 3 4 5 6 7 8 9
Explanation:Above test case has 3 sorted
arrays of size 3, 3, 3
arr[][] = [[1, 2, 3],[4, 5, 6], 
[7, 8, 9]]
The merged list will be 
[1, 2, 3, 4, 5, 6, 7, 8, 9].
``` 


**Example 2:**   
```
Input:
K = 4
arr[][]=[[1,2,3,4][2,2,3,4],
         [5,5,6,6],[7,8,9,9]]
Output:
1 2 2 2 3 3 4 4 5 5 6 6 7 8 9 9 
Explanation: Above test case has 4 sorted
arrays of size 4, 4, 4, 4
arr[][] = [[1, 2, 2, 2], [3, 3, 4, 4],
[5, 5, 6, 6]  [7, 8, 9, 9 ]]
The merged list will be 
[1, 2, 2, 2, 3, 3, 4, 4, 5, 5, 
6, 6, 7, 8, 9, 9 ].
```


### Constraints

+ `1 <= K <= 100`

## Solutions

```cpp
struct Node {
    int val;
    int index;
    int arr_index;
    Node(int v, int i, int a) : val(v), index(i), arr_index(a) {}
};

struct Compare {
    bool operator()(const Node &a, const Node &b) {
        return a.val > b.val;
    }
};


class Solution
{
    public:
    //Function to merge k sorted arrays.
    vector<int> mergeKArrays(vector<vector<int>> arr, int K)
    {
        //code here
        priority_queue<Node,vector<Node>,Compare> pq;
        for(int i=0; i<K; i++)
            pq.push(Node(arr[i][0], 0, i));
            
        vector<int> res; 
        while(!pq.empty()){
            Node ele = pq.top(); pq.pop();
            res.push_back(ele.val);
            if(ele.index < K-1) pq.push(Node(arr[ele.arr_index][ele.index+1], ele.index + 1, ele.arr_index));
        }
        return res;
    }   
};
```

