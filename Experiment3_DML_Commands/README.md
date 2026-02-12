
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
<img width="1235" height="557" alt="image" src="https://github.com/user-attachments/assets/5e71c208-98d5-46db-b031-f0d97f5e5b84" />


**Question 2**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.
# SQL QUERY
```sql
UPDATE suppliers SET address = '58 Lakeview, Magnolia' WHERE supplier_id = 5;
```

**Output:**

<img width="1184" height="389" alt="image" src="https://github.com/user-attachments/assets/f911ea75-5a2e-4820-84e1-9e58da704448" />


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

<img width="1162" height="374" alt="image" src="https://github.com/user-attachments/assets/900ecffb-aed0-4dc2-a029-ec6fbe9ac197" />


**Question 4**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.
# SQL QUERY
```sql
UPDATE Products SET sell_price = sell_price * 1.1 WHERE category = 'Bakery';
```

**Output:**
<img width="1147" height="603" alt="image" src="https://github.com/user-attachments/assets/6e2c2f1e-b4f1-4b71-8c6c-b14c2f08c6a6" />



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
<img width="1211" height="525" alt="image" src="https://github.com/user-attachments/assets/f86b46e4-2fbb-46f2-be60-f3e2b6f4c016" />

**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000
# SQL QUERY
```sql
DELETE FROM Customer WHERE GRADE = 3 AND CUST_NAME LIKE '%BBB%' AND PAYMENT_AMT > 2000
```

**Output:**

<img width="1121" height="511" alt="image" src="https://github.com/user-attachments/assets/05066ea0-27e5-4086-8cea-d45dcdde06b4" />


**Question 7**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'
# SQL QUERY
```sql
DELETE FROM Doctors WHERE specialization = 'Cardiology'
```

**Output:**

<img width="1245" height="384" alt="image" src="https://github.com/user-attachments/assets/9332632a-86c7-4482-a078-6d19ff3cc46c" />


**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.
# SQL QUERY
```sql
DELETE FROM customer WHERE GRADE >= 2;
```

**Output:**

<img width="733" height="545" alt="image" src="https://github.com/user-attachments/assets/12e2432a-ab24-41c4-8af4-acf8bc839b7d" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.
# SQL QUERY
```sql
DELETE FROM customer WHERE WORKING_AREA = 'New York';
```

**Output:**
<img width="1207" height="730" alt="image" src="https://github.com/user-attachments/assets/9756229b-a085-46d4-bcee-a367799fdd03" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.
# SQL QUERY
```sql
DELETE FROM customer WHERE GRADE < 2;
```

**Output:**

<img width="707" height="511" alt="image" src="https://github.com/user-attachments/assets/e1b54bcb-896b-4017-8571-599b993bd23c" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
