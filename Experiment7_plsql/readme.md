# Experiment 7: PL/SQL – Variables, Control Structures and Loops

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

**Expected Output:**  
Greater number is: 80

**Program:**  

```
DECLARE
    num1 NUMBER;
    num2 NUMBER;

BEGIN
    num1 := 50;
    num2 := 80;
    IF num1>num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
    END IF;
END;
/
```

**Result:**
<img width="559" height="683" alt="image" src="https://github.com/user-attachments/assets/d6fd0431-8d48-43b4-b5d1-5b18046b73a2" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55

**Program:**  

```
DECLARE
    i NUMBER := 1;
    n NUMBER := 10;
    sum NUMBER := 0;

BEGIN
    WHILE i<=n LOOP
        sum := sum+i;
        i := i+1;
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```

**Result:**
<img width="626" height="654" alt="image" src="https://github.com/user-attachments/assets/e46ca146-4ce8-45ba-9ced-9cff48a71d54" />

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

**Program:**  

```
DECLARE
      n NUMBER := 7;
      a NUMBER := 0;
      b NUMBER := 1;
      c NUMBER;
      i NUMBER := 1;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');
    WHILE i <= n LOOP
        DBMS_OUTPUT.PUT_LINE(a || ' ');
        c := a + b;
        a := b;
        b := c;
        i := i + 1;
    END LOOP;
END;
/
```

**Result:**
<img width="474" height="755" alt="image" src="https://github.com/user-attachments/assets/e353b90e-11c9-4ae2-bc66-f8118404eb2b" />


---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

**Program:** 

```
DECLARE
    n NUMBER := 1535;
    rem NUMBER;
    rev NUMBER := 0;
    temp NUMBER;
BEGIN
    temp := n;
    WHILE temp > 0 LOOP
        rem := MOD(temp, 10);
        rev := rev * 10 + rem;
        temp := FLOOR(temp / 10);
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Reversed number is: ' || rev);
END;
/
```

**Result:**
<img width="532" height="686" alt="image" src="https://github.com/user-attachments/assets/cbaa78db-58c3-4a57-a4c3-cf81b535a355" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

**Program:** 

```
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
    largest NUMBER;
BEGIN
    IF a > b AND a > c THEN
        largest := a;
    ELSIF b > c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;
    DBMS_OUTPUT.PUT_LINE('Largest number is: ' || largest);
END;
/
```

**Result:**
<img width="545" height="707" alt="image" src="https://github.com/user-attachments/assets/29f0fe5a-81b9-4909-aa9f-cb695c6a96d0" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
