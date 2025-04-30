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

**Question 1**
--
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email
![Screenshot 2025-04-30 131006](https://github.com/user-attachments/assets/a4c9f594-3be4-4c1b-bee8-fa8eb99ff1af)

# Query
```sql
INSERT INTO Customers
SELECT CustomerID, Name, Address, Email
FROM Old_customers;
```

**Output:**
![Screenshot 2025-04-29 192142](https://github.com/user-attachments/assets/2956cfaa-d3b2-4d37-92c3-87c2d6a478cf)


**Question 2**
---
Write a SQL query to add a new column MobileNumber of type NUMBER and a new column Address of type VARCHAR(100) to the Student_details table.
![Screenshot 2025-04-30 131046](https://github.com/user-attachments/assets/f49662a7-d529-4ab4-8b37-f94d47a6624c)

# Query
```sql
ALTER TABLE Student_details
ADD COLUMN MobileNumber NUMBER;
ALTER TABLE Student_details
ADD COLUMN Address VARCHAR(100);

```

**Output:**
![Screenshot 2025-04-29 192347](https://github.com/user-attachments/assets/a1e3cf10-5c47-42a2-a444-094aa6fabfe2)


**Question 3**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
![Screenshot 2025-04-30 131138](https://github.com/user-attachments/assets/e3212864-b363-4461-bb3f-29a8c275456f)


# Query
```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL CHECK(Amount>0),
DueDate DATE CHECK(DueDate>InvoiceDate),
OrderID INTEGER,
foreign key (OrderID) references  Orders(OrderID));
```

**Output:**

![Screenshot 2025-04-29 192832](https://github.com/user-attachments/assets/d8a0b1b0-de30-4533-88b6-d7641bf4f62d)


**Question 4**
---
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE
![Screenshot 2025-04-30 131211](https://github.com/user-attachments/assets/b991c8ea-150b-4077-8786-43ca0dc2e6c8)



# Query
```sql
CREATE TABLE Employees(
EmployeeID INTEGER,
FirstName TEXT,
LastName TEXT,
HireDate DATE);
```

**Output:**

![Screenshot 2025-04-29 192951](https://github.com/user-attachments/assets/2770d89d-9963-4c67-865d-be038221ac2c)


**Question 5**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.


# Query
```sql
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT UNIQUE NOT NULL,
Location TEXT);
```

**Output:**

![Screenshot 2025-04-29 193126](https://github.com/user-attachments/assets/2de29a1a-bca1-4704-a342-7e22c44d8d60)


**Question 6**
---
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

![Screenshot 2025-04-30 131321](https://github.com/user-attachments/assets/c4554dc2-8b1b-4584-b153-f8a1ecb56032)


# Query
```sql
ALTER TABLE customer
ADD COLUMN birth_date
timestamp;
```

**Output:**

![Screenshot 2025-04-29 193253](https://github.com/user-attachments/assets/bac8c0ad-76d8-4728-bf9d-63160683d440)

**Question 7**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

![Screenshot 2025-04-30 131352](https://github.com/user-attachments/assets/636acb2d-7512-4f86-9e68-52a20742a2ba)


# Query
```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(205,'Olivia Green','F',NULL,NULL);
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(207,'Liam Smith','M','Mathematics',85);
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(208,'Sophia Johnson','F','Science',NULL);
```

**Output:**

![Screenshot 2025-04-29 193410](https://github.com/user-attachments/assets/452b2f27-0f93-4cbd-9430-e3c307042875)


**Question 8**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

# Query
```sql
CREATE TABLE Bonuses(
BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
BonusAmount REAL CHECK(BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL,
foreign key (EmployeeID) references Employees(EmployeeID));
```

**Output:**

![Screenshot 2025-04-29 193538](https://github.com/user-attachments/assets/d4be315a-dcd6-4014-8dbc-3d61a1cb8342)


**Question 9**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
For example:

Test	
INSERT INTO Shipments (ShipmentID, ShipmentDate, SupplierID, OrderID) VALUES (2, '2024-08-03', 99, 1);
Result
Error: FOREIGN KEY constraint failed

# Query
```sql
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
foreign key (SupplierID) references Suppliers(SupplierID),
foreign key (OrderID) references Orders(OrderID));
```

**Output:**

![Screenshot 2025-04-29 193651](https://github.com/user-attachments/assets/b76d1407-6b14-404e-b72e-44d419c6b968)


**Question 10**
---
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.



# Query
```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
VALUES('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**

![Screenshot 2025-04-29 193752](https://github.com/user-attachments/assets/b49f81cd-8792-417a-85f9-1201b2ac69eb)


# Screenshot of Module 1 SEB Completion Grades
![Screenshot 2025-04-30 131707](https://github.com/user-attachments/assets/3b19dd95-30bb-4263-a17c-4ec80c9abf95)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
