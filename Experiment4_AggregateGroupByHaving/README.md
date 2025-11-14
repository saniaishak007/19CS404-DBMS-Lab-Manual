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
What is the count of male and female patients?

```sql
select Gender,COUNT(*) AS TotalPatients
from Patients
group by gender;
```

**Output:**

<img width="672" height="355" alt="image" src="https://github.com/user-attachments/assets/6197e7e1-550f-435c-b439-166a24147aee" />


**Question 2**
---
How many patients are there in each city?

Sample table: Patients Table

```sql
select Address,COUNT(PatientID)AS TotalPatients
from Patients
group by Address;
```

**Output:**

<img width="614" height="389" alt="image" src="https://github.com/user-attachments/assets/b290d6c9-fb83-4637-9b8b-a9ce3db7cb34" />


**Question 3**
---
What is the total number of medications prescribed for each patient?
```sql
select PatientID,COUNT(*)AS TotalMedications
from Prescriptions
group by PatientID;
```

**Output:**

<img width="678" height="730" alt="image" src="https://github.com/user-attachments/assets/7c2b9b55-e115-4cff-a6fc-384e1ac0953d" />

**Question 4**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

```sql
select sum(purch_amt) as TOTAL
from orders;
```

**Output:**

<img width="353" height="363" alt="image" src="https://github.com/user-attachments/assets/5140c722-edf7-46c0-8b00-8092728a817d" />


**Question 5**
---
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.
```sql
select count(DISTINCT age) AS COUNT
from employee;
```

**Output:**

<img width="457" height="297" alt="image" src="https://github.com/user-attachments/assets/5a23d9c5-0606-46fe-8d13-823790e92251" />

**Question 6**
---
Write a SQL query to find the average length of names for people living in Chennai?

```sql
SELECT AVG(LENGTH(name)) as avg_name_length
from customer
where city='Chennai';
```

**Output:**

<img width="416" height="375" alt="image" src="https://github.com/user-attachments/assets/c3be72e2-9b0f-4a06-a6a6-97a498d7b132" />

**Question 7**
---
Write a SQL query to find the average length of email addresses (in characters):

```sql
select avg(LENGTH(email)) as avg_email_length
from customer;
```

**Output:**

<img width="450" height="303" alt="image" src="https://github.com/user-attachments/assets/5cbeadac-7313-4413-a0ac-a6e383298eab" />

**Question 8**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

```sql
select city,sum(income) as Income
from employee
group by city
having sum(income)>200000;
```

**Output:**

<img width="577" height="523" alt="image" src="https://github.com/user-attachments/assets/d6b878fc-ab56-42c1-beeb-d8f9d2cbe3c2" />

**Question 9**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.
```sql
select (age/5)*5 as age_group,sum(salary)as "SUM(salary)"
from customer1
group by age_group
having SUM(salary)>5000;
```

**Output:**

<img width="580" height="352" alt="image" src="https://github.com/user-attachments/assets/a3348fcf-5ecb-4299-a6a4-1c99c566ef7f" />

**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

```sql
select occupation,sum(workhour) as "SUM(workhour)"
from employee1
group by occupation
having sum(workhour)>20;
```

**Output:**

<img width="655" height="442" alt="image" src="https://github.com/user-attachments/assets/18dfe236-2575-4117-8b27-012a7c2c111f" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
