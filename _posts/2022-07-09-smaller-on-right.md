---
layout: post
title: Smaller on Right              
summary:
tags:
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/smaller-on-right/0/?track=DSASP-BST&batchId=154)  

Given an array `arr[]` of `N` elements. The task is to count maximum number of distinct smaller elements on right side of any array element. For example, in {`10, 6, 9, 7, 20, 19, 21, 18, 17, 16`}, the result is `4`.  Note that `20` has maximum `4` smaller elements on right side. Other elements have less count, for example `10` has `3` smaller elements on right side.


**Input:**
The first line of input contains number of testcases T. For each testcase, first line of input contains number of elements in the array and next line contains array elements.

**Output:**
For each testcase, print the maximum count of smaller elements on right side.


### Example

```
Input:
4
10
10 6 9 7 20 19 21 18 17 16
5
5 4 3 2 1
5
1 2 3 4 5
5
1 2 3 2 1

Output:
4
4
0
2

Explanation:

Testcase 1: Number of smaller elements on right side of every element (from left to right)
 in the array are 3 0 1 0 4 3 3 2 1 and 0 respecitvely. Maximum of all these counts is 4.
Testcase 2: Number of smaller elements on right side of every element (from left to right) 
in the array are 4 3 2 1 and 0 respecitvely. Maximum of all these counts is 4.
```



### Constraints

+ `1 <= T <= 100`
+ `1 <= N <= 10^5`
+ `1 <= arr[i] <= 10^6`

## Solutions

```cpp
#include<iostream>
#include<set>
#include<iterator>
#include<algorithm>
using namespace std;

int smallOnRight(int a[], int n){
    set<int> s;
    int res=0;
    for(int i=n-1; i>=0; i--){
        s.insert(a[i]);
        res = max(res,(int)distance(s.begin(),s.find(a[i])));
    }
    return res;
}

int main() {
	//code
	int t;
	cin>>t;
	while(t--){
	    int n; cin>>n;
	    int a[n]; for(int i=0;i<n;i++) cin>>a[i];
	    cout << smallOnRight(a,n) << endl;
	}
	
	return 0;
}
```

