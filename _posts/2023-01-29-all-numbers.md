---
layout: post
title: All Numbers                     
summary:
tags:
    - geeksforgeeks
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/5a7e1a52f1b7796238f9efea4c6fda389f26c327/1)  

You are given two numbers A and B, Now you are asked to form two lists, first list contains all the numbers which are divisible by A and less than equal to B, second list contains all the numbers which are divisors of B and less than equal to A, finally you need to print common elements from both the lists in ascending order.

**Your Task:** 

You don't need to read, input, or print anything. Your task is to complete the function allNumbers() which takes two integers A and B as input parameters and returns a list of integers containing the common elements from both the lists in ascending order.

### Examples

**Example 1:**   
```
Input:
A=1000000000
B=2000000000

Output:
1000000000 2000000000

Explanation:
1000000000 and 2000000000 both are divisible by 1000000000 and are multiple of 2000000000.
```

**Example 2:**   
```
Input:
A=1000000000
B=3000000000

Output:
1000000000 3000000000

Explanation:
1000000000 and 3000000000 both are divisible by 1000000000 and are multiple of 3000000000.
```

### Constraints

+ `10^9 ≤ A ≤ 10^15`
+ `A ≤ B ≤ 10^15`

## Solutions

```cpp

class Solution{
	public:
	vector<long long> allNumbers(long long A,long long B)
	{
		//code here
        vector<long long> res;
        long long temp = A;
        while( temp<=B ) {
            if(B%temp==0) {
                res.push_back(temp);
            }
            temp+=A;
        }
        return res;
	}
};

```

