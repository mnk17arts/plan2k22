---
layout: post
title: The Number of Weak Characters in the Game                       
summary:
tags:
    - leetcode
    - array
    - stack
    - greedy
    - sorting
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/the-number-of-weak-characters-in-the-game/description/)  

You are playing a game that contains multiple characters, and each of the characters has two main properties: attack and defense. You are given a 2D integer array `properties` where `properties[i] = [attacki, defensei]` represents the properties of the `ith` character in the game.

A character is said to be weak if any other character has both attack and defense levels strictly greater than this character's attack and defense levels. More formally, a character `i` is said to be weak if there exists another character `j` where `attackj > attacki` and `defensej > defensei`.

Return the number of weak characters.


### Examples


**Example 1:**   
```
Input: properties = [[5,5],[6,3],[3,6]]
Output: 0
Explanation: No character has strictly greater attack and defense than the other.
```


**Example 2:**   
```
Input: properties = [[2,2],[3,3]]
Output: 1
Explanation: The first character is weak because the second character has a strictly greater attack and defense.
```

**Example 3:**   
```
Input: properties = [[1,5],[10,4],[4,3]]
Output: 1
Explanation: The third character is weak because the second character has a strictly greater attack and defense.
```


### Constraints

+ `2 <= properties.length <= 10^5`
+ `properties[i].length == 2`
+ `1 <= attacki, defensei <= 10^5`

## Solutions

```cpp

    class Solution {
    public:
        static bool sort2(const vector<int> &a, const vector<int> &b){
            if(a[0]!=b[0])
                return a[0]>b[0];
            return a[1] < b[1];
        }
        int numberOfWeakCharacters(vector<vector<int>>& p) {
            sort(p.begin(),p.end(),sort2);
            int maxV = INT_MIN;
            int res=0;
            for(auto i: p){
                if(maxV > i[1]) res++;
                else maxV = i[1];
            }
            return res;
        }
};
```

