---
layout: post
title: Contiguous Elements XOR                      
summary:
tags:
    - trie
    - geeksforgeeks
    - cpp
    - hard
minute: 12 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/contiguous-elements-xor4151/0/?t#)  

You are given an array `arr[]` of `N` positive integers. This time you are supposed to choose numbers from a contiguous sub-sequence of the given array, so that BITWISE XOR of all the chosen numbers is maximum..



**Your Task:** 

Complete `maxSubarrayXOR` function and return the maximum XOR value.


**Expected Time Complexity:** `O(NlogN)`              
**Expected Auxiliary Space:** `O(N)`



### Examples

**Example 1:**   
```
Input:
N = 4
arr[] = {8,1,2,12}
Output: 15
Explanation: 1, 2 and 12 can be chosen
from the array as contiguous sub
sequence which given us maximum
XOR value equal to 15.
```

**Example 2:**   
```
Input:
N = 4
arr[] = {1,2,3,4}
Output: 7
Explanation: 3 and 4 from the array
can be chosen  as contiguous sub
sequence which given us maximum XOR
value equal to 7.
```

### Constraints

+ `1 ≤ N <= 100000`
+ `1 <= arr[i] <= 10^6` (Must be in range of 32 bits signed integer)`


## Solutions

```cpp

struct TrieNode 
{ 
	int value;
	TrieNode *arr[2]; 
}; 

TrieNode *newNode(){
  
  TrieNode *temp = new TrieNode;
  temp->value = 0;
  temp->arr[0] = temp->arr[1] = NULL;
  return temp;

}

void insert(TrieNode *root, int pre_xor) { 
	TrieNode *temp = root; 
	for (int i=INT_SIZE-1; i>=0; i--) 	{ 
		bool val = pre_xor & (1<<i); 
		if (temp->arr[val] == NULL) 
			temp->arr[val] = newNode(); 
		temp = temp->arr[val]; 
	} 
	temp->value = pre_xor; 
} 

int query(TrieNode *root, int pre_xor) { 
	TrieNode *temp = root; 
	for (int i=INT_SIZE-1; i>=0; i--) 	{ 
		bool val = pre_xor & (1<<i); 
		if (temp->arr[1-val]!=NULL) 
			temp = temp->arr[1-val]; 
		else if (temp->arr[val] != NULL) 
			temp = temp->arr[val]; 
	} 
	return pre_xor^(temp->value); 
} 


class Solution {
    public:
    int maxSubarrayXOR(int arr[], int n)  { 
    	TrieNode *root = newNode(); 
    	insert(root, 0); 
    	int result = INT_MIN, pre_xor =0; 
    	for (int i=0; i<n; i++) 	{ 
    		pre_xor = pre_xor^arr[i]; 
    		insert(root, pre_xor); 
    		result = max(result, query(root, pre_xor)); 
    	} 
    	return result; 
    } 
};
```

