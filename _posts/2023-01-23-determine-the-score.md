---
layout: post
title: Determine the Score                        
summary:
tags:
    - codechef
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://www.codechef.com/problems/DETSCORE?tab=statement)  

Chef appeared for a placement test.

There is a problem worth X points. Chef finds out that the problem has exactly 10 test cases. It is known that each test case is worth the same number of points.

Chef passes N test cases among them. Determine the score Chef will get.

NOTE: See sample explanation for more clarity.
 

**Input Format:**

+ The first line contains an integer T, the number of test cases. Then the test cases follow.
+ Each test case contains of a single line of input, two integers X and N, the total points for the problem and the number of test cases which pass for Chef's solution.


**Output Format:**

For each test case, output the points scored by Chef.

### Examples

**Example 1:**   
```
Input :
4
10 3
100 10
130 4
70 0

Output :
3
100
52
0

Explanation :
Test Case 1: The problem is worth 10 points and since there are 10 test cases, each test case is worth 1 point. Since Chef passes 3 test cases, his score will be 1⋅3=3 points.

Test Case 2: The problem is worth 100 points and since there are 10 test cases, each test case is worth 10 points. Since Chef passes 10 test cases, his score will be 10⋅10=100 points.

Test Case 3: The problem is worth 130 points and since there are 10 test cases, each test case is worth 13 points. Since Chef passes 4 test cases, his score will be 13⋅4=52 points.	

Test Case 4: The problem is worth 70 points and since there are 10 test cases, each test case is worth 7 points. Since Chef passes 0 test cases, his score will be 7⋅0=0 points.

```

### Constraints

+ `1 ≤ T ≤ 100`
+ `10 ≤ X ≤ 200`
+ `0 ≤ N ≤ 10`
+ `X` is divisible by `10`

## Solutions

```cpp
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
int MOD = 1e9+7;

/* OBSERVATION
-> Given total no. of testcases are 10.
-> Therefore each testcase have X/10.
-> Points scored by chef will be equal to N*(X/10).
*/

/* CODE
input : X, N 
output : N*(X/10)
*/
int solution(int X, int N) {
    return N*(X/10);
}

int main() {

	int T; cin >> T;
	int X,N;
	while(T--) {
	    cin >> X >> N;
	    auto res = solution(X, N);
	    cout << res << endl;
	}
	return 0;
}

```

