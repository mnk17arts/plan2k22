---
layout: post
title: Restricted Pacman
description: In the game of Restricted Pacman, an infinite linear path is given. Pacman has to start at position 0 and eat as many candies as possible. In one move he can only jump a distance of either M or N.  If M and N are coprime numbers, find how many candies will be left on the board after the game is over.
summary: In the game of Restricted Pacman, an infinite linear path is given. Pacman has to start at position 0 and eat as many candies as possible. In one move he can only jump a distance of either M or N.  If M and N are coprime numbers, find how many candies will be left on the board after the game is over.
tags:
    - gfg
    - potd
    - java
    - medium
    - appris
    - edge_case
minute: 1
---

## Problem Statement
In the game of Restricted Pacman, an infinite linear path is given. Pacman has to start at position 0 and eat as many candies as possible. In one move he can only jump a distance of either M or N.  If M and N are coprime numbers, find how many candies will be left on the board after the game is over.<br/>
Note: The result is always finite as after a point X every index in the infinite path can be visited. 

### Edge Case
- Check with upper limits.
- M and N are coprime, to check for prime factors before testing with code.

### Note
- <code>M</code> and <code>N</code> are coprimes, so there is no chance of double counting a specific number. 

### Trivia
Find the largest index that can’t be obtained using any combination of M & N using [Frobenius Number](https://mathworld.wolfram.com/FrobeniusNumber.html) which defines X = (M * N) – M – N. 


## Solution
1. <code>O(1)</code> if you are familar with math behind [Coin Problem](https://mathworld.wolfram.com/CoinProblem.html)
```java
class Solution{
    static int candies(int m, int n){
        // Your code goes here
        return ((m-1)*(n-1)/2);
    }
}
```

2. <code>O(n)</code> Efficient Iterative DP Solution  
```java
class Solution{
    static int candies(int m, int n){
        // Your code goes here
        int cnt=0;
        int X = (n*m)-(n+m)+1;
        boolean[] flags = new boolean[X];
        flags[0]=true;
        for(int i=1;i<X;i++){
            if(i-n >= 0 && flags[i-n]==true){
                flags[i]=true;
            }
            if(i-m >= 0 && flags[i-m]==true){
                flags[i]=true;
            }
            if(!flags[i]){
                cnt++;
            }
        }
        return cnt;
    }
}
```
3. Brute Force Recusrive DP Solution 
```java
class Solution{
    static int N,M;
    static int candies(int m, int n){
        // Your code goes here
        N = n;
        M = m;
        boolean[] flags = new boolean[n*m];
        rectoggle(flags,0);
        
        return cntflag(flags);
    }
    
    static void rectoggle(boolean[] flags,int i){
        if(i<flags.length){
            flags[i]=true;
            rectoggle(flags,i+M);
            rectoggle(flags,i+N);
        }
        return;
    }
    
    static int cntflag(boolean[] flags){
        int cnt = 0;
        for(boolean flag:flags){
            if(!flag){
                cnt++;
            }
        }
        return cnt;
    }
}
```