# Experiment -6
## To perform advanced SQL operations using aggregate functions, grouping, formatting, and date calculations.
## 1. Compute the number of days remaining in this year
```sql
SELECT 
    TO_DATE(TO_CHAR(SYSDATE, 'YYYY') || '-12-31','YYYY-MM-DD') - SYSDATE 
    AS days_remaining
FROM dual;
```
## 2. Find the highest and lowest salaries and the difference between them
###
```sql
SELECT 
    MAX(sal) AS highest_salary,
    MIN(sal) AS lowest_salary,
    (MAX(sal) - MIN(sal)) AS difference
FROM employee;
```
## 3. List employees whose commission is greater than 25% of their salaries
###
```sql
SELECT ename, sal, comm
FROM employee
WHERE comm > (0.25 * sal);
```
## 4. Display salary in dollar format
###
```sql
SELECT ename, TO_CHAR(sal, '$999,999.99') AS salary_in_dollar
FROM employee;
```
## 5. Matrix query to display job, salary based on department, and total salary
###
```sql
SELECT 
    job,
    SUM(CASE WHEN deptno = 10 THEN sal END) AS dept10,
    SUM(CASE WHEN deptno = 20 THEN sal END) AS dept20,
    SUM(CASE WHEN deptno = 30 THEN sal END) AS dept30,
    SUM(sal) AS total_salary
FROM employee
GROUP BY job;
```
 ## 6. Display total employees and number hired in 1980, 1981, 1982, 1983
 ###
 ```sql
SELECT 
    COUNT(*) AS total_employees,
    SUM(CASE WHEN TO_CHAR(hiredate,'YYYY') = '1980' THEN 1 ELSE 0 END) AS "1980",
    SUM(CASE WHEN TO_CHAR(hiredate,'YYYY') = '1981' THEN 1 ELSE 0 END) AS "1981",
    SUM(CASE WHEN TO_CHAR(hiredate,'YYYY') = '1982' THEN 1 ELSE 0 END) AS "1982",
    SUM(CASE WHEN TO_CHAR(hiredate,'YYYY') = '1983' THEN 1 ELSE 0 END) AS "1983"
FROM employee;
```
## 7. Query to get the last Sunday of any month
###
```sql
SELECT NEXT_DAY(LAST_DAY(SYSDATE) - 7, 'SUNDAY') AS last_sunday
FROM dual;
```
## 8. Display department numbers and total number of employees in each department
###
```sql
SELECT deptno, COUNT(*) AS total_employees
FROM employee
GROUP BY deptno;
```
## 9. Display various jobs and total number of employees in each job group
###
```sql
SELECT job, COUNT(*) AS total_employees
FROM employee
GROUP BY job;
```
## 10. Display department numbers and total salary for each department
###
```sql
SELECT deptno, SUM(sal) AS total_salary
FROM employee
GROUP BY deptno;
```