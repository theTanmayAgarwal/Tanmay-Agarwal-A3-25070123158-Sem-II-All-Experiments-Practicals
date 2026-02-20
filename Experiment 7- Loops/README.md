# 🔁 STUDY OF LOOPS IN PYTHON

Name- Tanmay Agarwal <br/>
Branch- EnTC A3 <br/>
PRN- 25070123158 <br/>

---

## Title Page

**Project Name:** Study of Loops in Python <br/>
**Purpose:** Study and Implementation of Looping Statements <br/>
**Language:** Python <br/>

---

## 🎯 Aim of the Study

The aim of this project is to study looping statements in Python such as **while loop**, **for loop**, and the use of the **range() function**.  

This project helps in understanding how repetition works in programming and how loops help in reducing code redundancy by executing a block of code multiple times.

---

## 📌 Introduction

In programming, there are situations where we need to execute a statement multiple times. Writing the same statement again and again is inefficient and makes the code lengthy.

To solve this problem, Python provides **looping statements**.  

Loops allow execution of a block of code repeatedly until a given condition is satisfied.

Python mainly provides:

* while loop  
* for loop  
* Nested loops  
* Loop control statements  

---

## 📖 Study of Loops (Instructions)

* Understand the need of loops in programming  
* Learn the syntax of while and for loops  
* Study how range() function works  
* Practice programs using loops  
* Observe loop execution step-by-step  
* Understand infinite loops  
* Learn nested looping concepts  
* Practice logical problems using loops  

---

## 2. Algorithms

Below are the algorithms for the specific codes implemented in this experiment.

### Program 1: Print numbers 1 to 5 (While Loop)
1. Initialize a variable `i` to 1.
2. Check if `i` is less than or equal to 5.
3. If true, print the value of `i`.
4. Increment `i` by 1.
5. Repeat steps 2-4 until the condition becomes false.

### Program 2: Print numbers 1 to N (User Input)
1. Accept integer input `n` from the user.
2. Initialize counter `i` to 1.
3. While `i` is less than or equal to `n`:
    * Print `i` (staying on the same line).
    * Increment `i` by 1.
4. End loop.

### Program 3: Factorial of a number
1. Accept integer `n` from the user.
2. Initialize `fact` to 1.
3. While `n` is greater than or equal to 1:
    * Multiply `fact` by `n` (`fact = fact * n`).
    * Decrement `n` by 1.
4. Print the final value of `fact`.

### Program 4: Fibonacci Series
1. Accept `n` (number of terms) from the user.
2. Initialize variables: `a = 0`, `b = 1`, and counter `i = 0`.
3. While `i` is less than `n`:
    * Print `a`.
    * Calculate next term `c = a + b`.
    * Update `a = b` and `b = c`.
    * Increment `i` by 1.

### Program 5: Reverse a Number
1. Accept integer `num` from the user.
2. Initialize `rev` to 0.
3. While `num` is greater than 0:
    * Extract the last digit: `digit = num % 10`.
    * Update `rev`: `rev = rev * 10 + digit`.
    * Remove the last digit from `num` (integer division by 10).
4. Print `rev`.

### Program 6: Check Palindrome (String method)
1. Accept a string input `string`.
2. Create a reversed version of the string `rev` using slicing `[::-1]`.
3. Compare `string` with `rev`.
4. If they are equal, print "Palindrome".
5. Else, print "Not Palindrome".

### Program 7: Count digits in a number
1. Accept integer `num`.
2. Initialize `count` to 0.
3. While `num` is greater than 0:
    * Increment `count` by 1.
    * Remove the last digit of `num` (integer division by 10).
4. Print `count`.

### Program 8: Break Statement (Exit when i=3)
1. Initialize `i = 1`.
2. Start a while loop with condition `i < 6`.
3. Print `i`.
4. Check if `i` equals 3.
    * If true, execute `break` (exit loop).
5. Increment `i` by 1.
6. Repeat.

### Program 9: Search element in list (Linear Search)
1. Define a list of PRN strings `prn_nos`.
2. Accept PRN to search from the user.
3. Initialize index `i = 0` and get list length `length`.
4. While `i < length`:
    * Check if `prn_nos[i]` equals input PRN.
    * If true, print "Found" and index, then break.
    * Increment `i`.
5. If the loop completes without breaking (using `else` block of `while`), print "Not found".

### Program 10: Continue Statement (Skip 5)
1. Initialize `i = 1`.
2. While `i <= 10`:
    * Check if `i` equals 5.
    * If true, increment `i` and execute `continue` (skip printing).
    * Print `i`.
    * Increment `i`.

### Program 11: Print Odd Numbers (Skip Even)
1. Initialize `i = 1`.
2. While `i < 10`:
    * Check if `i` is even (`i % 2 == 0`).
    * If true, increment `i` and `continue`.
    * Print `i`.
    * Increment `i`.

### Program 12: Print 1 to 6 (For Loop)
1. Iterate variable `i` in the range 1 to 6 (exclusive of 7).
2. Print `i` in the same line.

### Program 13: Print Even Numbers 1 to 10
1. Iterate variable `x` in the range starting at 2, ending at 11, with a step of 2.
2. Print `x`.

### Program 14: Sum of first N numbers
1. Accept integer `n`.
2. Initialize `total = 0`.
3. Iterate `i` from 1 to `n` (inclusive):
    * Add `i` to `total`.
4. Print `total`.

### Program 15: Nested For Loop (Coordinates)
1. Start outer loop `i` from 1 to 3.
2. Start inner loop `j` from 1 to 3.
3. Print pair `(i, j)`.
4. End inner loop.
5. End outer loop.

### Program 16: 3x3 Matrix Display
1. Define a 3x3 matrix `A` (list of lists).
2. Start outer loop `i` from 0 to 2 (rows).
3. Start inner loop `j` from 0 to 2 (columns).
4. Print `A[i][j]` followed by a space.
5. After the inner loop finishes (end of a row), print a newline.

### Program 17: Matrix Multiplication
1. Define 3x3 matrices `A` and `B`.
2. Initialize a 3x3 zero matrix `Result`.
3. Start loop `i` (0 to 2) for rows of `A`.
4. Start loop `j` (0 to 2) for columns of `B`.
5. Start loop `k` (0 to 2) for dot product calculation.
    * `Result[i][j] += A[i][k] * B[k][j]`.
6. Print the `Result` matrix row by row.

### Program 18: Combinations of 3 Digits
1. Accept three string inputs.
2. Store them in a list `d`.
3. Use three nested loops (`i`, `j`, `k`) iterating from 0 to 2.
4. Check condition: If indices point to unique values (values are distinct), print the combination `d[i], d[j], d[k]`.

### Program 19: Armstrong Number Check
1. Accept number as string `num`.
2. Calculate length of string.
3. Initialize `sum = 0`.
4. Iterate `i` through each digit in `num`:
    * Convert digit to integer.
    * Raise digit to the power of length.
    * Add result to `sum`.
5. If `sum` equals the original integer `num`, print "Armstrong Number".
6. Else, print "Not an Armstrong Number".

### Program 20: Prime Number Check
1. Accept integer `num`.
2. Iterate `i` from 2 up to `num - 1`.
3. Check if `num % i == 0`.
    * If true, the number is not prime; break the loop.
4. If the loop completes without finding a divisor, the number is Prime.

### Program 21: Inverted Pyramid Pattern
1. Set `n = 5`.
2. Iterate `i` from 0 to `n-1`.
3. Print `i` spaces followed by `(n-i)` occurrences of the symbol `$`.

### Program 22: Pyramid Pattern
1. Set `n = 5`.
2. Iterate `i` from 0 to `n-1`.
3. Print `(n-i)` spaces followed by `i` occurrences of the symbol `$`.

### Program 23: Right Angled Triangle Pattern
1. Set `n = 5`.
2. Iterate `i` from 5 down to 1 (step -1).
3. Print `(n-i)` asterisks `*` (Note: based on output logic provided in code).

### Program 24: Floyd's Triangle
1. Accept number of rows `n`.
2. Initialize `number = 1`.
3. Outer loop `i` from 1 to `n`.
4. Inner loop `j` from 1 to `i`.
    * Print `number`.
    * Increment `number`.
5. Print newline after inner loop.

### Program 25: Number Pattern (1, 22, 333...)
1. Iterate `i` from 1 to 5.
2. Print `i` as a string, repeated `i` times (e.g., if `i` is 3, print "333").

## 🔑 Key Concepts Covered

* Iteration
* Condition checking
* Counter control
* range() function
* Nested loops
* Loop control statements (break, continue, pass)
* Infinite loops
* Indentation in loops

---

# 📘 THEORY (Study of Loops in Python)

---

## 1️⃣ What is a Loop?

A loop is a control structure that allows repeated execution of a block of code as long as a specified condition is true.

Loops are used to:
* Print numbers in sequence
* Perform repeated calculations
* Traverse data structures
* Build patterns

---

# 🔄 WHILE LOOP

## 📌 Definition

A while loop executes a block of code repeatedly **as long as the condition remains True**.

## 🧾 Syntax

while condition:
statements

## ⚙️ Working

1. The condition is checked.
2. If True → block executes.
3. Control goes back to condition.
4. Repeats until condition becomes False.

## ✅ Example

i = 1
while i <= 5:
print(i)
i += 1

## 🧠 Explanation

* Initial value is assigned.
* Condition is checked.
* Value is incremented.
* Loop stops when condition becomes False.

---

## ⚠ Infinite While Loop

If the condition never becomes False, the loop runs forever.

Example:

while True:
print("Hello")

This creates an infinite loop.

---

# 🔁 FOR LOOP

## 📌 Definition

A for loop is used to iterate over a sequence (like list, tuple, string, or range).

## 🧾 Syntax

for variable in sequence:
statements

## ⚙️ Working

* Takes each value from the sequence
* Assigns it to the variable
* Executes the block

---

## ✅ Example Using List

numbers = [1, 2, 3, 4, 5]
for num in numbers:
print(num)


---

# 🔢 RANGE() FUNCTION

## 📌 Definition

range() is used to generate a sequence of numbers.

## 🧾 Syntax

range(start, stop, step)


### Parameters:

* start → starting value (default 0)
* stop → ending value (not included)
* step → increment/decrement value

---

## ✅ Examples

### Example 1

for i in range(5):
print(i)

Output: 0 1 2 3 4

---

### Example 2

for i in range(1, 6):
print(i)


Output: 1 2 3 4 5

---

### Example 3 (Step value)



for i in range(1, 10, 2):
print(i)


Output: 1 3 5 7 9

---

# 🔁 NESTED LOOPS

## 📌 Definition

A loop inside another loop is called a nested loop.

## 🧾 Syntax



for i in range(3):
for j in range(3):
print(i, j)


## ⚙️ Working

* Outer loop executes first.
* For each outer loop iteration, inner loop runs completely.
* Used mainly in pattern programs and matrix operations.

---

# 🛑 LOOP CONTROL STATEMENTS

## 1️⃣ break

Stops the loop immediately.



for i in range(5):
if i == 3:
break
print(i)


---

## 2️⃣ continue

Skips the current iteration.



for i in range(5):
if i == 3:
continue
print(i)


---

## 3️⃣ pass

Does nothing (placeholder statement).



for i in range(5):
pass


---

# ✅ Advantages of Loops

* Reduces code repetition
* Makes program shorter and cleaner
* Saves time and effort
* Improves efficiency
* Useful in automation

---

# ❌ Disadvantages of Loops

* Infinite loop risk
* Harder to debug if condition incorrect
* May increase execution time if not optimized

---

# 🛠 Tools Used

* Python Interpreter
* Jupyter Notebook (.ipynb)
* VS Code / IDLE
* Command Prompt / Terminal

---

# 📂 Applications of Loops

* Printing number series
* Pattern programs
* Mathematical calculations
* Data processing
* Traversing lists and strings
* Game development
* Real-time automation

---

# 🎯 Conclusion

Loops are one of the most important control structures in Python programming.  

Through this study, we understood:

* The working of while loop
* The working of for loop
* The use of range() function
* Nested looping concepts
* Loop control statements

Mastering loops is essential for solving logical problems and building strong programming skills.

---

# 📎 Extra Notes

* Python uses indentation to define loop blocks
* range() does not include the stop value
* Always update loop variables in while loop
* Avoid infinite loops
* Practice logical problems regularly

---

✨ *End of README*
