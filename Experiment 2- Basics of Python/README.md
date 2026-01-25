**Experiment-2**

**Name: Tanmay Agarwal**

**PRN: 25070123158**

**Batch: EnTC A-3**

**Title**

**Python Environment, Data Types, Operators, and Basic Input/Output**

**Aim**

To study the Python programming environment and interface, understand
execution modes, variables, data types, operators, and basic
input/output operations in Python.

**Objectives**

-   To understand the Python programming environment and interface

-   To study Python execution modes

-   To understand comments in Python

-   To learn variables, identifier rules, and data types

-   To study different operators and expressions

-   To understand basic input and output mechanisms

**Theory**

**1. Python Environment and Interface**

The Python environment provides tools and interfaces to write, execute,
and debug Python programs. Python programs can be executed using
different interfaces such as:

-   Python Shell

-   Jupyter Notebook

-   Integrated Development Environments (IDEs) like Spyder, PyCharm, and
    VS Code

-   Cloud-based platforms like Google Colab

The interface allows users to write code, execute instructions, and view
results interactively.

**2. Python Execution Modes**

Python supports two main execution modes:

**a) Interactive Mode**

-   Commands are executed one line at a time

-   Immediate output is displayed

-   Useful for testing small code snippets and learning

Examples: Python shell, Jupyter Notebook cells, Google Colab

**b) Script Mode**

-   Programs are written in a file and executed as a whole

-   Suitable for developing complete applications

-   Files usually have .py extension

**3. Comments in Python**

Comments are non-executable statements used to explain code and improve
readability.

-   **Single-line comments:** Begin with \#

-   **Multi-line comments:** Written using triple quotes (\"\"\" \"\"\")

Comments help in documentation and understanding program logic.

**4. Variables and Identifiers**

A variable is a named memory location used to store data values.

**Rules for Identifiers:**

-   Must start with a letter (A--Z, a--z) or underscore \_

-   Cannot start with a digit

-   Case-sensitive

-   Should not use Python keywords

Python uses **dynamic typing**, meaning variables do not require
explicit data type declaration.

**5. Data Types in Python**

Python provides several built-in data types to store different kinds of
data.

**Basic Data Types**

-   **Integer (int)**: Whole numbers

-   **Floating-point (float)**: Decimal numbers

-   **String (str)**: Sequence of characters

-   **Boolean (bool)**: True or False

The data type of a variable can be identified using the type() function.

**6. Operators and Expressions**

Operators are symbols used to perform operations on variables and
values.

**Types of Operators**

-   **Arithmetic Operators:** Used for mathematical calculations\
    (+, -, \*, /, %)

-   **Relational Operators:** Used for comparison\
    (\>, \<, \>=, \<=, ==, !=)

-   **Logical Operators:** Used to combine conditions\
    (and, or, not)

-   **Assignment Operators:** Used to assign values\
    (=, +=, -=, \*=, /=)

-   **Bitwise Operators:** Perform operations at bit level\
    (&, \|, \^, \<\<, \>\>)

An **expression** is a combination of operators and operands that
produces a result.

**7. Basic Input and Output Operations**

Input and output operations allow interaction between the user and the
program.

-   **Input:**\
    input() function is used to accept input from the user.\
    Input is treated as a string by default and may require type
    conversion.

-   **Output:**\
    print() function is used to display output.\
    Formatted output can be achieved using commas or formatted strings.

**Conclusion**

Thus, the Python programming environment, execution modes, variables,
data types, operators, and basic input/output operations were studied
and understood.

# Python Programming Lab - Assignment 1

## #Program-1: Simple Calculator
### *Aim*
To create a program that performs basic arithmetic operations (addition, subtraction, multiplication, division, and modulus) on two user-provided numbers.

### *Theory*
In Python, the ⁠ input() ⁠ function is used to capture data from the user as a string. To perform mathematical operations, these strings must be converted into integers using the ⁠ int() ⁠ function. Arithmetic operators used include:
•⁠  ⁠⁠ + ⁠ (Addition)
•⁠  ⁠⁠ - ⁠ (Subtraction)
•⁠  ⁠⁠ * ⁠ (Multiplication)
•⁠  ⁠⁠ / ⁠ (Division)
•⁠  ⁠⁠ % ⁠ (Modulus - finds the remainder)

### *Steps*
1.⁠ ⁠Take two inputs from the user.
2.⁠ ⁠Typecast the inputs from string to integer.
3.⁠ ⁠Apply the arithmetic operators.
4.⁠ ⁠Print the results to the console.

### *Conclusion*
The program successfully demonstrates how to handle user input and perform basic arithmetic operations in Python.

---

## #Program-2: Sum and Average of Marks
### *Aim*
To calculate the total sum and the average marks of five students.

### *Theory*
The *Sum* is the total value of all inputs combined. The *Average* (Mean) is calculated by taking the total sum and dividing it by the count of inputs (in this case, 5).

### *Steps*
1.⁠ ⁠Accept five separate inputs representing marks.
2.⁠ ⁠Convert all inputs to integers.
3.⁠ ⁠Sum the five values together.
4.⁠ ⁠Divide the total sum by 5 to find the average.
5.⁠ ⁠Display both the total and the average.

### *Conclusion*
The program effectively calculates statistical data from multiple integer inputs.

---

## #Program-3: Area of a Circle
### *Aim*
To find the area of a circle based on a user-defined radius.

### *Theory*
The area of a circle is calculated using the mathematical formula:
$$Area = \pi r^2$$
In this program, we use *3.14* as the constant for $\pi$ and $r$ as the radius provided by the user.

### *Steps*
1.⁠ ⁠Accept the radius ($r$) as input.
2.⁠ ⁠Convert the input to an integer.
3.⁠ ⁠Calculate the area using the formula $3.14 * r * r$.
4.⁠ ⁠Print the final area.

### *Conclusion*
The program demonstrates the implementation of geometric formulas using Python variables.

---

## #Program-4: Area and Perimeter of a Rectangle
### *Aim*
To compute the area and the perimeter of a rectangle using its length and breadth.

### *Theory*
•⁠  ⁠*Area* is the total space inside the rectangle: $$Area = Length \times Breadth$$
•⁠  ⁠*Perimeter* is the total distance around the rectangle: $$Perimeter = 2 \times (Length + Breadth)$$

### *Steps*
1.⁠ ⁠Input the length ($l$) and breadth ($b$).
2.⁠ ⁠Convert both values to integers.
3.⁠ ⁠Calculate Area ($l * b$).
4.⁠ ⁠Calculate Perimeter ($2 * (l + b)$).
5.⁠ ⁠Output both results.

### *Conclusion*
The program successfully implements multiple geometric calculations in a single script.
