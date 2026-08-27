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
-- Paste Question 1 here
<img width="1101" height="563" alt="image" src="https://github.com/user-attachments/assets/a85a9494-84bb-413e-aa11-e81379a1774b" />

```
select DoctorID, count(*) as TotalAppointments
from Appointments
group by DoctorID
```

**Output:**
<img width="818" height="690" alt="image" src="https://github.com/user-attachments/assets/e68657e6-644c-436d-860f-04f125034ebc" />


**Question 2**
---
<img width="1077" height="573" alt="image" src="https://github.com/user-attachments/assets/1cd17134-058f-4b92-8849-235b37c256de" />


```
select Frequency, count(*) as TotalPrescriptions
from Prescriptions
group by Frequency
```

**Output:**
<img width="858" height="533" alt="image" src="https://github.com/user-attachments/assets/181736c6-c835-43eb-b34f-d1b4444414b6" />


**Question 3**
---
<img width="927" height="657" alt="image" src="https://github.com/user-attachments/assets/3074e40b-9f31-4b50-877c-b6b32c4b3f12" />


```sql
select InsuranceCompany, avg(EndDate-StartDate) as AvgCoverageDurationDays
from Insurance
group by InsuranceCompany;
```

**Output:**
<img width="1067" height="605" alt="image" src="https://github.com/user-attachments/assets/d852f6cf-eab8-459a-9883-f979f7410f39" />


**Question 4**
---
<img width="743" height="521" alt="image" src="https://github.com/user-attachments/assets/486aa0cb-4a6f-4993-bfbd-64f96f372ca2" />


```sql
select count(id) as employees_in_california
from employee
where city='California';
```

**Output:**
<img width="668" height="400" alt="image" src="https://github.com/user-attachments/assets/7773c8c2-3091-44d6-81f8-b84d14fc4197" />


**Question 5**
---
<img width="842" height="455" alt="image" src="https://github.com/user-attachments/assets/204e3d7b-35c3-4808-85ce-105ead90f5fd" />


```sql
select avg(income) as avg_income
from employee
where name like 'A%';
```

**Output:**
<img width="515" height="381" alt="image" src="https://github.com/user-attachments/assets/faf09297-bff2-432f-90e7-5d2d22020063" />


**Question 6**
---
<img width="755" height="471" alt="image" src="https://github.com/user-attachments/assets/cd3da2c9-b5d5-429d-9bdc-678ebf0496b1" />


```sql
select count(city) as unique_cities
from customer;
```

**Output:**
<img width="550" height="367" alt="image" src="https://github.com/user-attachments/assets/aa6c607e-9d1d-47d3-8870-e20d7a952c2f" />


**Question 7**
---
<img width="543" height="483" alt="image" src="https://github.com/user-attachments/assets/1423b282-9cfe-4cb8-a99c-e765ac00b6fb" />


```sql
select max(purch_amt) as MAXIMUM
from orders;
```

**Output:**
<img width="518" height="362" alt="image" src="https://github.com/user-attachments/assets/72257ad5-69a1-428b-b8bc-24bc0db56336" />


**Question 8**
---
<img width="838" height="523" alt="image" src="https://github.com/user-attachments/assets/c433689e-d5b4-4f1e-ae64-8d34a122c867" />


```sql
select age, AVG(income)
from employee
group by age
having AVG(income) between 300000 and 500000;
```

**Output:**
<img width="602" height="382" alt="image" src="https://github.com/user-attachments/assets/6a5bde39-0cb4-434f-880c-cb086cae0b29" />


**Question 9**
---
<img width="832" height="526" alt="image" src="https://github.com/user-attachments/assets/38197273-bd84-4617-be05-747e51210b22" />


```sql
select category_id, sum(price) as Total_Cost
from products
group by category_id
having sum(price)>50;
```

**Output:**
<img width="570" height="385" alt="image" src="https://github.com/user-attachments/assets/56d937e1-98b9-4d8c-be82-4575b008fbe6" />


**Question 10**
---
<img width="847" height="477" alt="image" src="https://github.com/user-attachments/assets/95a3956d-968a-469f-8413-831ad3ff08e2" />


```sql
select (age/5)*5 as age_group, 
MIN(salary)
from customer1
group by (age/5)*5
having MIN(salary)<2000;
```

**Output:**
<img width="611" height="402" alt="image" src="https://github.com/user-attachments/assets/d3da84ac-1719-4026-ba1b-08a4f62bf2b0" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
