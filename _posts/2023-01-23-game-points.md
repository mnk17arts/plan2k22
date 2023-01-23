---
layout: post
title: Game Points                       
summary:
tags:
    - codechef
    - math
    - cpp
    - easy
minute: 10+ min
---

## Problem Statement - [*link*](https://www.codechef.com/problems/D22001?tab=statement)  

A group of children divided themselves into 2 groups, A and B. They are playing a game. The game is played on a court of length L with a target to goal more than the other team. If the goal is done from a distance less than z from either side of the court, the team gets m points, otherwise they get n points with m < n. No player can goal from a distance greater than or equal to half the court length from their opponent's goal. That means that if a goal happens from middle of the court no points would be given to any team. Given that the p are the total number of goals in the match and the distance from (Team A's defending basket) from which a goal happened. Print the name of the team that one the match. Assume no self goals happen.
 

**Input Format:**

+ The first line contains an integer T, the number of test cases. Then the test cases follow.
+ Each test case consists of multiple lines of input.
    + The first line of each test case contains five integer L, z, m, n, p.
    + The next p lines contain a single integer, the distance from the team A's defending basket from which a goal happened.


**Output Format:**

For each test case, output in a single line the name of the team that won the match. If the match is a draw, output "TIE".

### Examples

**Example 1:**   
```
Input :
1
100 5 30 2 4
10
25
80
60
50

Output :
A

Explanation :
1st goal scored by B and they get 2 points 2nd goal scored by B and they get 2 points 3rd goal scored by A and they get 2 points 4th goal scored by A and they get 4 points 5th goal is scored from distance L/2 hence no one gets the score
```

### Constraints

+ `1 ≤ T ≤ 100`
+ `1 ≤ L ≤ 1000`
+ `1 ≤ z ≤ L/2`
+ `1 ≤ m,n ≤ 1000`
+ `1 ≤ p ≤ 100`
+ `0 ≤ distance from the goal ≤ L`

## Solutions

```cpp

#include <iostream>
#include <vector>
using namespace std;

int game(int l, int p, int z, int m, int n) {
    vector<int> v(p);
    for(int i=0;i<p;i++) {
        cin >> v[i];
    }
    int as = 0, bs = 0;
    int mid = l/2;
    for(int i: v) {
        if(i < mid) {
            // B goals
            if(i < z) {
                bs += m;
            }
            else {
                bs += n;
            }
        }
        else if(i > mid) {
            // A goals
            if( l-i < z) {
                as += m;
            }
            else {
                as += n;
            }
        }
    }
    if(as==bs) return -1;
    else if(as>bs) return 1;
    else return 0;
    
}

int main() {
	// your code goes here
	int T;
	cin >> T;
	int l,p,z,m,n, res;
	while(T--) {
	    cin >> l >> p >> z >> m >> n;
	    res = game(l,p,z,m,n);
	    if(res==1) cout << "A" << endl;
	    else if(res==0) cout << "B" << endl;
	    else cout << "TIE" << endl;
	}
	return 0;
}


```

