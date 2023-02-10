---
layout: post
title: Balloon Everywhere
summary:
tags:
    - geeksforgeeks
    - map
    - string
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/45fa306a9116332ece4cecdaedf50f140bd252d4/1) 

Bob is very fond of balloons. Once he visited an amusement park with his mother. The mother told Bob that she would buy him a balloon only if he answer her problem right. She gave Bob a string S [contains only lowercase characters] and asked him to use the characters of string to form as many instances of the word "balloon" as possible. Return the maximum number of instances that can be formed.

Help Bob to solve the problem.

Note: You can use each character in the string at most once.

**Your Task:** 

The task is to complete the function maxInstance() which takes a string as the only input parameter and should return the maximum instances that can be formed of the word "balloon" using the given string.



**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(26)`  



### Examples

**Example 1:**   
```
Input:
S: nlaebolko
Output: 1
Explanation:
Here, the number of occurence of 'b' = 1
of occurence of 'a' = 1
of occurence of 'l' = 2
of occurence of 'o' = 2
of occurence of 'n' = 1
So, we can form 1 "balloon" using the letters.
```

**Example 2:** 
```
Input:
S: loonbalxballpoon
Output: 2
Explanation:
Here, the number of occurence of 'b' = 2
of occurence of 'a' = 2
of occurence of 'l' = 4
of occurence of 'o' = 4
of occurence of 'n' = 2
So, we can form 2 "balloon" using the letters.
```

### Constraints

+ `1 <= s.length <= 10^6`

## Solutions

```cpp

class Solution{
  public:
    int maxInstance(string s){
        unordered_map<char, int> map;
        string b = "balloon";
        for(char c: b) {
            map[c]=0;
        }
        for(char c: s) {
            if(map.find(c)!=map.end()){
                map[c]++;
            }
        }
        int res = INT_MAX;
        for(auto m: map){
            if(m.first == 'l' || m.first == 'o') {
                res = min(res, (m.second) / 2);
            }
            else {
                res = min(res, m.second);
            }
        }
        return res;
    }
};

```
