---
layout: post
title: Snakes and Ladders                       
summary:
tags:
    - leetcode
    - array
    - bfs
    - hash
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/snakes-and-ladders/description/)  

You are given an n x n integer matrix board where the cells are labeled from 1 to n2 in a Boustrophedon style starting from the bottom left of the board (i.e. board[n - 1][0]) and alternating direction each row.

You start on square 1 of the board. In each move, starting from square curr, do the following:

+ Choose a destination square next with a label in the range [curr + 1, min(curr + 6, n2)].
    - This choice simulates the result of a standard 6-sided die roll: i.e., there are always at most 6 destinations, regardless of the size of the board.
+ If next has a snake or ladder, you must move to the destination of that snake or ladder. Otherwise, you move to next.
The game ends when you reach the square n2.
+ A board square on row r and column c has a snake or ladder if board[r][c] != -1. The destination of that snake or ladder is board[r][c]. Squares 1 and n2 do not have a snake or ladder.

Note that you only take a snake or ladder at most once per move. If the destination to a snake or ladder is the start of another snake or ladder, you do not follow the subsequent snake or ladder.

+ For example, suppose the board is [[-1,4],[-1,3]], and on the first move, your destination square is 2. You follow the ladder to square 3, but do not follow the subsequent ladder to 4.

Return the least number of moves required to reach the square n2. If it is not possible to reach the square, return -1.

### Examples


**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2018/09/23/snakes.png">
```
Input: board = [[-1,-1,-1,-1,-1,-1],[-1,-1,-1,-1,-1,-1],[-1,-1,-1,-1,-1,-1],[-1,35,-1,-1,13,-1],[-1,-1,-1,-1,-1,-1],[-1,15,-1,-1,-1,-1]]
Output: 4
Explanation: 
In the beginning, you start at square 1 (at row 5, column 0).
You decide to move to square 2 and must take the ladder to square 15.
You then decide to move to square 17 and must take the snake to square 13.
You then decide to move to square 14 and must take the ladder to square 35.
You then decide to move to square 36, ending the game.
This is the lowest possible number of moves to reach the last square, so return 4.
```


**Example 2:**   
```
Input: board = [[-1,-1],[-1,3]]
Output: 1
```


### Constraints

+ `n == board.length == board[i].length`
+ `2 <= n <= 20`
+ `board[i][j]` is either `-1` or in the range `[1, n^2]`.
+ The squares labeled `1` and `n^2` do not have any ladders or snakes.

## Solutions

```cpp
class Solution {
public:
    /*  OBSERVATION
    -> Must move in zigzagly from one row to another.
    -> Must move to next unless the node is snake or laddder.
    -> Find minimum no. of steps to reach last position.
    -> BFS would be a feasible approach for this problem.
    */

    /* APPROACH
    -> Created a visited array to mark the visited nodes.
    -> Mark visited only we reach the node via moving from 1 to 6 steps ahead.
    -> Run BFS using a queue of node values.
    */ 
    int snakesAndLadders(vector<vector<int>>& board) {
        int n = board.size();
        // Visited Array for marking nodes
        vector<bool> vis(n*n+1,false);
        // Queue for running BFS
        queue<int> q;
        // Starting from node 1
        q.push(1); vis.at(1)=true;
        // Result variable
        int res = -1;

        // Running BFS
        while(q.size()) {
            int cn = q.size();
            res++;
            while(cn--) {
                // current node;
                int cur = q.front(); q.pop();
                // check if we reached the last node
                if(cur==n*n) {
                    return res;
                } 
                // iterating for next viable node
                for(int i=1; i<7; i++) {
                    int next = cur + i;
                    // checking if next node is in the given range and already not visited.
                    if( next<=n*n && vis.at(next)==0 ) {
                        // mark as visited
                        vis.at(next)=true;
                        // row and column of next node (mapping them with board co-ords)
                        // n-1 because we are traversing from down according to the board
                        int r = (n-1) - (next-1)/n; 
                        // (n-r-1)%2 because we move zigzag from row to row
                        int c = (n-r-1)%2 ? (n-1-(next-1)%n) : (next-1)%n;
                        // if the next node is ladder or snake add destination node else add this next node in queue
                        if( board.at(r).at(c)!=-1 ) {
                            q.push(board.at(r).at(c));
                        } 
                        else {
                            q.push( next );
                        }                    
                    }

                }
            }
        }
        return -1;
    }
};
```

