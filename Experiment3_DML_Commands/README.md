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
For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.
```sql
UPDATE sales
SET sell_price=sell_price+3
WHERE product_id IN(
SELECT product_id
FROM products
WHERE supplier_id=4
);
```

**Output:**

<img width="1196" height="396" alt="image" src="https://github.com/user-attachments/assets/4f8f0884-697a-4bcb-9087-983f5bd59c7f" />


**Question 2**
---
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

```sql
UPDATE employees
SET hire_date='2024-01-24'
WHERE department_id=50;
```

**Output:**

<img width="1213" height="339" alt="image" src="https://github.com/user-attachments/assets/c4abbb41-9350-468a-8be0-7f6f83aa1de5" />


**Question 3**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

```sql
UPDATE products
SET reorder_lvl=40
WHERE category='Grocery';
```

**Output:**
<img width="1204" height="426" alt="image" src="https://github.com/user-attachments/assets/83934ba9-34fb-4162-a241-21d9bf6d2434" />


**Question 4**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

```sql
UPDATE employees
SET email='not available',
commission_pct=0.55
Where department_id=110;
```

**Output:**

<img width="1253" height="405" alt="image" src="https://github.com/user-attachments/assets/ccb06e6b-21d8-4d24-92d9-2e11e7e866aa" />


**Question 5**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

```sql
UPDATE products
SET product_name='Grapefruit'
where product_id=4
```

**Output:**

<img width="1210" height="295" alt="image" src="https://github.com/user-attachments/assets/b8af6458-4c7d-4d02-b835-c385485da829" />

**Question 6**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L'
```sql
DELETE from customer
WHERE cust_city LIKE 'L%';
```

**Output:**

<img width="1167" height="888" alt="image" src="https://github.com/user-attachments/assets/cfcbcbb3-2d9b-4812-b25a-b280917511e2" />

**Question 7**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000
```sql
DELETE from Customer
where grade =3
and cust_name LIKE '%BBB%'
and payment_amt>2000;
```

**Output:**

<img width="1188" height="499" alt="image" src="https://github.com/user-attachments/assets/a6f95e9e-2ffb-4dd8-94f6-250dc5fba986" />


**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

```sql
delete from Customer
where cust_city<>'New York'
and OUTSTANDING_AMT>5000;
```

**Output:**



**Question 9**
---
<img width="1220" height="621" alt="image" src="https://github.com/user-attachments/assets/bc49565d-5ee6-4cce-96f1-1bc0d52f26e3" />

```sql
delete from customer
where working_area='New York';
```

**Output:**

<img width="1031" height="690" alt="image" src="https://github.com/user-attachments/assets/bc359585-e995-4dbe-8af1-17da52e5d049" />

**Question 10**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

```sql
delete from customer
where grade>2 
and payment_amt<(select avg(payment_amt) from customer)
or outstanding_amt>8000;
```

**Output:**

<img width="1194" height="604" alt="image" src="https://github.com/user-attachments/assets/5c2005aa-4a27-4db0-af2f-007fdc927cd5" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
