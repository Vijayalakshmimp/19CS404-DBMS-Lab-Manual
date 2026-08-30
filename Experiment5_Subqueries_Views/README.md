# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1252" height="622" alt="image" src="https://github.com/user-attachments/assets/88787922-b1db-4b1a-8214-a3e967cdb1c2" />


```sql
select *
from GRADES g
where grade=(select min(grade) 
from GRADES
where subject=g.subject);
```

**Output:**
<img width="1247" height="452" alt="image" src="https://github.com/user-attachments/assets/5f77170f-19f9-4757-bf73-4feb588efbb9" />


**Question 2**
---
<img width="1092" height="521" alt="image" src="https://github.com/user-attachments/assets/a6f689a0-9308-4246-8623-a5f6250f8b99" />


```sql
select name, city
from Customer
where city in(
select city
from customer
where id in (3,7));
```

**Output:**

<img width="821" height="427" alt="image" src="https://github.com/user-attachments/assets/184405dd-6f1e-4fd6-8fe4-5d060cbad19a" />


**Question 3**
---
<img width="973" height="751" alt="image" src="https://github.com/user-attachments/assets/01b59342-8adc-4b5f-b5e9-c80e587d3f64" />


```sql
select * from CUSTOMERS
where age<30;
```

**Output:**

<img width="1242" height="573" alt="image" src="https://github.com/user-attachments/assets/8e269d4e-1d1f-4b00-85d3-0b591ec922f7" />


**Question 4**
---
<img width="1081" height="432" alt="image" src="https://github.com/user-attachments/assets/107d6880-aef4-440f-bfee-1d12f3f2a0eb" />


```sql
select department_id as depar, department_name
from Departments
where length(department_name) > (
select avg(length(department_name))
from Departments);
```

**Output:**

<img width="647" height="391" alt="image" src="https://github.com/user-attachments/assets/fda03dac-af43-4163-b95e-cd4b5ddfa5ce" />


**Question 5**
---
<img width="1000" height="616" alt="image" src="https://github.com/user-attachments/assets/cb2e5c14-448c-4411-b8fb-43808f9cc481" />


```sql
select *
from CUSTOMERS
where salary=1500;
```

**Output:**

<img width="1216" height="322" alt="image" src="https://github.com/user-attachments/assets/7f9fc386-ca23-4acc-98e0-f03653fbab5a" />


**Question 6**
---
<img width="932" height="613" alt="image" src="https://github.com/user-attachments/assets/40313c13-3ca5-4398-98a5-4bb1dc46edc7" />


```sql
select * from CUSTOMERS
where ADDRESS='Delhi';
```

**Output:**

<img width="1225" height="327" alt="image" src="https://github.com/user-attachments/assets/126367d0-08c5-41df-b593-7473b888bdd7" />


**Question 7**
---
<img width="1231" height="507" alt="image" src="https://github.com/user-attachments/assets/b635fa26-e534-4cc6-bc23-3c61325a84e1" />


```sql
select grade, COUNT(*)
from customer
where grade >(
select avg(grade)
from customer
where city='New York')
group by grade;
```

**Output:**

<img width="687" height="332" alt="image" src="https://github.com/user-attachments/assets/041d9806-ed6f-4c13-9ebc-f0c87242b2d0" />


**Question 8**
---
<img width="1112" height="657" alt="image" src="https://github.com/user-attachments/assets/01080084-0da9-4bee-be4f-df29afa65b50" />


```sql
select * from Employee
where age<(
select avg(age) 
from Employee
where income>250000);
```

**Output:**

<img width="1242" height="511" alt="image" src="https://github.com/user-attachments/assets/d0e5eb46-f6b2-45f4-9a12-34c15458c09a" />


**Question 9**
---
<img width="996" height="687" alt="image" src="https://github.com/user-attachments/assets/cdfc42c4-47a0-4353-b67a-df777c21637c" />


```sql
select *
from CUSTOMERS
where SALARY<2500;
```

**Output:**

<img width="1215" height="440" alt="image" src="https://github.com/user-attachments/assets/f9757b43-c2d3-4bb1-a19f-9e657a9c8c9c" />


**Question 10**
---
<img width="1111" height="612" alt="image" src="https://github.com/user-attachments/assets/8d45123c-f972-4167-9e9d-92d298f89f38" />


```sql
select * from Employee
where age<(
select avg(age) 
from Employee
where income>1000000);
```

**Output:**

<img width="1233" height="407" alt="image" src="https://github.com/user-attachments/assets/f1f9ec81-1651-4d22-bed6-97d99fa9707d" />


**Module 4 SEB GRADE:**
<img width="1418" height="408" alt="Screenshot 2026-08-30 155623" src="https://github.com/user-attachments/assets/6ac523fa-bc0f-427e-a579-5ecd5d364577" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
