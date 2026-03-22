# 📊 DATA BINNING AND DATA FORMATTING USING PYTHON

Name- Tanmay Agarwal <br/>
Branch- EnTC A3 <br/>
PRN- 25070123158 <br/>

---

## 📄 Title Page

**Experiment Name:** Data Binning and Data Formatting using Python <br/>
**Purpose:** Study of data binning techniques and data formatting methods using Python <br/>
**Language:** Python <br/>

---

## 🎯 Aim of the Experiment

The aim of this experiment is to understand **data binning** and **data formatting techniques** in Python and apply them to organize, clean, and prepare data for analysis.

---

## 📌 Introduction

In data analysis, raw data is often unstructured and difficult to interpret.  
**Data binning** is used to group continuous data into discrete intervals (bins), making it easier to analyze patterns.  

**Data formatting** involves transforming data into a suitable structure or format, improving readability and usability for further analysis.

Python libraries like **Pandas and NumPy** provide powerful tools for performing these operations efficiently.

---

## 📖 Study of Data Binning and Formatting (Instructions)

* Import required libraries (Pandas, NumPy)
* Load dataset into a DataFrame
* Analyze continuous data values
* Apply binning techniques to group data
* Label bins appropriately
* Perform data formatting operations
* Convert data types if required
* Verify and display formatted data

---

## 🔑 Key Concepts

* Data Binning
* Continuous vs Discrete Data
* Equal Width Binning
* Data Formatting
* Data Type Conversion
* Labeling Data

---

## 📘 Theory (Data Binning and Formatting)

### 1. Data Binning

Data binning is the process of dividing continuous data into intervals.

Example:

`pd.cut(df['Age'], bins=5)`

---

### 2. Equal Width Binning

Data is divided into bins of equal size.

Example:

`pd.cut(df['Marks'], bins=3, labels=['Low', 'Medium', 'High'])`

---

### 3. Equal Frequency Binning

Bins are created such that each bin has an equal number of data points.

Example:

`pd.qcut(df['Marks'], q=3)`

---

### 4. Labeling Bins

Labels are assigned to bins for better interpretation.

Example:

`pd.cut(df['Age'], bins=[0, 18, 35, 60], labels=['Young', 'Adult', 'Senior'])`

---

### 5. Data Formatting

Data formatting includes converting data into proper types and formats.

Example:

* Convert to integer:
  `df['Column'] = df['Column'].astype(int)`

* Convert to string:
  `df['Column'] = df['Column'].astype(str)`

---

### 6. Handling Inconsistent Data

Formatting helps in correcting inconsistent values in datasets.

Example:

`df['Column'] = df['Column'].str.lower()`

---

## 📊 Dataset Used

The dataset used in this experiment includes:

* Continuous numerical data (e.g., age, marks, income)
* Data requiring grouping into categories
* Columns requiring formatting and type conversion

The dataset is used to demonstrate **binning and formatting techniques effectively**.

---

## 🛠 Tools Used

* Python
* Jupyter Notebook
* Pandas Library
* NumPy Library
* VS Code / Google Colab

---

## 📂 Applications of Data Binning and Formatting

* Data preprocessing for machine learning
* Simplifying complex datasets
* Data visualization
* Statistical analysis
* Business intelligence

---

## 🎯 Conclusion

Data binning and formatting are essential preprocessing techniques in data analysis.  
They help in simplifying data, improving readability, and preparing datasets for further analysis or modeling.

This experiment demonstrated how to **group continuous data into bins and format datasets properly**, making them more structured and meaningful.

---

## 📎 Extra Notes

* Binning reduces data complexity
* Proper labeling improves understanding
* Formatting ensures consistency
* Always verify data after transformation
* Useful in real-world data analysis tasks

---

## Binning Formula                                                                      
                                                                                               
  ```python                                                                                    
  pd.cut(data, bins=[thresholds], labels=[categories])
                                                                                               
  ┌───────────┬─────────────────────────────┐
  │ Parameter │         Description         │                                                  
  ├───────────┼─────────────────────────────┤                                                  
  │ data      │ The numerical column to bin │
  ├───────────┼─────────────────────────────┤                                                  
  │ bins      │ List of boundary values     │                                                  
  ├───────────┼─────────────────────────────┤                                                  
  │ labels    │ Names for each bin category │                                                  
  └───────────┴─────────────────────────────┘                                                  
                  
  2.3 Key Concepts                                                                             
  
  ┌────────────────┬─────────────────────────────────────────────────────┐                     
  │    Concept     │                     Definition                      │
  ├────────────────┼─────────────────────────────────────────────────────┤
  │ Bins           │ Boundary values that divide data into intervals     │
  ├────────────────┼─────────────────────────────────────────────────────┤
  │ Labels         │ Names assigned to each bin interval                 │                     
  ├────────────────┼─────────────────────────────────────────────────────┤                     
  │ Left-inclusive │ Default: bins include left edge, exclude right edge │                     
  └────────────────┴─────────────────────────────────────────────────────┘                     
                  
  ---
                                                                    
  * Workflow Diagram
                                                                                               
  ┌─────────────────────────────────────────────────────────┐
  │                  DATA BINNING WORKFLOW                   │                                 
  ├─────────────────────────────────────────────────────────┤                                  
  │                                                         │                                  
  │   ┌──────────────┐      ┌──────────────┐               │                                   
  │   │ Load Dataset │ ───► │ Define Bins  │               │                                   
  │   └──────────────┘      │ & Labels     │               │                                   
  │                         └──────┬───────┘               │                                   
  │                                │                        │                                  
  │                                ▼                        │                                  
  │                         ┌──────────────┐               │                                   
  │                         │  pd.cut()    │               │                                   
  │                         └──────┬───────┘               │                                   
  │                                │                        │                                  
  │                                ▼                        │
  │                         ┌──────────────┐               │                                   
  │                         │ New Category │               │
  │                         │    Column    │                │
  │                         └──────┬───────┘               │                                   
  │                                │                        │
  │                                ▼                        │                                  
  │                         ┌──────────────┐               │                                   
  │                         │   Format &   │               │                                   
  │                         │   Sort Data  │               │                                   
  │                         └──────────────┘               │                                   
  │                                                         │                                  
  └─────────────────────────────────────────────────────────┘                                  
                                                                                               
  ---                                                                                 
  * Summary Table

  ┌────────────────┬───────────────┬───────────────────────────────────────────────────────┐
  │   Operation    │   Function    │                        Example                        │
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤   
  │ Binning        │ pd.cut()      │ pd.cut(df['Price'], bins=[0,100,200],                 │
  │                │               │ labels=['A','B'])                                     │   
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤   
  │ Type           │ astype()      │ df['col'].astype(float)                               │   
  │ Conversion     │               │                                                       │   
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤   
  │ Uppercase      │ str.upper()   │ df['col'].str.upper()                                 │
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤   
  │ Sorting        │ sort_values() │ df.sort_values(by='Price')                            │
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤
  │ Unique Values  │ unique()      │ df['col'].unique()                                    │
  └────────────────┴───────────────┴───────────────────────────────────────────────────────┘   
  
  ---
```                                                                                                                 

✨ *Thankyou* 

                                                                                               
