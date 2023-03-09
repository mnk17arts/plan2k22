---
layout: post
title: Find anagrams in linked list
summary:
tags:
  - geeksforgeeks
  - linkedlist
  - slidingwindow
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/de6f6a196aecdfb3e4939ba7729809a5a4bdfe90/1)

Given a linked list of characters and a string S.Return all the anagrams of the string present in the given linked list.In case of overlapping anagrams choose the first anagram from left.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function findAnagrams() which takes head node of the linked list and a string S as input parameters and returns an array of linked list which only stores starting point of the Anagram. If there is no anagram in the linked list,return -1.

**Expected Time Complexity:** `O(N)`, where N is length of LinkedList.  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**

```
Input: a -> b -> c -> a -> d -> b -> c -> a
S = bac
Output: [a -> b -> c, b -> c -> a]
Explanation: In the given linked list,
there are three anagrams: 
1. a -> b -> c -> a -> d -> b -> c -> a
2. a -> b -> c -> a -> d -> b -> c -> a
3. a -> b -> c -> a -> d -> b -> c -> a
But in 1 and 2, a -> b -> c and b -> c-> a
are ovelapping.So we take a -> b -> c as it
comes first from left.So the output is:
[a->b->c,b->c->a]
```

**Example 2:**

```
Input: a -> b -> d -> c -> a
S = bac
Output: -1 
Explanation: There is no anagrams, so output is -1
```

### Constraints

- `1 <= N <= 10^5`
- `1 <= |S| <= 10^5`

## Solutions

```cpp

/*
Definition for singly Link List Node
struct Node
{
    char data;
    Node* next;
    Node(int x) {  data = x;  next = NULL; }
};

You can also use the following for printing the link list.
printList(Node* node);
*/

class Solution {
  public:
    vector<Node*> findAnagrams(struct Node* head, string s) {
        // code here

        vector<Node*> res;
        
        map<char, int> m1;
        for(int i = 0; i < s.size(); i++){
            m1[s[i]]++;
        }
        
        struct Node* previ = NULL;
        struct Node* i = head;
        struct Node* prevj = NULL;
        struct Node* j = head;
        
        map<char, int> m2;
        int curr_size  = 0;
        while(j != NULL){
            
            if(curr_size < s.size()){
                if(j) m2[j->data]++;
                prevj = j;
                if(j) j = j->next;
                curr_size++;
            }
            else{
                previ = i;
                if(i) i = i->next;
                m2[previ->data]--;
                if(m2[previ->data] == 0){
                    m2.erase(previ->data);
                }
                m2[j->data]++;
                prevj = j;
                if(j) j = j->next;
            }
            
            if(m1 == m2){
                if(previ) previ->next = NULL;
                if(prevj) prevj->next = NULL;
                res.push_back(i);
                i = j;
                m2.clear();
                curr_size = 0;
            }
        }
        
        return res;
    }
};

```
