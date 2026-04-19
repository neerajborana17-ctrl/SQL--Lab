# SQL Lab-Experiment 4
### To write and execute SQL queries for retrieving, filtering, updating, and calculating employee data using various SQL clauses such as WHERE, LIKE, ORDER BY, and aggregate expressions.
## 1. Display the list of employees who have joined before 30-June-1980 or after 31-Dec-1981
### 
```sql
SELECT *
FROM employee
WHERE hiredate < '1980-06-30'
   OR hiredate > '1981-12-31';
```
## 2. Display the names of employees whose names have second alphabet 'A'
###
```sql
SELECT ename
FROM employee
WHERE ename LIKE '_A%';
```
## 3. Display the names of employees whose name is exactly five characters long
###
```sql
SELECT ename
FROM employee
WHERE ename LIKE '_____';
```
## 4. Display the names of employees whose names have second alphabet 'A'
###
```sql
SELECT ename
FROM employee
WHERE ename LIKE '_A%';
```
## 5. Display the names of employees who are not working as salesman, clerk or analyst
###
```sql
SELECT ename
FROM employee
WHERE job NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
```
## 6. Display employee name along with annual salary, highest salary first
###
```sql
SELECT ename, sal * 12 AS annual_salary
FROM employee
ORDER BY annual_salary DESC;
```
## 7. Display name, sal, hra, pf, da, totalsal for each employee
###
```sql
SELECT 
    ename,
    sal,
    sal * 0.15 AS hra,
    sal * 0.10 AS da,
    sal * 0.05 AS pf,
    (sal + (sal * 0.15) + (sal * 0.10) - (sal * 0.05)) AS totalsal
FROM employee
ORDER BY totalsal;
```
## 8. Update salary by 10% increment for employees not eligible for commission
###
```sql
UPDATE employee
SET sal = sal * 1.10
WHERE comm IS NULL;
```
## 9. Display employees whose salary is more than 3000 after 20% increment
###
```sql
SELECT ename, sal * 1.20 AS increased_salary
FROM employee
WHERE (sal * 1.20) > 3000;
```
## 10. Display employees whose salary contains at least 3 digits
###
```sql
SELECT ename, sal
FROM employee
WHERE sal >= 100;
```