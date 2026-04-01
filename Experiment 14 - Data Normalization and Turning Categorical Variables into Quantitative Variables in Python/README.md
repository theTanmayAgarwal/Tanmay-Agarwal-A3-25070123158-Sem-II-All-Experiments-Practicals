# 📊 Experiment 14 — Data Normalization & Encoding Categorical Variables in Python

---

## 🎓 Student Details

| Field | Details |
|---|---|
| **Name** | Tanmay Agarwal |
| **PRN** | 25070123158 |
| **Batch** | EnTC A3 |
| **Date** | 01/04/2026 |
| **Subject** | Data Analytics / Python Lab |

---

## 🎯 Aim of the Experiment

To study and implement the following data preprocessing techniques in Python using Pandas and Scikit-learn:

1. **Data Normalization** — Min-Max Normalization, Z-Score Normalization, and Decimal Scaling applied on product and Amazon datasets.
2. **Encoding Categorical Variables** — Label Encoding, One-Hot Encoding, and Dummy Encoding applied on order and student datasets.

---

## 📘 Introduction

In real-world data science and machine learning pipelines, raw datasets are rarely ready for direct use. Before any algorithm can be applied, the data must go through a **preprocessing** phase to ensure quality, consistency, and compatibility.

Two of the most essential preprocessing tasks are:

**1. Data Normalization (Feature Scaling):** Raw numerical features often differ dramatically in scale. For example, a dataset may contain `Price` values ranging from ₹299 to ₹24,999 and `Rating` values from 4.0 to 4.7. If fed directly into a model, the large-scale feature (Price) would dominate the smaller-scale one (Rating), causing biased predictions. Normalization transforms all features into a comparable range without distorting their relative relationships.

**2. Encoding Categorical Variables:** Machine learning algorithms fundamentally operate on numbers. Columns like `Gender`, `Department`, or `Payment_Method` contain text labels that must be converted into numeric form. Encoding techniques do this systematically while preserving the semantic meaning of the data where possible.

This experiment demonstrates both techniques across two practical datasets: a product sales dataset and an Amazon electronics dataset for normalization; an e-commerce orders dataset and a student placement dataset for encoding.

---

## 🐍 About the Libraries Used

### Pandas (`pandas`)
Pandas is the foundational Python library for data manipulation and analysis. It provides the `DataFrame` — a two-dimensional tabular data structure — along with hundreds of functions to load, clean, transform, and analyze data. In this experiment, Pandas is used to create datasets, apply manual normalization formulas via vectorized operations, and perform One-Hot / Dummy encoding using `pd.get_dummies()`.

### NumPy (`numpy`)
NumPy provides support for large multi-dimensional arrays and high-performance mathematical operations. While Pandas handles the table-level logic, NumPy underpins the arithmetic (mean, std, min, max) used in normalization calculations.

### Scikit-learn (`sklearn`)
Scikit-learn is Python's premier machine learning library. Its `preprocessing` module provides standardized, reusable transformers for scaling and encoding. In this experiment, `LabelEncoder` from `sklearn.preprocessing` is used to encode binary and ordinal categorical columns.

---

## 🔧 Preprocessing Techniques Covered

This experiment covers two major categories of preprocessing:

### Part A — Data Normalization

| Technique | Applied On | Formula |
|---|---|---|
| Min-Max Normalization | Price, Rating | `(x - min) / (max - min)` |
| Z-Score Normalization | Units_Sold | `(x - mean) / std` |
| Decimal Scaling | Price | `x / 10^k` |
| Multi-Column Min-Max | Price, Units_Sold, Discount | Vectorized on DataFrame |

### Part B — Encoding Categorical Variables

| Technique | Applied On | Tool Used |
|---|---|---|
| Label Encoding | Gender (Customer), Placement_Status | `sklearn LabelEncoder` |
| One-Hot Encoding | Payment_Method, Department | `pd.get_dummies()` |
| Dummy Encoding (Drop First) | Payment_Method, Department | `pd.get_dummies(drop_first=True)` |

---

## 📖 Detailed Theory

### 1. 📐 Min-Max Normalization

Min-Max normalization, also called **feature scaling**, rescales values so that they all fall within the range **[0, 1]**. The minimum value in the column maps to 0, the maximum maps to 1, and all other values are proportionally distributed in between.

**Formula:**

```
x_normalized = (x - x_min) / (x_max - x_min)
```

**Working Logic:**

1. Identify the column to normalize (e.g., `Price`).
2. Compute the minimum value of the column: `df['Price'].min()`.
3. Compute the maximum value of the column: `df['Price'].max()`.
4. Subtract the minimum from every element in the column.
5. Divide each result by the range `(max - min)`.
6. Store the result as a new column.

**Example (from notebook):**
```python
df['Price_MinMax'] = (df['Price'] - df['Price'].min()) / (df['Price'].max() - df['Price'].min())
```

**When to use:** When the algorithm requires input features in a bounded range, such as K-Nearest Neighbours, Neural Networks, or Support Vector Machines. Also useful when the distribution is not Gaussian.

---

### 2. 📉 Z-Score Normalization (Standardization)

Z-Score normalization transforms data so that it has a **mean of 0** and a **standard deviation of 1**. Unlike Min-Max, the output is not bounded to [0,1] — values can be negative or greater than 1 (they represent how many standard deviations away from the mean each data point lies).

**Formula:**

```
x_zscore = (x - μ) / σ
```
where μ = mean, σ = standard deviation.

**Working Logic:**

1. Compute the column mean: `df['Units_Sold'].mean()`.
2. Compute the column standard deviation: `df['Units_Sold'].std()`.
3. Subtract the mean from every element.
4. Divide by the standard deviation.
5. Positive values are above average; negative values are below average.

**Example (from notebook):**
```python
df['Units_Zscore'] = (df['Units_Sold'] - df['Units_Sold'].mean()) / df['Units_Sold'].std()
```

**When to use:** Best suited for algorithms that assume Gaussian-distributed data, such as Linear Regression, Logistic Regression, and Principal Component Analysis (PCA).

---

### 3. 🔢 Decimal Scaling

Decimal Scaling divides each value by a power of 10 (`10^k`) such that the absolute value of the scaled data becomes less than 1. The value of `k` is chosen based on the maximum absolute value in the dataset.

**Formula:**

```
x_scaled = x / 10^k
```

**Working Logic:**

1. Determine the number of digits in the maximum value (e.g., ₹24,999 has 5 digits → k = 5).
2. Divide every element in the column by `10^5` (i.e., `100000`).
3. The values are now decimal fractions between 0 and 1.

**Example (from notebook):**
```python
df['Price_decimal'] = df['Price'] / 100000  # 10^5
```

**When to use:** Useful for quick, simple normalization when all values are positive and you need a fast, interpretable scaling without computing statistics.

---

### 4. 🏷️ Label Encoding

Label Encoding assigns a unique integer to each distinct category in a column. It is done alphabetically by default, so `Female → 0` and `Male → 1`. The result is a single integer column replacing the original text column.

**Syntax:**
```python
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['Gender_Label'] = le.fit_transform(df['Customer_Gender'])
```

**Working Logic:**

1. Import `LabelEncoder` from `sklearn.preprocessing`.
2. Create an instance: `le = LabelEncoder()`.
3. Call `fit_transform(column)` on the target column — this simultaneously learns the mapping and applies it.
4. The encoded integers are stored in a new column.

**When to use:** Suitable for **binary** or **ordinal** categorical variables (e.g., Yes/No, Small/Medium/Large). Avoid for nominal multi-class variables where no natural ordering exists, as the model may incorrectly infer ordinality.

---

### 5. 🔥 One-Hot Encoding (`pd.get_dummies`)

One-Hot Encoding converts a categorical column with `n` unique values into `n` binary (True/False or 0/1) columns — one for each category. Each row has exactly one `True` and the rest are `False`. This avoids the implied ordering that Label Encoding introduces.

**Syntax:**
```python
df_encoded = pd.get_dummies(df1, columns=['Payment_Method'])
```

**Working Logic:**

1. Pass the DataFrame and the column(s) to encode to `pd.get_dummies()`.
2. Pandas scans all unique values in the specified column.
3. It creates one new boolean column for each unique value, named `ColumnName_Value`.
4. For each row, the column corresponding to its original value is set to `True`; all others are `False`.
5. The original column is dropped from the output.

**When to use:** Best for **nominal** categorical variables with no inherent order (e.g., City, Payment Method, Product Category). Suitable for most regression and classification algorithms.

---

### 6. 🃏 Dummy Encoding (`drop_first=True`)

Dummy Encoding is identical to One-Hot Encoding, but it **drops the first category column** to avoid the "dummy variable trap" (multicollinearity). If you have `n` categories, only `n-1` columns are created — the dropped category is implicitly represented when all remaining columns are `False`.

**Syntax:**
```python
df_dummy = pd.get_dummies(df1, columns=['Payment_Method'], drop_first=True)
```

**Working Logic:**

1. Same as One-Hot Encoding, but with the `drop_first=True` parameter.
2. The first category (alphabetically) is dropped.
3. Its presence can be inferred when all other dummy columns are 0.
4. This prevents multicollinearity in linear models.

**When to use:** Preferred in **linear regression** and **logistic regression** to satisfy the full-rank matrix assumption and avoid the dummy variable trap.

---

### Key Functions Reference

| Function / Command | Module | Description |
|---|---|---|
| `pd.DataFrame(data)` | pandas | Creates a DataFrame from a Python dictionary |
| `pd.read_csv("file.csv")` | pandas | Loads a CSV file into a DataFrame |
| `df['col'].min()` | pandas | Returns the minimum value of a column |
| `df['col'].max()` | pandas | Returns the maximum value of a column |
| `df['col'].mean()` | pandas | Returns the mean (average) of a column |
| `df['col'].std()` | pandas | Returns the standard deviation of a column |
| `pd.get_dummies(df, columns=[...])` | pandas | Applies One-Hot Encoding to specified columns |
| `pd.get_dummies(df, columns=[...], drop_first=True)` | pandas | Applies Dummy Encoding, dropping the first category |
| `LabelEncoder()` | sklearn.preprocessing | Creates a Label Encoder instance |
| `le.fit_transform(column)` | sklearn.preprocessing | Learns label mapping and encodes the column in one step |
| `le.fit(column)` | sklearn.preprocessing | Learns the label mapping without transforming |
| `le.transform(column)` | sklearn.preprocessing | Applies a previously learned label mapping |
| `MinMaxScaler()` | sklearn.preprocessing | Scikit-learn's built-in Min-Max scaler object |
| `StandardScaler()` | sklearn.preprocessing | Scikit-learn's built-in Z-Score scaler object |
| `scaler.fit_transform(X)` | sklearn.preprocessing | Fits and applies a scaler to the data in one step |
| `SimpleImputer(strategy='mean')` | sklearn.impute | Fills missing values with the column mean |

---

## ⚙️ Algorithm / Step-by-Step Logic

### Part A — Data Normalization

1. Import the necessary libraries: `pandas` and `numpy`.
2. Create the dataset as a Python dictionary and convert it to a Pandas DataFrame using `pd.DataFrame()`.
3. **Min-Max Normalization:** For the `Price` column, compute `(df['Price'] - df['Price'].min()) / (df['Price'].max() - df['Price'].min())` and store the result in a new column `Price_MinMax`.
4. **Z-Score Normalization:** For `Units_Sold`, compute `(df['Units_Sold'] - df['Units_Sold'].mean()) / df['Units_Sold'].std()` and store in `Units_Zscore`.
5. **Decimal Scaling:** For `Price`, divide each value by `100000` (10^5) and store in `Price_decimal`.
6. **Multi-column normalization:** Select multiple numeric columns into a subset `cols`, apply the Min-Max formula using vectorized Pandas operations, and display the normalized DataFrame `df_norm`.
7. Load the Amazon products CSV dataset using `pd.read_csv()`.
8. Repeat steps 3–5 on the CSV dataset for `Price` (Min-Max), `Rating` (Min-Max), `Units_Sold` (Z-Score), and `Price` (Decimal Scaling).
9. Verify results by displaying the DataFrame and confirming the range [0,1] for Min-Max and decimal < 1 for Decimal Scaling.

### Part B — Encoding Categorical Variables

1. Create the orders dataset as a dictionary with columns: `Order ID`, `Customer_Gender`, `Payment_Method`, `Product-category`, `City`, and `Order_value`.
2. Convert to a DataFrame using `pd.DataFrame()`.
3. **Label Encoding:** Import `LabelEncoder` from `sklearn.preprocessing`. Instantiate it as `le`. Call `le.fit_transform(df1['Customer_Gender'])` and store the result in `df1['Gender_Label']`.
4. **One-Hot Encoding:** Apply `pd.get_dummies(df1, columns=['Payment_Method'])` to create binary columns for each payment method. Display the result as `df_encoded`.
5. **Dummy Encoding:** Apply `pd.get_dummies(df1, columns=['Payment_Method'], drop_first=True)` to create `n-1` columns (avoids the dummy variable trap). Display the result as `df_dummy`.
6. Load the Student dataset using `pd.read_csv("Student-Dataset.csv")`.
7. Apply Label Encoding to `Placement_Status` column (Placed → 1, Not Placed → 0) and store in `Placement_Label`.
8. Apply One-Hot Encoding to `Department` column using `pd.get_dummies()` and verify binary columns for each department.
9. Apply Dummy Encoding to `Department` with `drop_first=True` to reduce the number of columns by one.
10. Display all resulting DataFrames to verify correctness.

---

## 📊 Charts & Visualization

While this experiment focuses on tabular transformations, the following chart types are commonly used to visualize the effect of normalization and encoding:

### 📌 Bar Chart — Original vs Normalized Values
A grouped bar chart comparing raw `Price` values against `Price_MinMax` values helps visualize how normalization compresses the scale while preserving relative ordering.

```python
import matplotlib.pyplot as plt
df[['Product', 'Price', 'Price_MinMax']].set_index('Product').plot(kind='bar', figsize=(10, 5))
plt.title('Original Price vs Min-Max Normalized Price')
plt.ylabel('Value')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

### 📌 Histogram — Distribution Before and After Z-Score Normalization
A histogram of `Units_Sold` before and after Z-Score normalization illustrates the shift of the distribution to mean=0.

```python
fig, axes = plt.subplots(1, 2, figsize=(12, 4))
df['Units_Sold'].hist(ax=axes[0], bins=6, color='steelblue')
axes[0].set_title('Units Sold — Original')
df['Units_Zscore'].hist(ax=axes[1], bins=6, color='salmon')
axes[1].set_title('Units Sold — Z-Score Normalized')
plt.tight_layout()
plt.show()
```

### 📌 Box Plot — Spread Comparison Across Multiple Columns
A box plot of the normalized columns can highlight the standardized distribution and any outliers.

```python
df[['Price_MinMax', 'Units_Zscore', 'Rating_MinMax']].boxplot(figsize=(8, 5))
plt.title('Box Plot of Normalized Features')
plt.ylabel('Normalized Value')
plt.show()
```

> **💡 Note:** Add these visualization cells to the notebook after the normalization section to generate the charts above.

---

## 🗃️ Dataset Description

### Dataset 1 — Product Sales (Manual)

A small manually created dataset used to demonstrate normalization formulas clearly.

| Column | Type | Description |
|---|---|---|
| `Product` | Categorical | Name of the product (Laptop, Mobile, Tablet, etc.) |
| `Price` | Numeric | Price of the product in INR |
| `Units_Sold` | Numeric | Number of units sold |
| `Discount` | Numeric | Discount percentage offered |

- **Rows:** 6
- **Source:** Manually defined in the notebook

### Dataset 2 — Amazon Products (`amazon_products_dataset_Expt-14.csv`)

A CSV dataset representing 50 Amazon electronics products, used to apply normalization on real data.

| Column | Type | Description |
|---|---|---|
| `Product_ID` | String | Unique identifier (P101–P150) |
| `Product_Name` | String | Name of the product |
| `Price` | Numeric | Price in INR (range: ₹299 – ₹24,999) |
| `Rating` | Numeric | Customer rating (range: 4.0 – 4.7) |
| `Reviews` | Numeric | Number of customer reviews |
| `Units_Sold` | Numeric | Number of units sold (range: 70 – 610) |

- **Rows:** 50
- **Source:** CSV file loaded via `pd.read_csv()`

### Dataset 3 — E-Commerce Orders (Manual)

A manually created dataset to demonstrate encoding techniques.

| Column | Type | Description |
|---|---|---|
| `Order ID` | Numeric | Unique order identifier (101–106) |
| `Customer_Gender` | Categorical | Male / Female |
| `Payment_Method` | Categorical | Credit Card / PayPal |
| `Product-category` | Categorical | Electronics / Clothing |
| `City` | Categorical | US city of delivery |
| `Order_value` | Numeric | Order value in USD |

- **Rows:** 6
- **Source:** Manually defined in the notebook

### Dataset 4 — Student Placement (`Student-Dataset.csv`)

A CSV dataset representing 10 engineering students and their placement outcomes.

| Column | Type | Description |
|---|---|---|
| `Roll_No` | Numeric | Student roll number (101–110) |
| `Gender` | Categorical | Male / Female |
| `Department` | Categorical | Computer / IT / ENTC / Mechanical / Civil |
| `CGPA` | Numeric | Cumulative GPA (6.5 – 9.1) |
| `Number_of_Backlogs` | Numeric | Number of backlogs (0 – 3) |
| `Attendance_Percentage` | Numeric | Attendance % (72 – 96) |
| `Placement_Status` | Categorical | Placed / Not Placed |
| `Salary` | Numeric | Offered salary in INR (0 if not placed) |

- **Rows:** 10
- **Source:** CSV file loaded via `pd.read_csv()`

---

## 🛠️ Tools & Technologies Used

| Tool / Library | Version | Purpose |
|---|---|---|
| **Python** | 3.x | Core programming language |
| **Pandas** | Latest | DataFrame operations, `get_dummies` encoding |
| **NumPy** | Latest | Underlying array math for normalization |
| **Scikit-learn** | Latest | `LabelEncoder` for categorical encoding |
| **Google Colab** | Cloud | Notebook execution environment |
| **Jupyter Notebook** | — | Code organization and output display |

---

## 💡 Applications

Data normalization and categorical encoding are foundational steps that power real-world systems across many industries:

- **E-Commerce Recommendation Systems:** Normalizing product prices and ratings ensures that high-price items do not unfairly dominate recommendation scores. Encoding product categories enables collaborative filtering algorithms to compare them numerically.

- **Credit Risk Assessment (Banking):** Label encoding of loan approval status (Approved/Rejected) and one-hot encoding of employment type enable logistic regression and decision tree models to predict loan defaults.

- **Healthcare & Medical Diagnosis:** Normalizing features like blood pressure, age, and glucose levels before feeding them into neural networks ensures stable training and accurate classification of diseases.

- **HR & Placement Prediction:** The Student dataset in this experiment directly mirrors how educational institutions use CGPA, attendance, and department (encoded) to predict placement outcomes using classification algorithms.

- **Natural Language Processing (NLP):** Label encoding of sentiment categories (Positive/Negative/Neutral) is a standard preprocessing step before training text classifiers.

- **Image Recognition & Computer Vision:** Feature vectors extracted from images are always normalized to a [0,1] range before being passed into convolutional neural networks.

---

## ✅ Conclusion

This experiment successfully demonstrated two fundamental data preprocessing techniques in Python:

**Part A — Data Normalization** was performed on both a manually created product dataset and a real Amazon electronics CSV dataset. Three normalization methods were implemented: Min-Max Normalization (rescaling Price and Rating to [0,1]), Z-Score Normalization (standardizing Units_Sold to mean=0, std=1), and Decimal Scaling (dividing Price by 10^5). All techniques were implemented using direct Pandas vectorized operations, producing clean and interpretable output DataFrames.

**Part B — Encoding Categorical Variables** was demonstrated on an e-commerce orders dataset and a student placement dataset. Label Encoding via Scikit-learn's `LabelEncoder` was applied to binary columns (`Customer_Gender`, `Placement_Status`). One-Hot Encoding via `pd.get_dummies()` was applied to nominal columns (`Payment_Method`, `Department`), creating separate binary columns for each unique category. Dummy Encoding with `drop_first=True` was then used to eliminate one redundant column per variable to prevent multicollinearity.

Through this experiment, it is evident that the choice of normalization technique depends on the data distribution and the downstream algorithm, while the encoding technique depends on whether the categorical variable has an implied ordering (ordinal → Label Encoding) or not (nominal → One-Hot/Dummy Encoding). These preprocessing steps are not optional — they are prerequisites for building reliable, unbiased machine learning models.

---

## 📝 Extra Notes

> **⚠️ Label Encoding vs. One-Hot Encoding — When to Use Which?**
>
> Label Encoding (0, 1, 2...) introduces an implicit ordinal relationship. For a column like `Department` with values Computer/IT/ENTC/Mechanical/Civil, assigning 0–4 suggests Computer < IT < ENTC < Mechanical < Civil — which is meaningless. This can confuse linear models. Always use One-Hot Encoding for nominal categories with more than 2 values.

> **⚠️ The Dummy Variable Trap**
>
> When you One-Hot encode a column with `n` categories, you get `n` binary columns. But these `n` columns are perfectly linearly dependent (they always sum to 1), which causes multicollinearity in linear models. The fix is to always use `drop_first=True` in linear regression contexts.

> **🔁 `fit()` vs. `fit_transform()` vs. `transform()`**
>
> - `fit()` — Learns the parameters (min, max, mean, categories) from the data. Does NOT change the data.
> - `transform()` — Applies the learned parameters to transform data. Must call `fit()` first.
> - `fit_transform()` — Combines both steps in one call. Use this on training data only.
>
> Always fit on training data and only transform on test data — never fit on test data, as this causes data leakage.

> **📌 Normalization Cheat Sheet**
>
> | Situation | Recommended Technique |
> |---|---|
> | Bounded output needed (neural nets, KNN) | Min-Max Normalization |
> | Gaussian data, outliers present | Z-Score Standardization |
> | Quick scaling with no statistics needed | Decimal Scaling |
> | Tree-based models (Decision Tree, RF) | Normalization not required |

---

*README generated for academic and GitHub documentation purposes — Experiment 14, EnTC A3 Batch.*
