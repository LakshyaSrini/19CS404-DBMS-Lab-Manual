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

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

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

Table name: dept
 
name        type

deptno       INT
dname       VARCHAR(100)
loc         VARCHAR(100)
For example:

Result
dept_location

ACCOUNTING, NEW YORK
RESEARCH, DALLAS
SALES, CHICAGO
OPERATIONS, BOSTON

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

emp table

cid         name        type        

0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT         
For example:

Result
ename       hiredate    DateAfter100Days

JONES       1981-04-02  1981-07-11
MARTIN      1981-09-28  1982-01-06
BLAKE       1981-05-01  1981-08-09
CLARK       1981-06-09  1981-09-17
SCOTT       1982-12-09  1983-03-19
KING        1981-11-17  1982-02-25
TURNER      1981-09-08  1981-12-17

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

emp table

cid         name        type        

0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT         
For example:

Result
ename       hiredate    days_worked

SMITH       2024-06-02  212.0
ALLEN       2024-07-20  164.0
WARD        2024-11-02  59.0

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

Sample table: Products

product_id | original_price | discount_percentage 

------------+----------------+--------------------- 

101 | 50.00 | 0.10 

102 | 75.00 | 0.00 

103 | 100.00 | 0.20

 

For example:

Result
product_id  original_price  discount_percentage  discounted_price
----------  --------------  -------------------  ----------------
101         50.0            0.1                  45.0
102         75.0            0.15                 63.75
103         100.0           0.2                  80.0


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

cid         name        type        notnull     dflt_value  pk

0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
 

For example:

Result
id          rounded_value

1           123.457
2           567.891
3           78.234
4           45.78

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

cid         name        type        notnull     dflt_value  pk

0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
 

For example:

Result
id          decimal     category

1           123.4567    High
2           567.891     High
3           78.234      Medium
4           45.78       Low

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

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT
For example:

Result
patient_id  first_name  admission_date  discharge_date
----------  ----------  --------------  --------------
4           Abhishek    2023-02-10      2023-02-10
5           Alice       2023-08-02      2023-08-02

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

name                     type

CategoryID           INTEGER
CategoryName     VARCHAR(25)
Description          VARCHAR(255)

For example:

Result
CategoryName  Description

Beverages     Soft drinks, coffees, teas, beers, and ales
Fruits        Apple, Grapes, Kiwi

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


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
