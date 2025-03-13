# Lesson 9: Data Cleaning and Visualization

## Introduction
Data is the backbone of any analysis. This lesson is divided into two main parts. First, we cover basic data cleaning using Pandas to ensure our dataset is reliable. Next, we dive into data visualization by focusing on various plots using matplotlib and then exploring similar techniques with other visualization libraries such as Seaborn.

---

## 1. Data Cleaning

Data cleaning is the process of correcting or removing incorrect, corrupted, improperly formatted, or duplicated data. In this section, we use Pandas to perform common cleaning tasks.

### Example: Cleaning a Dataset with Pandas
```python
import pandas as pd

# Load the dataset from a CSV file.
df = pd.read_csv("data.csv")  # Reads the file data.csv into a DataFrame

# Remove duplicate records.
df.drop_duplicates(inplace=True)  
# 'inplace=True' modifies the DataFrame in place rather than returning a new DataFrame.

# Fill missing numerical values with the median of the column.
df.fillna(df.median(), inplace=True)  
# 'fillna' replaces NaN values and 'df.median()' calculates the median for numerical columns.

print("Data cleaning complete.")
```

---

## 2. Data Visualization

Data visualization transforms numerical and categorical data into graphical representations. This section is organized into two subsections:  
A. Using matplotlib  
B. Using other data visualization libraries (e.g., Seaborn)  

---

### A. Visualization with matplotlib

Matplotlib offers a wide range of plotting options. Below, we break down various categories.

#### 2.A.1. Pairwise Data Plots

Pairwise plots compare two variables at a time.

##### Scatter Plot
```python
import matplotlib.pyplot as plt

# Example: Scatter Plot for two numerical columns (age vs income)
plt.figure(figsize=(8, 6))  # 'figsize' sets the width and height of the figure
plt.scatter(df["age"], df["income"], color="blue", alpha=0.5)
# 'plt.scatter' creates a scatter plot;
# 'color' sets the marker color;
# 'alpha' sets the marker transparency.
plt.title("Scatter Plot: Age vs. Income")
plt.xlabel("Age")  # Label for x-axis
plt.ylabel("Income")  # Label for y-axis
plt.show()  # Displays the plot
```

##### Bar Chart
```python
# Example: Bar Chart comparing categorical data (e.g., count of records per group)
groups = df['group'].value_counts()  # Assume 'group' is a categorical column in 'df'
plt.figure(figsize=(8, 6))
plt.bar(groups.index, groups.values, color="coral")
# 'plt.bar' creates a bar chart with category names on x-axis and counts on y-axis.
plt.title("Bar Chart: Group Counts")
plt.xlabel("Group")
plt.ylabel("Count")
plt.show()
```

##### Other Pairwise Plots (Line Plot)
```python
# Example: Line Plot showing trend over time (assuming a 'date' and 'value' column exists)
plt.figure(figsize=(10, 5))
plt.plot(df["date"], df["value"], color="green", linestyle="--", marker="o")
# 'plt.plot' creates a line plot;
# 'linestyle' defines the type of line (e.g., dashed '--');
# 'marker' indicates data points.
plt.title("Line Plot: Value Over Time")
plt.xlabel("Date")
plt.ylabel("Value")
plt.show()
```

#### 2.A.2. Statistical Distribution Plots

These plots help understand data distribution.

##### Histogram
```python
# Example: Histogram using matplotlib to display distribution of 'income'
plt.figure(figsize=(8, 6))
plt.hist(df["income"], bins=20, color="purple", edgecolor="black")
# 'bins' defines the number of intervals;
# 'edgecolor' outlines each bin.
plt.title("Histogram: Income Distribution")
plt.xlabel("Income")
plt.ylabel("Frequency")
plt.show()
```

##### Pie Chart
```python
# Example: Pie Chart displaying proportion of categories (from a categorical column 'category')
counts = df['category'].value_counts()  # Frequency of each category
plt.figure(figsize=(8, 8))
plt.pie(counts, labels=counts.index, autopct='%1.1f%%', startangle=90)
# 'autopct' shows percentages; 'startangle' rotates the start of the pie chart.
plt.title("Pie Chart: Category Distribution")
plt.show()
```

##### Other Statistical Distributions (Box Plot)
```python
# Example: Box Plot for visualizing distribution, median, and outliers of 'income'
plt.figure(figsize=(8, 6))
plt.boxplot(df["income"], patch_artist=True)
# 'plt.boxplot' creates a box plot; 'patch_artist=True' fills the box with color.
plt.title("Box Plot: Income")
plt.ylabel("Income")
plt.show()
```

#### 2.A.3. Gridded Data

Gridded data plots are useful for representing two-dimensional arrays.

##### pcolormesh
```python
import numpy as np

# Example: pcolormesh to visualize gridded data
data = np.random.rand(10, 10)  # Create a 10x10 grid of random values
plt.figure(figsize=(8, 6))
plt.pcolormesh(data, cmap="viridis")
# 'cmap' selects the color map style
plt.title("Pcolormesh: Gridded Data Visualization")
plt.colorbar()  # Displays a color scale reference
plt.show()
```

##### matshow
```python
plt.figure(figsize=(20, 6))
plt.matshow(df.corr(), cmap='coolwarm')
plt.colorbar()
plt.xticks(range(len(corelations.columns)), corelations.columns, rotation=45)
plt.yticks(range(len(corelations.columns)), corelations.columns)
```


#### 2.A.4. 3D and Volumetric Data

3D plotting extends visualization to spatial data.

##### 3D Bar Plot (bar3d)
```python
from mpl_toolkits.mplot3d import Axes3D

# Example: 3D Bar Plot
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection='3d')
# Sample data for 3D bars
_x = np.arange(4)
_y = np.arange(4)
_xx, _yy = np.meshgrid(_x, _y)
x, y = _xx.ravel(), _yy.ravel()
z = np.zeros_like(x)
dx = dy = 0.5 * np.ones_like(z)
dz = np.random.rand(len(z))
ax.bar3d(x, y, z, dx, dy, dz, color="teal", shade=True)
ax.set_title("3D Bar Plot: Volumetric Data")
ax.set_xlabel("X-axis")
ax.set_ylabel("Y-axis")
ax.set_zlabel("Value")
plt.show()
```

##### Fill Between (2D area filling)
```python
# Example: Fill Between for 2D area plotting
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.sin(x) + 0.5
plt.figure(figsize=(10, 6))
plt.plot(x, y1, label='sin(x)', color="blue")
plt.plot(x, y2, label='sin(x)+0.5', color="red")
plt.fill_between(x, y1, y2, color='gray', alpha=0.3)
# 'fill_between' shades the area between y1 and y2 with transparency 'alpha'
plt.title("Fill Between: Area Between Two Curves")
plt.xlabel("x")
plt.ylabel("y")
plt.legend()
plt.show()
```

---

### B. Visualization with Other Libraries: Seaborn

Seaborn is built on top of matplotlib to provide polished, high-level plotting functions.

#### 2.B.1. Pairwise Data Plots with Seaborn

##### Scatter Plot
```python
import seaborn as sns

plt.figure(figsize=(8, 6))
sns.scatterplot(x="age", y="income", hue="group", data=df)
# 'hue' adds color separation by a categorical variable 'group'
plt.title("Seaborn Scatter Plot: Age vs. Income")
plt.xlabel("Age")
plt.ylabel("Income")
plt.show()
```

##### Bar Chart
```python
plt.figure(figsize=(8, 6))
sns.countplot(x="group", data=df, palette="pastel")
# 'countplot' automatically counts occurrences of each category in 'group'
plt.title("Seaborn Bar Chart: Group Counts")
plt.xlabel("Group")
plt.ylabel("Count")
plt.show()
```

#### 2.B.2. Statistical Distribution Plots with Seaborn

##### Histogram
```python
plt.figure(figsize=(8, 6))
sns.histplot(df["income"], bins=20, kde=True, color="orchid")
# 'kde=True' overlays the Kernel Density Estimation for a smooth curve.
plt.title("Seaborn Histogram: Income Distribution")
plt.xlabel("Income")
plt.ylabel("Frequency")
plt.show()
```

##### Box Plot
```python
plt.figure(figsize=(8, 6))
sns.boxplot(x="group", y="income", data=df, palette="Set3")
plt.title("Seaborn Box Plot: Income by Group")
plt.xlabel("Group")
plt.ylabel("Income")
plt.show()
```

#### 2.B.3. Gridded and 3D Plots with Seaborn

Seaborn primarily focuses on statistical plots and does not directly support gridded or 3D plots. For gridded data, continue using matplotlib as shown; for simple 3D, matplotlib’s mplot3d remains the tool of choice.

---

## Summary

- **Data Cleaning:** We used Pandas to remove duplicates and fill missing values.
- **Data Visualization with matplotlib:**  
  - **Pairwise Data Plots:** Scatter, Bar, and Line plots.
  - **Statistical Distribution Plots:** Histograms, Pie charts, and Box plots.
  - **Gridded Data:** pcolormesh and Contour plots.
  - **3D and Volumetric Data:** 3D Bar plots and area fills.
- **Other Visualization Libraries:**  
  - **Seaborn:** Offers easy-to-use functions for pairwise and statistical plots; for advanced grid or 3D plots, matplotlib is recommended.