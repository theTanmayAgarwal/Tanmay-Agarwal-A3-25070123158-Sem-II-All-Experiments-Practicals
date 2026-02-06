# Experiment 6: Study of Conditional Statements in Python

**Name:** Tanmay Agarwal

**PRN:** 25070123158

**Batch:** EnTC A-3

---

## Title

To study Conditional Statements in Python.

---

## Aim

To understand and implement conditional statements (`if`, `if-else`, `if-elif-else`) in Python for decision-making, logical comparisons, and branching control flow based on given conditions.

## Theory: Conditional Statements in Python

Conditional statements are fundamental control structures in Python that allow a program to make decisions and execute different blocks of code based on given conditions. These conditions are logical expressions that evaluate to either `True` or `False`.

In real-world programming, not all instructions are executed sequentially. Often, certain operations must be performed only when specific conditions are satisfied. Conditional statements make this possible by controlling the flow of execution.

### 1. if Statement

The `if` statement is the simplest form of a conditional statement. It executes a block of code only when the specified condition evaluates to `True`. If the condition is `False`, the code inside the `if` block is skipped.

**Syntax:**

```
if condition:
    statement(s)
```

### 2. if-else Statement

The `if-else` statement provides an alternative path of execution. If the condition is `True`, the `if` block is executed; otherwise, the `else` block is executed.

**Syntax:**

```
if condition:
    statement(s)
else:
    statement(s)
```

### 3. if-elif-else Statement

When multiple conditions need to be checked, the `if-elif-else` ladder is used. The program evaluates conditions sequentially from top to bottom. The first condition that evaluates to `True` gets executed, and the rest are skipped. If none of the conditions are true, the `else` block is executed.

**Syntax:**

```
if condition1:
    statement(s)
elif condition2:
    statement(s)
else:
    statement(s)
```

### 4. Nested if Statements

An `if` statement inside another `if` statement is known as a nested `if`. These are used when a condition depends on the result of another condition.

### 5. Relational and Logical Operators in Conditions

Conditional statements commonly use:

* Relational operators: `>`, `<`, `>=`, `<=`, `==`, `!=`
* Logical operators: `and`, `or`, `not`

These operators help in forming complex decision-making conditions.

### Importance of Conditional Statements

Conditional statements are widely used in:

* Decision-making programs
* Input validation
* Grading systems
* Financial and business logic
* Date and time validation

They improve program flexibility, efficiency, and logical clarity.

---

## Problem Statements & Implementation

### 1. Basic Classification

* **Sign Check:**
  Program to identify whether a given number is positive, negative, or zero.

* **Parity Check:**
  Program to determine whether an integer is even or odd using the modulus (`%`) operator.

---

### 2. Comparison Logic

* **Numerical Dominance:**
  Program to find the greater value among two or three user-defined numbers using conditional statements.

---

### 3. Academic Grading System

* Calculates the average marks obtained across **five subjects**.
* Assigns grades based on the calculated average:

  * **Grade A** – Excellent performance
  * **Grade B** – Very good performance
  * **Grade C** – Good performance
  * **Grade D** – Satisfactory performance
  * **Grade E / Fail** – Needs improvement

---

### 4. Calendar & Date Logic

* **Leap Year Identification:**
  Implements the mathematical rules to check whether a given year is a leap year.

* **Date Incrementor:**
  A robust program that:

  * Validates a given date in `DD/MM/YYYY` format
  * Calculates the next day
  * Accounts for different month lengths
  * Handles leap years correctly

---

### 5. Financial Calculations

* **Gross Salary Calculation:**
  Automates the calculation of an employee’s gross salary by applying **HRA** (House Rent Allowance) and **DA** (Dearness Allowance) percentages based on predefined basic salary brackets.

---

## Conclusion

Conditional statements form the backbone of decision-making in Python programming. By using `if`, `if-else`, `if-elif-else`, and nested `if` statements, a program can respond intelligently to different inputs and situations. These constructs allow the programmer to control the flow of execution, apply logical reasoning, and handle real-world scenarios efficiently. Understanding conditional statements is essential for writing clear, flexible, and error-free programs.
