---
layout: post
title: Merge K sorted linked lists     
summary:
tags:
    - linkedlist
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/merge-k-sorted-linked-lists/0/?)  

Given `K` sorted linked lists of different sizes. The task is to merge them in such a way that after merging they will be a single sorted linked list. 


**Your Task:** 
The task is to complete the function `mergeKList()` which merges the `K` given lists into a sorted one. The printing is done automatically by the driver code.


**Expected Time Complexity:** `O(nkLogk)` 
**Expected Auxiliary Space:** `O(k)`
**Note**: `n` is the maximum size of all the `k` link list

### Examples

**Example 1:**   
```
Input:
K = 4
value = {{1,2,3},{4 5},{5 6},{7,8}}
Output: 1 2 3 4 5 5 6 7 8
Explanation:
The test case has 4 sorted linked 
list of size 3, 2, 2, 2
1st    list     1 -> 2-> 3
2nd   list      4->5
3rd    list      5->6
4th    list      7->8
The merged list will be
1->2->3->4->5->5->6->7->8.
```

**Example 2:**   
```
Input:
K = 3
value = {{1,3},{4,5,6},{8}}
Output: 1 3 4 5 6 8
Explanation:
The test case has 3 sorted linked
list of size 2, 3, 1.
1st list 1 -> 3
2nd list 4 -> 5 -> 6
3rd list 8
The merged list will be
1->3->4->5->6->8.
```


### Constraints

+ `1 <= k <= 10^3`

## Solutions

```cpp
class Solution{
    public:
    Node* merge(Node* h1,Node*h2){
        Node* res = NULL;
        if(!h1)    return h2;
        if(!h2)    return h1;
        
        if(h1->data <= h2->data){
            res = h1;
            res->next = merge(h1->next,h2);
        }
        else{
            res = h2;
            res->next = merge(h1,h2->next);
        }
        return res;
    }
    Node * mergeKLists(Node *arr[], int K)
    {
        for(int i=1;i<K;i++){
            arr[0] = merge(arr[0],arr[i]);
        }
        return arr[0];
    }
};
```

