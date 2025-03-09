# Pandas and Advanced Data Analysis: A Comprehensive Tutorial

This tutorial provides an in‐depth guide to using Pandas for data manipulation and analysis, along with a dedicated section on advanced topics. You will learn about DataFrames, reading data from various sources, filtering, aggregation, merging, and advanced techniques for data cleaning, time series analysis, pivot tables, and more.

---

## 1. Introduction to Pandas

Pandas is a versatile library that simplifies data processing. It builds upon the fast array computations of NumPy while offering rich data structures such as Series and DataFrames.

- **DataFrames:** Two-dimensional, size‐mutable, and heterogeneous tabular data.
- **Series:** One-dimensional labeled arrays capable of holding any data type.

---

## 2. Getting Started with Pandas

### 2.1 Reading Data from Files

Load data from a CSV file:
```python
import pandas as pd
df = pd.read_csv('data/sample.csv')
print(df.head())
```

Read from an Excel file:
```python
df_xlsx = pd.read_excel('data/sample.xlsx')
print(df_xlsx.head())
```

Read a delimited text file (e.g., tab-separated):
```python
df_txt = pd.read_csv('data/sample.txt', delimiter='\t')
print(df_txt.head())
```

---

## 3. Creating DataFrames from Other Sources

### 3.1 From a Dictionary
```python
data = {
    'Name': ['Alice', 'Bob'],
    'Age': [25, 30],
    'Score': [85, 92]
}
df_dic = pd.DataFrame(data)
print(df_dic)
```

### 3.2 From a NumPy Array
Create numerical data using NumPy and reshape it into a DataFrame:
```python
import numpy as np
np_data = np.arange(12).reshape(3, 4)
df_np = pd.DataFrame(np_data, columns=['A', 'B', 'C', 'D'])
print(df_np)
```

---

## 4. Exploring and Inspecting DataFrames

### 4.1 Viewing Data and Columns
```python
print(df.columns)  # List all column names
print(df.head())   # View first few rows
```

### 4.2 Selecting Rows and Columns
Select specific columns and rows:
```python
df_subset = df[['Name', 'Score']]
print(df_subset.iloc[0:2])
```

---

## 5. Filtering Data

### 5.1 Boolean Filtering
Filter rows based on conditions:
```python
high_scores = df.loc[df['Score'] > 90]
print(high_scores)
```

### 5.2 Filtering with String Methods and Regex
Filter rows using string operations:
```python
name_filter = df[df['Name'].str.contains('A')]
print(name_filter)
```

---

## 6. Descriptive Statistics and Sorting

### 6.1 Summary Statistics
Generate summary statistics for numerical columns:
```python
print(df.describe())
```

### 6.2 Sorting DataFrames
Sort data by one or more columns:
```python
sorted_df = df.sort_values(by='Score', ascending=False)
print(sorted_df)
```

---

## 7. Data Manipulation: Calculations & Conditional Updates

### 7.1 Adding New Columns
Compute a new column (e.g., a cumulative score):
```python
df['DoubleScore'] = df['Score'] * 2
print(df.head())
```

### 7.2 Conditional Updates
Update values based on conditions:
```python
df.loc[df['Age'] < 28, 'Category'] = 'Young'
df.loc[df['Age'] >= 28, 'Category'] = 'Mature'
print(df)
```

---

## 8. Aggregate Statistics: GroupBy and Aggregation

Group data and compute aggregates:
```python
grouped = df.groupby('Category').mean()
print(grouped)
```

Also, convert aggregation results into a dictionary:
```python
agg_dict = df.groupby('Category')['Score'].agg(list).to_dict()
print(agg_dict)
```

---

## 9. Handling Large Data: Chunking

For very large files, you can read and process data in chunks:
```python
chunk_df = pd.DataFrame()
for chunk in pd.read_csv('data/large_file.csv', chunksize=50):
    filtered_chunk = chunk[chunk['Score'] > 80]
    chunk_df = pd.concat([chunk_df, filtered_chunk], ignore_index=True)
print(chunk_df.info())
```

---

## 10. Merging and Joining DataFrames

Combine DataFrames using merge functionality:
```python
left_df = df.iloc[:, :2]
right_df = df.iloc[:, 1:4]
merged_df = pd.merge(left_df, right_df, on='Name', how='inner')
print(merged_df)
```

---

## 11. Customizing Display Options

Adjust Pandas display settings for better output formatting:
```python
pd.set_option('display.max_rows', 20)
pd.set_option('display.precision', 2)
pd.set_option('display.max_columns', 10)
print(df)
```

---

## 12. Handling Missing Data

Handle missing values using methods like isna, fillna, and dropna.
```python
# Example:
df_missing = pd.DataFrame({'A': [1, None, 3], 'B': [4, 5, None]})
print(df_missing.isna())
df_filled = df_missing.fillna(method='ffill')
print(df_filled)
```

## 13. Advanced Data Cleaning

Remove duplicates and clean string data.
```python
# Example:
df_clean = df.drop_duplicates()
// If a 'Name' column exists, strip and convert to lowercase
if 'Name' in df.columns:
    df['Name'] = df['Name'].str.strip().str.lower()
print(df_clean)
```

## 14. Time Series Analysis

Work with datetime objects, set time-based indices, and resample.
```python
# Example:
dates = pd.date_range(start='2020-01-01', periods=100, freq='D')
df_time = pd.DataFrame({'Date': dates, 'Value': range(100)})
df_time.set_index('Date', inplace=True)
monthly_mean = df_time.resample('M').mean()
print(monthly_mean)
```

## 15. Pivot Tables and MultiIndex

Create pivot tables to summarize data and work with hierarchical indexing.
```python
# Example:
df_pivot = pd.DataFrame({
    'Category': ['foo', 'foo', 'bar', 'bar'],
    'Type': ['one', 'two', 'one', 'two'],
    'Value': [1, 3, 2, 4]
})
pivot = df_pivot.pivot_table(values='Value', index='Category', columns='Type')
print(pivot)
```

## 16. Data Visualization using Pandas

Quickly visualize data with pandas’ built-in plotting capabilities.
```python
# Example:
import matplotlib.pyplot as plt
# Assuming 'Score' column exists in df
df['Score'].plot(kind='hist', bins=10, title='Score Distribution')
plt.xlabel('Score')
plt.ylabel('Frequency')
plt.show()
```

## 17. Applying Functions with apply and lambda

Apply custom functions to DataFrame columns using apply along with lambda functions.
```python
# Example:
df['Score_Adjusted'] = df['Score'].apply(lambda x: x * 1.1)
print(df.head())
```

---

## Conclusion

In this tutorial we have covered:
- The essentials of Pandas for reading, exploring, manipulating, and aggregating data.
- How to work with large datasets via chunking and merging DataFrames.
- Customizing output display for effective data analysis.
- Advanced Pandas techniques: handling missing data, advanced data cleaning, time series analysis, pivot tables, data visualization, and applying functions with apply and lambda.

Mastering these techniques will significantly enhance your data analysis workflow and allow you to tackle more complex problems with Pandas.
