# Pandas Cheat Sheet 

A beginner-friendly reference guide for essential **Python Pandas** functions and methods used in data analysis.

## 📚 Table of Contents

1. [Series, DataFrame & Basic Operations](#1-series-dataframe--basic-operations)
2. [Indexing & Data Selection](#2-indexing--data-selection)
3. [Filtering & Conditional Selection](#3-filtering--conditional-selection)
4. [Data Update, Add & Delete](#4-data-update-add--delete)
5. [Strings & Column Splitting](#5-strings--column-splitting)
6. [Sorting & Top/Bottom Values](#6-sorting--topbottom-values)
7. [Statistics & Value Counting](#7-statistics--value-counting)
8. [Grouping & Aggregation](#8-grouping--aggregation)

---

## 1. Series, DataFrame & Basic Operations

| Function / Method | Description |
|---|---|
| `pd.Series()` | Create a Pandas Series |
| `pd.DataFrame()` | Create a DataFrame |
| `pd.concat()` | Combine Series or DataFrames |
| `df.head()` | Display the first five rows by default |
| `df.tail()` | Display the last five rows by default |
| `df.shape` | Get the number of rows and columns |
| `df.columns` | Get column names |
| `df.index` | View index labels |
| `df.dtypes` | Check data types of columns |
| `df.info()` | Display a summary of the DataFrame |
| `df.describe()` | Generate descriptive statistics for numerical columns |

## 2. Indexing & Data Selection

| Method / Syntax | Description |
|---|---|
| `df['column']` | Select a single column |
| `df[['col1', 'col2']]` | Select multiple columns |
| `df.loc[]` | Select data using labels |
| `df.iloc[]` | Select data using integer positions |
| `df.set_index()` | Set a column as the index |
| `df.reset_index()` | Reset the index and return it to a column by default |

## 3. Filtering & Conditional Selection

| Method / Syntax | Description |
|---|---|
| `df[condition]` | Filter rows based on a condition |
| `==` | Check whether values are equal |
| `!=` | Check whether values are not equal |
| `>` , `<` | Compare values using greater than or less than |
| `>=` , `<=` | Compare values using greater than or equal to, or less than or equal to |
| `&` | Combine conditions using AND |
| `\|` | Combine conditions using OR |
| `~` | Reverse a Boolean condition using NOT |
| `.isin()` | Check whether values belong to a list of possible values |

**Example:**

```python
df[df['Age'] >= 18]

df[(df['Age'] >= 18) & (df['City'] == 'Lahore')]

df[df['City'].isin(['Lahore', 'Karachi'])]
```

> **Note:** Use parentheses around individual conditions when combining them with `&` or `|`.

## 4. Data Update, Add & Delete

| Method / Syntax | Description |
|---|---|
| `df['new_col'] = ...` | Create a new column |
| `df['col'] = ...` | Add or update column values |
| `df.rename()` | Rename columns or index labels |
| `df.drop()` | Remove specified rows or columns |
| `df.drop(columns=...)` | Remove specific columns |
| `df.drop(index=...)` | Remove rows with specified index labels |

**Example:**

```python
# Add a new column
df['Bonus'] = 1000

# Rename a column
df.rename(columns={'Name': 'Full Name'}, inplace=True)

# Remove a column
df.drop(columns=['Bonus'], inplace=True)

# Remove a row by index label
df.drop(index=0, inplace=True)
```

## 5. Strings & Column Splitting

| Method | Description |
|---|---|
| `.str.split()` | Split text into multiple parts |
| `.str.split(expand=True)` | Split text into separate columns |
| `.str.lower()` | Convert text to lowercase |
| `.str.contains()` | Check whether text contains a specific word or pattern |

**Example:**

```python
# Convert text to lowercase
df['Name'] = df['Name'].str.lower()

# Check whether a name contains "ali"
df[df['Name'].str.contains('ali', na=False)]

# Split full names into separate columns
df[['First_Name', 'Last_Name']] = (
    df['Name'].str.split(' ', n=1, expand=True)
)
```

## 6. Sorting & Top/Bottom Values

| Method | Description |
|---|---|
| `df.sort_values()` | Sort rows according to column values |
| `df.sort_index()` | Sort rows according to index labels |
| `df.nlargest()` | Return rows with the largest values |
| `df.nsmallest()` | Return rows with the smallest values |

**Example:**

```python
# Sort by age in ascending order
df.sort_values(by='Age')

# Sort by age in descending order
df.sort_values(by='Age', ascending=False)

# Get the five highest values
df.nlargest(5, 'Salary')

# Get the five lowest values
df.nsmallest(5, 'Salary')
```

## 7. Statistics & Value Counting

| Method | Description |
|---|---|
| `mean()` | Calculate the arithmetic mean (average) |
| `median()` | Calculate the median |
| `max()` | Get the maximum value |
| `min()` | Get the minimum value |
| `count()` | Count non-missing values |
| `value_counts()` | Count the frequency of each unique value |
| `value_counts(normalize=True)` | Calculate the relative frequency of each value |
| `value_counts(normalize=True) * 100` | Calculate percentage distribution |

**Example:**

```python
# Calculate average salary
df['Salary'].mean()

# Find the median age
df['Age'].median()

# Count unique cities
df['City'].value_counts()

# Get relative frequencies
df['City'].value_counts(normalize=True)

# Get percentage distribution
df['City'].value_counts(normalize=True) * 100
```

## 8. Grouping & Aggregation

| Method | Description |
|---|---|
| `groupby()` | Group data by one or more categories |
| `get_group()` | Retrieve a specific group from a GroupBy object |
| `agg()` | Apply one or more aggregation functions |
| `apply()` | Apply a function or operation to groups or other Pandas objects |

**Example:**

```python
# Calculate average salary for each department
df.groupby('Department')['Salary'].mean()

# Calculate multiple statistics
df.groupby('Department')['Salary'].agg(
    ['mean', 'max', 'min', 'count']
)

# Retrieve a specific group
groups = df.groupby('Department')
groups.get_group('IT')
```

---

## 🚀 Quick Start

Install Pandas:

```bash
pip install pandas
```

Import Pandas:

```python
import pandas as pd

# Create a sample DataFrame
data = {
    'Name': ['Ali', 'Ahmed', 'Sara', 'Ayesha'],
    'Age': [20, 22, 19, 21],
    'City': ['Lahore', 'Karachi', 'Lahore', 'Islamabad'],
    'Salary': [50000, 60000, 45000, 70000]
}

df = pd.DataFrame(data)

print(df.head())
print(df.describe())
```

## 🎯 Learning Goals

- Understand Series and DataFrames.
- Select and filter data efficiently.
- Clean, update, and transform columns.
- Sort data and calculate statistics.
- Group data and perform aggregations.
- Build a foundation for data analysis and AI projects.

## 📌 About This Repository

This cheat sheet is designed for beginners learning Pandas for Python programming, data analytics, and machine learning.

**Topics covered:** DataFrames, indexing, filtering, data manipulation, string operations, sorting, statistics, grouping, and aggregation.

---

⭐ If you find this cheat sheet helpful, consider starring the repository!
