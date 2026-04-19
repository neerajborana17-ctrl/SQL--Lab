# SQL Lab-Experiment 3
### To perform various SQL operation on the table such as creating a tablefrom another tale ,deleting record,updating records
## 1. List all employees and jobs in Department 30 in descending order by salary
###
``` sql
SELECT ename, job
FROM employee
WHERE deptno = 30
ORDER BY sal DESC;
```
## 2. List job and Department Number of employees whose name are five letters long, begin with 'A' and end with 'N'
###
``` sql
SELECT job, deptno
FROM employee
WHERE ename LIKE 'A___N';
```
## 3. Display the name of employees whose name starts with alphabet 'S'
###
``` sql
SELECT ename
FROM employee
WHERE ename LIKE 'S%';
```
## 4. Display the names of employees whose name ends with alphabet 'S'
###
```sql
SELECT ename
FROM employee
WHERE ename LIKE '%S';
```
## 5. Display the names of employees working in department number 10, 20, or 40 OR employees working as Clerk, Salesman, or Analyst
###
```sql
SELECT ename
FROM employee
WHERE deptno IN (10, 20, 40)
   OR job IN ('CLERK', 'SALESMAN', 'ANALYST');
```
## 6. Display employee number and names for employees who earn commission
### 
```sql
SELECT empno, ename
FROM employee
WHERE comm IS NOT NULL;
```
## 7. Display employee number and total salary for each employee
###
```sql
SELECT empno, (sal + IFNULL(comm, 0)) AS total_salary
FROM employee;
```
## 8. Display employee number and annual salary for each employee
### 
```sql
SELECT empno, sal * 12 AS annual_salary
FROM employee;
```
## 9. Display the names of all employees working as clerks and drawing a salary more than 3,000
###
```sql
SELECT ename
FROM employee
WHERE job = 'CLERK'
  AND sal > 3000;
```
## 10. Display the names of employees who are working as clerk, salesman or analyst and drawing a salary more than 3,000
###
```sql
SELECT ename
FROM employee
WHERE job IN ('CLERK', 'SALESMAN', 'ANALYST')
  AND sal > 3000;
```