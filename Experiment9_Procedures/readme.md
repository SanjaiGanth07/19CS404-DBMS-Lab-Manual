# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

### Program :
```
CREATE OR REPLACE PROCEDURE find_square(n IN NUMBER)
IS
    sq NUMBER;
BEGIN
    sq := n * n;
    DBMS_OUTPUT.PUT_LINE('Square of ' || n || ' is ' || sq);
END;


BEGIN
    find_square(6);
END;
```

**Expected Output:**  
Square of 6 is 36

<img width="452" height="202" alt="image" src="https://github.com/user-attachments/assets/630fc15d-e17e-42a6-9fc8-b51676dcd0d5" />

<img width="447" height="217" alt="image" src="https://github.com/user-attachments/assets/487b1d57-e808-4927-ac6c-412318b8a759" />

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

### Program :
```
CREATE OR REPLACE FUNCTION get_factorial(n IN NUMBER)
RETURN NUMBER
IS
    fact NUMBER := 1;
BEGIN
    FOR i IN 1..n LOOP
        fact := fact * i;
    END LOOP;

    RETURN fact;
END;

BEGIN
    DBMS_OUTPUT.PUT_LINE('Factorial of 5 is ' || get_factorial(5));
END;
```

**Expected Output:**  
Factorial of 5 is 120

<img width="340" height="182" alt="image" src="https://github.com/user-attachments/assets/fc127afb-5fa5-4dc7-b797-00be7833667e" />

<img width="372" height="123" alt="image" src="https://github.com/user-attachments/assets/cb6a7299-901b-4263-95b0-736752cc6f98" />

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

### Program :
```
CREATE OR REPLACE PROCEDURE check_even_odd(n IN NUMBER)
IS
BEGIN
    IF MOD(n, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(n || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(n || ' is Odd');
    END IF;
END;


BEGIN
    check_even_odd(12);
END;
```

**Expected Output:**  
12 is Even

<img width="345" height="82" alt="image" src="https://github.com/user-attachments/assets/7c1cb163-5e48-45cf-b999-e63eaed09f05" />
<img width="365" height="120" alt="image" src="https://github.com/user-attachments/assets/80b2e1a4-5eba-48be-a21a-6e1ae5c8c73e" />


---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

### Program :
```
CREATE OR REPLACE FUNCTION reverse_number(n IN NUMBER)
RETURN NUMBER
IS
    num NUMBER := n;
    rev NUMBER := 0;
    rem NUMBER;
BEGIN
    WHILE num > 0 LOOP
        rem := MOD(num, 10);
        rev := rev * 10 + rem;
        num := TRUNC(num / 10);
    END LOOP;

    RETURN rev;
END;


BEGIN
    DBMS_OUTPUT.PUT_LINE(
        'Reversed number of 1234 is ' || reverse_number(1234)
    );
END;
```

**Expected Output:**  
Reversed number of 1234 is 4321

<img width="357" height="93" alt="image" src="https://github.com/user-attachments/assets/131be4b7-44bb-4aeb-a730-b9c81d62cb9c" />

<img width="370" height="132" alt="image" src="https://github.com/user-attachments/assets/e85a9ec1-4e99-4f7b-86d2-189b41ef7094" />


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

### Program :
```
CREATE OR REPLACE PROCEDURE print_table(n IN NUMBER)
IS
BEGIN
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(n || ' x ' || i || ' = ' || (n * i));
    END LOOP;
END;

BEGIN
    print_table(5);
END;
```

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

<img width="345" height="80" alt="image" src="https://github.com/user-attachments/assets/df458a9c-90ea-4e65-be09-d02f2dd44a37" />

<img width="358" height="295" alt="image" src="https://github.com/user-attachments/assets/b3c7d8bc-53cf-4fb4-991b-e375a78a7648" />


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
