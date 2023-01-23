---
layout: post
title: Fitness                        
summary:
tags:
    - codechef
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://www.codechef.com/problems/PRACLIST?tab=statement)  

CodeChef recently revamped its practice page to make it easier for users to identify the next problems they should solve by introducing some new features:

+ Recent Contest Problems - contains only problems from the last 2 contests
+ Separate Un-Attempted, Attempted, and All tabs
+Problem Difficulty Rating - the Recommended dropdown menu has various difficulty ranges so that you can attempt the problems most suited to your experience
+ Popular Topics and Tags

Our Chef is currently practicing on CodeChef and is a beginner. The count of ‘All Problems’ in the Beginner section is X. Our Chef has already ‘Attempted’ Y problems among them. How many problems are yet ‘Un-attempted’?
 

**Input Format:**

+ The first and only line of input contains two space-separated integers X and Y — the count of 'All problems' in the Beginner's section and the count of Chef's 'Attempted' problems, respectively.



**Output Format:**

Output a single integer in a single line — the number of problems that are yet 'Un-attempted'.

### Examples

**Example 1:**   
```
Input :
10 4

Output :
6

Explanation :
Test Case 1: There are 10 problems in total in the Beginner's section, out of which 4 have been attempted. Hence, there are 6 Un-attempted problems.

```

### Constraints

+ `1 ≤ Y <= X ≤ 1000`

## Solutions

```cpp
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
int MOD = 1e9+7;

int solution(int x, int y) {
    return abs(x-y);
}

int main() {
	// your code goes here
	int T; 
// 	cin >> T;
    T = 1;
	int x,y;
	while(T--) {
	    cin >> x >> y;
	    auto res = solution(x,y);
	    cout << res << endl;
	}
	return 0;
}


```

