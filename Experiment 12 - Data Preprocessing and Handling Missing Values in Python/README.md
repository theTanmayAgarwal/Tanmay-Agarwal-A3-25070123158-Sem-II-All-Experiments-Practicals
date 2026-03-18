# 🧹 DATA PREPROCESSING AND HANDLING MISSING VALUES IN PYTHON

Name- Tanmay Agarwal <br/>
Branch- EnTC A3 <br/>
PRN- 25070123158 <br/>

---

## 📄 Title Page

**Experiment Name:** Data Preprocessing and Handling Missing Values in Python <br/>
**Purpose:** Study of data preprocessing techniques and handling missing data using Python <br/>
**Language:** Python <br/>

---

## 🎯 Aim of the Experiment

The aim of this experiment is to understand **data preprocessing techniques** and learn how to **identify, handle, and clean missing values** in a dataset using Python and the Pandas library.

---

## 📌 Introduction

Data preprocessing is a crucial step in data analysis and machine learning.  
Real-world datasets often contain **missing, inconsistent, or noisy data**, which can affect analysis and model performance.

Handling missing values properly ensures **data quality, accuracy, and reliability**.  
Python provides powerful tools like **Pandas and NumPy** to preprocess and clean data efficiently.

---

## 📖 Study of Data Preprocessing (Instructions)

* Import necessary libraries (Pandas, NumPy)
* Load dataset into a DataFrame
* Identify missing values in the dataset
* Analyze the pattern of missing data
* Apply techniques to handle missing values
* Perform data cleaning and transformation
* Verify the final dataset after preprocessing

---

## 🔑 Key Concepts

* Data Preprocessing
* Missing Values
* Data Cleaning
* Data Transformation
* Imputation Techniques
* Data Consistency

---

## 📘 Theory (Handling Missing Values)

### 1. Identifying Missing Values

Missing values can be detected using functions like:

`df.isnull()`  
`df.isnull().sum()`

---

### 2. Removing Missing Values

Rows or columns containing missing values can be removed using:

`df.dropna()`

---

### 3. Filling Missing Values

Missing values can be replaced using appropriate values:

* Fill with mean:
  `df.fillna(df.mean())`

* Fill with median:
  `df.fillna(df.median())`

* Fill with mode:
  `df.fillna(df.mode().iloc[0])`

* Fill with constant value:
  `df.fillna(0)`

---

### 4. Forward Fill and Backward Fill

* Forward Fill:
  `df.fillna(method='ffill')`

* Backward Fill:
  `df.fillna(method='bfill')`

---

### 5. Data Transformation

After handling missing values, data may be transformed for better analysis.

Example:

`df['Column'] = df['Column'].astype(int)`

---

### 6. Checking Cleaned Data

After preprocessing, verify that no missing values remain:

`df.isnull().sum()`

---

## 📊 Dataset Used

The dataset used in this experiment contains:

* Numerical and categorical columns
* Missing values in different fields
* Real-world structured data for preprocessing practice

The dataset is used to demonstrate various **data cleaning and preprocessing techniques**.

---

## 🛠 Tools Used

* Python
* Jupyter Notebook
* Pandas Library
* NumPy Library
* VS Code / Google Colab

---

## 📂 Applications of Data Preprocessing

* Machine Learning model preparation
* Data cleaning in real-world datasets
* Business analytics
* Data science projects
* Improving data quality

---

## 🎯 Conclusion

Data preprocessing is a fundamental step in any data analysis workflow.  
Handling missing values properly ensures that the dataset is clean, reliable, and ready for analysis or machine learning.

This experiment demonstrated various techniques such as **removing, filling, and transforming data**, which are essential for working with real-world datasets.

---

## 📎 Extra Notes

* Always analyze missing data before handling it
* Choose appropriate imputation technique
* Avoid unnecessary data loss
* Clean data improves model accuracy
* Practice preprocessing techniques regularly

---

✨ THANKYOU
