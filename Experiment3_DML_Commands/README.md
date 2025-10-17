# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
-- Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.
Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT           
For example:

Test	Result
select changes();
changes()
----------
4

```sql
-- update Products
set category='Household' 
where product_name like '%Detergent%';
```

**Output:**

![image](https://github.com/user-attachments/assets/d2b12f85-fe99-4a14-9dbd-c81bca033a1b)


**Question 2**
---
--Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info
suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

For example:

Test	Result
select changes();
changes()
----------
1

```sql
-- 
```update suppliers
set supplier_name='A1 Suppliers'
where supplier_id=8;

**Output:**

![image](https://github.com/user-attachments/assets/51c063b4-19f5-4bf3-9970-dcdfdabe011d)

**Question 3**
---
---Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
For example:

Test	Result
SELECT EMPLOYEE_ID, FIRST_NAME, EMAIL, SALARY, JOB_ID FROM EMPLOYEES 
WHERE department_id = 20;
EMPLOYEE_ID  FIRST_NAME  EMAIL       SALARY      JOB_ID
-----------  ----------  ----------  ----------  ----------
201          Michael     MHARTSTE    26000       MK_MAN
202          Pat         PFAY        6000        MK_REP
-- 

```update Employees
set salary=2*salary
where department_id=20 and job_ID like '%MAN%';
```

**Output:**

![image](https://github.com/user-attachments/assets/62526d8b-5b8a-464e-90d5-d163cacdedd9)


**Question 4**
---
-- Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT           
For example:

Test	Result
select changes();
changes()
----------
4

```sql
-- update Products
set sell_price= sell_price*1.15
where quantity<50 and supplier_id=10;
```

**Output:**

![image](https://github.com/user-attachments/assets/b8ce45da-285c-4197-90f4-667c3fdde3f3)


**Question 5**
---
--  Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)
For example:

Test	Result
select changes();
changes()
----------
3

```sql
-- update SALES
set total_sell_price=quantity*sell_price
where product_id=10;
```

**Output:**

![image](https://github.com/user-attachments/assets/f54391d8-fddf-4fdf-b3f1-5cf420016d4b)


**Question 6**
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select distinct(grade)from customer;
GRADE
----------
2
3
1
0
GRADE
----------
1
0

```sql
-- delete from Customer
where GRADE >=2;
```

**Output:**

![image](https://github.com/user-attachments/assets/443ceaf5-5651-49ca-a36f-196efb3170b4)


**Question 7**
---
-- Write a query to retrieve the first four characters of  EmpLname from the EmployeeInfo table.

EmployeeInfo Table
EmpID
EmpFname
EmpLname
Department
Project
Address
DOB
Gender
1
Sanjay
Mehra
HR
P1
Hyderabad(HYD)
01/12/1976
M
2
Ananya
Mishra
Admin
P2
Delhi(DEL)
02/05/1968
F
For example:

Result
SUBSTR(EmpLname, 1, 4)
----------------------
Mehr
Mish
Diwa
Kulk
Kapo

```sql
-- select SUBSTR(EmpLname, 1, 4) FROM EmployeeInfo;
```

**Output:**
![image](https://github.com/user-attachments/assets/151764d8-935e-4e24-9d13-1f19ee5bd194)


**Question 8**
---
-- Write a SQL query to Delete a Specific Surgery whose ID is 3
Sample table: Surgeries
attributes: surgery_id, patient_id, surgeon_id, surgery_date
For example:
Test	Result
SELECT * FROM surgeries;
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28
3           3           3           2024-03-25
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28

```sql
--DELETE FROM Surgeries
where surgery_id =3;
```

**Output:**

![image](https://github.com/user-attachments/assets/6747e911-3eaf-4aae-b49b-65bbf6c22aa6)


**Question 9**
---
-- Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
For example:

Test	Result
SELECT * FROM surgeries;
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28
3           3           3           2024-03-25
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
3           3           3           2024-03-25

```sql
--delete from Surgeries
where surgery_date='2024-02-28';
```

**Output:**
![image](https://github.com/user-attachments/assets/4923b6c7-c01c-4ed0-9887-bf4eb3e63503)


**Question 10**
---
-- Write a query to get all the records from EmployeePosition table who have joined in the year 2020.

EmpID
EmpPosition
DateOfJoining
Salary
1
Manager
01/05/2024
500000
2
Executive
02/05/2024
75000

For example:

Result
EmpID       EmpPosition  DateOfJoining  Salary
----------  -----------  -------------  ----------
1           Manager      2020-05-01     500000
2           Executive    2020-05-02     75000
1           Manager      2020-05-01     500000
2           Executive    2020-05-02     75000

```sql
-- select * from EmployeePosition 
where DateOfJoining between '2020-01-01' and '2020-12-31';
```

**Output:**

![image](https://github.com/user-attachments/assets/7cb71cea-910e-476f-b2c1-62ffa05069ba)

SEB OUTPUT GRADE:
![image](https://github.com/user-attachments/assets/1ba90d65-4990-4054-aa72-ab7e9382d145)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
