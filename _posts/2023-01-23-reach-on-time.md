---
layout: post
title: Reach on Time                        
summary:
tags:
    - codechef
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://www.codechef.com/problems/TIMELY?tab=statement)  

Chef has recently moved into an apartment. It takes 30 minutes for Chef to reach office from the apartment.

Chef left for the office X minutes before Chef was supposed to reach. Determine whether or not Chef will be able to reach on time.
 

**Input Format:**

+ The first line contains an integer T, the number of test cases. Then the test cases follow.
+ Each test case consists of a single integer X.


**Output Format:**

For each test case, output YES if Chef will reach on time, NO otherwise.

The output is case-insensitive. Thus, the strings YES, yes, yeS, and Yes are all considered the same.

### Examples

**Example 1:**   
```
Input :
6
30
60
14
29
31
42

Output :
YES
YES
NO
NO
YES
YES

Explanation :
Test Case 1: Chef leaves 30 minutes before he is supposed to reach, so he will reach the office exactly on time since it takes 30 minutes to commute.

Test Case 2: Chef leaves 60 minutes before he is supposed to reach, so he will reach the office exactly on time since it takes 30 minutes to commute. 

Test Case 3: Chef leaves 14 minutes before he is supposed to reach, so he will not reach the office on time since it takes 30 minutes to commute.	

Test Case 4: Chef leaves 29 minutes before he is supposed to reach, so he will not reach the office on time since it takes 30 minutes to commute.

Test Case 5: Chef leaves 31 minutes before he is supposed to reach, so he will reach the office on time since it takes 30 minutes to commute.

Test Case 6: Chef leaves 42 minutes before he is supposed to reach, so he will reach the office on time since it takes 30 minutes to commute.

```

### Constraints

+ `1 ≤ T ≤ 60`
+ `1 ≤ X ≤ 60`

## Solutions

```cpp
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
int MOD = 1e9+7;

/* OBSERVATION
+ If the time he has is greater than or equal to 30 then the chef can reach the apartment, else can't.
*/

/* CODE
INPUT: X
OUTPUT: if(X<30) => NO, else => YES
*/
string solution(int X) {
    return X<30 ? "NO" :"YES";
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

