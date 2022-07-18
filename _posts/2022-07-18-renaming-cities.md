---
layout: post
title: Renaming Cities                    
summary:
tags:
    - trie
    - string
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/renaming-cities28581833/0/?tra#)  

Some cities are going to be renamed and accordingly name of their railway stations will also change. Changing the name of railway station should also result in changed station code. Railways have an idea that station code should be the shortest prefix out of all railway stations renamed prior to this. If some city has same name, then prefix will be the name with suffix as the count of occurence of that city prior to this and including this, seperated with spaces.

Given `N` renamed cities consisting of lowercase alphabets only. The task is to generate a station ID for all the stations.

**Your Task:** 

Complete `check` function which takes array of strings and number of string '`n`' as arguments and print the require answer in the function itself. You have to provide new line in the function itself.


**Expected Time Complexity:** `O(N * WORD_LEN)`              
**Expected Auxiliary Space:** `O(N * WORD_LEN)`



### Examples

**Example 1:**   
```
Input:
N = 6
Cities[] = {shimla,safari,jammu,delhi,
                jammu,dehradun}
Output:
s
sa
j
d
jammu 2
deh
Explanation: Till shimla, no stations are there.
So, it's first character will be the unique
smallest prefix. For safari, first character of
shimla matches, so unique smallest prefix is sa
Similarly, j is smallest unique prefix for jammu
and d is for delhi. For last city jammu, we have
countered jammu before, and therefor no smallest
prefix is possible. So, we can generate its code
as jammu with suffix equal to the count of jammu,
i.e, 2. Smallest unique prefix is jammu2. Now,
delhi can be renamed as d, and dehradun can be
renamed as deh, since deh is the smallest non
matching prefix. 
```

### Constraints

+ `1 ≤ N <= 10^6`
+ `1 <= Word Length <= 100`

## Solutions

```cpp
// arr : array of strings
// n : count of the number of strings in the array
class Solution
{
    public:

    void insert(string str, Node* root){
        string res = "";
        Node* cur = root;
        bool flag = false;
        for(char c: str){
            if(!flag) res+=c;
            if(cur->mp.find(c)==cur->mp.end()){
                flag = true;
                cur->mp[c] = newNode();
            }
            cur = cur->mp[c];
        }
        if(cur->isEndOfWord) cout << res << " " << cur->count1+1 <<endl;
        else cout << res << endl;
        cur->isEndOfWord = true;
        cur->count1++;
    }

    void check(string *arr, int n){
    //code here
    Node* root = newNode();
        for(int i=0;i<n;i++){
            insert(arr[i],root);
        }
    }

};

```

