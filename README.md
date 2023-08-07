# SQL-Lab2

# We will use the Employees and Awards table below:

 <img src="Lab2.png" width="500" height="500">

### Q1: Choose all employees who have received an award (Nested Query)?
Query:

``` sql
SELECT * 
FROM employee 
WHERE id IN (
  SELECT employee_id
  FROM awards )
```
Output:
 <img src="1.png" width="1000" >

### Q2: Choose all employees who have never received an award (Nested Query)?
Query:
``` sql
SELECT * 
FROM employee 
WHERE id NOT IN (
  SELECT employee_id
  FROM awards )
```
Output:
 <img src="22.png" width="1000" >
 
### Q3: Choose all Developers who make more than all Managers combined (Nested Query)?
Query:
``` sql
SELECT * 
FROM employee 
WHERE role = 'Developer' AND salary > (
  SELECT max(salary)
  FROM employee
  WHERE role = 'Manager')
```
Output:
 <img src="3.png" width="1000" >
 
### Q4: Choose all Developers who make more money than any Manager (Nested Query)?
Query:
``` sql
SELECT * 
FROM employee 
WHERE role = 'Developer' AND salary > (
  SELECT salary
  FROM employee
  WHERE role = 'Manager')
```
Output:
 <img src="4.png" width="1000" >
 
### Q5: Choose all employees whose salaries are higher than the average for their position. (Nested Query)?
Query:
``` sql
SELECT * 
FROM employee 
WHERE salary > (
  SELECT avg(salary)
  FROM employee
  GROUP by role )
```
Output:
 <img src="5.png" width="1000" >
