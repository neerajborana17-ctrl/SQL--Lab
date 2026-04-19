# SQL Lab-Experiment 5
###  To perform aggregate functions and string operations on an employee database using SQL functions like COUNT, SUM, AVG, MAX, MIN, and string functions.

## 1. Display the total number of employees working in the company
###
```sql
SELECT COUNT(*) AS total_employees
FROM employee;
```
## 2. Display the total salary being paid to all employees
###
```sql
SELECT SUM(sal) AS total_salary
FROM employee;
```
## 3. Display the maximum salary from employee table
###
```sql
SELECT MAX(sal) AS max_salary
FROM employee;
```
## 4. Display the minimum salary from employee table
###
```sql
SELECT MIN(sal) AS min_salary
FROM employee;
```
## 5. Display the average salary from employee table
###
```sql
SELECT AVG(sal) AS avg_salary
FROM employee;
```
## 6. Display the maximum salary being paid to clerk
###
```sql
SELECT MAX(sal) AS max_clerk_salary
FROM employee
WHERE job = 'CLERK';
```
## 7. Display the maximum salary being paid in dept no 20
###
```sql
SELECT MAX(sal) AS max_salary_dept20
FROM employee
WHERE deptno = 20;
```
## 8. Display the minimum salary paid to any salesman
###
```sql
SELECT MIN(sal) AS min_salesman_salary
FROM employee
WHERE job = 'SALESMAN';
```
## 9. Display the average salary drawn by managers
###
```sql
SELECT AVG(sal) AS avg_manager_salary
FROM employee
WHERE job = 'MANAGER';
``` 
## 10. Display the total salary drawn by analyst working in dept no 40
###
```sql
SELECT SUM(sal) AS total_analyst_salary
FROM employee
WHERE job = 'ANALYST' AND deptno = 40;
```
## 11. Display the names of the employee in uppercase
###
```sql
SELECT UPPER(ename) AS uppercase_name
FROM employee;
```
## 12. Display the names of the employee in lowercase
###
```sql
SELECT LOWER(ename) AS lowercase_name
FROM employee;
```
## 13. Display the names of the employee in proper case
###
```sql
SELECT CONCAT(UPPER(LEFT(ename,1)), LOWER(SUBSTRING(ename,2))) AS proper_case_name
FROM employee;
```
## 14. Display the length of your name
###
```sql
SELECT LENGTH('YourName') AS name_length;
```
## 15. Display the length of all employee names
###
```sql
SELECT ename, LENGTH(ename) AS name_length
FROM employee;
```
