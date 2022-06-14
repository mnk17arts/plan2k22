---
layout: post
title: Separate chaining in Hashing
summary:
tags:
    - hash
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/separate-chaining-in-hashing-1587115621/0/)  

Separate chaining technique in hashing allows to us to use a linked list at each hash slot to handle the problem of collisions. That is, every slot of the hash table is a linked list, so whenever a collision occurs, the element can be appened as a node to the linked list at the slot.

In this question, we'll learn how to fill up the hash table using Separate chaining technique. Given an array and a hashtable size, you have to fill the elements of the array into a hash table of given size. 

**Your Task:** 
This is a function problem. You need to complete the function separateChaining that takes `hashSize`, `arr`, and `sizeOfArr` as parameters, inserts elements of arr in the hashTable at positions by using `arr[i]%hashSize` and then returns the has table. The printing is done automatically by the driver code. 


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
hashSize = 10
sizeOfArray = 6
arr[] = {92,4,14,24,44,91}
Output:
1->91
2->92
4->4->14->24->44
Explanation: 92%10=2 so 92 goes to slot 2.
4%10=4 so 4 goes to slot 4. 14%10=4. But 4
is already occupied so we make a linked
list at this position and add 14 after 4 
in slot 4 and so on.
```

**Example 2:**   
```
Input:
hashSize = 10
sizeOfArray = 5
arr[] = {12,45,36,87,11}
Output:
1->11
2->12
5->45
6->36
7->87
Explanation: 12%10=2 so 12 goes to slot 2.
45%10=5 goes to slot 5. 36%10=6 goes to
slot 6. 87%10=7 goes to slot 7 and finally
11%10=1 goes to slot 1.
```

### Constraints

+ `2 <= hashSize <= 10^3`
+ `1 <= sizeOfArray <= 10^3`
+ `0 <= arr[i] <= 10^7` 

## Solutions

```cpp
class Solution{
    public:
    //Complete this function
    //Function to insert elements of array in the hashTable avoiding collisions.
    vector<vector<int>> separateChaining(int hashSize,int arr[],int sizeOfArray)
    {
       //Your code here
       vector<vector<int>> hashTable(hashSize);
       for(int i=0; i<sizeOfArray ; i++){
           int key = arr[i]%hashSize ;
           hashTable[key].push_back(arr[i]);
       }
       return hashTable;
    }
};
```

