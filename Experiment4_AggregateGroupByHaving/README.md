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
<img width="1101" height="563" alt="image" src="https://github.com/user-attachments/assets/a85a9494-84bb-413e-aa11-e81379a1774b" />


```sql
select DoctorID, count(*) as TotalAppointments
from Appointments
group by DoctorID
```

**Output:**
<img width="818" height="690" alt="image" src="https://github.com/user-attachments/assets/e68657e6-644c-436d-860f-04f125034ebc" />


**Question 2**
---
<img width="1077" height="573" alt="image" src="https://github.com/user-attachments/assets/1cd17134-058f-4b92-8849-235b37c256de" />

```sql
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
---<img width="847" height="477" alt="image" src="https://github.com/user-attachments/assets/95a3956d-968a-469f-8413-831ad3ff08e2" />

```sql
select (age/5)*5 as age_group, 
MIN(salary)
from customer1
group by (age/5)*5
having MIN(salary)<2000;
```

**Output:**

<img width="611" height="402" alt="image" src="https://github.com/user-attachments/assets/d3da84ac-1719-4026-ba1b-08a4f62bf2b0" />

**Module 3 SEB GRADE:**

<img width="1418" height="408" alt="Screenshot 2026-08-30 155623" src="https://github.com/user-attachments/assets/099dbb7c-95a4-4ab1-a0c2-3b76750e5faf" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
