---
layout: post
title: Course Schedule
summary:
tags:
    - dfs
    - bfs
    - topological-sort
    - graph
    - leetcode
    - cpp
    - medium  
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/course-schedule)  

There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [ai, bi]` indicates that you must take course `bi` first if you want to take course `ai`.

+ For example, the `pair [0, 1]`, indicates that to take course `0` you have to first take course `1`.

Return `true` *if you can finish all courses. Otherwise, return* `false`.

### Examples
**Example 1:**  
```
Input: numCourses = 2, prerequisites = [[1,0]]
Output: true
Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0. So it is possible.
```

**Example 2:**  
```
Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
Output: false
Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.
```

### Constraints

+ `1 <= numCourses <= 10^5`
+ `0 <= prerequisites.length <= 5000`
+ `prerequisites[i].length == 2`
+ `0 <= ai, bi < numCourses`
+ All the pairs `prerequisites[i]` are unique.

## Solutions

```cpp
class Solution {
public:
  
    bool DFSCycle(vector<int> adj[], int s, bool visited[], bool recSt[]) {
        visited[s] = true;
        recSt[s] = true;
        for (int i = 0; i < adj[s].size(); ++i) {
            if (!visited[adj[s][i]] and DFSCycle(adj, adj[s][i], visited, recSt)) 
                return true;
            else if (recSt[adj[s][i]]) 
                return true;
        }
        recSt[s] = false;
        return false;
    }
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
      int V = numCourses;
      vector<int> g[V];
      for(auto e: prerequisites)
        g[e[1]].push_back(e[0]);
      
      bool visited[V], recStack[V];
      memset(visited, false, sizeof(visited));
      memset(recStack, false, sizeof(recStack));
      
      for(int i=0; i<V; ++i)
        if(!visited[i])
          if(DFSCycle(g, i, visited, recStack))
            return false;
      
      return true;
      
    }
};
```