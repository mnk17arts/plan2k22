---
layout: post
title: Possible Words From Phone Digits  
summary:
tags:
    - recursion
    - array
    - string
    - math
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/possible-words-from-phone-digits-1587115620/1#)  

Given a keypad as shown in the diagram, and an `N` digit number which is represented by array `a[ ]`, the task is to list all words which are possible by pressing these numbers.    

<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/Mobile-keypad.png">

**Your Task:** 
You don't need to read input or print anything. You just need to complete the function `possibleWords()` that takes an array `a[ ]` and `N` as input parameters and returns an array of all the possible words in lexicographical increasing order. 

**Expected Time Complexity**: `O(4^N *N)`.   
**Expected Auxiliary Space:**   `O(N)`.


### Examples

**Example 1:**   
```
Input: N = 3, a[] = {2, 3, 4}
Output:
adg adh adi aeg aeh aei afg afh afi 
bdg bdh bdi beg beh bei bfg bfh bfi 
cdg cdh cdi ceg ceh cei cfg cfh cfi 
Explanation: When we press 2,3,4 then 
adg, adh, adi, ... cfi are the list of 
possible words.
```

**Example 2:**   
```
Input: N = 3, a[] = {3, 4, 5}
Output:
dgj dgk dgl dhj dhk dhl dij dik dil 
egj egk egl ehj ehk ehl eij eik eil 
fgj fgk fgl fhj fhk fhl fij fik fil
Explanation: When we press 3,4,5 then 
dgj, dgk, dgl, ... fil are the list of 
possible words.
```

### Constraints

+ `1 <= N <= 10`
+ `2 <= a[i] <= 9`

## Solutions

```cpp
class Solution
{
    public:
//Function to find list of all words possible by pressing given numbers.
    vector<string> phno = {"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
    void possibleWordsUtil(int a[],int n, int id,string s,vector<string> &ans)
    {
        if(n==id){
            ans.push_back(s);
            return;
        }
        int num=a[id];
        for(int i=0;i<phno[num].size();i++){
            s+=phno[num][i];
            possibleWordsUtil(a,n,id+1,s,ans);
            s.pop_back();
        }
    }    
    vector<string> possibleWords(int a[], int N)
    {
        //Your code here
        vector<string> ans;
        string s = "";
        possibleWordsUtil(a, N, 0, s, ans);
        return ans;
    }
};
```

