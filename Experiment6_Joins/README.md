# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id
```
SELECT p.first_name AS patient_name, t.*
FROM patients AS p
INNER JOIN test_results AS t
ON p.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';
```

**Output:**

<img width="1308" height="447" alt="image" src="https://github.com/user-attachments/assets/b843203c-7edf-49be-a744-980116985d25" />


**Question 2**
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman

```
SELECT s.name AS Salesman,
       c.cust_name,
       s.city
FROM salesman s
JOIN customer c
ON s.city = c.city;
```

**Output:**

<img width="997" height="730" alt="image" src="https://github.com/user-attachments/assets/91d09981-50f9-4291-8c32-ed031f3c6347" />


**Question 3**
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

Sample table: customer



```
SELECT c.cust_name,
       c.city,
       o.ord_no,
       o.ord_date,
       o.purch_amt AS "Order Amount",
       s.name,
       s.commission
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
LEFT JOIN salesman s
ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1328" height="731" alt="image" src="https://github.com/user-attachments/assets/4eae7d45-e864-4abd-aa0c-31837591965f" />


**Question 4**
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

Sample table: orders

```
SELECT o.ord_no,
       o.ord_date,
       o.purch_amt,
       c.cust_name AS "Customer Name",
       c.grade,
       s.name AS "Salesman",
       s.commission
FROM orders o
JOIN customer c
    ON o.customer_id = c.customer_id
JOIN salesman s
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1311" height="817" alt="image" src="https://github.com/user-attachments/assets/11079962-8005-41e4-a457-053eb627a100" />


**Question 5**
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer

```
SELECT c.cust_name,
       c.city,
       c.grade,
       s.name AS Salesman,
       s.city
FROM customer c
JOIN salesman s
    ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="1301" height="843" alt="image" src="https://github.com/user-attachments/assets/11a9f812-c2db-45fe-9645-dce84035dcb4" />


**Question 6**
Write the SQL query that achieves the selection of all columns from the "patients" table, with an inner join on the "doctor_id" column, and includes a condition filtering for patients whose doctors have the first name 'John' and last name 'Smith'.

PATIENTS TABLE:

```
SELECT p.*
FROM patients p
INNER JOIN doctors d
    ON p.doctor_id = d.doctor_id
WHERE d.first_name = 'John'
  AND d.last_name = 'Smith';
```

**Output:**

<img width="1295" height="472" alt="image" src="https://github.com/user-attachments/assets/7ca4ec6b-0d1d-4657-bc0d-c988d137d674" />


**Question 7**
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

Sample table: customer

```
SELECT c.cust_name AS "Customer Name",
       c.city,
       s.name AS Salesman,
       s.commission
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1281" height="817" alt="image" src="https://github.com/user-attachments/assets/2cdcc9d8-8566-4056-b179-3ca397683369" />


**Question 8**
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

```
SELECT s.name,
       c.cust_name,
       c.city,
       c.grade,
       c.salesman_id
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id
WHERE c.salesman_id IN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
)
ORDER BY c.salesman_id, c.customer_id;
```

**Output:**

<img width="1308" height="662" alt="image" src="https://github.com/user-attachments/assets/8d2d89bb-e0d9-4bf5-96f9-c66c8b7302e3" />


**Question 9**
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```
SELECT c.cust_name,
       o.ord_no,
       o.ord_date,
       o.purch_amt
FROM customer AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id;
```

**Output:**

<img width="1256" height="713" alt="image" src="https://github.com/user-attachments/assets/11b31023-a099-4d0f-9231-b4b65490ad86" />


**Question 10**
Write the SQL query that achieves the selection of all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id



```
SELECT t.*
FROM test_results AS t
INNER JOIN patients AS p
    ON t.patient_id = p.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

<img width="1305" height="448" alt="image" src="https://github.com/user-attachments/assets/05d52f8b-77b5-4e26-b5e9-bbab3c2fb39f" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
