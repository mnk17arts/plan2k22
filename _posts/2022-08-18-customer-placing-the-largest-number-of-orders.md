---
layout: post
title: Customer Placing the Largest Number of Orders                       
summary:
tags:
    - mysql
    - sql
    - leetcode
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/customer-placing-the-largest-number-of-orders/)  

**SQL Schema** 
```sql
Create table If Not Exists orders (order_number int, customer_number int)
Truncate table orders
insert into orders (order_number, customer_number) values ('1', '1')
insert into orders (order_number, customer_number) values ('2', '2')
insert into orders (order_number, customer_number) values ('3', '3')
insert into orders (order_number, customer_number) values ('4', '3')
```


**Your Task:** 

Write an SQL query to find the customer_number for the customer who has placed the largest number of orders.

The test cases are generated so that exactly one customer will have placed more orders than any other customer.

The query result format is in the following example.


### Example
   
```
Input: 
Orders table:
+--------------+-----------------+
| order_number | customer_number |
+--------------+-----------------+
| 1            | 1               |
| 2            | 2               |
| 3            | 3               |
| 4            | 3               |
+--------------+-----------------+
Output: 
+-----------------+
| customer_number |
+-----------------+
| 3               |
+-----------------+
Explanation: 
The customer with number 3 has two orders, which is greater than either customer 1 or 2 because each of them only has one order. 
So the result is customer_number 3.
```


## Solutions

```sql

-- Write your T-SQL query statement below
# Write your MySQL query statement below
select distinct customer_number from orders 
group by customer_number
order by count(order_number) desc 
limit 1
;

```

