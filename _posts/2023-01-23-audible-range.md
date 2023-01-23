---
layout: post
title: Audible Range                        
summary:
tags:
    - codechef
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://www.codechef.com/problems/AUDIBLE?tab=statement)  

Chef's dog binary hears frequencies starting from 67 Hertz to 45000 Hertz (both inclusive).

If Chef's commands have a frequency of X Hertz, find whether binary can hear them or not. 

**Input Format:**

+ The first line contains an integer T, the number of test cases. Then the test cases follow.
+ Each test case consists of a single integer X - the frequency of Chef's commands in Hertz.


**Output Format:**

For each test case, output on a new line YES, if binary can hear Chef's commands. Otherwise, print NO.

The output is case-insensitive. Thus, the strings YES, yes, yeS, and Yes are all considered the same.

### Examples

**Example 1:**   
```
Input :
5
42
67
402
45000
45005

Output :
NO
YES
YES
YES
NO

Explanation :
Test Case 1: Chef's command has a frequency of 42 Hertz which is less than 67. Thus, it would not be audible to binary.

Test Case 2: Chef's command has a frequency of 67 Hertz which is equal to 67. Thus, it would be audible to binary.

Test Case 3: Chef's command has a frequency of 402 Hertz which is greater than 67. Thus, it would be audible to binary.

Test Case 4: Chef's command has a frequency of 45000 Hertz which is equal to 45000. Thus, it would be audible to binary.

Test Case 5: Chef's command has a frequency of 45005 Hertz which is greater than 45000. Thus, it would not be audible to binary.

```

### Constraints

+ `1 ≤ T ≤ 10000`
+ `1 ≤ X ≤ 1000000`

## Solutions

```cpp
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
int MOD = 1e9+7;

/* OBSERVATION
+ The dog hears frequencies from 67 to 45000 Hertz.
+ Anything between this range is audible to the dog
*/

/* CODE
INPUT: X
OUTPUT: if( 67 <= X <= 45000 ) => YES , else => NO
*/
string solution(int X) {
    return (67<=X && X<=45000) ? "YES" : "NO";
}

int main() {

	int T; cin >> T;
	int x;
	while(T--) {
	    cin >> x;
	    auto res = solution(x);
	    cout << res << endl;
	}
	return 0;
}

```

