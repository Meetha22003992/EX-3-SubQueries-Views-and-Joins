# EX 3 SubQueries, Views and Joins 
## DATE: 18.08.2023

## AIM: 
To implement subqueries, views and joins

## Create employee Table
```sql
CREATE TABLE EMP (EMPNO INT PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR INT,HIREDATE DATE,SAL INT,COMM INT,DEPTNO INT);
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO INT PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.

### QUERY:
select ename from emp where sal >(select sal from emp where empno = 7566);

### OUTPUT:
![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/4e4ccca5-07d6-4509-92f5-389de3867a0f)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
select ename,job from emp where sal=800; 

### OUTPUT:
![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/8e8a8c3c-2946-4333-956d-6eaaa4d9b0bc)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
select ename,job from emp where deptno=10 and job='sales';

### OUTPUT:
![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/2f568cae-8ee7-40e0-a139-e2d46c1374ee)

### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
 create view EMPV5 as select empno, ename, job from emp where dpetno=10;
 
### OUTPUT:

![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/39a489d4-dd98-4e8a-af23-7519acba4137)


### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
create view EMPV30 (emplpoyee_no,employee_name,employee_sal) as select empno,empname,sal from emp where deptno=30;

### OUTPUT:

![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/68cc8409-bba9-40bc-b4e9-0ed66bb38692)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
update EMPVS5 set sal= sal+(sal*10/100) where job="clerk";

### OUTPUT:

![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/f07e09fa-557e-494f-b9e0-503e7f92555e)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
select customer1.cust_name, salesman1.name, salesman.city from salesman1, customer1 where salesman1.city = customer1.city;

### OUTPUT:
![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/9d2bb240-3f0f-4354-abb9-41e7a95adebf)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.

### QUERY:
select a.cust_anme as "CUSTOMER NAME", a.city, b.name as "SALESMAN", b.comission from customer1 a inner join salesman1 b on a.salesman_id=salesman_id where b.comission>12;

### OUTPUT:
![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/e218a7a3-25f4-428a-a6b1-6d9a908d005c)

### Q9) Perform Natural join on both tables

### QUERY:
select * from customer1 natural join salesman1;

### OUTPUT:
![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/8f7615a3-f4c8-4cc4-a635-e08c66505735)


### Q10) Perform Left and right join on both tables

### QUERY:
select customer_id,cust_name,name,comission from customer1 left join salesman1 on customer1.salesman = salesman1.salesman_id;

### OUTPUT:
![image](https://github.com/Meetha22003992/EX-3-SubQueries-Views-and-Joins/assets/119401038/702826e0-c950-4369-936f-3204a20d4e55)

