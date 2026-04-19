# Experiment -6
### To use SQL functions like DECODE and date functions for data transformation and calculations.
## 1. Display empno, ename, deptno and show department name using DECODE
```sql
SELECT 
    empno,
    ename,
    DECODE(deptno,
        10, 'ACCOUNTING',
        20, 'RESEARCH',
        30, 'SALES',
        40, 'OPERATIONS'
    ) AS dept_name
FROM employee;
```
## 2. Display your age in days
###
```sql
SELECT (SYSDATE - TO_DATE('2003-01-01','YYYY-MM-DD')) AS age_in_days
FROM dual;
```
## 3. Display your age in months
###
```sql
SELECT MONTHS_BETWEEN(SYSDATE, TO_DATE('2003-01-01','YYYY-MM-DD')) AS age_in_months
FROM dual;
```
##  4. Display the current date as "15th August Friday Nineteen Ninety-Seven"
###
```sql
SELECT TO_CHAR(SYSDATE, 'DDth Month Day YYYY') AS formatted_date
FROM dual;
```
## 5. "Scott has joined the company on Wednesday 13th August Nineteen Ninety"
###
```sql
SELECT 
    INITCAP(ename) || ' has joined the company on ' ||
    TO_CHAR(hiredate, 'Day DDth Month YYYY') AS joining_info
FROM employee;
```
## 6. "Scott has joined the company on Wednesday 13th August Nineteen Ninety"
###
###
```sql
SELECT 
    INITCAP(ename) || ' has joined the company on ' ||
    TO_CHAR(hiredate, 'Day DDth Month YYYY') AS joining_info
FROM employee;
```
## 7. Find the date for nearest Saturday after current date
###
```sql
SELECT NEXT_DAY(SYSDATE, 'SATURDAY') AS next_saturday
FROM dual;
```
## 8. Display current time
###
```sql
SELECT TO_CHAR(SYSDATE, 'HH24:MI:SS') AS current_time
FROM dual;
```
## 9. Display the date three months before the current date
###
```sql
SELECT ADD_MONTHS(SYSDATE, -3) AS three_months_before
FROM dual;
```
## 10. Display employees who joined in the month of December
###
```sql
SELECT ename, hiredate
FROM employee
WHERE TO_CHAR(hiredate, 'MM') = '12';
```
## 11. Employees whose first 2 characters of hire date = last 2 digits of salary
###
```sql
SELECT ename, hiredate, sal
FROM employee
WHERE SUBSTR(TO_CHAR(hiredate, 'DDMMYY'), 1, 2) = SUBSTR(TO_CHAR(sal), -2);
```
## 12. Employees whose 10% salary equals year of joining
###
```sql
SELECT ename, sal, hiredate
FROM employee
WHERE (sal * 0.10) = TO_NUMBER(TO_CHAR(hiredate, 'YYYY'));
```
## 13. Employees who joined before 15 months from today
###
```sql
SELECT ename, hiredate
FROM employee
WHERE hiredate < ADD_MONTHS(SYSDATE, -15);
```
## 14. Employees who joined before 15th of any month
###
```sql
SELECT ename, hiredate
FROM employee
WHERE TO_NUMBER(TO_CHAR(hiredate, 'DD')) < 15;
```
## 15. Employees whose joining date is available in deptno (interpreted as same dept joined on same date)
###
```sql
SELECT e1.ename, e1.deptno, e1.hiredate
FROM employee e1
WHERE EXISTS (
    SELECT 1
    FROM employee e2
    WHERE e1.deptno = e2.deptno
      AND e1.hiredate = e2.hiredate
      AND e1.empno <> e2.empno
);
```