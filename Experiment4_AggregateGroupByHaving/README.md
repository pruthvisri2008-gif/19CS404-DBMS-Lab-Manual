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
What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table



```
select
    Medication,
    AVG(Dosage) AS AvgDosage
from Prescriptions
group by Medication;
```

**Output:**

<img width="745" height="775" alt="image" src="https://github.com/user-attachments/assets/7ee55249-88b0-4130-b8e4-06866b2ceeb7" />


**Question 2**
What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table



```
select DoctorID, count(*) as TotalAppointments
from Appointments
group by DoctorID;
```

**Output:**

<img width="712" height="642" alt="image" src="https://github.com/user-attachments/assets/0cfcd019-953c-46cd-993c-af7a232c5588" />


**Question 3**
How many appointments are scheduled for each doctor?

Sample table:Appointments Table

```
select DoctorID, count(*) as TotalAppointments
from Appointments
group by DoctorID;
```

**Output:**

<img width="712" height="651" alt="image" src="https://github.com/user-attachments/assets/88a94ef7-4f9f-4326-b70f-2dd417f38b45" />


**Question 4**
Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```
select AVG(LENGTH(email)) AS avg_email_length
from customer;
```

**Output:**

<img width="577" height="366" alt="image" src="https://github.com/user-attachments/assets/6ac57cdd-b9c9-44a5-af2d-bc145f4d098b" />


**Question 5**
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

```
select COUNT(*) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

<img width="525" height="362" alt="image" src="https://github.com/user-attachments/assets/53551c7d-5848-4300-9bc3-e8d11c1d7944" />


**Question 6**
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```
select AVG(LENGTH(name)) AS avg_name_length
FROM customer
where city = 'Chennai';
```

**Output:**

<img width="502" height="363" alt="image" src="https://github.com/user-attachments/assets/42ba6508-a80c-4678-9e3d-49a663332179" />


**Question 7**
Write a SQL query to find the minimum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```
select MIN(purch_amt) AS MINIMUM
FROM orders;
```

**Output:**

<img width="446" height="415" alt="image" src="https://github.com/user-attachments/assets/b53a944f-0a30-435d-807a-d9ddaa3c5789" />


**Question 8**
Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

Table: customer1

```
select 
    (age/5)*5 AS age_group,
    MIN(salary) 
from customer1
group by (age/5)*5
HAVING MIN(salary) < 2000;
```

**Output:**

<img width="682" height="390" alt="image" src="https://github.com/user-attachments/assets/646c261b-1a40-4473-b4be-03055ce2c6b4" />


**Question 9**
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

Sample table: customer1


```
SELECT (age/5)*5 as age_group,SUM(salary)
from customer1
group by age_group   
having SUM(salary) > 5000;
```

**Output:**

<img width="637" height="396" alt="image" src="https://github.com/user-attachments/assets/15be2f11-e200-4646-801d-3d75bdb530a3" />


**Question 10**
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

Sample table: customer1

```
SELECT address,SUM(salary)
from customer1
group by address   
having SUM(salary) > 2000;
```

**Output:**

![Uploading image.png…]()



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
