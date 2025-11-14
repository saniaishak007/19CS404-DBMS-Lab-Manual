# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n") and the "department_name" column from the "departments" table, with an inner join on the "department_id" column.

```sql
select n.*,
d.department_name
from nurses n
inner join 
departments d ON n.department_id=d.department_id;
```

**Output:**
<img width="1261" height="565" alt="image" src="https://github.com/user-attachments/assets/c99a3810-edd2-45b3-b102-9e1e371b638a" />

**Question 2**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```sql
SELECT 
    p.first_name AS patient_name, 
    d.specialization AS Doctor_specialization
FROM 
    patients p
INNER JOIN 
    doctors d 
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="759" height="393" alt="image" src="https://github.com/user-attachments/assets/5d7e16b9-de8f-4f57-b7a9-810b0e38a035" />

**Question 3**
---
Write an SQL query to select all columns from the 'customer' table (aliased as 'c') by performing a LEFT JOIN with the 'orders' table on the 'customer_id' column, including only those orders where the order date falls between '2012-08-01' and '2012-08-30'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
SELECT DISTINCT 
    c.*
FROM 
    customer c
INNER JOIN 
    orders o
ON 
    c.customer_id = o.customer_id
WHERE 
    o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';

```

**Output:**

<img width="1291" height="513" alt="image" src="https://github.com/user-attachments/assets/241000a0-2782-40d3-9d41-fbb08bf0c151" />


**Question 4**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS Salesman,
    s.commission
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1306" height="888" alt="image" src="https://github.com/user-attachments/assets/ab1c3555-191e-40b2-9606-7d5064a39d9e" />

**Question 5**
---
Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o
ON 
    c.customer_id = o.customer_id
WHERE 
    c.city = 'London';

```

**Output:**

<img width="1268" height="566" alt="image" src="https://github.com/user-attachments/assets/640424f4-74e3-4816-a40d-32af49e9b1b5" />

**Question 6**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id;

```

**Output:**

<img width="1249" height="558" alt="image" src="https://github.com/user-attachments/assets/57f80cae-475e-48dd-820c-1e4633ef7250" />


**Question 7**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.-- Paste Question 7 here

```sql
SELECT 
    c.cust_name AS "cust_name",
    c.city,
    o.ord_no AS "ord_no",
    o.ord_date AS "ord_date",
    o.purch_amt AS "Order Amount"
FROM 
    customer c
LEFT JOIN 
    orders o
ON 
    c.customer_id = o.customer_id
ORDER BY 
    o.ord_date ASC;
```

**Output:**

<img width="784" height="776" alt="image" src="https://github.com/user-attachments/assets/fa5be636-73ee-471b-9e22-12a03c8f99f9" />


**Question 8**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission. 

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS Salesman,
    s.commission
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;

```

**Output:**

<img width="1247" height="772" alt="image" src="https://github.com/user-attachments/assets/7fab5c3b-5bc2-4070-b4ba-9bd8899a34db" />


**Question 9**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM 
    orders o
JOIN 
    customer c
ON 
    o.customer_id = c.customer_id
WHERE 
    o.purch_amt BETWEEN 500 AND 2000;

```

**Output:**

<img width="1262" height="552" alt="image" src="https://github.com/user-attachments/assets/d4869b41-def2-4e95-a291-0b5d6b78c3ae" />


**Question 10**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
JOIN 
    customer c
ON 
    o.customer_id = c.customer_id
JOIN 
    salesman s
ON 
    o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1246" height="770" alt="image" src="https://github.com/user-attachments/assets/ac62e8cf-a19f-4ee6-9af9-d6af4804a4c4" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
