
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
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

# SQL QUERY
```sql
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15 AND sale_date = '2023-01-31';
```

**Output:**
<img width="1195" height="430" alt="image" src="https://github.com/user-attachments/assets/53b48619-a0e4-4e59-937f-4ce356bccd5b" />



**Question 2**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.
# SQL QUERY
```sql
UPDATE suppliers SET address = '58 Lakeview, Magnolia' WHERE supplier_id = 5;
```

**Output:**

<img width="1211" height="381" alt="image" src="https://github.com/user-attachments/assets/1be0c5b5-5a00-4527-be35-92336df74812" />


**Question 3**
---
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

# SQL QUERY
```sql
UPDATE Employees
SET hire_date = '2024-01-24'
WHERE department_id = 50;
```

**Output:**
<img width="1221" height="296" alt="image" src="https://github.com/user-attachments/assets/6e08c8c7-e0c5-48b8-94d2-838f8248d0d4" />


**Question 4**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.
# SQL QUERY
```sql
UPDATE Products SET sell_price = sell_price * 1.1 WHERE category = 'Bakery';
```

**Output:**

<img width="1208" height="487" alt="image" src="https://github.com/user-attachments/assets/2693f1df-6921-4965-959d-8268ccf3a11f" />


**Question 5**
---
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

# SQL QUERY
```sql
UPDATE products
SET reorder_lvl = reorder_lvl * 0.70
WHERE product_name LIKE '%cream%' AND quantity > reorder_lvl;
```

**Output:**

<img width="1223" height="486" alt="image" src="https://github.com/user-attachments/assets/9ba81d95-2eda-4a2f-89fd-dafa1c9d44f2" />


**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000

# SQL QUERY
```sql
DELETE FROM Customer WHERE GRADE = 3 AND CUST_NAME LIKE '%BBB%' AND PAYMENT_AMT > 2000
```

**Output:**

<img width="1226" height="493" alt="image" src="https://github.com/user-attachments/assets/5d5241d4-2336-409a-9cb8-20824668d466" />


**Question 7**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

# SQL QUERY
```sql
DELETE FROM Doctors WHERE specialization = 'Cardiology'
```

**Output:**
<img width="1241" height="402" alt="image" src="https://github.com/user-attachments/assets/24bbe4f1-cb55-4be7-b058-318e34f3a874" />


**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

 
# SQL QUERY
```sql
DELETE FROM customer WHERE GRADE >= 2;
```

**Output:**
<img width="737" height="552" alt="image" src="https://github.com/user-attachments/assets/1d806e18-32de-4a36-b95d-33c4e6e9ee4e" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

# SQL QUERY
```sql
DELETE FROM customer WHERE WORKING_AREA = 'New York';
```

**Output:**
<img width="1171" height="713" alt="image" src="https://github.com/user-attachments/assets/a59349d3-6973-4ac6-bb2d-cf7f61ae132e" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

# SQL QUERY
```sql
DELETE FROM customer WHERE GRADE < 2;
```

**Output:**
<img width="697" height="532" alt="image" src="https://github.com/user-attachments/assets/3d28145b-f95e-4ea0-b927-022e21296d66" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
