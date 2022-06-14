---
layout: post
title: Quadratic Probing in Hashing
summary:
tags:
    - hash
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/quadratic-probing-in-hashing-1587115621/0/)  

Quadratic probing is a collision handling technique in hashing. Quadratic probing says that whenever a collision occurs, search for i2 position.

Given an array of integers and a Hash table. Fill the elements of the array into the hash table by using Quadratic Probing in case of collisions.

**Note:**  
All the positions that are unoccupied are denoted by `-1` in the hash table.
An empty slot can only be found if `load factor < 0.5` and hash table size is a `prime number`.
The given testcases satisfy the above condition so you can assume that an empty slot is always reachable.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `QuadraticProbing()` which takes the hash table `hash[]`, the hash table size `hashSize`, an array `arr[]` and the size of the array `N` as inputs and inserts all the elements of the array `arr[]` into the hash table using Quadratic Probing as a collision handling technique.

**Note**: You need to map duplicate elements incase, they have the same hash value even after quadratic probing. 


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
hashSize = 11
N = 4
Array[] = {21,10,32,43}
Output: 
10 -1 -1 32 -1 -1 -1 -1 43 -1 21
Explanation: 21%11=10 so 21 goes into 
hashTable[10] position. 10%11=10. 
hashTable[10] is already filled so we try 
for (10+12)%11=0 position. hashTable[0] 
is empty so we put 10 there. 32%11=10. 
hashTable[10] is filled. We try 
(32+12)%11=0. But hashTable[0] is also 
already filled. We try (32+22)%11=3. 
hashTable[3] is empty so we put 32 in 
hashTable[3] position. 43 uses 
(43+32)%11=8. We put it in hashTable[8].
```

**Example 2:**   
```
Input:
hashSize = 11
N = 4
Array[] = {880,995,647,172 }
Output:
880 -1 -1 -1 -1 995 -1 172 -1 647 -1 
Explanation: Using the similar approach 
as used in above explanation we will get 
the output like 
880 -1 -1 -1 -1 995 -1 172 -1 647 -1.
```

### Constraints

+ `2 <= hashSize (prime) <= 97`
+ `1 <= N < hashSize*0.5`
+ `0 <= arr[i] <= 10^5` 

## Solutions

```cpp
class Solution{
    public:
    //Function to fill the array elements into a hash table 
    //using Quadratic Probing to handle collisions.
    void QuadraticProbing(vector <int>&hash, int hashSize, int arr[], int N)
    {
        //Your code here
        for(int i=0; i<N; i++){
            int key = arr[i]%hashSize ;
            if(hash[key] == -1 || hash[key] == arr[i])
                {hash[key] = arr[i]; continue;}
            int k = 1;
            int nkey = (key + k*k)%hashSize ;
            while(hash[nkey] != -1){
                if(nkey == key) return;
                if(hash[nkey] == arr[i]) break;
                else {
                    k++;
                    nkey = (key + k*k)%hashSize;
                }
            }
            hash[nkey] = arr[i];
        }
    }
};
```

