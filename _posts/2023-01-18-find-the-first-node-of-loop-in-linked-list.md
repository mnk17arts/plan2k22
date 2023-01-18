---
layout: post
title: Find the first node of loop in linked list                       
summary:
tags:
    - linkedlist
    - 2pointers
    - geeksforgeeks
    - cpp
    - easy
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/44bb5287b98797782162ffe3d2201621f6343a4b/1)  

Given a singly linked list of N nodes. Find the first node of the loop if the linked list has a loop. If a loop is present return the node data of the first node of the loop else return -1.
 

**Your Task:** 

The task is to complete the function findFirstNode() which contains reference to the head as only argument. This function should return the value of the first node of the loop if the linked list contains a loop, else return -1.


**Expected Time Complexity:** `O(n)`              
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20211123204900/lloop-300x105.jpg">

```
Output: 3
Explanation:
We can see that there exists a loop 
in the given linked list and the first
node of the loop is 3.
```

**Example 2:**   

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20211123223611/lloop2-300x87.jpg">

```
Output: -1
Explanation: No loop exists in the above
linked list.So the output is -1.
```

### Constraints

+ `1 <= N <= 10^5`
+ `1 <= Data on node  <= 10^6`
+ `0 <= pos <= N`


## Solutions

```cpp

/*struct Node
{
    int data;
    struct Node *next;
    Node(int x) {
        data = x;
        next = NULL;
    }

*/
class Solution
{
    public:
     //Function to find first node if the linked list has a loop.
    int findFirstNode(Node* head)
    {
        // your code here
        int result = -1;
        Node* slowPtr = head, *fastPtr = head;
        while( fastPtr!=NULL && fastPtr->next!=NULL )
        {
            slowPtr = slowPtr->next;
            fastPtr = fastPtr->next->next;
            if( fastPtr==NULL || fastPtr->next==NULL )
                return result;            
            if( slowPtr==fastPtr ) 
            {
                if(slowPtr==head)
                {
                    while(slowPtr->next!=head) slowPtr = slowPtr->next;
                    result = slowPtr->next->data;
                    break;
                }
                slowPtr = head;
                while( slowPtr->next!=fastPtr->next )
                {
                    slowPtr = slowPtr->next;
                    fastPtr = fastPtr->next;
                }
                result = fastPtr->next->data;
                break;
            }
        }
        return result;
        
    }
};

```

