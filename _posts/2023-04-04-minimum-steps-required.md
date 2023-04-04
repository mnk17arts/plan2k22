---
layout: post
title: Minimum Steps Required
summary:
tags:
  - geeksforgeeks
  - string
  - cpp
  - medium
minute: 8+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/6a1b365b520f10c8a29b533eb72951b4b4237b57/1)

Given a string str consisting of only two characters 'a' and 'b'. You need to find the minimum steps required to make the string empty by removing consecutive a's and b's

**Your Task:**

You need to complete the function minSteps() which takes a string str as the only input parameter and returns an integer, denoting the minimum steps required to make the string empty.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
str = "bbaaabb"
Output:
2
Explanation:
Operation 1: Removal of all a's modifies str to "bbbb".
Operation 2: Removal of all remaining b's makes str
empty.
Therefore, the minimum number of operations required
is 2.
```

**Example 2:**

```
Input:
str = "aababaa"
Output:
3
Explanation:
Operation 1: Removal of b's modifies str to "aaabaa".
Operation 2: Removal of b's modifies str = "aaaaa".
Operation 3: Removal of all remaining a's makes str 
empty.
Therefore, the minimum number of operations required 
is 3.
```

### Constraints

- `1 <= str.length() ≤ 10^5`
- `'a' <= str[i] <= 'b'`

## Solutions

```cpp

class Solution {
  public:
  int minSteps(string str) {
      // Write your code here.
      int a = 0,b=0,ans=0;
      if(str[0] == 'a')
      a++;
      else
      b++;
      char last = str[0];
      for(int i=1;i<str.size();i++)
      {
          if(str[i] != last)
          {
              if(str[i] == 'a')
              a++;
              else
              b++;
          }
          last = str[i];
      }
      int mini = min(a,b);
      ans += mini +1;
      return ans;   
  }
};

```
