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
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

![image](https://github.com/user-attachments/assets/282dab09-7e66-4e4b-bea0-0c8ce98ada32)


# Query
```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
INNER JOIN 
    customer c ON o.customer_id = c.customer_id
INNER JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/8b1509ea-b57b-4364-b755-9a80ca60595d)


**Question 2**
---
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

Sample table: customer

![image](https://github.com/user-attachments/assets/0c5799a6-4ae3-4fc3-9f39-8aa9fb7a2934)


# Query
```sql
select c.cust_name as "Customer Name", c.city, s.name as "Salesman" , s.commission
from customer c
inner join salesman s
on c.salesman_id = s.salesman_id
where s.commission > 0.12;
```

**Output:**

![image](https://github.com/user-attachments/assets/b3240d4c-9c58-4dac-b636-1c8cd7296ba0)


**Question 3**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman

![image](https://github.com/user-attachments/assets/b136c08c-8296-4ad5-9159-20d549bf2ff3)


# Query
```sql
select s.name as Salesman, c.cust_name, s.city
from salesman s
inner join customer c
on c.city = s.city;
```

**Output:**
![image](https://github.com/user-attachments/assets/79dfc7ea-68ef-4793-a087-75c6cf0188e4)



**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

![image](https://github.com/user-attachments/assets/5c8dadf6-601f-403e-b547-8408238fec3c)


# Query
```sql
select p.first_name as patient_name, t.test_name
from PATIENTS p
inner join test_results t
on p.patient_id = t.patient_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/597df8fb-0aa0-4791-b467-9214ac85939a)


**Question 5**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for customers with a grade less than or equal to 100.


![image](https://github.com/user-attachments/assets/50ab0179-656e-4a43-9669-802387e460dd)


# Query
```sql
select s.name, c.cust_name , c.city, c.grade, c.salesman_id
from customer c
left join salesman s
on c.salesman_id = s.salesman_id
where c.grade <= 100;
```

**Output:**

![image](https://github.com/user-attachments/assets/71b2666d-a055-4250-ae38-7367cd528a37)


**Question 6**
---
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.

PATIENTS TABLE:

![image](https://github.com/user-attachments/assets/9312635d-a69d-42e1-aabf-514a9f345890)


# Query
```sql
select p.*, d.specialization as doctor_specialization
from patients p
inner join doctors d
on p.doctor_id = d.doctor_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/5ff3895f-be82-4ec3-a889-6553be6c1f5a)


**Question 7**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount greater than 1000.


![image](https://github.com/user-attachments/assets/0b4e26a5-e159-40f9-9d42-6a394e326a8c)


# Query
```sql
select c.cust_name,o.ord_no,o.ord_date,o.purch_amt
from customer c
left join orders o
on c.customer_id = o.customer_id
where o.purch_amt >1000;
```

**Output:**

![image](https://github.com/user-attachments/assets/41590d5f-fe66-48c6-8c03-fe0b10d51847)


**Question 8**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.


![image](https://github.com/user-attachments/assets/6737f713-e16b-4bbd-b0ec-06883fc10699)


# Query
```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount",
    s.name,
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON o.salesman_id = s.salesman_id;


```

**Output:**

![image](https://github.com/user-attachments/assets/2dc1dbd2-5c26-4aac-a021-3e353da0a718)


**Question 9**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.


![image](https://github.com/user-attachments/assets/a8abfc28-e7ce-4aed-9496-ccce34d8298a)



# Query
```sql
select p.first_name as patient_name 
from patients p
inner join test_results t
on p.patient_id = t.patient_id
where t.test_name = 'Blood Pressure';

```

**Output:**
![image](https://github.com/user-attachments/assets/9f5aee15-9492-4d18-8d70-00a50ea9d2ec)


**Question 10**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 


![image](https://github.com/user-attachments/assets/bb5e4fac-73aa-408b-828a-06b764e97368)


# Query
```sql
select c.cust_name, c.city, c.grade, s.name as Salesman, s.city
from customer c
inner join salesman s
on c.salesman_id = s.salesman_id
where c.grade<300
order by customer_id asc;
```

**Output:**

![image](https://github.com/user-attachments/assets/3f8d8d04-ceb1-4c06-a937-e4d4b55a6d3d)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
