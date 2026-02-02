# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="1289" height="325" alt="image" src="https://github.com/user-attachments/assets/ff2aaadd-3ff5-4c62-ac72-9b228703e34e" />


```sql
CREATE TABLE Attendance (
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);

```

**Output:**

<img width="1387" height="165" alt="image" src="https://github.com/user-attachments/assets/ec2821a8-069c-4e29-9e7b-a248acc122ec" />


**Question 2**
---
<img width="914" height="306" alt="image" src="https://github.com/user-attachments/assets/c2efe96e-4314-46dc-bc1f-e64d09cbfd24" />


```sql
INSERT INTO Products (Name, Category, Price ,stock)
VALUES
('Smartphone','Electronics',800,150),
('Headphones','Accessories',200,300);
```

**Output:**

<img width="1312" height="346" alt="image" src="https://github.com/user-attachments/assets/4ed1f529-c39e-4191-ab48-625eb865e621" />


**Question 3**
---
<img width="1047" height="261" alt="image" src="https://github.com/user-attachments/assets/9c0e9f71-71c6-43a1-8fe2-917ed7d82a0b" />


```sql
ALTER TABLE employee
ADD COLUMN first_name varchar(50);

ALTER TABLE employee
ADD COLUMN last_name varchar(50);

```

**Output:**

<img width="1333" height="311" alt="image" src="https://github.com/user-attachments/assets/49ced96f-a33e-41c4-8a06-8b7c7162a24d" />


**Question 4**
---
<img width="1151" height="423" alt="image" src="https://github.com/user-attachments/assets/14e195a6-5521-4cc8-b44a-93223a9194f0" />


```sql
CREATE TABLE Reviews(
  ReviewID INTEGER,
  ProductID INTEGER,
  Rating REAL,
  ReviewText TEXT
);
```

**Output:**

<img width="1380" height="324" alt="image" src="https://github.com/user-attachments/assets/b0d24993-357a-4cdb-9720-68aa1fcb015d" />


**Question 5**
---
<img width="1067" height="327" alt="image" src="https://github.com/user-attachments/assets/1b198082-21a1-4d7b-9612-a6f0e8966679" />


```sql
CREATE TABLE Employees(
EmployeeID INTEGER PRIMARYKEY,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL,
Email TEXT UNIQUE,
Salary REAL CHECK (salary>0),
DepartmentID integer,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1352" height="341" alt="image" src="https://github.com/user-attachments/assets/67875006-41ac-47a4-8f29-0c12612a79df" />


**Question 6**
---
<img width="932" height="343" alt="image" src="https://github.com/user-attachments/assets/356daf54-6622-4e8d-a3ea-2e11e639d194" />


```sql
INSERT INTO Employee(EmployeeID , Name,Department,Salary)
SELECT EmployeeID,Name,Department,Salary
FROM Former_employees
```

**Output:**

<img width="1229" height="331" alt="image" src="https://github.com/user-attachments/assets/875cd054-9bfc-4a1c-813f-caebaaba7771" />


**Question 7**
---
<img width="1092" height="461" alt="image" src="https://github.com/user-attachments/assets/d4725cbd-0b1f-441a-bf65-a0ae129430d3" />


```sql
INSERT INTO Student_details(RollNo,Name,Gender)
VALUES (204,'Samuel Black','M');

```

**Output:**

<img width="1265" height="336" alt="image" src="https://github.com/user-attachments/assets/dc8bc3ff-3471-4f11-8124-bc6abb4d20a4" />


**Question 8**
---
<img width="1120" height="404" alt="image" src="https://github.com/user-attachments/assets/da00b18f-20aa-4f5d-a324-c0e33898f5fe" />


```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER,
icom_id TEXT(4),
foreign key (icom_id) 
REFERENCES company(com_id)
ON UPDATE CASCADE
ON DELETE CASCADE
);
```

**Output:**

<img width="1251" height="312" alt="image" src="https://github.com/user-attachments/assets/14432bb8-d8eb-499b-bb79-1361960fb055" />


**Question 9**
---
<img width="1370" height="282" alt="image" src="https://github.com/user-attachments/assets/82bf4f5c-24ae-4e28-a0a5-7ea8ed167309" />


```sql
-CREATE TABLE contacts(
contact_id INTEGER primary key,
first_name TEXT NOT NULL ,
last_name TEXT NOT NULL,
email TEXT,
phone text not null check(length(phone)>=10)
)
```

**Output:**

<img width="1368" height="208" alt="image" src="https://github.com/user-attachments/assets/85896ca0-06f5-4228-96f5-338db3153b22" />


**Question 10**
---
<img width="1304" height="384" alt="image" src="https://github.com/user-attachments/assets/2725fbff-2401-47ad-8b42-6cf1046af5ea" />


```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**

<img width="1345" height="362" alt="image" src="https://github.com/user-attachments/assets/d286c742-4886-45ac-aa5b-3493cc4f1bcf" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
