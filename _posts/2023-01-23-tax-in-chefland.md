---
layout: post
title: Tax in Chefland                        
summary:
tags:
    - codechef
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://www.codechef.com/problems/TAXES?tab=statement)  

In Chefland, a tax of rupees 10 is deducted if the total income is strictly greater than rupees 100.

Given that total income is X rupees, find out how much money you get.
 

**Input Format:**

+ The first line contains an integer T, the number of test cases. Then the test cases follow.
+ The first and only line of each test case contains a single integer X — your total income.


**Output Format:**

For each test case, output on a new line, the amount of money you get.

### Examples

**Example 1:**   
```
Input :
4
5
105
101
100

Output :
5
95
91
100

Explanation :
Test Case 1: Your total income is 5 rupees which is less than 100 rupees. Thus, no tax would be deducted and you get 5 rupees.

Test Case 2: Your total income is 105 rupees which is greater than 100 rupees. Thus, a tax of 10 rupees would be deducted and you get 95 rupees. 

Test Case 3: Your total income is 101 rupees which is greater than 100 rupees. Thus, a tax of 10 rupees would be deducted and you get 91 rupees.	

Test Case 4: Your total income is 100 rupees which is equal to 100 rupees. Thus, no tax would be deducted and you get 100 rupees.

```

### Constraints

+ `1 ≤ T ≤ 100`
+ `1 ≤ X ≤ 1000`

## Solutions

```cpp
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
int MOD = 1e9+7;

/* OBSERVATION
+ Chef have to tax only when the income is above 100.
+ So amount of money the chef gets depends on the income value.
+ If income is above 100 then chef gets income-10, else the gets total income.
*/

/* CODE
INPUT: X 
OUTPUT: if(X<=100) => X , else => X-100; 
*/
int solution(int X) {
    return X<=100 ? X : X-10;
}

int main() {

	int T; cin >> T;
	int X;
	while(T--) {
	    cin >> X;
	    auto res = solution(X);
	    cout << res << endl;
	}
	return 0;
}

```

