---
layout: post
title: LCM hates GCD                        
summary:
tags:
    - codechef
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://www.codechef.com/problems/LCM_GCD?tab=statement)  

Chef has two integers A and B.
Chef wants to find the minimum value of lcm(A,X)−gcd(B,X) where X is any positive integer.

Help him determine this value.


**Input Format:**

+ The first line contains an integer, T - the number of testcases.

+ Each testcase contains 2 space-separated integers: A, B.


**Output Format:**

For each testcase, print the rank of the maximum ranked coin, on a new line.

### Examples

**Example 1:**   
```
Input :
3
12 15
5 50
9 11

Output :
9
0
8

Explanation :
Test case 1: For X=6: lcm(12,6)−gcd(15,6)=12−3=9 which is the minimum value required.

Test case 2: For X=1: lcm(5,1)−gcd(50,1)=5−1=4 which is the minimum value required.

Test case 3: For X=2: lcm(9,2)−gcd(11,2)=9−2=7 which is the minimum value required.

```

### Constraints

+ `1 ≤ T ≤ 10^5`
+ `1 ≤ A, B ≤ 10^9`

## Solutions

```cpp
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
int MOD = 1e9+7;

/* OBSERVATION
-> We need to minimum value of lcm(A,X)-gcd(B,X).
-> So lcm must be minimum for this.
-> lcm of x,y is minimum when both are equal(x=y) and lcm=x.
-> So we take X as A for minimum result.
*/

/* CODE
INPUT: A, B
OUTPUT: A-gcd(A,B);
*/
int solution(int a, int b) {
    return a-__gcd(a,b);
}

int main() {

	int T; cin >> T;
	int a,b;
	while(T--) {
	    cin >> a >> b;
	    auto res = solution(a,b);
	    cout << res << endl;
	}
	return 0;
}

```

