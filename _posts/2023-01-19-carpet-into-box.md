---
layout: post
title: Carpet into Box                       
summary:
tags:
    - geeksforgeeks
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/230d87552a332a2970b2092451334a007f2b0eec/1)  

There is a carpet of a size a*b [length * breadth]. You are given a box of size c*d. The task is, one has to fit the carpet in the box in a minimum number of moves. 

In one move, you can either decrease the length or the breadth of the carpet by half (floor value of its half).

Note: One can even turn the carpet by 90 degrees any number of times, wont be counted as a move.
 

**Your Task:** 

You don't need to read input or print anything. You only need to complete the function carpetBox() that takes an integer A, B, C and D as input and returns an integer denoting the minimum numbers of moves required to fit the carpet into the box.


**Expected Time Complexity:** `O(max( log(a), log(b) ))`              
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
A = 8, B = 13
C = 6, D = 10
Output:
Minimum number of moves: 1
Explanation:
Fold the carpet by breadth, 13/2 i.e. 6, 
so now carpet is 6*8 and can fit fine.
```

**Example 2:**   
```
Input:
A = 4, B = 8
C = 3, D = 10
Output:
Minimum number of moves: 1
Explanation: Fold the carpet by length , 4/2 i.e. 2,
so now carpet is 2*8 and can fit fine.
```

### Constraints

+ `1<= A,B,C,D <= 10^9`


## Solutions

```cpp

class Solution{
    public:
    int carpetBox(int A, int B, int C, int D){
        //code here
        int normal = 0, rotated = 0;
        int a=A,b=B;
        while(A>C) {
            A/=2;
            normal++;
        }
        while(B>D) {
            B/=2;
            normal++;
        }
        A=b,B=a;
        while(A>C) {
            A/=2;
            rotated++;
        }
        while(B>D) {
            B/=2;
            rotated++;
        }
        
        return min(normal, rotated);
    }
};

```

