---
layout: post
title: Sum of two large numbers                   
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/sum-of-numbers-or-number1219/1)  

Given two strings denoting non-negative numbers X and Y. Calculate the sum of X and Y. 

**Your Task:** 

Your task is to complete the function findSum() which takes two strings as inputs and returns the string without leading zeros. You do not need to take any input or print anything


**Expected Time Complexity:** `O(|X| + |Y|)`               
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
X = "25", Y = "23"
Output:
48
Explanation:
The sum of 25 and 23 is 48.
```

**Example 2:**   
```
Input:
X = "2500", Y = "23"
Output:
2523
Explanation:
The sum of 2500 and 23 is 2523.
```

### Constraints

+ `1 <= |X|, |Y| <= 10^5`

## Solutions

```cpp
class Solution {
  public:
    string findSum(string X, string Y) {
        // Your code goes here

        int n1=X.size(), n2=Y.size();
        int i=0;
        while(i<n1 && X[i]=='0') i++;
        if(i==n1) X = string(1,'0');
        else X = X.substr(i);
        i=0;
        while(i<n2 && Y[i]=='0') i++;
        if(i==n2) Y = string(1,'0');
        else Y = Y.substr(i);
        n1=X.size(), n2=Y.size();
        string a = (n1>=n2) ? X : Y;
        string b = (n1<n2) ? X : Y;
        int car = 0, j=b.size()-1, sum=0; i=a.size()-1;
        while(i>=0&&j>=0){
            sum = car + (a[i]-'0') + (b[j]-'0');
            car = sum/10;
            a[i] = ((sum%10)+'0');
            i--,j--;
        }
        if(j==-1) {
            while(i!=-1&&car>0){
                sum = (a[i]-'0') + car;
                car = sum/10;
                a[i] = (sum%10)+'0';
                i--;
            }
            if(car>0)
                a = string(1,car+'0') + a;
        }
        return a;
    }
};
```

