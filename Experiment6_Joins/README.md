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
<img width="1262" height="842" alt="image" src="https://github.com/user-attachments/assets/180d0f6c-d75c-4caf-bc7f-be025b95268b" />

**Program:**

```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt as 'Order Amount'
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;
```

**Output:**

<img width="1282" height="825" alt="image" src="https://github.com/user-attachments/assets/80d20dde-fac9-4d0e-92d3-f085e49169b9" />


**Question 2**
---
<img width="1270" height="800" alt="image" src="https://github.com/user-attachments/assets/47589ef0-acc5-4aff-a44d-07e5ef24fb64" />

**Program:**
```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM orders o
JOIN customer c
    ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**
<img width="1265" height="420" alt="Screenshot 2026-09-01 095002" src="https://github.com/user-attachments/assets/5bb0c46e-dcbb-4102-a006-1b6d80b8fd63" />



**Question 3**
---
<img width="1308" height="717" alt="image" src="https://github.com/user-attachments/assets/c981aba4-5210-4811-aa2a-c921362d8344" />


**Program:**
```sql
SELECT 
    p.first_name,
    s.*
FROM patients p
INNER JOIN surgeries s
    ON p.patient_id = s.patient_id
WHERE p.discharge_date BETWEEN '2024-03-01' AND '2024-03-31'
  AND p.admission_date NOT BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**

<img width="1285" height="382" alt="image" src="https://github.com/user-attachments/assets/24e07f9b-7c65-4152-87b6-41b0b3a0e3ae" />


**Question 4**
---
<img width="1186" height="692" alt="image" src="https://github.com/user-attachments/assets/2b034084-2eee-4826-96c1-fafeadb82215" />


**Program:**
```sql
SELECT 
    p.first_name AS patient_name,
    a.*
FROM patients p
INNER JOIN appointments a
    ON p.patient_id = a.patient_id;
```

**Output:**

<img width="1288" height="506" alt="image" src="https://github.com/user-attachments/assets/290c8758-045f-458c-aff3-e5c7f5944c6f" />


**Question 5**
---
<img width="1261" height="610" alt="image" src="https://github.com/user-attachments/assets/9fb37404-b301-43e8-9430-c302622a6d62" />

**Program:**
```sql
SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id;
```

**Output:**

<img width="1260" height="827" alt="image" src="https://github.com/user-attachments/assets/a2384ea9-18e9-4c62-8e47-d1e81043aa97" />


**Question 6**
---
<img width="1287" height="340" alt="image" src="https://github.com/user-attachments/assets/060f5ada-412e-4708-87d9-445d06bdeb20" />

**Program:**
```sql
SELECT c.*
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-07-01' AND '2012-07-30';
```

**Output:**

<img width="1287" height="382" alt="image" src="https://github.com/user-attachments/assets/36ae0118-a52c-4467-9528-d907d330d0a6" />


**Question 7**
---
<img width="1257" height="826" alt="image" src="https://github.com/user-attachments/assets/74770ae9-75c6-4178-98b4-39993ccb2f70" />

**Program:**
```sql
SELECT 
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="1275" height="841" alt="image" src="https://github.com/user-attachments/assets/a94a2cd3-9f46-4aa6-934f-d36e0f92e853" />


**Question 8**
---
<img width="1285" height="857" alt="image" src="https://github.com/user-attachments/assets/51f9df42-56f4-4378-b17a-907ad756d706" />

**Program:**
```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city as customer_city,
    c.grade,
    s.name as salesman_name,
    s.city as salesman_city,
    s.commission
FROM orders o
INNER JOIN customer c
    ON o.customer_id = c.customer_id
INNER JOIN salesman s
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1277" height="847" alt="image" src="https://github.com/user-attachments/assets/55821b8b-117e-4578-9e28-9f0d614bc78d" />


**Question 9**
---
<img width="1287" height="627" alt="image" src="https://github.com/user-attachments/assets/84954da3-7709-458b-ae27-fe0a94d14aea" />

**Program:**
```sql
SELECT 
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d
    ON p.doctor_id = d.doctor_id
WHERE p.date_of_birth > '1990-01-01';
```

**Output:**

<img width="881" height="357" alt="image" src="https://github.com/user-attachments/assets/e6df53e6-9ecd-4e97-a361-acfbc8ca3386" />


**Question 10**
---
<img width="973" height="811" alt="image" src="https://github.com/user-attachments/assets/345e0e50-b1d6-4a65-8c72-78362f22a2bf" />

**Program:**
```sql
SELECT 
    s.name AS Salesman,
    c.cust_name,
    c.city
FROM salesman s
INNER JOIN customer c
    ON s.city = c.city;
```

**Output:**
<img width="1002" height="617" alt="image" src="https://github.com/user-attachments/assets/981e3021-2431-4aff-b4d3-5c589e03e7c8" />


**Module 5 SEB Grade:**
<img width="1452" height="492" alt="image" src="https://github.com/user-attachments/assets/d74630dd-c016-41fb-a899-5836934907b2" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
