---
layout: post
title: Antique Collections
summary:
tags:
  - geeksforgeeks
  - array
  - hash
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-98/problems/#)

Geeky had developed a deep interest in antique items and was determined to acquire them all. However, as he started visiting different shops, he realized that the same antique item was being sold at different prices by different vendors.Geeky knew that he had to be smart with his purchases if he wanted to save money and acquire all the different types of antique items in the market.

He created two arrays of size n called items[] and prices[]. Each item at index i in the items[] array had a corresponding price at index i in the prices[] array.Can you help Geeky find his minimum budget to get all the different types of antique items from the market?

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function antiqueItems() which takes one integers n and two arrays called items[] and price[] of size n recpectively as input parameters and  returns an integer representing the minimum cost to buy all different types of antique items from the market.

### Examples

**Example 1:**

```
Input :
n=4
items={1,2,2,3}
price={3,4,5,6} 

Output : 
13 

Explanation :
item 1 is having a price : 3
item 2 and item 3 is same so we have taken item 
2 to have money, hence item 2 having a price : 4 
item 4 is having a price : 6 
total price = 3 + 4 + 6 = 13 
```

**Example 2:**

```
Input : 
n=1
items={2}
price={4}

Output : 
4

Explanation :
Only one Item 1 is having  price : 4
total price is 4
```

### Constraints

- `1 <= n <= 10^6`
- `1 <= items[i] <= 10^3`
- `1 <= prices[i] <= 10^3`

## Solutions

```cpp


class Solution {
  public:
    int antiqueItems(int n, vector<int> &items, vector<int> &price) {
        // code here
        unordered_map<int, int> map;
        for(int i = 0; i < n; i++) {
            if(map.find(items[i]) == map.end()) {
                map[items[i]] = price[i];
            }
            else {
                map[items[i]] = min(map[items[i]], price[i]);
            }
        }
        int res = 0;
        for(auto it: map) {
            res += it.second;
        }
        return res;
    }
};


```
