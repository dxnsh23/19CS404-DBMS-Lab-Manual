# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability

```sql
update products set availability=availability*2 where product_id=1;
```

**Output:**
<img width="1130" height="700" alt="image" src="https://github.com/user-attachments/assets/57a4dd73-dd12-4ebe-a5a8-28c3982e14d1" />


**Question 2**
---
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
 

```sql
update Employees set email='Unavailable';
```

**Output:**


**Question 3**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

```sql
update products set product_name='Grapefruit' where product_id=4;
```

**Output:**
<img width="1075" height="706" alt="image" src="https://github.com/user-attachments/assets/6c31c38e-a017-40b8-ad8e-aa0827939e80" />


**Question 4**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

```sql
delete from Customer where GRADE!=3;
```

**Output:**
<img width="670" height="884" alt="image" src="https://github.com/user-attachments/assets/55fbe429-80e5-425d-a0be-c300a6728564" />


**Question 5**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

```sql
delete from Doctors where last_name is null;
```

**Output:**
<img width="1067" height="1008" alt="image" src="https://github.com/user-attachments/assets/22a36eec-b488-4813-8816-6321c15be625" />


**Question 6**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4.

```sql
delete from Surgeries where surgery_id=3 or surgeon_id=4;
```

**Output:**
<img width="888" height="1034" alt="image" src="https://github.com/user-attachments/assets/0103757a-7bd9-41ef-a959-7c21e91dce78" />


**Question 7**
---
Write a query to fetch details of employees with the address as “DELHI(DEL)” from EmployeeInfo table.

```sql
select * from EmployeeInfo where Address like "DELHI(DEL)";
```

**Output:**

<img width="1262" height="588" alt="image" src="https://github.com/user-attachments/assets/ee9c3826-01cb-4b45-a1b8-3277238d85c6" />


**Question 8**
---
write a SQL query to create a union of two queries that shows the customer id, cities, and ratings of all customers. Those with a rating of 300 or greater will have the words 'High Rating', while the others will have the words 'Low Rating'.

customer table

cid           name          type   notnull       dflt_value  pk
------------  ------------  -----  ------------  ----------  ----------
0             customer_id   int    0                         0
1             cust_name     text   0                         0
2             city          text   0                         0
3             grade         int    0                         0
4             salesman_id   int    0                         0

```sql
select customer_id,city,grade,"High Rating" as Rating from customer
where grade >= 300

union

select customer_id,city,grade,"Low Rating" as Rating from customer
where grade < 300;
```

**Output:**

<img width="789" height="780" alt="image" src="https://github.com/user-attachments/assets/76313696-de8e-4420-9836-3dd95244f77e" />


**Question 9**
---
Write a SQL statement to Display names and city of salesman, who belongs to the city of London or Rome.

                                                                Inventory.db

```sql
select name,city from salesman where city in ('London','Rome') ;
```

**Output:**

<img width="711" height="664" alt="image" src="https://github.com/user-attachments/assets/c23597fb-f77f-4609-b958-c61d0f0622a9" />


**Question 10**
---
write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
select * from customer where city in ("New York") or grade<=100;
```

**Output:**
<img width="851" height="711" alt="image" src="https://github.com/user-attachments/assets/6bdd15a0-64a4-4df4-8831-07c8b25eeab5" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
