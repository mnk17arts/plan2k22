---
layout: post
title: Second Highest Salary                       
summary:
tags:
    - mysql
    - sql
    - leetcode
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/second-highest-salary/)  

**SQL Schema** 
```sql
Create table If Not Exists Employee (id int, salary int)
Truncate table Employee
insert into Employee (id, salary) values ('1', '100')
insert into Employee (id, salary) values ('2', '200')
insert into Employee (id, salary) values ('3', '300')
```

Table: `Employee`

```
+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| salary      | int  |
+-------------+------+
id is the primary key column for this table.
Each row of this table contains information about the salary of an employee.
```


**Your Task:** 

Write an SQL query to report the second highest salary from the Employee table. If there is no second highest salary, the query should report null.

The query result format is in the following example.


### Example
   
```
Input: 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
Output: 
+---------------------+
| SecondHighestSalary |
+---------------------+
| 200                 |
+---------------------+
```


## Solutions

```sql

-- Write your T-SQL query statement below
select max(salary) as SecondHighestSalary from employee where salary < (select max(salary) from employee);

```

