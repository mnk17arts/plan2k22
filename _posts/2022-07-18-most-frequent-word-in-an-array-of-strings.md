---
layout: post
title: Most frequent word in an array of strings                      
summary:
tags:
    - trie
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/most-frequent-word-in-an-array-of-strings3528/0/?tr)  

Given an array arr containing `N` words consisting of lowercase characters. Your task is to find the most frequent word in the array. If multiple words have same frequency, then print the word whose first occurence occurs last in the array as compared to the other strings with same frequency.

**Your Task:** 

Complete `mostFrequentWord` function which takes array of strings and its length as arguments and returns the most frequent word. The printing is done by the driver code.


**Expected Time Complexity:** `O(N * WORD_LEN)`              
**Expected Auxiliary Space:** `O(N * WORD_LEN)`



### Examples

**Example 1:**   
```
Input:
N = 3
arr[] = {geeks,for,geeks}
Output: geeks
Explanation: "geeks" comes 2 times.
```

**Example 2:**
```
Input:
N = 2
arr[] = {hello,world}
Output: world
Explanation: "hello" and "world" both
have 1 frequency. We print world as
its first occurence comes last in the
input array.
```

### Constraints

+ `1 ≤ N <= 5*10^4`
+ `1 <= |each string| <= 50`
+ `Sum of length of every string does not exceed 5*10^5`

## Solutions

```cpp
class Solution
{
    public:
    struct node{
        node* next[26];
        int c;
        int f;
        node(){
            c = 0;
            f = 0;
            for(int i=0;i<26;i++)
                next[i]=NULL;
        }
    };
    //Function to find most frequent word in an array of strings.
    string mostFrequentWord(string arr[], int n) 
    {
        // code here
        string res = "";
        int count = 0;
        int f2 ;
        node* root = new node();
        for(int i=0;i<n;i++){
            node* temp = root;
            for(int j=0;j<arr[i].length();j++){
                int id = arr[i][j]-'a';
                if(temp->next[id]==NULL)
                    temp->next[id] = new node();
                temp = temp->next[id];
            }
            temp->c++;
            if(temp->c==1)
                temp->f = i;
            if(temp->c > count || temp->c==count&& temp->f > f2){
                res = arr[i];
                count = temp->c;
                f2 = temp->f;
            }
        }
        return res;
    }
};
```

