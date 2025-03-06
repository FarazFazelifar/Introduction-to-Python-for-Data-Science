# NumPy Tutorial

This tutorial provides an in-depth guide to NumPy, the powerful numerical library for Python. We will cover everything from what NumPy is to advanced techniques such as boolean masking and linear algebra operations.

---

## 1. What is NumPy?

NumPy is a Python library used for efficient numerical computations. It introduces the powerful n-dimensional array object and provides tools for working with these arrays.

**Key Points:**
- Efficient storage and manipulation of numerical data.
- Supports vectorized operations, which eliminates costly Python loops.
- Extensively used in data science, machine learning, and scientific computing.

---

## 2. Arrays vs. Python Lists

While Python lists can store sequence of items, they are not optimized for numerical operations. In contrast, NumPy arrays:
- Store elements of the same type.
- Are stored in contiguous memory blocks.
- Enable vectorized operations, making computations much faster.

*Example:*
```python
# Creating a Python list and a NumPy array
py_list = [1, 2, 3, 4]
import numpy as np
np_array = np.array([1, 2, 3, 4])
```

---

## 3. Creating NumPy Arrays

NumPy provides multiple functions to create arrays:
- **np.array:** Create an array from a list of items.
- **np.zeros, np.ones:** Create arrays filled with 0s or 1s.
- **np.full, np.full_like:** Create arrays filled with any other number.
- **np.random.rand, np.random.randint:** Create arrays filled with random numbers.
- **np.identity:** Create an identity matrix.

*Examples:*
```python
import numpy as np

# Basic array from list
a = np.array([1, 2, 3, 4])
print(a)

# Two-dimensional arrays
b = np.array([[9.0, 8.0, 7.0], [6.0, 5.0, 4.0]], dtype='float32')
print(b)

# Special arrays
zeros = np.zeros((2, 3))
ones = np.ones((4, 2), dtype='int32')
full = np.full((2, 2), 99)
identity = np.identity(5)
random_decimal = np.random.rand(4, 2)
random_int = np.random.randint(-4, 8, size=(3, 3))
```

---

## 4. Array Attributes

NumPy arrays have several useful attributes:
- **ndim:** Number of dimensions.
- **shape:** Dimensions of the array.
- **dtype:** Data type of the elements.
- **itemsize:** Size (in bytes) of each element.
- **nbytes:** Total size (in bytes).
- **size:** Total number of elements.

*Example:*
```python
print("Dimensions:", b.ndim)
print("Shape:", b.shape)
print("Data type:", b.dtype)
print("Item size:", a.itemsize)
print("Total bytes:", b.nbytes)
print("Number of elements:", b.size)
```

---

## 5. Arithmetic and Vectorized Operations

NumPy allows you to perform element-wise arithmetic operations very efficiently.

*Examples:*
```python
a = np.array([1, 2, 3, 4])
print(a + 2)      # Element-wise addition
print(a - 2)      # Element-wise subtraction
print(a * 2)      # Element-wise multiplication
print(a / 2)      # Element-wise division
print(a ** 2)     # Element-wise exponentiation

# Operations with arrays of the same shape
b = np.array([1, 0, 1, 0])
print(a + b)
```

Also, many mathematical functions like `np.sin` operate element-wise:
```python
print(np.sin(a))
```

---

## 6. Indexing and Slicing

You can access or change specific elements, rows, or columns using indexing and slicing.

*Examples:*
```python
# Creating a 2D array for demonstration
a = np.array([[1, 2, 3, 4, 5, 6, 7],
              [8, 9, 10, 11, 12, 13, 14]])
print(a)

# Access specific element [row, column]
print(a[1, 5])  # Outputs: 13

# Access a specific row and column
print(a[0, :])  # First row
print(a[:, 2])  # Third column

# Fancy slicing
print(a[0, 1:2])
```

Changing values:
```python
a[1, 5] = 20
a[:, 2] = [1, 2]
print(a)
```

*3D Example:*
```python
b = np.array([[[1, 2],
               [3, 4]],
              [[5, 6],
               [7, 8]]])
print(b)
# Access inside multidim array
print(b[1,0,1])
```

---

## 7. Reshaping and Stacking Arrays

Reshaping lets you change the dimensions of an array, while stacking joins arrays together.

*Reshaping Example:*
```python
before = np.array([[1, 2, 3, 4],
                   [5, 6, 7, 8]])
print(before)
after = before.reshape((1, -1))
print(after)
```

*Vertical and Horizontal Stacking:*
```python
# Vertically stacking vectors
v1 = np.array([1, 2, 3, 4])
v2 = np.array([5, 6, 7, 8])
vertical = np.vstack([v1, v2, v1, v2])
print(vertical)

# Horizontal stack
h1 = np.ones((2, 4))
h2 = np.zeros((2, 2))
horizontal = np.hstack((h1, h2))
print(horizontal)
```

---

## 8. Linear Algebra Operations

NumPy supports many linear algebra operations. Common operations include:

- **Matrix Multiplication:** Using `np.matmul` or the `@` operator.
- **Determinant:** Using `np.linalg.det`.
- **Eigenvalues and Eigenvectors:** Using `np.linalg.eig`.
- **Trace:** Sum of diagonal elements via `np.trace`.

*Example:*
```python
a = np.ones((2, 3))
b = np.full((3, 2), 2)
print(np.matmul(a, b))

c = np.identity(3)
print("Determinant:", np.linalg.det(c))
print("Eigen:", np.linalg.eig(c))
print("Trace:", np.trace(c))
```

---

## 9. Advanced Indexing and Boolean Masking

Boolean masks let you select elements that satisfy a condition.

*Example:*
```python
# Create an array for demonstration
filedata = np.array([[1, 13, 21, 11, 196, 75, 4, 3, 34, 6, 7, 8, 0, 1, 2, 3, 4, 5],
                     [3, 42, 12, 33, 766, 75, 4, 55, 6, 4, 3, 4, 5, 6, 7, 0, 11, 12],
                     [1, 22, 33, 11, 999, 11, 2, 1, 78, 0, 1, 2, 9, 8, 7, 1, 76, 88]])
# Boolean conditions
mask = filedata > 50
print(mask)

# Combining conditions
combined_mask = ~((filedata > 50) & (filedata < 100))
print(combined_mask)

# Use mask to get elements > 50
print(filedata[filedata > 50])
```

---

## 10. Loading Data from Files

NumPy can load data from files easily using functions like `np.genfromtxt`.

*Example:*
```python
# Assuming 'data.txt' is a CSV file with numeric data.
filedata = np.genfromtxt('data.txt', delimiter=',')
filedata = filedata.astype('int32')
print(filedata)
```

---

## 11. Handling Special Values and Complex Numbers

### Dealing with NaN Values:
```python
a = np.array([np.nan, 1, 2, np.nan, 3, 4, 5])
print(a)
# Create a mask for non-nan values
mask = ~np.isnan(a)
print(mask)
print(a[mask])  # Only prints non-nan values
```

### Working with Complex Numbers:
```python
a = np.array([1, 2+6j, 5, 3.5+5j])
print(a.dtype)              # Shows complex number data type if any element is complex
print(a[np.iscomplex(a)])   # Extracts only complex numbers
```

---

## Conclusion

This tutorial covered:
- What NumPy is and its importance.
- The high-performance n-dimensional array and its key differences compared to lists.
- How to create, inspect, and manipulate arrays.
- Vectorized operations, slicing, reshaping, stacking, and linear algebra.
- Handling advanced indexing, boolean masking, file I/O, missing data, and complex numbers.

By mastering these core concepts, you'll be well-prepared to use NumPy for efficient numerical and scientific computing in Python.

Happy coding with NumPy!
