# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
What is the total number of medications prescribed for each patient?

```sql
select PatientID,COUNT(Medication) as TotalMedications from Prescriptions group by PatientID;
```

**Output:**

<img width="814" height="948" alt="image" src="https://github.com/user-attachments/assets/b60342c9-cc39-4214-926b-e3ce1d705303" />


**Question 2**
---
How many prescriptions were written by each doctor?

```sql
select DoctorID, COUNT(Medication) as TotalPrescriptions from Prescriptions group by DoctorID;
```

**Output:**

<img width="899" height="943" alt="image" src="https://github.com/user-attachments/assets/8fec86b8-88e7-432f-a17a-ece3eedd4cb7" />


**Question 3**
---
What is the most common diagnosis among patients?

```sql
select Diagnosis,COUNT(Diagnosis) as DiagnosisCount from MedicalRecords group by Diagnosis order by DiagnosisCount desc limit 1;-- Paste your SQL code below for Question 3
```

**Output:**

<img width="1146" height="732" alt="image" src="https://github.com/user-attachments/assets/bc10f19f-451f-43f5-b899-349c53d90498" />


**Question 4**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
select sum(purch_amt) as TOTAL from orders;
```

**Output:**
<img width="823" height="649" alt="image" src="https://github.com/user-attachments/assets/a6123cb3-2b49-4422-94d1-259859e09fdf" />


**Question 5**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
select AVG(purch_amt) as AVERAGE from orders;
```

**Output:**
<img width="702" height="728" alt="image" src="https://github.com/user-attachments/assets/f9bdc897-1f4a-4d97-a436-02ae6fe54f09" />


**Question 6**
---
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```sql
select COUNT(DISTINCT city) as unique_cities from customer;
```

**Output:**
<img width="768" height="730" alt="image" src="https://github.com/user-attachments/assets/62bce30a-51d7-42a0-8a37-9f5394b05e0a" />


**Question 7**
---
Write a SQL query to count the number of customers. Return number of customers.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

```sql
select COUNT(cust_name) as "COUNT" from customer;
```

**Output:**

<img width="701" height="720" alt="image" src="https://github.com/user-attachments/assets/454a24e8-7adb-4a68-92f6-6d9052a685ae" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.

```sql
select age,MAX(income) as "MAX(income)" from employee group by age having MAX(income)>2000000;
```

**Output:**

<img width="832" height="767" alt="image" src="https://github.com/user-attachments/assets/69e250f9-f9a2-4f33-a22d-d8b0f55d8db7" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

```sql
select age,MIN(income) as Income from employee group by age having MIN(income)<1000000;
```

**Output:**
<img width="896" height="797" alt="image" src="https://github.com/user-attachments/assets/ecffc3ec-0655-4065-89a5-d75d9cba76d2" />


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

```sql
select age,AVG(income) from employee group by age having AVG(income) between 300000 and 500000;
```

**Output:**
<img width="909" height="681" alt="image" src="https://github.com/user-attachments/assets/762d25ea-4af7-4fcc-af5b-5efdfd392bf6" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
