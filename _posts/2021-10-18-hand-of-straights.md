---
layout: post
title:  Hand of Straights
description: 
summary: 
tags:
    - array
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/hand-of-straights/)
Alice has some number of cards and she wants to rearrange the cards into groups so that each group is of size groupSize, and consists of `groupSize` consecutive cards.

Given an integer array hand where `hand[i]` is the value written on the `ith` card and an integer `groupSize`, return *`true` if she can rearrange the cards, or `false` otherwise.*


### Examples   

**Example 1:**  
```
Input: hand = [1,2,3,6,2,3,4,7,8], groupSize = 3
Output: true
Explanation: Alice's hand can be rearranged as [1,2,3],[2,3,4],[6,7,8]
```

**Example 2:**  
```
Input: hand = [1,2,3,4,5], groupSize = 4
Output: false
Explanation: Alice's hand can not be rearranged into groups of 4.
```

### Constraints
+ `1 <= hand.length <= 10^4`
+ `0 <= hand[i] <= 10^9`
+ `1 <= groupSize <= hand.length`

**Note:** This question is the same as 1296: [https://leetcode.com/problems/divide-array-in-sets-of-k-consecutive-numbers/](https://leetcode.com/problems/divide-array-in-sets-of-k-consecutive-numbers/)

## Solutions

```cpp
class Solution {
public:
    bool isNStraightHand(vector<int>& hand, int groupSize) {
        
        if(hand.size()%groupSize) return false;
        
        map<int, int> mp;
        sort(hand.begin(), hand.end());
        
        for(int i: hand)
            mp[i]++;            

        while(mp.size()){
            auto m = mp.begin();
            for(int i=1; i<groupSize; i++){
                
                int _m = m->first+i;
                
                if(mp.find(_m)==mp.end()) return false;
                
                int f = m->second;
                
                int _f = mp[_m];
                
                if(_f < f) return false;
                
                if(_f == f) mp.erase(_m);
                else mp[_m] -= f;
                
            }
            mp.erase(m->first);
        }

        return mp.size()==0;
    }
};
```

