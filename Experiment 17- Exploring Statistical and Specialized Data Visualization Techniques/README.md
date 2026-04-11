# 📊 Experiment 17 – Exploring Statistical and Specialized Data Visualization Techniques

---

## 📋 Title Page

| **Field**           | **Details**                                                         |
| ------------------- | ------------------------------------------------------------------- |
| **Name**            | Tanmay Agarwal                                                      |
| **PRN**             | 25070123158                                                         |
| **Branch / Batch**  | EnTC A3                                                             |
| **Experiment No.**  | 17                                                                  |
| **Subject**         | Exploratory Data Analysis (EDA)                                     |
| **Date**            | 08 / 04 / 2026                                                      |
| **Title**           | Exploring Statistical and Specialized Data Visualization Techniques |

---

## 🎯 Aim of the Experiment

To explore and implement various **statistical and specialized data visualization techniques** using Python libraries such as Matplotlib, Seaborn, and Pandas. The experiment aims to:

1. Understand the importance of statistical visualization in data analysis
2. Learn to create various statistical plots including histograms, KDE plots, box plots, violin plots, pair plots, and heatmaps
3. Analyze distributions, detect outliers, and identify correlations in datasets
4. Gain hands-on experience with advanced visualization techniques for multivariate analysis
5. Develop skills for interpreting statistical visualizations and deriving meaningful insights

---

## 📖 Introduction

Statistical data visualization is a fundamental aspect of exploratory data analysis (EDA) that enables data scientists and analysts to understand the underlying patterns, distributions, and relationships within datasets. Unlike basic charts that simply display data points, statistical visualizations provide deeper insights into the statistical properties of data including central tendency, dispersion, skewness, and outliers.

This experiment focuses on **specialized visualization techniques** that go beyond basic plotting methods. These techniques are essential for:

- **Distribution Analysis**: Understanding how data is spread across different values
- **Outlier Detection**: Identifying anomalous data points that deviate significantly from the norm
- **Correlation Analysis**: Discovering relationships between multiple variables
- **Multivariate Exploration**: Analyzing interactions between multiple variables simultaneously
- **Density Estimation**: Understanding the probability distribution of continuous variables

Statistical visualizations serve as a bridge between raw data and actionable insights, making them indispensable tools in data science, machine learning, and business analytics workflows.

---

## 🔬 About Statistical Data Visualization

### What is Statistical Visualization?

Statistical visualization refers to graphical representations that emphasize the statistical properties of data. These visualizations help analysts understand:

| Property | Description |
|----------|-------------|
| **Central Tendency** | Mean, median, and mode of the data |
| **Dispersion** | Spread of data (variance, standard deviation, range) |
| **Distribution Shape** | Skewness and kurtosis |
| **Outliers** | Data points that significantly deviate from the pattern |
| **Correlations** | Relationships between variables |

### Importance in Data Analysis

1. **Pattern Recognition**: Identify trends, cycles, and anomalies
2. **Data Quality Assessment**: Detect missing values, outliers, and errors
3. **Feature Selection**: Understand which variables are important
4. **Model Assumptions**: Verify statistical assumptions before modeling
5. **Communication**: Present findings effectively to stakeholders

### Difference Between Basic and Statistical Charts

| Aspect | Basic Charts | Statistical Charts |
|--------|--------------|-------------------|
| **Purpose** | Display raw data | Reveal statistical properties |
| **Examples** | Bar, Line, Pie | Box, Violin, KDE, Heatmap |
| **Information Depth** | Surface-level | Deep statistical insights |
| **Complexity** | Simple interpretation | Requires statistical knowledge |
| **Use Case** | Reporting | Analysis & Research |

---

## 📚 About Libraries Used

### 🎨 Matplotlib

**Matplotlib** is Python's foundational plotting library that provides a MATLAB-like interface for creating static, animated, and interactive visualizations.

**Key Features:**
- Low-level plotting interface with fine control
- Support for various plot types (line, scatter, bar, histogram)
- Customizable axes, labels, legends, and styles
- Integration with NumPy and Pandas

```python
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.plot(x, y)
plt.title("My Plot")
plt.show()
```

---

### 🌊 Seaborn

**Seaborn** is a high-level statistical data visualization library built on top of Matplotlib. It provides beautiful default styles and color palettes, and is specifically designed for statistical graphics.

**Key Features:**
- Beautiful default themes and color palettes
- Built-in statistical aggregations and estimations
- Automatic handling of Pandas DataFrames
- Specialized plots for categorical and statistical data
- Seamless integration with Matplotlib

**Statistical Plot Types in Seaborn:**

| Plot Type | Function | Purpose |
|-----------|----------|---------|
| Histogram | `sns.histplot()` | Distribution of a single variable |
| KDE Plot | `sns.kdeplot()` | Probability density estimation |
| Box Plot | `sns.boxplot()` | Distribution summary with outliers |
| Violin Plot | `sns.violinplot()` | Distribution with density |
| Pair Plot | `sns.pairplot()` | Pairwise relationships |
| Heatmap | `sns.heatmap()` | Matrix visualization |
| Swarm Plot | `sns.swarmplot()` | Non-overlapping points |

```python
import seaborn as sns
sns.set_style("whitegrid")
sns.boxplot(x='category', y='values', data=df)
plt.show()
```

---

### 🐼 Pandas

**Pandas** is Python's primary data manipulation library that provides data structures and functions for efficiently handling structured data.

**Key Features:**
- DataFrame and Series data structures
- Data cleaning and preprocessing
- GroupBy and pivot operations
- Statistical computations
- Built-in plotting capabilities

```python
import pandas as pd
df = pd.read_csv('data.csv')
df.describe()  # Statistical summary
df.corr()      # Correlation matrix
```

---

## 📈 Statistical Visualization Techniques

### 1. Distribution Plot (Histogram + KDE)

**Definition:**
A distribution plot shows how data values are distributed across different ranges. It combines a histogram (bars showing frequency) with a Kernel Density Estimate (KDE) curve that provides a smooth probability density function.

**Syntax Example:**
```python
# Histogram
plt.hist(data, bins=20, color='skyblue', edgecolor='black')

# Histogram with KDE
sns.histplot(data, kde=True, bins=20)

# KDE Plot
sns.kdeplot(data, fill=True, color='blue')
```

**When to Use:**
- Analyzing the shape of data distribution
- Checking for normality or skewness
- Comparing distributions across groups
- Understanding frequency of values

**Interpretation:**
- **Peak**: Indicates the mode (most frequent values)
- **Spread**: Shows data dispersion
- **Tails**: Reveal outliers and extreme values
- **Symmetry**: Left/right skew indicates deviation from normal distribution

---

### 2. KDE Plot (Kernel Density Estimation)

**Definition:**
KDE Plot is a non-parametric method to estimate the probability density function of a continuous variable. It creates a smooth curve representing the distribution shape.

**Syntax Example:**
```python
# Single KDE
sns.kdeplot(data=df, x='column', fill=True)

# Multiple KDEs by category
sns.kdeplot(data=df, x='column', hue='category', fill=True, alpha=0.5)
```

**When to Use:**
- Visualizing probability distributions
- Comparing distributions across groups
- Identifying multimodal distributions
- Smoothing discrete data into continuous form

**Interpretation:**
- **Height**: Probability density at that point
- **Width**: Spread of the data
- **Multiple Peaks**: Indicates multimodal distribution
- **Area Under Curve**: Represents probability (integrates to 1)

---

### 3. Box Plot (Box-and-Whisker Plot)

**Definition:**
A box plot is a standardized way of displaying the distribution of data based on five summary statistics: minimum, first quartile (Q1), median, third quartile (Q3), and maximum. It also identifies outliers.

**Syntax Example:**
```python
# Single box plot
plt.boxplot(data)

# Seaborn box plot
sns.boxplot(x='category', y='values', data=df)

# Horizontal box plot
sns.boxplot(y='values', data=df)
```

**When to Use:**
- Comparing distributions across categories
- Outlier detection
- Understanding data spread and central tendency
- Quick statistical summary

**Interpretation:**

| Component | Description |
|-----------|-------------|
| **Box** | Interquartile range (IQR) from Q1 to Q3 |
| **Line inside box** | Median (Q2) |
| **Whiskers** | Typically 1.5 × IQR from quartiles |
| **Points outside whiskers** | Outliers |
| **Box width** | Proportional to sample size (optional) |

---

### 4. Violin Plot

**Definition:**
A violin plot combines a box plot with a kernel density estimation, showing the probability density of the data at different values, smoothed by a kernel density estimator.

**Syntax Example:**
```python
# Basic violin plot
sns.violinplot(x='category', y='values', data=df)

# With inner quartile lines
sns.violinplot(x='category', y='values', data=df, inner='quartile')

# Split violin for comparison
sns.violinplot(x='category', y='values', hue='group', data=df, split=True)
```

**When to Use:**
- Visualizing distribution shape alongside summary statistics
- Comparing multiple groups
- When sample size is large enough for density estimation
- Understanding both central tendency and spread

**Interpretation:**
- **Width**: Probability density at that value
- **Symmetry**: Check if distribution is symmetric
- **Inner box/quartiles**: Shows median and IQR
- **Shape**: Reveals multimodal distributions better than box plots

---

### 5. Pair Plot

**Definition:**
A pair plot creates a grid of axes showing the relationship between pairs of variables in a dataset. Diagonal plots show the distribution of individual variables, while off-diagonal plots show relationships between pairs.

**Syntax Example:**
```python
# Basic pair plot
sns.pairplot(df)

# With hue for categorical coloring
sns.pairplot(df, hue='category')

# Selected columns
sns.pairplot(df[['col1', 'col2', 'col3', 'category']], hue='category')

# Corner plot (lower triangle only)
sns.pairplot(df, corner=True)
```

**When to Use:**
- Exploratory data analysis on multivariate datasets
- Feature selection for machine learning
- Identifying correlations between variables
- Understanding pairwise relationships

**Interpretation:**
- **Diagonal**: Distribution of each variable
- **Off-diagonal**: Scatter plots showing relationships
- **Patterns**: Linear, quadratic, or no relationship
- **Clusters**: Groupings visible when using hue

---

### 6. Heatmap (Correlation Matrix)

**Definition:**
A heatmap is a two-dimensional graphical representation of data where values are represented by colors. In statistical analysis, it's commonly used to visualize correlation matrices.

**Syntax Example:**
```python
# Correlation heatmap
corr = df.corr()
sns.heatmap(corr, annot=True, cmap='coolwarm')

# With formatting
sns.heatmap(corr,
            annot=True,           # Show values
            fmt='.2f',            # Decimal format
            cmap='coolwarm',      # Color map
            center=0,             # Center color at 0
            square=True,          # Square cells
            linewidths=0.5)       # Cell borders
```

**When to Use:**
- Visualizing correlation matrices
- Feature selection in machine learning
- Identifying multicollinearity
- Understanding relationships in large datasets

**Interpretation:**

| Correlation Value | Interpretation |
|-------------------|----------------|
| **0.7 to 1.0** | Strong positive correlation |
| **0.3 to 0.7** | Moderate positive correlation |
| **-0.3 to 0.3** | Weak or no correlation |
| **-0.7 to -0.3** | Moderate negative correlation |
| **-1.0 to -0.7** | Strong negative correlation |

---

## 🔧 Specialized Visualization Techniques

### Correlation Heatmaps

Correlation heatmaps provide a visual summary of relationships between all numeric variables in a dataset. They are essential for:

- **Feature Selection**: Identifying which features to include in models
- **Multicollinearity Detection**: Finding highly correlated predictors
- **Data Understanding**: Quick overview of variable relationships

```python
# Enhanced correlation heatmap
plt.figure(figsize=(10, 8))
corr = df.corr()
mask = np.triu(np.ones_like(corr, dtype=bool))  # Upper triangle mask
sns.heatmap(corr, mask=mask, annot=True, cmap='coolwarm',
            center=0, square=True, linewidths=0.5)
plt.title('Correlation Matrix Heatmap')
plt.show()
```

---

### Multi-variable Relationships (Pairplot)

Pair plots excel at revealing complex multivariate relationships:

- **Linear Relationships**: Points forming a line pattern
- **Non-linear Relationships**: Curved patterns
- **Clusters**: Groupings based on categorical variables
- **Outliers**: Points far from the main cluster

---

### Density Estimation

Density estimation techniques (KDE) allow us to:

- Estimate probability density functions
- Identify multiple modes in data
- Compare distributions across groups
- Smooth discrete data for analysis

---

## 🎨 Visual Encoding in Statistical Plots

### Color Gradients

| Encoding | Usage |
|----------|-------|
| **Sequential** | Low to high values (e.g., `Blues`, `Greens`) |
| **Diverging** | Positive and negative (e.g., `coolwarm`, `RdBu`) |
| **Categorical** | Distinct categories (e.g., `Set1`, `tab10`) |

### Density Representation

- **Alpha transparency**: Overlapping regions appear darker
- **Fill opacity**: Emphasizes areas under curves
- **Color intensity**: Represents density concentration

### Distribution Spread

- **Box width**: IQR representation
- **Whisker length**: Data range
- **Violin width**: Probability density

### Outliers

- **Individual points**: Beyond whiskers in box plots
- **Symbols**: Circles, diamonds, or custom markers
- **Color coding**: Different from main data points

---

## 📋 Functions and Commands Table

| Function / Command | Library | Description |
|-------------------|---------|-------------|
| `plt.figure(figsize=(w,h))` | Matplotlib | Create a new figure with specified dimensions |
| `plt.show()` | Matplotlib | Display the current figure |
| `plt.title("Title")` | Matplotlib | Set the plot title |
| `plt.xlabel("Label")` | Matplotlib | Set x-axis label |
| `plt.ylabel("Label")` | Matplotlib | Set y-axis label |
| `plt.legend()` | Matplotlib | Display legend for plotted elements |
| `plt.subplot(rows, cols, index)` | Matplotlib | Create multiple plots in one figure |
| `plt.hist(data, bins=n)` | Matplotlib | Create a histogram |
| `plt.scatter(x, y)` | Matplotlib | Create a scatter plot |
| `plt.fill_between(x, y)` | Matplotlib | Create an area plot |
| `plt.pie(values, labels)` | Matplotlib | Create a pie chart |
| `plt.boxplot(data)` | Matplotlib | Create a box plot |
| `sns.set_style("style")` | Seaborn | Set the aesthetic style (darkgrid, whitegrid, etc.) |
| `sns.histplot(data, kde=True)` | Seaborn | Plot histogram with optional KDE |
| `sns.kdeplot(data, x, hue)` | Seaborn | Plot kernel density estimate |
| `sns.boxplot(x, y, data)` | Seaborn | Create a box plot with categorical grouping |
| `sns.violinplot(x, y, data)` | Seaborn | Create a violin plot |
| `sns.pairplot(df, hue)` | Seaborn | Create pair plot for all numeric variables |
| `sns.heatmap(corr, annot=True)` | Seaborn | Create a heatmap from matrix data |
| `sns.scatterplot(x, y, data, hue, size)` | Seaborn | Enhanced scatter plot with semantic mapping |
| `sns.countplot(x, data)` | Seaborn | Show counts of observations |
| `sns.swarmplot(x, y, data)` | Seaborn | Categorical scatter with non-overlapping points |
| `sns.jointplot(x, y, data)` | Seaborn | Draw a bivariate plot with marginal distributions |
| `df.head()` | Pandas | Display first 5 rows |
| `df.describe()` | Pandas | Generate descriptive statistics |
| `df.corr()` | Pandas | Compute pairwise correlation |
| `df.groupby()` | Pandas | Group data for aggregation |
| `df.pivot_table()` | Pandas | Create a pivot table |
| `pd.cut()` | Pandas | Segment data into bins |
| `df.value_counts()` | Pandas | Count unique values |
| `np.random.seed()` | NumPy | Set random seed for reproducibility |
| `np.random.randint()` | NumPy | Generate random integers |

---

## 🔢 Algorithm / Logic

### Step-by-Step Procedure

```
STEP 1: Import Libraries
        - Import matplotlib.pyplot, seaborn, pandas, numpy
        - Set visualization styles if needed

STEP 2: Create/Load Dataset
        - Create synthetic data using numpy.random
        - Or load external dataset using pandas.read_csv()

STEP 3: Explore Dataset
        - Use df.head() to preview data
        - Use df.describe() for statistical summary
        - Check data types and missing values

STEP 4: Select Variables
        - Identify numeric columns for analysis
        - Identify categorical columns for grouping
        - Select appropriate columns for each plot type

STEP 5: Apply Statistical Plots
        - Distribution plots for univariate analysis
        - Box/Violin plots for outlier detection
        - Heatmaps for correlation analysis
        - Pair plots for multivariate relationships

STEP 6: Customize Visualizations
        - Add titles, labels, legends
        - Apply color palettes
        - Adjust figure sizes

STEP 7: Interpret Patterns
        - Analyze distribution shapes
        - Identify outliers and anomalies
        - Examine correlations between variables
        - Draw meaningful conclusions

STEP 8: Display Visualizations
        - Use plt.show() to render plots
        - Save figures if needed with plt.savefig()
```

---

## 📊 Charts / Output Section

### 📈 Dataset 1: Category Sales Data

#### 1. Area Plot
![Area Plot](./charts/01_area_plot.png)
*Area plot showing values across categories with gradient fill*

#### 2. Sales and Profit Area Plot
![Sales and Profit Area Plot](./charts/02_area_plot_sales_profit.png)
*Comparative area plot showing Sales and Profit across categories*

#### 3. Pie Chart
![Pie Chart](./charts/03_pie_chart.png)
*Pie chart showing proportional distribution of categories*

#### 4. Donut Chart
![Donut Chart](./charts/04_donut_chart.png)
*Donut chart - pie chart with center hollow for enhanced visualization*

#### 5. Box Plot (Outlier Detection)
![Box Plot](./charts/05_boxplot.png)
*Box plot showing distribution summary with outlier identification*

#### 6. Correlation Heatmap
![Heatmap](./charts/06_heatmap.png)
*Heatmap displaying correlation matrix between numeric variables*

#### 7. Bubble Plot (Matplotlib)
![Bubble Plot](./charts/07_bubble_plot.png)
*Scatter plot with bubble size representing a third variable*

#### 8. Bubble Plot (Seaborn)
![Seaborn Bubble Plot](./charts/08_bubble_plot_seaborn.png)
*Enhanced bubble plot using Seaborn with hue and size mapping*

---

### 📊 Dataset 2: Loan Application Data

#### 9. Loan Amount Boxplot
![Loan Boxplot](./charts/09_loan_boxplot.png)
*Box plot showing loan amount distribution with outlier detection*

#### 10. Credit Score Histogram
![Histogram](./charts/10_histogram.png)
*Histogram showing frequency distribution of credit scores with mean line*

#### 11. Income vs Loan Amount Bubble Plot
![Income vs Loan Bubble](./charts/11_income_loan_bubble.png)
*Bubble plot showing relationship between Income and Loan Amount with Credit Score as bubble color*

#### 12. Correlation Matrix Heatmap
![Correlation Heatmap](./charts/12_correlation_heatmap.png)
*Correlation matrix showing relationships between Age, Income, Loan Amount, and Credit Score*

---

### 📈 Advanced Visualizations (Self Learning)

#### 13. Pair Plot
![Pair Plot](./charts/13_pair_plot.png)
*Pair plot showing pairwise relationships between all numeric variables with Loan Status coloring*

#### 14. Violin Plot
![Violin Plot](./charts/14_violin_plot.png)
*Violin plots comparing Credit Score and Income distributions by Loan Status*

#### 15. Joint Plot
![Joint Plot](./charts/15_joint_plot.png)
*Joint distribution plot showing Income vs Loan Amount with marginal distributions and regression line*

#### 16. Subplots Dashboard
![Subplots Dashboard](./charts/16_subplots_dashboard.png)
*Multi-panel dashboard combining KDE plot, Histogram, Box plot, and Scatter plot*

#### 17. Count Plot
![Count Plot](./charts/17_count_plot.png)
*Count plots showing Loan Status distribution by Age Group and Credit Category*

#### 18. Stacked Bar Chart
![Stacked Bar Chart](./charts/18_stacked_bar.png)
*Stacked bar chart showing Loan Status distribution across Age Groups*

#### 19. KDE Plot
![KDE Plot](./charts/19_kde_plot.png)
*Kernel Density Estimation plots comparing distributions by Loan Status and Age Group*

#### 20. Swarm Plot
![Swarm Plot](./charts/20_swarm_plot.png)
*Swarm plot showing individual Credit Score points by Loan Status with Age Group coloring*

#### 21. GroupBy Analysis
![GroupBy Analysis](./charts/21_groupby_analysis.png)
*Bar chart comparing average statistics between Approved and Rejected loans*

#### 22. Summary Statistics Table
![Summary Table](./charts/22_summary_table.png)
*Comprehensive summary statistics table for the Loan Application dataset*

---

## 📁 Dataset Description

### Dataset 1: Category Sales Data

| Column | Type | Description |
|--------|------|-------------|
| `Category` | Categorical | Product categories (A, B, C, D, E) |
| `Values` | Numeric | Value for each category |
| `Sales` | Numeric | Sales figures |
| `Profit` | Numeric | Profit values |

### Dataset 2: Loan Application Data

| Column | Type | Description | Range |
|--------|------|-------------|-------|
| `Customer_ID` | Integer | Unique customer identifier | 1-100 |
| `Age` | Integer | Customer age | 20-60 |
| `Income` | Integer | Annual income | $20,000-$100,000 |
| `Loan_Amount` | Integer | Requested loan amount | $5,000-$50,000 |
| `Credit_Score` | Integer | Credit score | 300-900 |
| `Loan_Status` | Categorical | Loan approval status | Approved/Rejected |

**Key Relationships:**
- Credit Score > 600 → Loan Approved
- Credit Score ≤ 600 → Loan Rejected

---

## 🛠️ Tools Used

| Tool | Version | Purpose |
|------|---------|---------|
| **Python** | 3.9+ | Programming language |
| **Jupyter Notebook** | Latest | Interactive development environment |
| **Matplotlib** | 3.x | Basic plotting library |
| **Seaborn** | 0.12+ | Statistical visualization |
| **Pandas** | 2.x | Data manipulation and analysis |
| **NumPy** | 1.24+ | Numerical computations |

---

## 💼 Applications

### Data Science
- **Exploratory Data Analysis (EDA)**: Understanding data before modeling
- **Feature Engineering**: Creating new features based on insights
- **Data Cleaning**: Identifying and handling outliers
- **Pattern Recognition**: Discovering hidden patterns in data

### Machine Learning
- **Feature Selection**: Identifying important variables
- **Model Validation**: Checking assumptions before modeling
- **Hyperparameter Tuning**: Visualizing model performance
- **Result Interpretation**: Communicating model outputs

### Statistical Analysis
- **Hypothesis Testing**: Visualizing distributions for tests
- **Regression Analysis**: Understanding variable relationships
- **Quality Control**: Monitoring process variations
- **Survey Analysis**: Understanding respondent distributions

### Business Analytics
- **Customer Segmentation**: Identifying customer groups
- **Risk Assessment**: Evaluating credit risk scores
- **Performance Metrics**: Tracking KPIs and trends
- **Market Research**: Analyzing survey data

---

## 📝 Conclusion

This experiment successfully demonstrated various **statistical and specialized data visualization techniques** using Python libraries. Key learnings include:

1. **Distribution Analysis**: Understanding data spread using histograms, KDE plots, and violin plots
2. **Outlier Detection**: Identifying anomalies using box plots
3. **Correlation Analysis**: Visualizing relationships using heatmaps and pair plots
4. **Multivariate Analysis**: Exploring multiple variables simultaneously using pair plots
5. **Visual Encoding**: Effectively using colors, sizes, and positions to represent data

These visualization techniques form the foundation of exploratory data analysis and are essential for any data science workflow. They enable quick identification of patterns, anomalies, and relationships that might not be apparent from raw data alone.

The skills acquired in this experiment directly apply to real-world data analysis tasks including feature engineering, model selection, and result communication.

---

## 📌 Extra Notes

### Best Practices for Statistical Visualization

1. **Choose the Right Plot**: Match visualization to data type and analysis goal
2. **Use Appropriate Colors**: Ensure accessibility and clarity
3. **Label Clearly**: Always include titles, axis labels, and legends
4. **Consider Audience**: Adjust complexity based on viewer expertise
5. **Maintain Consistency**: Use consistent styling across related plots

### Common Pitfalls to Avoid

- ❌ Over-plotting (too many points obscuring patterns)
- ❌ Misleading scales (truncated axes)
- ❌ Poor color choices (not colorblind-friendly)
- ❌ Missing context (no labels or units)
- ❌ Cherry-picking data to support conclusions

### Resources for Further Learning

- [Seaborn Documentation](https://seaborn.pydata.org/)
- [Matplotlib Gallery](https://matplotlib.org/gallery.html)
- [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)
- [Kaggle Visualization Tutorials](https://www.kaggle.com/learn/data-visualization)

---

## 🚀 Extra / Self Learning

This section covers advanced visualization techniques beyond the core experiment, demonstrating independent learning and exploration.

### 🔹 Swarm Plot

**Definition:**
A swarm plot is a categorical scatter plot that adjusts points to avoid overlap, showing all individual observations.

```python
sns.swarmplot(x='category', y='values', data=df)
```

**When to Use:**
- Showing all data points without overlap
- Small to medium datasets
- Understanding distribution and individual values

**Output:**
![Swarm Plot](./charts/20_swarm_plot.png)

---

### 🔹 Strip Plot

**Definition:**
A strip plot is similar to a swarm plot but uses jitter to prevent overlap of points.

```python
sns.stripplot(x='category', y='values', data=df, jitter=True)
```

**When to Use:**
- Quick scatter plot visualization
- Overlay on violin or box plots
- Showing raw data distribution

---

### 🔹 Joint Plot

**Definition:**
A joint plot combines a bivariate scatter plot with univariate histograms/KDEs on the margins.

```python
sns.jointplot(x='var1', y='var2', data=df, kind='reg')
```

**When to Use:**
- Analyzing relationship between two variables
- Understanding marginal distributions
- Fitting regression lines

**Output:**
![Joint Plot](./charts/15_joint_plot.png)

---

### 🔹 Facet Grid

**Definition:**
Facet grids create multiple plots based on categorical subsets of data.

```python
g = sns.FacetGrid(df, col='category1', row='category2')
g.map(sns.histplot, 'values')
```

**When to Use:**
- Comparing distributions across multiple groups
- Creating dashboard-like visualizations
- Complex multivariate analysis

---

### 🔹 Count Plot

**Definition:**
A count plot shows the frequency of observations in each categorical bin.

```python
sns.countplot(x='category', hue='group', data=df)
```

**When to Use:**
- Frequency analysis of categorical variables
- Comparing group sizes
- Quick overview of data balance

**Output:**
![Count Plot](./charts/17_count_plot.png)

---

### 🔹 Stacked Bar Chart

**Definition:**
A stacked bar chart shows the composition of categories by stacking segments.

```python
df.groupby(['cat1', 'cat2']).size().unstack().plot(kind='bar', stacked=True)
```

**When to Use:**
- Showing part-to-whole relationships
- Comparing compositions across groups
- Visualizing survey responses

**Output:**
![Stacked Bar Chart](./charts/18_stacked_bar.png)

---

### 🔹 GroupBy Aggregations

**Definition:**
GroupBy operations split data into groups and apply aggregate functions.

```python
df.groupby('category').agg({
    'numeric1': ['mean', 'std'],
    'numeric2': ['min', 'max']
})
```

**When to Use:**
- Summary statistics by group
- Data transformation
- Feature engineering

**Output:**
![GroupBy Analysis](./charts/21_groupby_analysis.png)

---

### 🔹 Pivot Tables

**Definition:**
Pivot tables create multi-dimensional summaries of data.

```python
pd.pivot_table(df, values='value', index='row', columns='col', aggfunc='mean')
```

**When to Use:**
- Multi-dimensional analysis
- Cross-tabulation
- Creating summary reports

---

### 🔹 Feature Engineering

**Definition:**
Creating new variables from existing data to enhance analysis.

```python
# Debt-to-Income Ratio
df['DTI'] = df['Loan_Amount'] / df['Income'] * 100

# Age Grouping
df['Age_Group'] = pd.cut(df['Age'], bins=[0, 30, 50, 100], labels=['Young', 'Middle', 'Senior'])
```

**When to Use:**
- Creating meaningful derived variables
- Categorizing continuous variables
- Enabling group-based analysis

---

### 🔹 Ranking

**Definition:**
Ordering data by specific criteria to identify top/bottom performers.

```python
df['Rank'] = df['Score'].rank(method='dense', ascending=False)
top_10 = df.nsmallest(10, 'Rank')
```

**When to Use:**
- Identifying top performers
- Creating leaderboards
- Filtering by rank

---

### 🔹 Cross-Tabulation

**Definition:**
Computing frequency tables showing relationships between categorical variables.

```python
pd.crosstab(df['cat1'], df['cat2'], margins=True, normalize='index')
```

**When to Use:**
- Analyzing relationships between categories
- Creating contingency tables
- Statistical testing (Chi-square)

---

## 📎 Key Insights from Self Learning

| Technique | Key Benefit |
|-----------|-------------|
| **Swarm Plot** | Shows all data points without overlap |
| **Joint Plot** | Combines bivariate and marginal analysis |
| **Facet Grid** | Multi-panel visualizations by category |
| **Pivot Tables** | Multi-dimensional summaries |
| **Feature Engineering** | Creates meaningful derived variables |
| **Cross-Tabulation** | Categorical relationship analysis |
| **Ranking** | Identify top/bottom performers |

---

<div align="center">

**Made by Tanmay Agarwal**

**EnTC A3 | PRN: 25070123158**

---

*This README is part of Experiment 17 - Exploratory Data Analysis (EDA)*

</div>
