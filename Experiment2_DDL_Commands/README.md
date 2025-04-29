# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

## PROGRAMS

### Question 1

Create a table named Members with the following columns:
    - MemberID as INTEGER
    - MemberName as TEXT
    - JoinDate as DATE

    CCREATE TABLE Members(
    MemberID INTEGER,
    MemberName TEXT,
    JoinDate DATE);

**Output:**

![image](https://github.com/user-attachments/assets/b1cfd9dd-c5ee-4168-89a6-3e2df6a1a344)



### Question 2

Create a table named Products with the following columns:
  - ProductID as INTEGER
  - ProductName as TEXT
  - Price as REAL
  - Stock as INTEGER

        CREATE TABLE Products(
        ProductID INTEGER,
        ProductName TEXT,
        Price REAL,
        Stock INTEGER);

**Output:**

![image](https://github.com/user-attachments/assets/83cdc4c3-e700-463f-af5a-ae2ef5c5f1ba)



### Question 3

Create a table named Orders with the following constraints:
- OrderID as INTEGER should be the primary key.
- OrderDate as DATE should be not NULL.
- CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).


      CREATE TABLE Orders(
      OrderID INT PRIMARY KEY,
      OrderDate DATE NOT NULL,
      CustomerID INT,
      FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID));

**Output:**

![image](https://github.com/user-attachments/assets/11fac081-a6a0-4a20-a28d-be0f361dc2ce)



### Question 4

Write a SQL query to Add a new column mobilenumber as number in the Student_details table.

    ALTER TABLE Student_details ADD mobilenumber number;

**Output:**

![image](https://github.com/user-attachments/assets/2677d406-eb76-4cfa-94a8-f4e5beb53672)



### Question 5

Write an SQL command can to add a column named email of type TEXT to the customers table

    ALTER TABLE Customers ADD email TEXT;

**Output:**

![image](https://github.com/user-attachments/assets/75e626a1-6214-4dbf-a1eb-4843e95590f1)



### Question 6

Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.

    ALTER TABLE Student_details ADD ParentsNumber number;
    ALTER TABLE STudent_details ADD Adhar_Number number;

**Output:**

![image](https://github.com/user-attachments/assets/434c518d-b5c6-404f-93a6-f709d9f30b90)



### Question 7

In the Cusomers table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

CustomerID  Name          Address      City        ZipCode
----------  ------------  ----------   ----------  ----------
306         Diana Prince  Themyscira
307         Bruce Wayne   Wayne Manor  Gotham      10007
308         Peter Parker  Queens                   11375

    INSERT INTO Customers(CustomerID, Name, Address, City, ZipCode) VALUES(306, 'Diana Prince', 'Themyscira', NULL, NULL);
    INSERT INTO Customers(CustomerID, Name, Address, City, ZipCode) VALUES(307, 'Bruce Wayne', 'Wayne Manor', 'Gotham', 10007);
    INSERT INTO Customers(CustomerID, Name, Address, City, ZipCode) VALUES(308, 'Peter Parker', 'Queens', NULL, 11375);

**Output:**

![image](https://github.com/user-attachments/assets/48fb22a0-ace9-4fa5-88b8-2daae5d069dd)



### Question 8

Insert all products from Discontinued_products into Products.
Table attributes are ProductID, ProductName, Price, Stock


    INSERT INTO Products(ProductID, ProductName, Price, Stock) 
    SELECT ProductID, ProductName, Price, Stock 
    FROM Discontinued_products;

**Output:**

![image](https://github.com/user-attachments/assets/169e9eaa-376b-45f5-b4b3-03f0ef6d7aeb)



### Question 9

Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          

Note: The Subject and MARKS columns will use their default values.

    INSERT INTO Student_details(RollNo, Name, Gender) VALUES(204, 'Samuel Black', 'M');

**Output:**

![image](https://github.com/user-attachments/assets/e7958b6a-c4b5-4c6c-9260-4aac79787ff1)



### Question 10

Insert all books from Out_of_print_books into Books
Table attributes are ISBN, Title, Author, Publisher, YearPublished

    INSERT INTO Books(ISBN, Title, Author, Publisher, YearPublished)
    SELECT ISBN, Title, Author, Publisher, YearPublished 
    FROM Out_of_print_books

**Output:**

![image](https://github.com/user-attachments/assets/898d7a53-ddb1-4ea4-a2aa-2fa84362eb03)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
