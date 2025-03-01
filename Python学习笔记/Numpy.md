---
banner: "[[beamer图片1.png]]"
---
# Important Concepts

## Built-int type and np's own type

## NumPy Array Copy vs View 

| Original-Array      | View-Array                                                                                                       | Copy-Array                                                                                    |
| ------------------- | ---------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| a = np.array( [ ] ) | just a compass towards the original array.could be read as an map(一一映射),affect and be affected by original array | a brand-new array,after copy the data from original array and have nothing to do with it then |
|                     | view_array = a.view()                                                                                            | copy_array = a.copy()                                                                         |
|                     |                                                                                                                  |                                                                                               |





# The Dimension of Array

```python
import numpy as np
arr = np.array()
```

## Basic Definition

### Nested Arrays

### 0-D Arrays

### 1-D Arrays

### 2-D Arrays

### 3-D Arrays

### Higher Dimensional Arrays
示例:
```python
import numpy as np

arr = np.array([1, 2, 3, 4], ndmin=5)

print(arr)
print('number of dimensions :', arr.ndim)
```

> [!bug]

## NumPy Array Indexing


## NumPy Array Slicing





**nested array**


## Related Functions

### a.shape

the shape of an  array is the number of elements in each dimension.
### a.reshape
###  a.ndim

np.ndim = len(np.shape)





**shape**
**ndimn**
**index**
**step**















