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
<img width="872" height="82" alt="image" src="https://github.com/user-attachments/assets/d87ad37e-7bea-4edd-a9fa-3678bf3660eb" />


```sql
update Customer
set grade='5'
where city='Chennai';
```

**Output:**
<img width="1176" height="462" alt="image" src="https://github.com/user-attachments/assets/54118e6d-66a7-4439-8016-4d3954852c31" />



**Question 2**
---
<img width="1062" height="632" alt="image" src="https://github.com/user-attachments/assets/a13e915d-d81e-40f3-acab-2097c1f17b82" />


```sql
update Employees
set email='Unavailable';
```


**Output:**
<img width="1182" height="441" alt="image" src="https://github.com/user-attachments/assets/c6adb3a7-0bb3-475b-ac0f-5526e8ace2f2" />


**Question 3**
---
<img width="1066" height="542" alt="image" src="https://github.com/user-attachments/assets/31284523-d848-409f-bcd8-97b3936f28d0" />


```sql
update Products
set category='Household'
where product_name like'%Detergent%';
```

**Output:**
<img width="1177" height="495" alt="image" src="https://github.com/user-attachments/assets/59975cab-ee6f-4a5c-bd57-41768b7df5a1" />


**Question 4**
---
<img width="1202" height="602" alt="image" src="https://github.com/user-attachments/assets/74716e7f-6325-4806-8141-2bcf51ddc8e5" />


```sql
update Employees
set salary = '8000'
where employee_id='105' and salary<5000;
```

**Output:**
<img width="1182" height="237" alt="image" src="https://github.com/user-attachments/assets/fc132bc3-c25f-4510-933f-d1698c6fba30" />


**Question 5**
---
<img width="1205" height="632" alt="image" src="https://github.com/user-attachments/assets/5c531846-7faf-42e1-bb6b-bb298c4e8d86" />


```sql
update Employees
set salary=salary*2
where department_id=20 and job_id like '%MAN';
```

**Output:**
<img width="1182" height="333" alt="image" src="https://github.com/user-attachments/assets/44694b0f-0dce-4a31-8a2f-ba82f9ab8c7b" />


**Question 6**
---
<img width="1192" height="531" alt="image" src="https://github.com/user-attachments/assets/9ceea7ab-00d4-4b52-aeba-255a3bb317d1" />


```sql
delete from Doctors
where (specialization='Pediatrics' or specialization='Cardiology') and last_name='Brown';
```

**Output:**
<img width="1067" height="747" alt="image" src="https://github.com/user-attachments/assets/7d976b0a-955b-4c3d-bc79-a798f3ebb50a" />


**Question 7**
---
<img width="861" height="472" alt="image" src="https://github.com/user-attachments/assets/2a95fb60-9b9f-4d86-b2f1-0c7e764db84a" />


```sql
delete from Surgeries
where surgery_date='2024-02-28';
```

**Output:**
<img width="1190" height="381" alt="image" src="https://github.com/user-attachments/assets/a22cfb92-aa62-492f-b5c7-f2a09c54bcc8" />


**Question 8**
---
<img width="1196" height="677" alt="image" src="https://github.com/user-attachments/assets/57e7d5c5-dfb7-4b0d-a47c-e9ad76d9f7fc" />


```sql
delete from Customer
where GRADE<2;
```

**Output:**
<img width="770" height="540" alt="image" src="https://github.com/user-attachments/assets/b0620061-aece-4cf0-b3e3-fe4f911a3deb" />


**Question 9**
---
<img width="1217" height="517" alt="image" src="https://github.com/user-attachments/assets/b21c65ba-1889-4ea7-adb5-b091cddf9aef" />


```sql
delete from Customer
where GRADE=2 and CUST_NAME like 'M%' and PAYMENT_AMT < 3000;
```

**Output:**
<img width="1197" height="406" alt="image" src="https://github.com/user-attachments/assets/10d2fcb1-6e35-48a9-bf2d-9af46c8a4f08" />


**Question 10**
---
<img width="1212" height="481" alt="image" src="https://github.com/user-attachments/assets/2543ce8d-edee-443b-8d78-908d2712742a" />


```sql
delete from Customer
where (GRADE=3 or AGENT_CODE='A008') and OUTSTANDING_AMT<5000;
```

**Output:**
<img width="1175" height="377" alt="image" src="https://github.com/user-attachments/assets/150e6e73-904d-4abd-8cc0-b991c2d3dbe7" />

**Module 2 SEB GRADE:**
<img width="1418" height="408" alt="Screenshot 2026-08-30 155623" src="https://github.com/user-attachments/assets/abd24d42-1582-47de-b867-aeb8cc4927d8" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
