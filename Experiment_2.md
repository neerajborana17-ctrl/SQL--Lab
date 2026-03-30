# SQL Lab-Experiment 2
### To perform various SELECT operations on employee table

## 1 List all distinct jobs in employee
###
```sql
SELECT DISTINCT job FROM employee;
```
## 2 List all information about employee in department number 30
###
```sql
SELECT * FROM employee WHERE deptno=30;
```
## 3 Find all department number with department names greater than 20
###
```sql
SELECT deptno,dname FROM department WHERE deptno>20;
```
## 4 Find all managers and clerks in department 30
###
```sql
SELECT * FROM employee
WHERE deptno=30 AND job IN ('MANAGER','CLERK');
```
## 5 List employee name, employee number and department of all clerks
###
```sql
SELECT ename,empno,deptno FROM employee WHERE job='CLERK';
```
## 6 Find all managers not in department 30
###
```sql
SELECT * FROM employee 
WHERE job='MANAGER' AND deptno<>30;
```
## 7 List employees in department 10 who are not manager or clerks
###
```sql
SELECT * FROM employee 
WHERE deptno=10 AND job NOT IN ('MANAGER','CLERK');
```
## 8 Find employees and jobs earning between 1200 and 1400
###
```sql
SELECT ename,job FROM employee 
WHERE sal BETWEEN 1200 AND 1400;
```
## 9 List name and department number of clerks, analyst or salesman
###
```sql
SELECT ename,deptno FROM employee 
WHERE job IN ('CLERK','ANALYST','SALESMAN');
```
## 10 List name and department number of employee whose name begins with M
###
```sql
SELECT ename,deptno FROM employee 
WHERE ename LIKE 'M%';
```