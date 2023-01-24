---
layout: post
title: Xenny and Coin Rank                        
summary:
tags:
    - codechef
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://www.codechef.com/problems/XENRANK?tab=statement)  

Xenny reverse-engineered all the binaries released by the International Security Agency (ISA) during summer vacation just to pass time. As a reward, the ISA gave him infinite ByteCoins.

Out of sheer boredom and a sense of purposelessness in life, Xenny decided to arrange the Coins on a 2-Dimensional Euclidean Plane. The boredom was so strong that he arranged these coins in a specific pattern, as opposed to the usual, monotonous way of storing coins in a Piggy Bank.

On each integer co-ordinate (x, y) where x ≥ 0 and y ≥ 0, a single coin was placed. And each coin was assigned a rank. The following pattern was followed in the arrangement:

Let's denote the co-ordinates of the kth coin by (xk, yk) and its rank by Rk.

<img src="https://docs.google.com/drawings/d/11xOeiWc_yhJz9WxoLddlTWO872Hel8of6atHHhWD2-Q/pub?w=475&h=422" /> 

For any 2 coins i, j:

if (xi + yi) < (xj + yj) or ( (xi + yi) == (xj + yj) and xi < xj)

then Ri < Rj. We sort all the coins by this comparison.

The index of the coin (C) in this sorted list of coins (1-indexed) is its rank.

Each query is as follows: Given (U, V). Among the coins that are lying on or inside the rectangle with its diagonal end-points being (0, 0) and (U, V), which is the coin that has the maximum rank?

**Input Format:**

+ The first line contains an integer, T - the number of testcases.

+ Each testcase contains 2 space-separated integers: U, V.


**Output Format:**

For each testcase, print the rank of the maximum ranked coin, on a new line.

### Examples

**Example 1:**   
```
Input :
1
1 2

Output :
8

Explanation :
.
. .
(0 2)4 (1 2)8
(0 1)2 (1 1)5 .
(0 0)1 (1 0)3 . .

```

### Constraints

**Subtask 1: (40 points)**
+ `1 ≤ T ≤ 100`
+ `1 ≤ U,V ≤ 1000`

**Subtask 2: (60 points)**
+ `1 ≤ T ≤ 100`
+ `1 ≤ U,V ≤ 10^9`

## Solutions

```cpp
#include <iostream>
using namespace std;

#define ll long long

ll solve(ll u, ll v) {
    ll res = u + v;
    res = res*(res+1)/2;
    res += (u + 1);
    return res;
}

int main() {
	// your code goes here
	int t;
	cin >> t;
	ll u,v;
	while(t--) {
	    cin >> u >> v;
	    auto res = solve(u, v);
	    cout << res << endl;
	}
	return 0;
}

```

