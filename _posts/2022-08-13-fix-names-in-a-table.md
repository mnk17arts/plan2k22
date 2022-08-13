---
layout: post
title: Fix Names in a Table                       
summary:
tags:
    - mysql
    - sql
    - leetcode
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/fix-names-in-a-table/)  

**SQL Schema** 
```sql
Create table If Not Exists Users (user_id int, name varchar(40))
Truncate table Users
insert into Users (user_id, name) values ('1', 'aLice')
insert into Users (user_id, name) values ('2', 'bOB')
```

Table: `Users`

```
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| user_id        | int     |
| name           | varchar |
+----------------+---------+
user_id is the primary key for this table.
This table contains the ID and the name of the user. The name consists of only lowercase and uppercase characters.
```


**Your Task:** 

Write an SQL query to fix the names so that only the first character is uppercase and the rest are lowercase.

Return the result table ordered by user_id.

The query result format is in the following example.


### Example
   
```
Input: 
Users table:
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | aLice |
| 2       | bOB   |
+---------+-------+
Output: 
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | Alice |
| 2       | Bob   |
+---------+-------+
```


## Solutions

```sql

-- Write your T-SQL query statement below
select user_id, concat(upper(substr(name,1,1)), lower(substr(name,2))) as name from users order by user_id;

```

