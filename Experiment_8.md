# Experiment -8
## To perform SQL queries using joins to retrieve related data from multiple tables such as employee, department, and salary grade.
## 1. Display all employees with their department name
###
```sql
SELECT e.ename, d.dname
FROM employee e
JOIN department d
ON e.deptno = d.deptno;
```
## 2. Display employees whose manager name is 'JONES' along with their manager name
###
```sql
SELECT e.ename AS employee, m.ename AS manager
FROM employee e
JOIN employee m
ON e.mgr = m.empno
WHERE m.ename = 'JONES';
```
## 3. Display employee name, job, department name, manager name, and grade
###
```sql
SELECT 
    e.ename,
    e.job,
    d.dname,
    m.ename AS manager,
    s.grade
FROM employee e
JOIN department d ON e.deptno = d.deptno
LEFT JOIN employee m ON e.mgr = m.empno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
ORDER BY d.dname;
```
## 4. List employee name, job, salary grade, and department name (excluding 'CLERK'), sorted by highest salary
###
```sql
SELECT 
    e.ename,
    e.job,
    s.grade,
    d.dname,
    e.sal
FROM employee e
JOIN department d ON e.deptno = d.deptno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE e.job <> 'CLERK'
ORDER BY e.sal DESC;
```
## 5. Display employee name, job and manager (including employees without manager)
###
```sql
SELECT 
    e.ename AS employee,
    e.job,
    NVL(m.ename, 'No Manager') AS manager
FROM employee e
LEFT JOIN employee m
ON e.mgr = m.empno;
```
## 6. List employee name, job, annual salary, deptno, dept name and grade who earn 36000/year or are not clerks
###
```sql
SELECT 
    e.ename,
    e.job,
    (e.sal * 12) AS annual_salary,
    e.deptno,
    d.dname,
    s.grade
FROM employee e
JOIN department d ON e.deptno = d.deptno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE (e.sal * 12) = 36000
   OR e.job <> 'CLERK';
```
## 7. List employee details who earn 30000/year and are not clerks
###
```sql
SELECT 
    e.ename,
    e.job,
    (e.sal * 12) AS annual_salary,
    e.deptno,
    d.dname,
    s.grade
FROM employee e
JOIN department d ON e.deptno = d.deptno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE (e.sal * 12) = 30000
  AND e.job <> 'CLERK';
```
## 8. List employee name & number with manager name & number (show 'No Manager' if none)
###
```sql
SELECT 
    e.empno AS emp_no,
    e.ename AS employee,
    NVL(m.empno, 'No Manager') AS mgr_no,
    NVL(m.ename, 'No Manager') AS manager
FROM employee e
LEFT JOIN employee m
ON e.mgr = m.empno;
```
## 9. Select department name, dept no and sum of salary
###
```sql
SELECT 
    d.dname,
    d.deptno,
    SUM(e.sal) AS total_salary
FROM employee e
JOIN department d
ON e.deptno = d.deptno
GROUP BY d.dname, d.deptno;
```
## 10. Display employee number, name and department location
###
```sql
SELECT 
    e.empno,
    e.ename,
    d.loc
FROM employee e
JOIN department d
ON e.deptno = d.deptno;
```
## 11. Display employee name and department name for each employee
###
```sql
SELECT 
    e.ename,
    d.dname
FROM employee e
JOIN department d
ON e.deptno = d.deptno;
```