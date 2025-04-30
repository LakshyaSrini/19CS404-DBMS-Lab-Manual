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
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)


![image](https://github.com/user-attachments/assets/2c12017c-bbc9-4092-affb-39f35e68c2b6)


# Query
```sql
SELECT medication_id as medic,medication_name,dosage
FROM Medications
WHERE dosage = (SELECT MIN(dosage) FROM Medications);
```

**Output:**

![image](https://github.com/user-attachments/assets/538f1423-343d-4c4c-b8a8-81c10e709952)


**Question 2**
---
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)


![image](https://github.com/user-attachments/assets/72595397-3bd3-4645-8b0d-6f1daa075cf2)


# Query
```sql
SELECT * FROM GRADES g
WHERE grade = (SELECT MIN(grade) FROM GRADES
WHERE subject = g.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/08654864-6b35-4fb3-ae58-04962868f75e)


**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS

![image](https://github.com/user-attachments/assets/df311d79-9a79-40b5-8580-2b7ee65feded)


# Query
```sql
SELECT * FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```

**Output:**

![image](https://github.com/user-attachments/assets/42642137-d948-4bbc-8f81-27ebdd2f2dfc)


**Question 4**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

![image](https://github.com/user-attachments/assets/2a13ff4a-5436-4bd5-9f17-87baa839833d)


# Query
```sql
SELECT id,name,age,city,income
FROM Employee
WHERE age < (SELECT AVG(age) FROM Employee
WHERE income > 250000);
```

**Output:**
![image](https://github.com/user-attachments/assets/1022e822-bdc5-48c3-a6f3-2a705ae5d9b1)


**Question 5**
---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.


![image](https://github.com/user-attachments/assets/b94934db-17be-421e-a8b3-f645f6eb0f25)


# Query
```sql
SELECT s.salesman_id,s.name
FROM salesman s
JOIN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
) c ON s.salesman_id = c.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/e20d65ea-45fd-433d-a697-4f52f00520af)


**Question 6**
---
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)


![image](https://github.com/user-attachments/assets/679482bd-9505-4afd-af5e-404102fb4d7d)


# Query
```sql
SELECT medication_id as medic,medication_name,dosage
FROM Medications
WHERE dosage = (SELECT MAX(dosage) FROM Medications);
```

**Output:**

![image](https://github.com/user-attachments/assets/b44a760d-14a1-4823-990f-490f8866e419)


**Question 7**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

![image](https://github.com/user-attachments/assets/92fae648-c5ea-4d93-868f-5d0af34f5e8c)


# Query
```sql
SELECT * FROM CUSTOMERS
WHERE SALARY < 2500;
```

**Output:**
![image](https://github.com/user-attachments/assets/980a0de6-f002-4d55-9018-da75cabbdf55)


**Question 8**
---
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)


![image](https://github.com/user-attachments/assets/ffd2e5ba-1daf-4f98-9d91-3e761110c32d)


# Query
```sql
SELECT * FROM GRADES g
WHERE grade=(SELECT MAX(grade) FROM GRADES
WHERE subject = g.subject);
```

**Output:**
![image](https://github.com/user-attachments/assets/efa82f4e-683b-4166-b022-406efbefc9ca)


**Question 9**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS

![image](https://github.com/user-attachments/assets/5bff7624-689c-40d3-a5fa-2a867b1cf6ce)


# Query
```sql
SELECT * FROM CUSTOMERS
WHERE SALARY>4500;
```

**Output:**
![image](https://github.com/user-attachments/assets/922ea0e5-9765-4d81-802c-3fe28145adb9)


**Question 10**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.


![image](https://github.com/user-attachments/assets/66666b0e-54e2-425d-a1e0-76343a943b35)

# Query
```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);

```

**Output:**

![image](https://github.com/user-attachments/assets/d80f74e0-b965-44a2-955c-672ffa8a6e6f)


# Screenshot of Module 3 SEB Completion Grades
![image](https://github.com/user-attachments/assets/5b65c9a4-5239-4746-acea-e372933e1d5d)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
