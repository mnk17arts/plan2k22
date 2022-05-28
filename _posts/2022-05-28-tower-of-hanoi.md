---
layout: post
title:  Tower Of Hanoi
summary:
tags:
    - recursion
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/tower-of-hanoi-1587115621/1#)  

The [tower of Hanoi](https://en.wikipedia.org/wiki/Tower_of_Hanoi) is a famous puzzle where we have three rods and `N` disks. The objective of the puzzle is to move the entire stack to another rod. You are given the number of discs `N`. Initially, these discs are in the rod `1`. You need to print all the steps of discs movement so that all the discs reach the 3rd rod. Also, you need to find the total moves.
Note: The discs are arranged such that the top disc is numbered `1` and the bottom-most disc is numbered `N`. Also, all the discs have different sizes and a bigger disc cannot be put on the top of a smaller disc. Refer the provided link to get a better clarity about the puzzle.

**Your Task:** 
You don't need to read input or print anything. You only need to complete the function `toh()` that takes following parameters: `N`(number of discs), `from` (The rod number from which we move the disc), `to` (The rod number to which we move the disc), `aux` (The rod that is used as an auxiliary rod) and prints the required moves inside function body (See the example for the format of the output) as well as return the count of total moves made. The total number of moves are printed by the driver code.
Please take care of the case of the letters.

**Expected Time Complexity**: ` O(2^N)`.   
**Expected Auxiliary Space:**   `O(N)`.


### Examples

**Example 1:**   
```
Input:
N = 2
Output:
move disk 1 from rod 1 to rod 2
move disk 2 from rod 1 to rod 3
move disk 1 from rod 2 to rod 3
3
Explanation: For N=2 , steps will be
as follows in the example and total
3 steps will be taken.
```

**Example 2:**   
```
Input:
N = 3
Output:
move disk 1 from rod 1 to rod 3
move disk 2 from rod 1 to rod 2
move disk 1 from rod 3 to rod 2
move disk 3 from rod 1 to rod 3
move disk 1 from rod 2 to rod 1
move disk 2 from rod 2 to rod 3
move disk 1 from rod 1 to rod 3
7
Explanation: For N=3 , steps will be
as follows in the example and total
7 steps will be taken.
```

### Constraints

+ `1 <= N <= 16`

## Solutions

```cpp
class Solution
{
    public:
    // You need to complete this function

    // avoid space at the starting of the string in "move disk....."
    long long toh(int n, int from, int to, int aux) {
        // Your code here
        if (n == 1) {
            cout << "move disk 1 from rod " << from << " to rod " << to << endl;
            return 1;
        }
        long long count = 1;
        count += toh(n - 1, from, aux, to);
        cout << "move disk " << n << " from rod " <<  from << " to rod " << to << endl; 
        count +=toh(n - 1, aux, to, from);
        return count;
    }
};
```

