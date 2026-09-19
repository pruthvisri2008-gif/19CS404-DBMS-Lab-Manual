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
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```
UPDATE products
SET  product_name = 'Premium Bread'
WHERE product_id = 5;
```

**Output:**

<img width="1253" height="465" alt="image" src="https://github.com/user-attachments/assets/78462961-0cfa-4447-9938-8760f8ce3046" />


**Question 2**

For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)

```
UPDATE sales 
set sell_price = sell_price + 3
where product_id IN (
    select product_id
    from products
    where supplier_id = 4
);
```

**Output:**

<img width="1251" height="427" alt="image" src="https://github.com/user-attachments/assets/4b3fa811-10f2-430c-bf13-e923908b0936" />


**Question 3**
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

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

```
update employees
set first_name = 'John'
where department_id = 80 and commission_pct < 0.35;
```

**Output:**

<img width="1272" height="590" alt="image" src="https://github.com/user-attachments/assets/b3983246-c591-4e2e-ae61-c5c00448bbe5" />


**Question 4**

Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```
update suppliers
set supplier_name = upper(supplier_name)
where contact_person like '%Singh%';
```

**Output:**

<img width="1280" height="406" alt="image" src="https://github.com/user-attachments/assets/2cab0848-c9a4-4e25-a3e2-b8a6d55eb5b6" />


**Question 5**

Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

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

```
update employees
set email = 'Unavailable'
```

**Output:**

<img width="1275" height="487" alt="image" src="https://github.com/user-attachments/assets/097de435-64f4-4530-a2f7-205c8c899610" />


**Question 6**
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |


```
delete from Customer
where LENGTH(CUST_NAME)=6;
```

**Output:**

<img width="1267" height="740" alt="image" src="https://github.com/user-attachments/assets/5c44bcf8-d34a-44ae-b350-5f27783abe42" />


**Question 7**
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

Sample table: Customer



```
delete from Customer
where (GRADE=2 or CUST_NAME='M')
and PAYMENT_AMT < 3000;
```

**Output:**

<img width="1261" height="468" alt="image" src="https://github.com/user-attachments/assets/c2da7148-6f38-405b-9bb5-1f1486e65b15" />


**Question 8**
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',

Sample table: Customer

```
delete from customer
where cust_country = 'India'
    and cust_city != 'Chennai';
```

**Output:**

<img width="1272" height="835" alt="image" src="https://github.com/user-attachments/assets/df929cbf-e1ea-4cfe-ae14-51d1da7c1261" />


**Question 9**
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

Sample table: Customer



```
delete from Customer
where OPENING_AMT between 4000 and 6000;
```

**Output:**

<img width="1252" height="615" alt="image" src="https://github.com/user-attachments/assets/981bcaa9-7987-41fb-ac89-0923f9fbea82" />


**Question 10**
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

 
Sample table: Customer

```
delete from Customer
where GRADE >= 2;
```

**Output:**

<img width="697" height="586" alt="image" src="https://github.com/user-attachments/assets/e51c86af-b0ef-4a24-861d-85df4fb32d97" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
