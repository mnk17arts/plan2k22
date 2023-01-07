---
layout: post
title: Merging Details                   
summary:
tags:
    - disjoint-set
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/merging-details/1)  

Bob, a teacher of St. Joseph School given a task by his principal to merge the details of the students where each element details[i] is a list of strings, where the first element details[i][0] is a name of the student, and the rest of the elements are emails representing emails of the student.   Two details definitely belong to the same student if there is some common email to both detail.  After merging the details, return the details of the student in the following format: the first element of each detail is the name of the student, and the rest of the elements are emails in sorted order. The details themselves can be returned in any order.  Note: Two details have the same name, they may belong to different people as people could have the same name. A person can have any number of details initially, but all of their details definitely have the same name.

**Your Task:** 

You don't need to read or print anything. Your task is to complete the function mergeDetails() which takes 2D List of string details denoting the details of the students and returns the list of strings denoting the details of student after merging.


**Expected Time Complexity:** `O(N*M*logN)` - where N is the size of details length and M is the size of number of strings for a name.              
**Expected Auxiliary Space:** `O(N*M)` - where N is the size of details length and M is the size of number of strings for a name.


### Examples

**Example 1:**   
```
Input: 
n: 4
details = 
[["John","johnsmith@mail.com","john_newyork@mail.com"],
["John","johnsmith@mail.com","john00@mail.com"],
["Mary","mary@mail.com"],
["John","johnnybravo@mail.com"]]
Output: 
[["John","john00@mail.com","john_newyork@mail.com",
"johnsmith@mail.com"],["Mary","mary@mail.com"],
["John","johnnybravo@mail.com"]]
Explanation:
The first and second John's are the same person as 
they have the common email "johnsmith@mail.com".
The third John and Mary are different people as none
of their email addresses are used by other accounts.
We could return these lists in any order, for example
the answer [['Mary', 'mary@mail.com'], 
['John', 'johnnybravo@mail.com'], 
['John', 'john00@mail.com', 'john_newyork@mail.com', 
'johnsmith@mail.com']] 
would still be accepted.
```

**Example 2:**   
```
Input: 
n: 5
details = 
[["Gabe","Gabe0@m.co","Gabe3@m.co","Gabe1@m.co"],["Kevin","Kevin3@m.co","Kevin5@m.co","Kevin0@m.co"],["Ethan","Ethan5@m.co","Ethan4@m.co","Ethan0@m.co"],["Hanzo","Hanzo3@m.co","Hanzo1@m.co","Hanzo0@m.co"],["Fern","Fern5@m.co","Fern1@m.co","Fern0@m.co"]]
Output: 
[["Ethan","Ethan0@m.co","Ethan4@m.co","Ethan5@m.co"],["Gabe","Gabe0@m.co","Gabe1@m.co","Gabe3@m.co"],["Hanzo","Hanzo0@m.co","Hanzo1@m.co","Hanzo3@m.co"],["Kevin","Kevin0@m.co","Kevin3@m.co","Kevin5@m.co"],["Fern","Fern0@m.co","Fern1@m.co","Fern5@m.co"]]
Explanation:
We don't have any common emails in any of the users.
We just sorted the emails of each person and we
return a list of the emails.(The details can be
returned in any order).
```

### Constraints

+ `1 <= details.length <= 1000`
+ `2 <= details[i].length <= 10`
+ `1 <= details[i][j].length <= 30`
+ details[i][0] consists of English letters.
+ details[i][j] (for j > 0) is a valid email

## Solutions

```cpp
class Solution {
  public:
    vector<vector<string>> mergeDetails(vector<vector<string>>& details) {
        // code here
        map<string, int> mp;
        vector<pair<string, set<string>>> v;
        for(auto &i: details){
            int p = -1;
            for(auto j=i.begin()+1; j!=i.end(); j++){
                if(mp.find(*j)!=mp.end()){
                    p = mp[*j];
                    break;
                }
            }
            if(p==-1) p = v.size(), v.push_back(make_pair(i[0], set<string>()));
            for(auto j=i.begin()+1; j!=i.end(); j++){
                v[p].second.insert(*j);
                mp[*j] = p;
            }
        }
        vector<vector<string>> ans(v.size());
        for(int i=0; i<v.size(); i++){
            ans[i].push_back(v[i].first);
            ans[i].insert(ans[i].end(), v[i].second.begin(), v[i].second.end());
        }
        sort(ans.rbegin(), ans.rend());
        return ans;
    }
};
```

