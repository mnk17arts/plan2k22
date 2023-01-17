---
layout: post
title: Invalid Transactions                       
summary:
tags:
    - leetcode
    - array
    - string
    - sorting
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/invalid-transactions/description/)  

A transaction is possibly invalid if:

+ the amount exceeds $1000, or;
+ if it occurs within (and including) 60 minutes of another transaction with the same name in a different city.


You are given an array of strings transaction where transactions[i] consists of comma-separated values representing the name, time (in minutes), amount, and city of the transaction.

Return a list of transactions that are possibly invalid. You may return the answer in any order.

### Examples


**Example 1:**   
```
Input: transactions = ["alice,20,800,mtv","alice,50,100,beijing"]
Output: ["alice,20,800,mtv","alice,50,100,beijing"]
Explanation: The first transaction is invalid because the second transaction occurs within a difference of 60 minutes, have the same name and is in a different city. Similarly the second one is invalid too.
```


**Example 2:**   
```
Input: transactions = ["alice,20,800,mtv","alice,50,1200,mtv"]
Output: ["alice,50,1200,mtv"]
```

**Example 3:**   
```
Input: transactions = ["alice,20,800,mtv","bob,50,1200,mtv"]
Output: ["bob,50,1200,mtv"]
```


### Constraints

+ `transactions.length <= 1000`
+ Each `transactions[i]` takes the form "`{name},{time},{amount},{city}`"
+ Each `{name}` and `{city}` consist of lowercase English letters, and have lengths between `1` and `10`.
+ Each `{time}` consist of digits, and represent an integer between `0` and `1000`.
+ Each `{amount}` consist of digits, and represent an integer between `0` and `2000`.

## Solutions

```cpp
class Solution {
public:
    vector<string> invalidTransactions(vector<string>& transactions) {
        int n = transactions.size();
        vector<string> city(n),name(n), time(n),money(n);
        for(int i=0;i<n;i++){
            stringstream ss(transactions[i]);
            getline(ss,name[i],',');
            getline(ss,time[i],',');
            getline(ss,money[i],',');
            getline(ss,city[i],',');                
        }
        vector<bool> vis(n);
        for(int i=0;i<n;i++){
            if(stoi(money[i])>1000)
                vis[i]=1;
        }

        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(i==j) continue;
                if( abs( stoi(time[i]) - stoi(time[j]) ) <= 60 ){
                    if(name[i]==name[j] && city[i]!=city[j]){
                        vis[i]=1;
                        vis[j]=1;
                    }
                }
            }
        }

        vector<string> res;
        for(int i=0;i<n;i++){
            if(vis[i]) res.push_back(transactions[i]);
        }

        return res;
    }
};
```

