---
layout: post
title: Arithmetic Number
summary:
tags:
    - geeksforgeeks
    - math
    - cpp
    - easy
minute: 2+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/arithmetic-number2815/1) 

Given three integers  'A' denoting the first term of an arithmetic sequence , 'C' denoting the common difference of an arithmetic sequence and an integer 'B'. you need to tell whether 'B' exists in the arithmetic sequence or not. Return 1 if B is present in the sequence. Otherwise, returns 0

**Your Task:** 

You do not need to read input or print anything. Your task is to complete the function inSequence() which takes A, B and C and returns 1 if B is present in the sequence. Otherwise, returns 0.



**Expected Time Complexity:** `O(1)`  
**Expected Auxiliary Space:** `O(1)`  



### Examples

**Example 1:**   
```
Input: A = 1, B = 3, C = 2
Output: 1
Explaination: 3 is the second term of the 
sequence starting with 1 and having a common 
difference 2.
```

**Example 2:** 
```
Input: A = 1, B = 2, C = 3
Output: 0
Explaination: 2 is not present in the sequence.1 → 15 → 20
Output:
2 → 13 → 19
Explanation:
The nearest prime of 1 is 2.
The nearest primes of 15 are 13 and 17,
since 13 is smaller so, 13 will be chosen.
The nearest prime of 20 is 19.
```

### Constraints

+ `-10^9 ≤ A, B, C ≤ 10^9`

## Solutions

```cpp

class Solution{
public:
    int inSequence(int A, int B, int C){
        // code here
        if(A > B && C > 0) {
            return 0;
        }
        if(A < B && C < 0) {
            return 0;
        }
        if(C == 0) {
            return A == B;
        }
        return (B - A) % C == 0;
    }
};

```
