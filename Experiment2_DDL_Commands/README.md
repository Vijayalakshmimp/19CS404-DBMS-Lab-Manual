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
-- Paste Question 1 here
<img width="1056" height="560" alt="image" src="https://github.com/user-attachments/assets/66a11362-ccef-4b39-a0bd-b24cffe8515e" />

```
INSERT into Student_details SELECT * From Archived_students;
```

**Output:**
<img width="1234" height="363" alt="image" src="https://github.com/user-attachments/assets/c2ce7521-ffda-41dd-a3a5-8fbf1f2ca480" />


**Question 2**
---
<img width="1233" height="386" alt="image" src="https://github.com/user-attachments/assets/e58caabd-a0b2-4fcc-b2f0-205c0daa28ac" />


```
create table Products(ProductID INTEGER PRIMARY KEY,
                     ProductName TEXT UNIQUE NOT NULL,
                     Price REAL check (price>0),
                     StockQuantity INTEGER CHECK (StockQuantity>=0)
);
```

**Output 2:**

<img width="1207" height="358" alt="image" src="https://github.com/user-attachments/assets/9488328c-ff34-4ac9-86db-eab8342d0b6d" />


**Question 3**
---
<img width="969" height="376" alt="image" src="https://github.com/user-attachments/assets/46b91d36-1cef-439e-b9a1-89cd43b5a01a" />


```
ALTER Table Student_details ADD Date_of_birth Date;
```

**Output:**

<img width="1150" height="432" alt="image" src="https://github.com/user-attachments/assets/ffc6bc72-3f31-4285-a68d-a467b037c1d7" />


**Question 4**
---
<img width="1060" height="397" alt="image" src="https://github.com/user-attachments/assets/3414ecc9-628b-4fee-bbd4-385c6c153063" />

-- 

```
INSERT INTO Customers(CustomerID,Name,Address,City,Zipcode)
values
(302,'Laura Croft','456 Elm St','Seattle',98101),
(303,'Bruce Wayne','789 Oak St','Gotham',10001);
       
```

**Output:**
<img width="1085" height="452" alt="image" src="https://github.com/user-attachments/assets/9d928b0d-1a6e-48ee-bee3-abb81358f645" />


**Question 5**
---
<img width="1082" height="518" alt="image" src="https://github.com/user-attachments/assets/b4886bf6-0656-4333-9b5f-4b26cbbea4d1" />

-- 

```
ALTER TABLE customer ADD birth_date timestamp;
       
```

**Output:**

<img width="994" height="488" alt="image" src="https://github.com/user-attachments/assets/3cd24d6c-3a16-448a-83e7-6aacbc28cfe8" />


**Question 6**
---
<img width="1001" height="478" alt="image" src="https://github.com/user-attachments/assets/97605e62-eb29-4a7a-b540-7c8fc511e892" />

-- 

```
CREATE TABLE Invoices(InvoiceID INTEGER PRIMARY KEY,
                     InvoiceDate DATE,
                     Amount REAL check (Amount>0),
                     DueDate DATE check (DueDate>InvoiceDate),
                     OrderID INTEGER references Orders(OrderID)
);
```

**Output:**
<img width="1046" height="361" alt="image" src="https://github.com/user-attachments/assets/eecd828c-27f0-45d7-9954-8d9a18affd32" />


**Question 7**
---
<img width="1095" height="369" alt="image" src="https://github.com/user-attachments/assets/051156a2-518f-4d5a-9d43-9c18f6a0d7bd" />


```
CREATE TABLE contacts(contact_id INTEGER PRIMARY KEY,
                     first_name TEXT NOT NULL,
                     last_name TEXT NOT NULL,
                     email TEXT,
                     phone TEXT NOT NULL check (LENGTH(phone)>=10)
);
```

**Output:**
<img width="1116" height="401" alt="image" src="https://github.com/user-attachments/assets/35e20b94-21da-4d78-80c1-6ca1c024c8da" />


**Question 8**
---
<img width="1082" height="246" alt="image" src="https://github.com/user-attachments/assets/d65dce13-776d-44ed-9001-4a6175607df1" />


```
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
values
('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**
<img width="1109" height="313" alt="image" src="https://github.com/user-attachments/assets/a6e7d299-cc90-41c7-9550-3d56e62d5e4f" />


**Question 9**
---
<img width="1060" height="373" alt="image" src="https://github.com/user-attachments/assets/def97871-af7d-4096-a6e8-d50d754943fb" />

```
CREATE TABLE Departments(DepartmentID INTEGER,
                         DepartmentName TEXT
);
```

**Output:**
<img width="1166" height="437" alt="image" src="https://github.com/user-attachments/assets/1418b0ed-2c52-4bda-b37d-f6617993e1b3" />


**Question 10**
---
<img width="1087" height="315" alt="image" src="https://github.com/user-attachments/assets/ff940559-143c-4e43-9ca2-b71d8c242f05" />


```
Create table Orders(OrderID INTEGER PRIMARY KEY,
                   OrderDate DATE NOT NULL,
                   CustomerID INTEGER references Customers(CustomerID)
);
```

**Output:**

<img width="1104" height="351" alt="image" src="https://github.com/user-attachments/assets/7982c770-2112-4c19-8b9c-02a14581b696" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
