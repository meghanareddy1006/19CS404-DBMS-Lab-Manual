# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
--How many prescriptions were written by each doctor?

Sample tablePrescriptions Table

For example:

Result
DoctorID    TotalPrescriptions
----------  ------------------
1           1
2           1
3           1
4           1
5           1
6           1
7           1
8           1
9           1
10          1

```sql
-- SELECT DoctorID,count(*)as TotalPrescriptions from Prescriptions
group by DoctorID;
```

**Output:**

![image](https://github.com/user-attachments/assets/26bcfad7-56f8-46e7-936f-e0cb9e545dba)

**Question 2**
---
-- How many medical records are there for each patient?

Sample table:MedicalRecords Table

For example:

Result
PatientID   TotalRecords
----------  ------------
4           4
5           1
6           1
7           1
8           1

```sql
--select PatientID,count(*) as TotalRecords from MedicalRecords
group by PatientID
order by PatientID; 
```

**Output:**
![image](https://github.com/user-attachments/assets/cef070d3-ef49-457c-bf22-81bbcd196dad)


**Question 3**
---
-- What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table
For example:

Result
Medication     AvgDosage
-------------  ----------
Ciprofloxacin  500.0
Doxorubicin    60.0
Ibuprofen      400.0
Levothyroxine  50.0
Lisinopril     10.0
MMR            0.5
Pending        0.0
Prenatal vita  1.0
Sertraline     50.0
Topiramate     25.0

```sql
-- SELECT Medication,AVG(dosage) as AvgDosage from Prescriptions
group by Medication;

```

**Output:**
![image](https://github.com/user-attachments/assets/62c3db60-d077-48b7-bfa6-1547bbf9e32b)


**Question 4**
---
-- Write a SQL query to count the number of customers. Return number of customers.

Sample table: customer
customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002
For example:

Result
COUNT
--

```sql
-- select count(*) as COUNT from customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/024d176f-bc75-4d92-a661-5bb5f713afaa)

**Question 5**
---
-- Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 

Note: Inventory attribute contains amount of fruits
Table: fruits
name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
For example:

Result
total_available_amount
----------------------
160

```sql
--select sum(inventory) as total_available_amount from fruits
where price>0.5;
```

**Output:**

![image](https://github.com/user-attachments/assets/ac22288e-7ede-445e-acb7-5dbe4a9afc3f)

**Question 6**
---
-- Write a SQL query to find the minimum purchase amount.
Sample table: orders
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
For example:

Result
MINIMUM
----------
65.26

```sql
-- select min(purch_amt)as MINIMUM from orders;
```

**Output:**
![image](https://github.com/user-attachments/assets/7ff7c106-0c60-4551-a802-9f4fce00542f)


**Question 7**
---
-- Write a SQL query to find the total income of employees aged 40 or above.
Table: employee
name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
total_income
------------
1800000

```sql
--SELECT SUM(income) as total_income from employee
where age>=40;
```

**Output:**

![image](https://github.com/user-attachments/assets/fdc39ff5-e30b-46a2-8102-107e8c1eca9e)

**Question 8**
---
--Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee
For example:
Result
age         Income
----------  ----------
32          200000
40          350000
45          450000

```sql
-- select age,min(income) as Income from employee
group by age
having income <1000000;
```

**Output:**
![image](https://github.com/user-attachments/assets/4cef10f5-f777-4665-acf6-d0a7cde9b8bb)


**Question 9**
---
-- Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.

Sample table: products
For example:

Result
category_id  product_name  Price
-----------  ------------  ----------
1            Orange        15.5
2            Monitor       25

```sql
-- select category_id ,product_name,max(price) as Price from products
group by category_id
having price > 15;
```

**Output:**

![image](https://github.com/user-attachments/assets/f5f9c0c1-2e73-48c0-9248-6c992db4bc4f)

**Question 10**
---
--Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.
Sample table: employee
For example:

Result
city        Income
----------  ----------
Alaska      450000
Arizona     1000000
California  5300000
Florida     5350000
Georgia     250000 

```sql
-- select city,sum(income) as Income from employee
group by city
having income >200000;
```

**Output:**
![image](https://github.com/user-attachments/assets/1c6890e1-b6fb-4b3f-8b5c-acbd3d4dab1a)

SEB OUTPUT GRADE:
![image](https://github.com/user-attachments/assets/5d7190d1-9113-4f37-bbf9-645ea289c1a4)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
