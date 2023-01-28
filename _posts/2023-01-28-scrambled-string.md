---
layout: post
title: Scrambled String                     
summary:
tags:
    - geeksforgeeks
    - string
    - heap
    - recursion
    - cpp
    - hard
minute: 15+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/scrambled-string/1)  

Given two strings S1 and S2 of equal length, the task is to determine if S2 is a scrambled form of S1.

Scrambled string: Given string str, we can represent it as a binary tree by partitioning it into two non-empty substrings recursively.
Below is one possible representation of str = coder:

<img src="data:image/png;base64,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">

To scramble the string, we may choose any non-leaf node and swap its two children. 
Suppose, we choose the node co and swap its two children, it produces a scrambled string ocder.
Similarly, if we continue to swap the children of nodes der and er, it produces a scrambled string ocred.

Note: Scrambled string is not the same as an Anagram.

Print "Yes" if S2 is a scrambled form of S1 otherwise print "No".

**Your Task:** 

You don't need to read input or print anything. You only need to complete the function isScramble() which takes two strings S1 and S2 as input and returns a boolean value.



**Expected Time Complexity:** `O(N*N)`              
**Expected Auxiliary Space:** `O(N*N)` 



### Examples

**Example 1:**   
```
Input: S1="coder", S2="ocder"
Output: Yes
Explanation: ocder is a scrambled 
form of coder.

    ocder
   /    \
  oc    der
 / \    
o   c  

As "ocder" can represent it 
as a binary tree by partitioning 
it into two non-empty substrings.
We just have to swap 'o' and 'c' 
to get "coder".
```

**Example 2:**   
```
Input: S1="abcde", S2="caebd" 
Output: No
Explanation: caebd is not a 
scrambled form of abcde.
```

### Constraints

+ `S1.length = S2.length`
+ `S1.length <= 31`
+ `S1 and S2 contain lower case English alphabets`

## Solutions

```cpp

class Solution{
    public:
    unordered_map<string, bool> m;
    bool isScramble(string S1, string S2){
        //code here
        if( S1==S2 ) return true;
        int n = S1.length();
        if( n <= 1 ) return false;
        string cur = S1 + " " + S2;
        if( m.find(cur) != m.end() ) {
            return m[cur];
        }
        bool ans = false;
        for( int i=1; i<n; i++ ) {
            if((isScramble( S1.substr(0, i), S2.substr(0, i) ) && isScramble( S1.substr(i, n-i), S2.substr(i, n-i)))
            || ((isScramble( S1.substr(0, i), S2.substr(n-i,i)) && isScramble( S1.substr(i, n-i), S2.substr(0, n-i))))) {
                ans = true;
                break;
            }
        }
        return m[cur]=ans;
    }    
};

```

