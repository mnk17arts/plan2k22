---
layout: post
title: Data Stream as Disjoint Intervals                       
summary:
tags:
    - leetcode
    - binary-search
    - heap
    - cpp
    - hard
minute: 15+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/data-stream-as-disjoint-intervals/description/)  

Given a data stream input of non-negative integers a1, a2, ..., an, summarize the numbers seen so far as a list of disjoint intervals.

Implement the SummaryRanges class:

SummaryRanges() Initializes the object with an empty stream.
void addNum(int value) Adds the integer value to the stream.
int[][] getIntervals() Returns a summary of the integers in the stream currently as a list of disjoint intervals [starti, endi]. The answer should be sorted by starti.

### Examples


**Example 1:**   
```
Input
["SummaryRanges", "addNum", "getIntervals", "addNum", "getIntervals", "addNum", "getIntervals", "addNum", "getIntervals", "addNum", "getIntervals"]
[[], [1], [], [3], [], [7], [], [2], [], [6], []]
Output
[null, null, [[1, 1]], null, [[1, 1], [3, 3]], null, [[1, 1], [3, 3], [7, 7]], null, [[1, 3], [7, 7]], null, [[1, 3], [6, 7]]]

Explanation
SummaryRanges summaryRanges = new SummaryRanges();
summaryRanges.addNum(1);      // arr = [1]
summaryRanges.getIntervals(); // return [[1, 1]]
summaryRanges.addNum(3);      // arr = [1, 3]
summaryRanges.getIntervals(); // return [[1, 1], [3, 3]]
summaryRanges.addNum(7);      // arr = [1, 3, 7]
summaryRanges.getIntervals(); // return [[1, 1], [3, 3], [7, 7]]
summaryRanges.addNum(2);      // arr = [1, 2, 3, 7]
summaryRanges.getIntervals(); // return [[1, 3], [7, 7]]
summaryRanges.addNum(6);      // arr = [1, 2, 3, 6, 7]
summaryRanges.getIntervals(); // return [[1, 3], [6, 7]]
```

**Example 2:**   
```
Input 
["SummaryRanges","addNum","getIntervals","addNum","getIntervals","addNum","getIntervals","addNum","getIntervals","addNum","getIntervals","addNum","getIntervals","addNum","getIntervals","addNum","getIntervals","addNum","getIntervals","addNum","getIntervals"]
[[],[6],[],[6],[],[0],[],[4],[],[8],[],[7],[],[6],[],[4],[],[7],[],[5],[]]
Output
[null,null,[[6,6]],null,[[6,6]],null,[[0,0],[6,6]],null,[[0,0],[4,4],[6,6]],null,[[0,0],[4,4],[6,8]],null,[[0,0],[4,4],[6,8]],null,[[0,0],[4,4],[6,8]],null,[[0,0],[4,4],[6,8]],null,[[0,0],[4,4],[6,8]],null,[[0,0],[4,4],[5,5],[6,8]],null,[[0,0],[4,5],[6,8]]]

Explanation
SummaryRanges summaryRanges = new SummaryRanges();
summaryRanges.addNum(6);      // arr = [6]
summaryRanges.getIntervals(); // return [[6, 6]]
summaryRanges.addNum(6);      // arr = [6]
summaryRanges.getIntervals(); // return [[6, 6]]
summaryRanges.addNum(0);      // arr = [0, 6]
summaryRanges.getIntervals(); // return [[0, 0], [6, 6]]
summaryRanges.addNum(4);      // arr = [0, 4, 6]
summaryRanges.getIntervals(); // return [[0, 0], [4, 4], [6, 6]]
summaryRanges.addNum(8);      // arr = [0, 4, 6, 8]
summaryRanges.getIntervals(); // return [[0, 0], [4, 4], [6, 8]]
summaryRanges.addNum(7);      // arr = [0, 4, 6, 7, 8]
summaryRanges.getIntervals(); // return [[0, 0], [4, 4], [6, 8]]
summaryRanges.addNum(6);      // arr = [0, 4, 6, 7, 8]
summaryRanges.getIntervals(); // return [[0, 0], [4, 4], [6, 8]]
summaryRanges.addNum(4);      // arr = [0, 4, 6, 7, 8]
summaryRanges.getIntervals(); // return [[0, 0], [4, 4], [6, 8]]
summaryRanges.addNum(7);      // arr = [0, 4, 6, 7, 8]
summaryRanges.getIntervals(); // return [[0, 0], [4, 4], [6, 8]]
summaryRanges.addNum(5);      // arr = [0, 4, 5, 6, 7, 8]
summaryRanges.getIntervals(); // return [[0, 0], [4, 5], [6, 8]]
summaryRanges.addNum(5);      // arr = [0, 4, 5, 6, 7, 8]
summaryRanges.getIntervals(); // return [[0, 0], [4, 5], [6, 8]]
```



### Constraints

+ `0 <= value <= 10^4`
+ At most `3 * 10^4` calls will be made to `addNum` and `getIntervals`.

## Solutions

```cpp
class SummaryRanges {
public:
    map<int, int> m;
    SummaryRanges() {
        
    }
    
    void addNum(int value) {
        auto cur = m.lower_bound(value);
        bool flag = false;
        if(cur != m.begin()) {
            auto pre = cur;
            pre--;
            if(pre->second+1 >= value) {
                pre->second = max(pre->second, value);
                flag = true;
            }
        }
        if(cur != m.end() && cur->first - 1 <= value) {
            if(flag) {
                auto pre = cur;
                pre--;
                if(pre->second >= cur->first-1) {
                    pre->second = max(pre->second, cur->second);
                    m.erase(cur);
                }
            }
            else {
                flag = true;
                if(cur->first != value) {
                    pair<int, int> ccur = *cur;
                    ccur.first = min(ccur.first, value);
                    cur = m.insert(cur, ccur);
                    cur++;
                    if(cur != m.end()) {
                        m.erase(cur);
                    }
                }
            }
        }
        // If the value cant be merged in any of the available intervals.
        if(!flag) {
            m.insert(cur, {value, value});
        }
    }
    
    vector<vector<int>> getIntervals() {
        vector<vector<int>> ints;
        for(const auto &i: m) {
            ints.push_back({i.first, i.second});
        }
        return ints;
    }
};

/**
 * Your SummaryRanges object will be instantiated and called as such:
 * SummaryRanges* obj = new SummaryRanges();
 * obj->addNum(value);
 * vector<vector<int>> param_2 = obj->getIntervals();
 */
```

