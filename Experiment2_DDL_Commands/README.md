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
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders ( OrderID INTEGER PRIMARY KEY, OrderDate DATE NOT NULL, CustomerID INTEGER, FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID) ); 
```

**Output:**

<img width="1267" height="366" alt="image" src="https://github.com/user-attachments/assets/552ea348-27c6-4855-9a85-b77fa57c4af6" />


**Question 2**
---
Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
ALTER TABLE customer ADD discount DECIMAL(5,2);
```

**Output:**

<img width="866" height="436" alt="image" src="https://github.com/user-attachments/assets/cd9e8aac-bd3b-4b5b-8da6-499bc893d21c" />


**Question 3**
---
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
For example:

Test	Result
SELECT Name, Category, Price, Stock FROM Products;

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
```sql
INSERT INTO Products (Name, Category, Price, Stock) VALUES ('Smartphone', 'Electronics', 800, 150), ('Headphones', 'Accessories', 200, 300);
```

**Output:**
<img width="874" height="415" alt="image" src="https://github.com/user-attachments/assets/1926b2d8-0524-493d-b9dc-7e5a75609af8" />


**Question 4**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

For example:

Test	Result
select * from Customers;
CustomerID  Name             Address         Email
----------  ---------------  --------------  ---------------------
301         Michael Johnson  123 Elm Street  michael.j@example.com
302         Sarah Lee        456 Oak Avenue  sarah.lee@example.com
303         David Wilson     789 Pine Road   david.w@example.com

```sql
INSERT INTO Customers (CustomerID, Name, Address ,Email)
SELECT CustomerID,Name, Address , Email
FROM Old_customers;
```

**Output:**

<img width="892" height="393" alt="image" src="https://github.com/user-attachments/assets/78fe8d52-d460-4d5b-8615-1aad4ff1dd91" />


**Question 5**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
CREATE TABLE contacts (
    contact_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT,
    phone TEXT NOT NULL CHECK (LENGTH(phone) >= 10)
);
```
**Output:**

 <img width="1234" height="384" alt="image" src="https://github.com/user-attachments/assets/35266800-e523-45b8-a752-f3a2253b66c1" />



**Question 6**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item ( item_id TEXT PRIMARY KEY, item_desc TEXT NOT NULL, rate INTEGER NOT NULL, icom_id TEXT CHECK(LENGTH(icom_id) = 4), FOREIGN KEY (icom_id) REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE );
```

**Output:**

<img width="843" height="357" alt="image" src="https://github.com/user-attachments/assets/712e8129-cce9-45d5-863d-ad6de54f6513" />


**Question 7**
---
Create a table named Events with the following columns:

EventID as INTEGER
EventName as TEXT
EventDate as DATE

```sql
CREATE TABLE Events (EventID INTEGER, EventName TEXT, EventDate DATE);
```

**Output:**

<img width="919" height="456" alt="image" src="https://github.com/user-attachments/assets/a30ef8d7-73a6-4456-81c8-73849dba3fc1" />

**Question 8**
Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

 
```sql
ALTER TABLE books ADD ISBN varchar(30); ALTER TABLE books ADD domain_dept varchar(30);
```

**Output:**

<img width="835" height="397" alt="image" src="https://github.com/user-attachments/assets/a80ea545-396e-4247-b0b6-cbb6d50e0669" />


**Question 9**
---

Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
```sql
CREATE TABLE Attendance (
AttendanceID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
AttendanceDate DATE,
Status TEXT CHECK(Status IN('Present','Absent','Leave')),
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID));
```

**Output:**

<img width="850" height="351" alt="image" src="https://github.com/user-attachments/assets/b7da89b5-646f-4761-b70b-c5fc155f6867" />


**Question 10**
---
Insert the below data into the Books table, allowing the Publisher and Year columns to take their default values.

ISBN             Title                 Author
---------------  --------------------  ---------------
978-6655443321   Big Data Analytics    Karen Adams

Note: The Publisher and Year columns will use their default values.
 

```sql
INSERT INTO Books (ISBN, Title, Author) VALUES ('978-6655443321', 'Big Data Analytics', 'Karen Adams');
```

**Output:**

<img width="868" height="328" alt="image" src="https://github.com/user-attachments/assets/967926a8-1bff-448b-9ab8-2cd76ff84d20" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
