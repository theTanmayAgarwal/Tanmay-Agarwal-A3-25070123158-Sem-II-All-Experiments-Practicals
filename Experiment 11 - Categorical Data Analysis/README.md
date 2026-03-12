# 📊 CATEGORICAL DATA ANALYSIS USING PYTHON

Name- Tanmay Agarwal <br/>
Branch- EnTC A3 <br/>
PRN- 25070123158 <br/>

---

## 📄 Title Page

**Experiment Name:** Categorical Data Analysis using Python <br/>
**Purpose:** Study and analysis of categorical data using Python and Pandas <br/>
**Language:** Python <br/>

---

## 🎯 Aim of the Experiment

The aim of this experiment is to analyze **categorical data using Python** by applying different data analysis techniques such as **frequency count, unique values, cross tabulation, grouping, filtering, and sorting** using the **Pandas library**.

---

## 📌 Introduction

Categorical data refers to data that can be divided into specific groups or categories.  
In data analysis, categorical variables represent characteristics such as **gender, department, grade, product category, or payment method**.

Python provides powerful tools for analyzing categorical data using the **Pandas library**, which allows easy manipulation, summarization, and exploration of datasets.

---

## 📖 Study of Categorical Data Analysis (Instructions)

* Create a dataset containing categorical variables
* Import the **Pandas library**
* Load data into a DataFrame
* Perform frequency analysis
* Identify unique values in categorical columns
* Perform cross-tabulation between variables
* Analyze percentage distribution
* Apply filtering, grouping, and sorting operations

---

### 🔑 Key Concepts

  | Function | Description |
  |----------|-------------|
  | `DataFrame()` | Creates a 2D labeled data structure with columns of potentially different types |
  | `value_counts()` | Returns a Series containing counts of unique values |
  | `nunique()` | Returns the number of unique values in a column |
  | `crosstab()` | Computes a cross-tabulation of two or more factors |
  | `groupby()` | Groups data based on specified criteria |
  | `sort_values()` | Sorts DataFrame by specified column(s) |
  | `read_csv()` | Reads a comma-separated values file into DataFrame |

---

## 📘 Theory (Categorical Data Analysis)

### 1. Frequency Count

Frequency count determines how many times each category appears in a dataset.

Example:

`df['Category'].value_counts()`

---

### 2. Unique Values

This operation displays all distinct values present in a categorical column.

Example:

`df['Category'].unique()`

---

### 3. Number of Unique Values

This calculates the total number of unique categories.

Example:

`df['Category'].nunique()`

---

### 4. Cross Tabulation

Cross tabulation compares two categorical variables and shows their relationship.

Example:

`pd.crosstab(df['Category'], df['Payment_Method'])`

---

### 5. Percentage Distribution

It shows the percentage share of each category.

Example:

`df['Category'].value_counts(normalize=True)*100`

---

### 6. Filtering Data

Filtering is used to extract rows that match specific conditions.

Example:

`df[df['Category'] == 'Electronics']`

---

### 7. Grouping Data

Grouping helps analyze relationships between multiple categorical variables.

Example:

`df.groupby('Category')['Payment_Method'].value_counts()`

---

### 8. Sorting Data

Sorting arranges the dataset in ascending or descending order based on a column.

Example:

`df.sort_values(by='Category')`

---

## 📊 Dataset Used

Two datasets were used in this experiment:

### Dataset 1
Order dataset containing:

* Order ID
* Product Category
* Payment Method
* Delivery Type
* Customer Type

Used to perform categorical analysis on **product orders and payment methods**.

### Dataset 2
Student dataset containing:

* Student Grade
* Department
* Gender

Used to analyze **academic performance and demographic distribution**.

---
## Function Reference Table

  ┌──────┬────────────────┬──────────────────────────────┬──────────────────────────────────────────┐
  │ S.No │    Function    │            Syntax            │                 Purpose                  │
  ├──────┼────────────────┼──────────────────────────────┼──────────────────────────────────────────┤
  │ 1    │ DataFrame()    │ pd.DataFrame(data)           │ Creates DataFrame from dictionary/list   │
  ├──────┼────────────────┼──────────────────────────────┼──────────────────────────────────────────┤
  │ 2    │ value_counts() │ df['col'].value_counts()     │ Returns frequency count of unique values │
  ├──────┼────────────────┼──────────────────────────────┼──────────────────────────────────────────┤
  │ 3    │ nunique()      │ df['col'].nunique()          │ Returns number of unique values          │
  ├──────┼────────────────┼──────────────────────────────┼──────────────────────────────────────────┤
  │ 4    │ crosstab()     │ pd.crosstab(col1, col2)      │ Creates contingency table                │
  ├──────┼────────────────┼──────────────────────────────┼──────────────────────────────────────────┤
  │ 5    │ groupby()      │ df.groupby('col')            │ Groups data by specified column          │
  ├──────┼────────────────┼──────────────────────────────┼──────────────────────────────────────────┤
  │ 6    │ sort_values()  │ df.sort_values(by='col')     │ Sorts DataFrame by column                │
  ├──────┼────────────────┼──────────────────────────────┼──────────────────────────────────────────┤
  │ 7    │ read_csv()     │ pd.read_csv('filepath')      │ Reads CSV file into DataFrame            │
  ├──────┼────────────────┼──────────────────────────────┼──────────────────────────────────────────┤
  │ 8    │ normalize      │ value_counts(normalize=True) │ Returns proportions instead of counts    │
  └──────┴────────────────┴──────────────────────────────┴──────────────────────────────────────────┘
---

## 🛠 Tools Used

* Python
* Jupyter Notebook
* Pandas Library
* Google Colab / VS Code

---

## 📂 Applications of Categorical Data Analysis

* Business sales analysis
* Customer behavior analysis
* Market research
* Academic performance analysis
* Data-driven decision making

---

## 🎯 Conclusion

Categorical data analysis is an important technique in data science and statistics.  
Using Python and the Pandas library, we can efficiently analyze categorical variables, identify patterns, and generate meaningful insights from datasets.

This experiment demonstrated various techniques such as **frequency analysis, cross tabulation, grouping, and filtering**, which are essential for real-world data analysis tasks.

---

## 📎 Extra Notes

* Pandas provides powerful tools for categorical analysis
* Cross-tabulation helps compare different variables
* Grouping allows deeper insights into datasets
* Data analysis helps in better decision making

---

*THANKYOU*
