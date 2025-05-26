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
--
Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.

NURSES TABLE:

ATTRIBUTES - nurse_id, first_name, last_name, department_id



DEPARTMENTS TABLE:

ATTRIBUTES - department_id, department_name

```sql
SELECT n.nurse_id, d.department_name
FROM nurses AS n
INNER JOIN departments AS d
ON n.department_id = d.department_id
WHERE n.first_name = 'David' AND n.last_name = 'Moore';
```

**Output:**


![Screenshot 2025-05-12 190241](https://github.com/user-attachments/assets/9d267cb5-4dec-4aef-a73c-cbfac28525b4)

**Question 2**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 



```sql
SELECT 
    o.ord_no, o.purch_amt, o.ord_date, 
    c.cust_name AS cust_name, c.city AS customer_city, c.grade, 
    s.name AS salesman_name, s.city AS salesman_city, s.commission
FROM orders AS o
INNER JOIN customer AS c ON o.customer_id = c.customer_id
INNER JOIN salesman AS s ON o.salesman_id = s.salesman_id;
```

**Output:**

![Screenshot 2025-05-12 190304](https://github.com/user-attachments/assets/31858a07-51b8-4ab0-aa5a-5b4cb15ca819)
![Screenshot 2025-05-12 190321](https://github.com/user-attachments/assets/e85a3eab-88b6-41c3-94fd-67bfbaa9590e)


**Question 3**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount less than 100.

```sql
SELECT c.cust_name
FROM customer AS c
LEFT JOIN orders AS o ON c.customer_id = o.customer_id
WHERE o.purch_amt < 100;
```

**Output:**

![Screenshot 2025-05-12 190336](https://github.com/user-attachments/assets/df2e6479-04e3-407b-a504-fea7be72e0d4)

**Question 4**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n"), with an inner join on the "department_id" column and a condition filtering for nurses in the 'Pediatrics' department.

NURSES TABLE:

ATTRIBUTES - nurse_id, first_name, last_name, department_id



DEPARTMENTS TABLE:

ATTRIBUTES - department_id, department_name

```sql
SELECT n.*
FROM nurses AS n
INNER JOIN departments AS d ON n.department_id = d.department_id
WHERE d.department_name = 'Pediatrics';
```

**Output:**


![Screenshot 2025-05-12 190351](https://github.com/user-attachments/assets/de37b067-955e-4d54-a496-78d69a355e9a)

**Question 5**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 



```sql
SELECT 
    c.cust_name, 
    c.city AS city, 
    c.grade, 
    s.name AS Salesman, 
    s.city AS city
FROM customer AS c
LEFT JOIN salesman AS s ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id;
```

**Output:**

![Screenshot 2025-05-12 190408](https://github.com/user-attachments/assets/75ed914f-2fd4-4cf4-9303-4e3c1eb22d13)


**Question 6**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.



```sql
SELECT s.name AS Salesman, c.cust_name, c.city
FROM salesman AS s
INNER JOIN customer AS c ON s.city = c.city;
```

**Output:**

![Screenshot 2025-05-12 190424](https://github.com/user-attachments/assets/cb7af1a4-6809-4281-8a2b-cda8144e9bd7)


**Question 7**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  


```sql
SELECT 
    c.cust_name AS "Customer Name", 
    c.city AS "city", 
    s.name AS "Salesman", 
    s.city AS "city", 
    s.commission
FROM customer AS c
INNER JOIN salesman AS s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12 AND c.city <> s.city;
```

**Output:**

![Screenshot 2025-05-12 190440](https://github.com/user-attachments/assets/d06bcc7a-ccf9-4f84-9e47-27bd605f185f)


**Question 8**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c") and the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the same city as the salesman.

```sql
SELECT c.cust_name, s.name
FROM customer AS c
LEFT JOIN salesman AS s ON c.salesman_id = s.salesman_id
WHERE c.city = s.city;
```

**Output:**

![Screenshot 2025-05-12 190808](https://github.com/user-attachments/assets/831a4db8-4631-49d8-bbaa-1687a86023ea)


**Question 9**
---
Write the SQL query that achieves the selection of the date of birth from the "patients" table (aliased as "p") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id



APPOINTMENTS TABLE:

ATTRIBUTES - appointment_id, patient_id, doctor_id, appointment_date

```sql
SELECT p.date_of_birth, a.*
FROM patients AS p
INNER JOIN appointments AS a ON p.patient_id = a.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

![Screenshot 2025-05-12 190822](https://github.com/user-attachments/assets/4be94a6b-a58b-4ce5-bbd7-b950890b746f)


**Question 10**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  


```sql
SELECT 
    c.cust_name AS "Customer Name", 
    c.city, 
    s.name AS "Salesman", 
    s.commission
FROM customer AS c
INNER JOIN salesman AS s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;
```

**Output:**

![Screenshot 2025-05-12 190840](https://github.com/user-attachments/assets/45aec7f0-a6de-4c1c-9725-06fbf65753e6)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
