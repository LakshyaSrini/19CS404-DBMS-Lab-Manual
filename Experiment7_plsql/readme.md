# Experiment 6: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**PL/SQL QUERY**
~~~
DECLARE
   a NUMBER := 80;
   b NUMBER := 50;
BEGIN
   IF a > b THEN
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
   END IF;
END;
~~~
**Expected Output:**  
Greater number is: 80


**Output**


![Screenshot 2025-05-15 133406](https://github.com/user-attachments/assets/46d7efd2-263a-467a-b8f4-50c9ca4e6339)

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**PL/SQL QUERY**
~~~
DECLARE
   n     INTEGER := 10; 
   i     INTEGER := 1;   
   sum   INTEGER := 0;  
BEGIN
   WHILE i <= n LOOP
      sum := sum + i;
      i := i + 1;
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
~~~
**Expected Output:**  
Sum of first 10 natural numbers is: 55

**Output**


![Screenshot 2025-05-15 133816](https://github.com/user-attachments/assets/45cc2620-20fd-4eee-a821-a8eeb686cce1)

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**PL/SQL QUERY**
~~~
DECLARE
    n NUMBER := 7;           -- Number of terms in the Fibonacci sequence
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 3;
    output VARCHAR2(1000);
BEGIN
    -- Initialize the output with the first two terms
    IF n = 1 THEN
        output := TO_CHAR(a);
    ELSIF n >= 2 THEN
        output := TO_CHAR(a) || ', ' || TO_CHAR(b);
    END IF;

    WHILE i <= n LOOP
        c := a + b;
        output := output || ', ' || TO_CHAR(c);
        a := b;
        b := c;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: ' || output);
END;
/
~~~
**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

**Output**


![image](https://github.com/user-attachments/assets/5caebc9d-25a3-4009-a91b-16542f53bfcc)


---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**PL/SQL QUERY**
~~~
DECLARE
    n NUMBER := 1535;
    reversed NUMBER := 0;
    remainder NUMBER;
    original NUMBER := n;
BEGIN
    WHILE n > 0 LOOP
        remainder := MOD(n, 10);
        reversed := reversed * 10 + remainder;
        n := TRUNC(n / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('n = ' || original);
    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reversed);
END;
/
~~~
**Expected Output:**  
n = 1535  
Reversed number is 5351

**Output**


![image](https://github.com/user-attachments/assets/16e78ab4-b0c7-4ed6-8a9c-b73bcf29ec94)

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**PL/SQL QUERY**
~~~
DECLARE
   a INTEGER := 10;
   b INTEGER := 9;
   c INTEGER := 15;
BEGIN
   IF a >= b AND a >= c THEN
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || a);
   ELSIF b >= a AND b >= c THEN
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || b);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || c);
   END IF;
END;
/
~~~
**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

**Output**


![image](https://github.com/user-attachments/assets/fe248f2c-bfa0-41b0-8e2c-9f7cd9457466)

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
