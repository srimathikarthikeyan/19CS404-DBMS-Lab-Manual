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
How many male and female doctors are there in each medical specialty?

Sample table: Doctors Table
![image (4)](https://github.com/user-attachments/assets/38b9a8b9-a4ea-44bc-b2a1-32871e168642)

```sql
    SELECT Specialty, Gender, COUNT(DoctorID) AS TotalDoctors
    FROM Doctors
    GROUP BY Specialty,gender
```
    
**Output:**

![image](https://github.com/user-attachments/assets/11ded668-e771-44c0-9524-e5f94c8c1007)


**Question 2**
--
What is the total number of appointments scheduled by each doctor?

Sample table: Appointments table
![image (5)](https://github.com/user-attachments/assets/f23be234-921a-4174-9d7c-fb94c784af89)

```sql
    SELECT DoctorID, COUNT(AppointmentID) AS TotalAppointments
    FROM Appointments
    GROUP BY DoctorID
```
    
**Output:**

![image](https://github.com/user-attachments/assets/4ec7113f-0499-46fc-b652-77db99dc9b85)


**Question 3**
--
How many appointments are scheduled in each hour of the day?

```sql
    SELECT STRFTIME('%H', AppointmentDateTime) AS HourOfDay, COUNT(*) AS TotalAppointments
    FROM Appointments
    GROUP BY HourOfDay
    ORDER BY HourOfDay
```

**Output:**

![image](https://github.com/user-attachments/assets/f030b275-4e82-48a9-ad32-e9fe9ecfb56a)


**Question 4**
--
Write a SQL query to find  how many employees work in California?

```sql
    SELECT COUNT(*) AS employees_in_california
    FROM employee
    GROUP BY city HAVING city = 'California'
```

**Output:**

![image](https://github.com/user-attachments/assets/527f21c5-ffcd-4523-b1ee-acb5cd305629)


**Question 5**
--
Write a SQL query to find the total number of unique cities in the customer table?

```sql
    SELECT COUNT(city) AS unique_cities
    FROM customer
    ORDER BY city limit 1
```

**Output:**

![image](https://github.com/user-attachments/assets/8e7f5158-da5a-40c0-b16b-552d4b88bcf1)


**Question 6**
--
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

```sql
    SELECT MAX(age) - MIN(age) AS age_difference 
    FROM employee
```

**Output:**

![image](https://github.com/user-attachments/assets/cb55c152-d990-4602-b243-07ee71bd38f2)


**Question 7**
--
Write a SQL query to  find the average salary of all employees?

```sql
    SELECT AVG(income) AS Average_Salary
    FROM employee
```

**Output:**

![image](https://github.com/user-attachments/assets/04843c47-404f-4c22-a5a7-60be79250fb7)


**Question 8**
--
Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000

Sample table: customer1
![unnamed](https://github.com/user-attachments/assets/76aa6f72-9a2e-465b-ac0a-87a98f529990)

```sql
    SELECT address, AVG(salary)
    FROM customer1
    GROUP BY address HAVING AVG(salary) < 15000
```

**Output:**

![image](https://github.com/user-attachments/assets/41bd5921-f3ec-436c-8a5d-599f269890ec)


**Question 9**
--
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1
![unnamed](https://github.com/user-attachments/assets/bcb889bc-26a8-467f-b058-815cedd30868)

```sql
    SELECT occupation, AVG(workhour)
    FROM employee1
    GROOUP BY occupation HAVING AVG(workhour) BETWEEN 10 AND 12
```

**Output:**

![image](https://github.com/user-attachments/assets/fd22181b-76c2-4a3f-9a8f-44ef999224c1)


**Question 10**
--
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee
![unnamed](https://github.com/user-attachments/assets/c6ca4449-b41e-461a-9a86-c042340545c8)

```sql
    SELECT age, MIN(income) AS Income
    FROM employee
    GROUP BY age HAVING MIN(income) < 1000000
```

**Output:**

![image](https://github.com/user-attachments/assets/77799283-2861-40b0-ac01-05b75a90a921)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
