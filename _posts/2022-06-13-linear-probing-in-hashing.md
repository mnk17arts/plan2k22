---
layout: post
title: Linear Probing in Hashing 
summary:
tags:
    - hash
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/linear-probing-in-hashing-1587115620/0/)  

Linear probing is a collision handling technique in hashing. Linear probing says that whenever a collision occurs, search for the immediate next position.

Given an array of integers and a hash table size. Fill the array elements into a hash table using Linear Probing to handle collisions. Duplicate elements must be mapped to the same position in the hash table while colliding elements must be mapped to the `[(value+1)%hashSise]` position. 

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `linearProbing()` which takes the hash table size (`hashSize`), an integers array `arr[]` and its size `N` as input parameters and inserts all the elements of the array `arr[]` into a hash table. The function should return the hash table. 
The empty cells of the hash table are to be given a value of `-1`.
Also, if there's no more space to insert a new element, just drop that element. 


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
hashSize = 10
sizeOfArray = 4 
Array[] = {4,14,24,44}
Output:
-1 -1 -1 -1 4 14 24 44 -1 -1
Explanation: 4%10=4. So put 4 in 
hashtable[4].Now, 14%10=4, but 
hashtable[4] is alreadyfilled so put 
14 in the next slot and so on.
```

**Example 2:**   
```
Input:
hashSize = 10
sizeOfArray = 4 
Array[] = {9,99,999,9999}
Output:
99 999 9999 -1 -1 -1 -1 -1 -1 9
Explanation: 9%10=9. So put 9 in 
hashtable[9]. Now, 99%10=9, but 
hashtable[9] is already filled so 
put 99 in the (99+1)%10 =0 slot so
99 goes into hashtable[0] and so on.
```

### Constraints

+ `1 <= hashSize <= 100`
+ `1 <= sizeOfArray <= 100`
+ `0 <= arr[i] <= 10^5` 

## Solutions

```cpp
class Solution{
    public:
    //Function to fill the array elements into a hash table 
    //using Linear Probing to handle collisions.
    vector<int> linearProbing(int hashSize, int arr[], int sizeOfArray)
    {
        //Your code here
        vector<int> hashTable(hashSize,-1);
        for(int i=0; i<sizeOfArray; i++){
            int key = arr[i]%hashSize ;
            if(hashTable[key] == -1 || hashTable[key] == arr[i]){
                hashTable[key] = arr[i];
                continue;
            }
            int k=1;
            int nkey = (key + k)%hashSize;
            while( hashTable[nkey] != -1){
                if(nkey == key) return hashTable;
                if(hashTable[nkey] == arr[i]) break;
                else { k++; nkey = (key + k)%hashSize; }
            }
            hashTable[nkey] = arr[i];
        }
        return hashTable;
    }
};
```

