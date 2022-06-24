---
layout: post
title: Convert a sentence into its equivalent mobile numeric keypad sequence   
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/convert-a-sentence-into-its-equivalent-mobile-numeric-keypad-sequence0547/1#)  

Given a sentence in the form of a string in uppercase, convert it into its equivalent mobile numeric keypad sequence.   
<img src="https://contribute.geeksforgeeks.org/wp-content/uploads/Phone.png">

**Your Task:** 
You dont need to read input or print anything. Complete the function `printSequence()` which takes a string as input parameter and returns its equivalent mobile numeric keypad sequence as a string.
**NOTE** : Characters of string can be empty space or capital alphabets.


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
S = "GFG"
Output: 43334
Explanation: For 'G' press '4' one time.
For 'F' press '3' three times.
```

**Example 2:**   
```
Input:
S = "HEY U"
Output: 4433999088
Explanation: For 'H' press '4' two times.
â€‹For 'E' press '3' two times. For 'Y' press '9' 
three times. For white space press '0' one time.
For 'U' press '8' two times.
```


### Constraints

+ `1 <= N <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    string printSequence(string S)
    {
        //code here.
        string s[26] = {
            "2","22","222","3","33","333","4","44","444","5","55","555","6","66","666","7","77","777","7777","8","88","888","9","99","999","9999"};
        string res="";
        for(char c: S)
            if(c==' ') res+='0';
            else res += s[c-'A'];
        return res;
    }
};
```

