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
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

![image](https://github.com/user-attachments/assets/d921da7b-d711-4050-9198-ffe9fdc79f57)

# Query
```sql
UPDATE suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**

![Screenshot 2025-04-29 194718](https://github.com/user-attachments/assets/fcf153a2-cb5b-48e2-8f1c-1430c702a7e6)


**Question 2**
---
Write a SQL query to Retrieve the department name and location concatenated with a comma

![image](https://github.com/user-attachments/assets/6a22eeb7-eefc-4f0b-976d-501cef70c427)


# Query
```sql
SELECT dname || ', ' || loc AS dept_location
FROM dept;
```

**Output:**

![Screenshot 2025-04-29 194949](https://github.com/user-attachments/assets/23294c8c-c2f9-430a-9838-7de5710e0531)


**Question 3**
---
Write a SQL query to find the exact date that is 100 days after each employee's hire date.


![image](https://github.com/user-attachments/assets/6bf854f1-1dde-4bb0-9d77-08ce8a2834e6)


# Query
```sql
SELECT ename,hiredate,DATE(JULIANDAY(hiredate)+100) AS DateAfter100Days
FROM emp;
```

**Output:**

![Screenshot 2025-04-29 195230](https://github.com/user-attachments/assets/44168a58-fb29-4a53-9b7d-b9d252fb4577)


**Question 4**
---
Write a SQL query to calculate the number of days between the hiredate and a specified date ('2024-12-31') for each employee using the JULIANDAY function from the emp table.


![image](https://github.com/user-attachments/assets/7789690a-bb06-470e-b2f4-1298db6ac612)


# Query
```sql
SELECT ename,hiredate,JULIANDAY('2024-12-31') - JULIANDAY(hiredate) AS days_worked
FROM emp;
```

**Output:**

![Screenshot 2025-04-29 195400](https://github.com/user-attachments/assets/cc304487-e226-4429-906b-ca5e09bf50b6)


**Question 5**
---
Write a SQL query to calculate the discounted price for products where the discount percentage is greater than 0, and order the results by discounted_price in ascending order. Return product_id, original_price, discount_percentage, and discounted_price.


![image](https://github.com/user-attachments/assets/af9f4a30-383c-4ddf-8313-0c71fffc102b)

# Query
```sql
SELECT product_id , original_price ,discount_percentage , (original_price *(1-Discount_percentage)) AS discounted_price
FROM Products
WHERE discount_percentage > 0 
ORDER BY discounted_price ASC;
```

**Output:**

![Screenshot 2025-04-29 195559](https://github.com/user-attachments/assets/b226c524-613d-4b19-baa1-2aeef320b289)


**Question 6**
---
Write a SQL query to round the decimal column to 3 decimal places from the Calculations table.


![image](https://github.com/user-attachments/assets/83455bf8-7550-4087-ba96-42df8f9642b1)



# Query
```sql
SELECT id,ROUND(decimal,3) AS rounded_value
FROM Calculations;

```

**Output:**

![Screenshot 2025-04-29 195942](https://github.com/user-attachments/assets/95229a90-46a5-4c5b-802e-923b803103f8)


**Question 7**
---
Write a SQL query to categorize decimal as 'High', 'Medium', or 'Low' based on whether it is greater than 100, between 50 and 100, or less than 50 in the Calculations table

![image](https://github.com/user-attachments/assets/187173e5-8d63-4619-a834-32f98dc2eaf0)


# Query
```sql
SELECT id, decimal,
CASE
WHEN decimal > 100 THEN 'High'
WHEN decimal BETWEEN 50 AND 100 THEN 'Medium'
ELSE 'Low'
END AS category
FROM Calculations;
```

**Output:**

![Screenshot 2025-04-29 200118](https://github.com/user-attachments/assets/ec305079-d2a9-47c9-a0ba-591ec6f94861)


**Question 8**
---
Write a SQL query to Select all patients who were admitted for one day.

Table: Patients



![image](https://github.com/user-attachments/assets/b670ea5a-0179-44c7-9f8b-0f58f02b8608)



# Query
```sql
SELECT patient_id , first_name , admission_date , discharge_date
FROM Patients
WHERE admission_date = discharge_date ;
```

**Output:**

![Screenshot 2025-04-29 200230](https://github.com/user-attachments/assets/b537251e-f63f-4fc3-b7a7-35bceecad41b)


**Question 9**
---
Show the categoryName and description from the categories table sorted by categoryName.


![image](https://github.com/user-attachments/assets/15ba9091-8a85-4b12-94c1-7e5fbc6b6b16)


# Query
```sql
SELECT CategoryName , Description
FROM categories
ORDER BY categoryName ASC;
```

**Output:**

![Screenshot 2025-04-29 200352](https://github.com/user-attachments/assets/f467016e-8c5f-40d1-9184-d7efbf74f50b)


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

# Query
```sql
DELETE FROM Customer
WHERE grade <> 3;
```

**Output:**

![Screenshot 2025-04-29 200508](https://github.com/user-attachments/assets/149ff21b-4511-46d5-885b-f77f7e663f6f)

# Screenshot of Module 1 SEB Completion Grades
![image](https://github.com/user-attachments/assets/1932eecb-faa6-4cb2-83b2-35fb1ff55966)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
