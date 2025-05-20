# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
Write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count from the given rables

```sql
SELECT grade, COUNT(*)
FROM customer
WHERE grade > (
SELECT avg(grade)
FROM customer
WHERE city = 'New York')
GROUP BY grade
```

**Output:**

![image](https://github.com/user-attachments/assets/491d1527-269d-4078-8268-b79d633bf9e3)


**Question 2**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500
```

**Output:**

![image](https://github.com/user-attachments/assets/dcc51205-3948-47a3-a22d-dc2c35158552)


**Question 3**
---
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)
![image (6)](https://github.com/user-attachments/assets/584cb093-acf9-4f51-8f19-cc038d5c3733)

```sql
SELECT medication_id, medication_name, dosage
FROM Medications
WHERE CAST(REPLACE(dosage, 'mg', '') AS INT) = (
SELECT MAX(CAST(REPLACE(dosage, 'mg', '') AS INT))
FROM Medications
)

```

**Output:**

![image](https://github.com/user-attachments/assets/4f8dada7-bbdf-4f93-92cf-bed8f5a9f527)


**Question 4**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500
```

**Output:**

![image](https://github.com/user-attachments/assets/b5cc6f15-1884-4275-a9f7-2b8f9c037b59)


**Question 5**
---
Write a SQL query to find salespeople who had more than one customer. Return salesman_id and name from the given tables

```sql
SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id) > 1

```

**Output:**

![image](https://github.com/user-attachments/assets/a280e951-c0a4-4ad7-aea8-d07674a05779)


**Question 6**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE customer_id = (
SELECT salesman_id
FROM salesman
WHERE name = 'Mc Lyon') - 2001
```

**Output:**

![image](https://github.com/user-attachments/assets/38375a5c-c549-4da2-a3a5-c28363eec556)


**Question 7**
---
Write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id from the given tables

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, orders.salesman_id
FROM orders
JOIN salesman
ON orders.salesman_id = salesman.salesman_id
WHERE salesman.name = 'Paul Adam'
```

**Output:**

![image](https://github.com/user-attachments/assets/cc292c51-48ac-4760-8b48-1904075b243b)


**Question 8**
---
Write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id from the given tables

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, orders.salesman_id
FROM orders
JOIN salesman
ON orders.salesman_id = salesman.salesman_id
WHERE salesman.city = 'New York'
```

**Output:**

![image](https://github.com/user-attachments/assets/61210d70-094d-4d6d-9063-8310b19c3637)


**Question 9**
---
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

```sql
SELECT *
FROM GRADES g
WHERE grade = (
SELECT MIN(grade)
FROM GRADES
WHERE subject = g.subject)
```

**Output:**

![image](https://github.com/user-attachments/assets/44b07486-4f69-4178-b6d3-6f84d638c57a)


**Question 10**
---
Write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id from the given tables.

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s
ON o.salesman_id = s.salesman_id
WHERE s.commission = (
SELECT MAX(commission)
FROM salesman)

```

**Output:**

![image](https://github.com/user-attachments/assets/9a8d529c-3bb0-499d-9c5b-46d8af6bb0b9)



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
