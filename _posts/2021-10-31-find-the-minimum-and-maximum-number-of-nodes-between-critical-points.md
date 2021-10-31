---
layout: post
title:  Find the Minimum and Maximum Number of Nodes Between Critical Points
description: 
summary: 
tags:
    - linkedlist
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/find-the-minimum-and-maximum-number-of-nodes-between-critical-points/)  
A **critical point** in a linked list is defined as **either** a **local maxima** or a **local minima**.

A node is a **local maxima** if the current node has a value **strictly greater** than the previous node and the next node.

A node is a **local minima** if the current node has a value **strictly smaller** than the previous node and the next node.

Note that a node can only be a local maxima/minima if there exists **both** a previous node and a next node.

Given a linked list `head`, return *an array of length 2 containing `[minDistance, maxDistance]` where `minDistance` is the **minimum distance** between any two distinct critical points and `maxDistance` is the **maximum distance** between any two distinct critical points. If there are fewer than two critical points, return `[-1, -1]`.*

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/10/13/a1.png">   
```
Input: head = [3,1]
Output: [-1,-1]
Explanation: There are no critical points in [3,1].
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/10/13/a2.png">  
```
Input: head = [5,3,1,2,5,1,2]
Output: [1,3]
Explanation: There are three critical points:
- [5,3,1,2,5,1,2]: The third node is a local minima because 1 is less than 3 and 2.
- [5,3,1,2,5,1,2]: The fifth node is a local maxima because 5 is greater than 2 and 1.
- [5,3,1,2,5,1,2]: The sixth node is a local minima because 1 is less than 5 and 2.
The minimum distance is between the fifth and the sixth node. minDistance = 6 - 5 = 1.
The maximum distance is between the third and the sixth node. maxDistance = 6 - 3 = 3.
```

**Example 3:**  
<img src="https://assets.leetcode.com/uploads/2021/10/14/a5.png">  
```
Input: head = [1,3,2,2,3,2,2,2,7]
Output: [3,3]
Explanation: There are two critical points:
- [1,3,2,2,3,2,2,2,7]: The second node is a local maxima because 3 is greater than 1 and 2.
- [1,3,2,2,3,2,2,2,7]: The fifth node is a local maxima because 3 is greater than 2 and 2.
Both the minimum and maximum distances are between the second and the fifth node.
Thus, minDistance and maxDistance is 5 - 2 = 3.
Note that the last node is not considered a local maxima because it does not have a next node.
```

**Example 4:**     
<img src="https://assets.leetcode.com/uploads/2021/10/13/a4.png">   
```
Input: head = [2,3,3,2]
Output: [-1,-1]
Explanation: There are no critical points in [2,3,3,2].
```

### Constraints
+ The number of nodes in the list is in the range `[2, 10^5]`.
+ `1 <= Node.val <= 10^5`

## Solutions

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    vector<int> nodesBetweenCriticalPoints(ListNode* head) {
      if(!head->next->next) return {-1,-1};
      vector<int> v;
      ListNode* t;
      t = head;
      head = head->next;
      int n=2;
      
      while(head->next){
        if(
            ((t->val > head->val) and (head->val < head->next->val)) 
            or 
            ((t->val < head->val) and (head->val > head->next->val)) 
        )
          v.push_back(n);
        t = head;
        head = head->next;
        n++;
      }
      
      if(v.size() < 2) return {-1,-1};
      
      int mx = v[v.size()-1] - v[0];
      int mn = INT_MAX;
      for(int i=1; i<v.size(); i++)
        mn = min(mn,v[i]-v[i-1]);
      for(int x: v) cout<<x<<endl;
      return {mn,mx};
       
    }
};
```

