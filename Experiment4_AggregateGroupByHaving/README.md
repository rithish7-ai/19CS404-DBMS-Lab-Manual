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
How many medical records does each doctor have?

Sample table:MedicalRecords Table
<img width="1089" height="164" alt="image (6)" src="https://github.com/user-attachments/assets/d1a9080d-f88a-44d0-a33b-ab097fc2c170" />


```sqlSELECT 
  DoctorID, 
  COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID;
```

**Output:**
<img width="434" height="787" alt="image" src="https://github.com/user-attachments/assets/4329261e-e485-4c0a-99a6-05518b94dcd3" />


**Question 2**
---
How many appointments are scheduled in each hour of the day?

Sample table:Appointments Table

name                              type
--------------------          ----------
AppointmentID               INTEGER
PatientID                         INTEGER
DoctorID                         INTEGER
AppointmentDateTime   DATETIME
Purpose                           TEXT
Status                              TEXT     

For example:

Result
HourOfDay   TotalAppointments
----------  -----------------
09          2
10          5
11          1
14          1
16          1
```sql
SELECT 
  STRFTIME('%H', AppointmentDateTime) AS HourOfDay, 
  COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY HourOfDay
ORDER BY HourOfDay;
```

**Output:**
<img width="662" height="630" alt="image" src="https://github.com/user-attachments/assets/feaca30a-82cd-442d-ad42-9b327bc1c101" />


**Question 3**
---
How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table

<img width="1039" height="162" alt="image (4)" src="https://github.com/user-attachments/assets/132939d3-2a1d-4fd1-8e6e-c4dd384b3e9e" />


For example:

Result
Specialty          Gender    TotalDoctors
-----------------  --------  --------------
Cardiology         Male      1
Dermatology        Male      1
Gastroenterology   Female    4
Gastroenterology   Male      1
Pediatrics         Female    1
Pediatrics         Male      2
```sql
SELECT Specialty, Gender, COUNT(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty, Gender
ORDER BY Specialty, Gender;
```

**Output:**
<img width="617" height="644" alt="image" src="https://github.com/user-attachments/assets/dcdfa741-b8ab-4c54-83db-3e8123d3d584" />


**Question 4**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

For example:

Result
TOTAL
----------
17541.18


```sql
SELECT SUM(purch_amt) AS TOTAL
FROM orders;
```

**Output:**
<img width="625" height="353" alt="image" src="https://github.com/user-attachments/assets/41d6a5dc-a1ab-486e-bf80-545252f4bfae" />


**Question 5**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

For example:

Result
MAXIMUM
----------
5760.0

```sql
SELECT 
  MAX(purch_amt) AS MAXIMUM
FROM orders;
```

**Output:**
<img width="611" height="396" alt="image" src="https://github.com/user-attachments/assets/4e4ccd06-2bb6-485d-8c8c-0abc0875284c" />



**Question 6**
---
Write a SQL query to find the youngest employee in the company?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 

For example:

Result
Employee_Name  Age
-------------  ----------
Peter          32


```sql
SELECT name AS Employee_Name,age AS Age
FROM employee
WHERE age = (SELECT MIN(age) FROM employee)
LIMIT 1;
```

**Output:**

<img width="631" height="362" alt="image" src="https://github.com/user-attachments/assets/0b6a1762-34ee-4249-8083-9a812689b502" />


**Question 7**
---
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

For example:

Result
total
----------
225


```sql
SELECT SUM(inventory) AS total
FROM fruits
WHERE unit = 'LB';
```

**Output:**
<img width="566" height="330" alt="image" src="https://github.com/user-attachments/assets/acee476d-6cf2-4e58-a7a4-33fdc9d532ba" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.

Sample table: employee1


<img width="1031" height="203" alt="unnamed" src="https://github.com/user-attachments/assets/96c76cb3-56b0-45a4-8bef-db28edbdff7c" />

```sql
SELECT jdate, AVG(workhour)
FROM employee1
GROUP BY jdate
HAVING AVG(workhour) < 10;
```

**Output:**
<img width="652" height="333" alt="image" src="https://github.com/user-attachments/assets/1dcd5ad3-fd34-4d54-9b27-2f1837fb2e4d" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.
Sample table: customer1
<img width="992" height="173" alt="unnamed" src="https://github.com/user-attachments/assets/5119112d-6843-4ed5-8f7e-c3a2cba82f89" />



```sql
SELECT (age/5)*5 AS age_group,
       SUM(salary)
FROM customer1
GROUP BY (age/5)*5
HAVING SUM(salary) > 5000;
```

**Output:**

<img width="662" height="382" alt="image" src="https://github.com/user-attachments/assets/a3230663-69a7-4499-9a80-cfbe2892be20" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1
<img width="1031" height="203" alt="unnamed" src="https://github.com/user-attachments/assets/0769c9b6-55c1-4d2e-a148-1a42edde55e0" />

```sql
SELECT occupation,
       MIN(workhour) 
FROM employee1
GROUP BY occupation
HAVING MIN(workhour) > 5;
```

**Output:**
<img width="662" height="524" alt="image" src="https://github.com/user-attachments/assets/03c4c4d6-4d35-43c4-a6e4-9ab525cdda8e" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
