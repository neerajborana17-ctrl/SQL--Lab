# SQL Lab-Experiment 1
### To perform various SQL operation on the table such as creating a tablefrom another tale ,deleting record,updating records

## 1 Create employee_master table using employee table
###
```sql 
CREATE TABLE employee_master AS SELECT * FROM employee;
```
## 2 Delete all records from employee_master where deptno is 10
### 
```sql
DELETE  FROM employee_master WHERE deptno=10;
```

## 3 Increase salary by 10% from employees of deptno is 20 
### 
```sql
UPDATE employee_master WHERE deptno=20;
```

## 4 Alter salary column size to (10,2)
### 
```sql
ALTER TABLE employee_master MODIFY sal DECIMAL(10,2)
```
## 5 Drop employee table
###
```sql
DROP TABLE employee_master;
```