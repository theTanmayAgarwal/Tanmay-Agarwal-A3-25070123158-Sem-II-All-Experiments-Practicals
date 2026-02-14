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
