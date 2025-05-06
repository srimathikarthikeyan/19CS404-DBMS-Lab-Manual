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
## PROGRAM

### Question 1

Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.


    UPDATE Employees
    SET salary = 8000
    WHERE employee_id = 105


**Output:**

![image](https://github.com/user-attachments/assets/9dfa4084-fa2f-4f5f-89b3-b975f772b0c4)


### Question 2

Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.


    UPDATE Products
    SET category = 'Household'
    WHERE product_name LIKE '%Detergent%'


**Output:**

![image](https://github.com/user-attachments/assets/3f24aae8-3e2b-4006-b6aa-5f8fd230d008)


**Question 3**

For increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.


    UPDATE SALES
    SET sell_price = sell_price + 3
    WHERE product_id IN(
        SELECT product_id
        FROM PRODUCTS
        WHERE supplier_id = 4);


**Output:**

![image](https://github.com/user-attachments/assets/ca92bfba-15e2-4d68-a691-6a48979ce274)


**Question 4**

Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.


    DELETE FROM customer 
    WHERE GRADE >= 2


**Output:**

![image](https://github.com/user-attachments/assets/64453fed-644f-4bc2-962f-63feef24afe5)


**Question 5**

Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:


    DELETE FROM Customer
    WHERE (GRADE > 2 AND PAYMENT_AMT < (SELECT AVG(PAYMENT_AMT) FROM Customer))
        OR OUTSTANDING_AMT > 8000


**Output:**

![image](https://github.com/user-attachments/assets/fb8a3b32-13c9-40aa-951d-7fe1b09d0cd2)


**Question 6**

Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.
Sample table: Surgeries
attributes: surgery_id, patient_id, surgeon_id, surgery_date


    DELETE FROM Surgeries
    WHERE surgery_date = '2024-02-28'


**Output:**

![image](https://github.com/user-attachments/assets/779663fb-0e9e-4964-855b-0d8b6108c377)


**Question 7**

Write a SQL query to Select all patients whose name starts with A.


    SELECT * FROM Patients
    WHERE first_name LIKE 'A%'


**Output:**

![image](https://github.com/user-attachments/assets/9365d57c-2386-480f-aae5-28fb622a36fc)


**Question 8**

Show the categoryName and description from the categories table sorted by categoryName.


    SELECT categoryName, Description FROM categories
    ORDER BY categoryName


**Output:**

![image](https://github.com/user-attachments/assets/d05ab02d-edc3-470c-a7d4-2cc5cd8dc1cf)


**Question 9**

Write a SQL query to assess the performance of value2 as 'Poor', 'Average', or 'Excellent' based on whether it is less than 30, between 30 and 70, or greater than 70 in the Calculations table


    SELECT id, value2, 
        CASE
            WHEN value2 < 30 THEN 'Poor'
            WHEN value2 BETWEEN 30 AND 70 THEN 'Average'
            ELSE 'Excellent'
        END AS performance
    FROM Calculations


**Output:**

![image](https://github.com/user-attachments/assets/9de93a81-1f91-4e8c-83bd-7cd162b8d8c7)


**Question 10**

Write a SQL query to calculate the discounted price for products whose original price is between $50 and $150. Return product_id, original_price, discount_percentage, and discounted_price.


    SELECT product_id, original_price, discount_percentage, original_price * (1 - discount_percentage) AS discounted_price 
    FROM Products
    WHERE original_price BETWEEN 50 AND 150


**Output:**

![image](https://github.com/user-attachments/assets/06ea8e9c-35a5-40a8-abc1-5ea924765688)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
