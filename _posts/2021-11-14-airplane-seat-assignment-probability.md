---
layout: post
title: Airplane Seat Assignment Probability
description: 
summary:
tags:
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/airplane-seat-assignment-probability)  

`n` passengers board an airplane with exactly `n` seats. The first passenger has lost the ticket and picks a seat randomly. But after that, the rest of passengers will:

+ Take their own seat if it is still available, 
+ Pick other seats randomly when they find their seat occupied 

What is the probability that the `n`-th person can get his own seat?

### Examples

**Example 1:**    
```
Input: n = 1
Output: 1.00000
Explanation: The first person can only get the first seat.
```

**Example 2:**    
```
Input: n = 2
Output: 0.50000
Explanation: The second person has a probability of 0.5 to get the second seat (when first person gets the first seat).
```

### Constraints
+ `1 <= n <= 10^5`

## Solutions

```cpp
class Solution {
public:
    double nthPersonGetsNthSeat(int n) {
      return n==1 ? 1.00000 : 0.50000;
    }
};
```


### Explanation
```
First person choosing first seat = 1/n (This case everybody will get their allotted seat)
First person choosing second seat = 1/n
Now we have n-1 seats for the second person and if he chooses the first seat everybody else will get their allotted seat. So this is now a sub-problem of the first problem even though orginal seat of second person is taken, if and only if he takes the seat of the first person then only everyone else will get their allotted seat, which in turn can be seen as the allotted seat for the second person in the sub-problem.
So if first person chooses second seat P(nth person getting his seat) = 1/n * f(n-1) ----(1)
Now if the first person chooses the 3rd seat the second person would choose his own seat and when the 3rd person comes in he will have (n-2) seats to choose,
then P(nth person getting his seat) = 1/n * f(n-2)
.
.
if first person chooses last seat P = 1/n * f(n-n) = 0

f(0) = 0
f(1) = 1
	Total probabilty,  f(n) = 1/n + 1/n * f(n-1) + 1/n * f(n-2) + 1/n * f(n-3)......... + 1/n* f(0) --------(2)

Let's use induction to solve this eq:
	f(n+1) = 1/n+1 + 1/n+1 * (f(n) + ...... + 1/n+1 * f(0) ----(3)
	f(n) = 1/n + 1/n * f(n-1) + ..... + 1/n * f(0) ------(4)
	(3) - (4) = (n+1)*f(n+1) - n*f(n) = f(n)
				(n+1)*f(n+1) = (n+1)*f(n)
				f(n+1) = f(n) --- (5)

Using (5) in (2)
		let f(n) = k
		k * n = 1 + k + ........+ 0
		k * n = 1 + (n-2) * k , for n >1
		k = 0.5
```
