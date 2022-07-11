---
layout: post
title:  Binary Heap Operations             
summary:
tags:
    - heap
    - priority-queue
    - geeksforgeeks
    - cpp
    - easy
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/operations-on-binary-min-heap/0/?track=DSASP-Heap&batchId=154)  

A binary heap is a Binary Tree with the following properties:

+ Its a complete tree (All levels are completely filled except possibly the last level and the last level has all keys as left as possible). This property of Binary Heap makes them suitable to be stored in an array.

+ A Binary Heap is either Min Heap or Max Heap. In a Min Binary Heap, the key at the root must be minimum among all keys present in Binary Heap. The same property must be recursively true for all nodes in Binary Tree. Max Binary Heap is similar to MinHeap.

You are given an empty Binary Min Heap and some queries and your task is to implement the three methods `insertKey`,  `deleteKey`,  and `extractMin` on the Binary Min Heap and call them as per the query given below:
1. 1  x  (a query of this type means to insert an element in the min-heap with value x )
1. 2  x  (a query of this type means to remove an element at position x from the min-heap)
1. 3  (a query like this removes the min element from the min-heap and prints it ).


**Your Task:** 
You are required to complete the 3 methods `insertKey()` which take one argument the value to be inserted, `deleteKey()` which takes one argument the position from where the element is to be deleted and `extractMin()` which returns the minimum element in the heap(-1 if the heap is empty)



**Expected Time Complexity:** `O(Q*Log(size of Heap))`           
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
Q = 7
Queries:
insertKey(4)
insertKey(2)
extractMin()
insertKey(6)
deleteKey(0)
extractMin()
extractMin()
Output: 2 6 - 1
Explanation: In the first test case for
query 
insertKey(4) the heap will have  {4}  
insertKey(2) the heap will be {2 4}
extractMin() removes min element from 
             heap ie 2 and prints it
             now heap is {4} 
insertKey(6) inserts 6 to heap now heap
             is {4 6}
deleteKey(0) delete element at position 0
             of the heap,now heap is {6}
extractMin() remove min element from heap
             ie 6 and prints it  now the
             heap is empty
extractMin() since the heap is empty thus
             no min element exist so -1
             is printed.
``` 


**Example 2:**   
```
Input:
Q = 5
Queries:
insertKey(8)
insertKey(9)
deleteKey(1)
extractMin()
extractMin()
Output: 8 -1
```


### Constraints

+ `1 <= Q <= 10^4`
+ `1 <= x <= 10^4`

## Solutions

```cpp
//Function to extract minimum value in heap and then to store 
//next minimum value at first index.
int MinHeap::extractMin() 
{
    // Your code here
    int res = -1;
    if(heap_size){
        swap(harr[0],harr[--heap_size]);
        if(heap_size > 1) MinHeapify(0);
        res = harr[heap_size];
    }
    return res;
}

//Function to delete a key at ith index.
void MinHeap::deleteKey(int i)
{
    // Your code here
    if(i<heap_size&&heap_size) {
        decreaseKey(i,INT_MIN);
        extractMin();
    }
}

//Function to insert a value in Heap.
void MinHeap::insertKey(int k) 
{
    // Your code here
    if(heap_size==capacity) return;
    harr[heap_size++] = k;
    int i=heap_size-1;
    while(i>=0&&harr[i]<harr[parent(i)]){
        swap(harr[i],harr[parent(i)]);
        i = parent(i);
    }
}
```

