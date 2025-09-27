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
Create a table named ProjectAssignments with the following constraints:

AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.
```sql
CREATE TABLE ProjectAssignments
(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="1201" height="366" alt="image" src="https://github.com/user-attachments/assets/5a0bc253-3038-409d-b882-bcc317512014" />


**Question 2**
---
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT

```sql
CREATE TABLE Locations
(
LocationID INTEGER,LocationName TEXT,Address TEXT
);
```

**Output:**

<img width="1177" height="360" alt="image" src="https://github.com/user-attachments/assets/74d62b47-cc71-479e-b922-0b5bb533adff" />


**Question 3**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
CREATE TABLE Employees
(
EmployeeID INTEGER PRIMARY KEY,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL,
Email TEXT UNIQUE NOT NULL,
Salary INTEGER CHECK(Salary>0),
DepartmentID INTEGER,
FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);
```

**Output:**

<img width="1038" height="297" alt="image" src="https://github.com/user-attachments/assets/db8c2aa8-3dc5-434c-bca5-d1aa045c92a7" />


**Question 4**
---
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
INSERT INTO Books(ISBN, Title, Author, Publisher, YearPublished)SELECT * FROM Out_of_print_books 
```

**Output:**

<img width="1208" height="335" alt="image" src="https://github.com/user-attachments/assets/6ef4ab16-3ca9-4e99-a432-127fa4667faa" />

**Question 5**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```sql
CREATE TABLE Bonuses(
BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
BonusAmount REAL CHECK(BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1200" height="323" alt="image" src="https://github.com/user-attachments/assets/fe610550-782c-465f-9798-9e4eb1b077a3" />


**Question 6**
---
Write a SQL query to Add a new column State as text in the Student_details table.
```
Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
```
```sql
ALTER TABLE Student_details 
ADD COLUMN State TEXT;
```

**Output:**

<img width="1206" height="443" alt="image" src="https://github.com/user-attachments/assets/5118eadc-7ca1-47e4-8e9b-abe3bfbf8521" />


**Question 7**
---
Write a SQL query to Add a new column Country as text in the Student_details table.
```
Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
```
```sql
ALTER TABLE Student_details 
ADD COLUMN Country TEXT;
```

**Output:**

<img width="1210" height="397" alt="image" src="https://github.com/user-attachments/assets/fb0d0716-fdad-4d36-8da9-6282b7d43890" />

**Question 8**
---
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

```sql
INSERT into Books(ISBN,Title,Author,Publisher,Year)values('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**

<img width="1186" height="209" alt="image" src="https://github.com/user-attachments/assets/94670ca1-e45e-420c-a93a-0ae4fc918ddf" />

**Question 9**
---
In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.
```
ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021
```
```sql
INSERT into Books(ISBN,Title,Author)values('978-1234567890','Introduction to AI','John Doe'); 
INSERT into Books(ISBN,Title,Author,Publisher,Year)values('978-9876543210','Deep Learning','Jane Doe','TechPress',2022); 
INSERT into Books(ISBN,Title,Author,Year)values('978-1122334455','Cybersecurity Essentials','Alice Smith',2021); 

```

**Output:**

<img width="1196" height="296" alt="image" src="https://github.com/user-attachments/assets/a8f86ff9-800d-44d1-b1fc-1471a49a690c" />

**Question 10**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.
```sql
CREATE TABLE Products(
ProductID INTEGER PRIMARY KEY,
ProductName TEXT NOT NULL,
Price REAL CHECK (Price>0),
Stock INTEGER CHECK (Stock>=0)

);
```

**Output:**

<img width="1184" height="258" alt="image" src="https://github.com/user-attachments/assets/d157a415-3eca-42cd-aa79-e507b00cf77c" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
