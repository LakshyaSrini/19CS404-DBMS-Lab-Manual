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
How many medical records are there for each patient?

Sample table:MedicalRecords Table

![image](https://github.com/user-attachments/assets/bf99daa6-7e6b-4a9f-8bf9-71c21ca22732)


# Query
```sql
SELECT PatientID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/5a31b74b-2e37-469c-ac0a-a99f1e79ee8d)


**Question 2**
---
How many patients are covered by each insurance company?

Sample table:Insurance Table

![image](https://github.com/user-attachments/assets/d7b0f482-3b9a-41c9-8863-1cff48f887ad)



# Query
```sql
SELECT InsuranceCompany,COUNT(*) AS TotalPatients
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

![image](https://github.com/user-attachments/assets/c73340bc-fd1a-462f-8079-4f071b142906)

**Question 3**
---
What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table

![image](https://github.com/user-attachments/assets/b3a29d2f-71ae-479c-aea7-75b73e4b62af)


# Query
```sql
SELECT Medication,AVG(Dosage) AS AvgDosage
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

![image](https://github.com/user-attachments/assets/8cbfea8c-39e4-4be9-9500-3d65d4e11ba6)


**Question 4**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

![image](https://github.com/user-attachments/assets/48ff6e68-8f37-4a82-8ca2-3ea05822817f)


# Query
```sql
SELECT MAX(purch_amt) AS MAXIMUM
FROM orders
LIMIT 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/c4b38e9c-4d39-4e7a-98a8-1832bf9fcaf5)

**Question 5**
---
Write a SQL query to  find the average salary of all employees?

Table: employee

![image](https://github.com/user-attachments/assets/92dbdab0-2d68-482f-9480-1d3bc64b73a5)


# Query
```sql
SELECT avg(income) AS Average_Salary
FROM employee
LIMIT 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/633983a1-f35b-4fdf-9441-3168d380a019)


**Question 6**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

![image](https://github.com/user-attachments/assets/41410d4c-d9df-4292-9dce-e6e519038b11)


# Query
```sql
SELECT COUNT(*) AS COUNT
FROM customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/2e879fb0-b6a5-4840-8be2-0925107a0b29)


**Question 7**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

![image](https://github.com/user-attachments/assets/c311b316-f1d8-4bc7-9223-a7fe905f6d46)



# Query
```sql
SELECT SUM(income) as total_income
FROM employee
WHERE age >= 40
LIMIT 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/1b0c8315-e39a-47f5-9650-8a7de8850e00)


**Question 8**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1

![image](https://github.com/user-attachments/assets/ca1a5051-21e8-49cd-9d86-ef7805989c3d)


# Query
```sql
SELECT occupation,MIN(workhour)
FROM employee1
GROUP BY occupation
HAVING MIN(workhour) > 8
ORDER BY occupation;
```

**Output:**

![image](https://github.com/user-attachments/assets/686a0f39-212d-4392-af15-e8a2f2f14f7f)


**Question 9**
---
Write the SQL query that performs grouping by age groups and displays the maximum salary for each group, excluding groups where the maximum salary is not greater than 8000. 

Note: Calculate the age group as multiples of 5.

Eg., 20,22,23 comes in age group 20. 

25,27,29 comes in age group 25.

Sample table: customer1


![image](https://github.com/user-attachments/assets/39d4e737-c5be-4ace-96e7-6d02856f4d3d)


# Query
```sql
SELECT (age-(age % 5)) as age_group,MAX(salary)
FROM customer1
GROUP BY age_group
HAVING MAX(salary) > 8000
ORDER BY age_group;
```

**Output:**

![image](https://github.com/user-attachments/assets/c5a1459c-a74d-44b1-82e2-f28bac1bb292)


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by age intervals using the expression (age/5)5, calculates the minimum age for each group, and excludes groups where the minimum age is not less than 25.

Sample table: customer1


![image](https://github.com/user-attachments/assets/3f50f140-1c8b-46e5-84fc-fcc02a840712)


# Query
```sql
SELECT (age/5)*5 AS age_group,MIN(age)
FROM customer1
GROUP BY age_group
HAVING MIN(age) < 25;

```

**Output:**

![image](https://github.com/user-attachments/assets/fb769fd4-a1fc-4952-82b1-6e6e11475135)



# Screenshot of Module 3 SEB Completion Grades
![image](https://github.com/user-attachments/assets/f088f9cb-5f61-4695-8fc3-5ed82ce00164)

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
