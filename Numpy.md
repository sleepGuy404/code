# Numpy

## matrix和ndarray的区别

 NumPy 中 ndarray 和 matrix 的使用差异和转换方法。示例代码假设已导入 `numpy`：

```python
import numpy as np
```

### 1. 维数限制

matrix 和 ndarray 所能表示的数据维数不同，matrix 只能表示二维数据，而 ndarray 可以表示 N 维数据。

#### 1.1. matrix

matrix 只能是**二维**，可以使用如下的方法生成两个 2 * 2 的 matrix：

```python
a = np.mat([[1, 2],[3, 4]])
# a = [[1 2]
#      [3 4]]
b = np.mat('5 6; 7 8');
# b = [[5 6]
#      [7 8]]
```

如果尝试生成多于二维的矩阵，会产生报错：

```python
c = np.mat([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])  
# ValueError: matrix must be 2-dimensional
```

#### 1.2. ndarray

ndarray 可以是 **N 维**，如使用如下的方法生成两个 2 * 2 的 ndarray:

```python
x = np.array([[1, 2], [3, 4]])
# x = [[1 2]
#      [3 4]]
y = np.array([[5, 6], [7, 8]])
# y = [[5 6]
#      [7 8]]
```

可以生成任意维数的 ndarray：

```python
z = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
# z = [[[1 2]
#       [3 4]]
#
#      [[5 6]
#       [7 8]]]
```

### 2. 矩阵乘法

matrix 和 ndarray 在进行矩阵乘法时的操作不同。

#### 2.1. matrix

对于 matrix，使用运算符 `*` 或 NumPy 的 [`dot()`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.dot.html) 方法计算矩阵乘法，使用NumPy 的 [`multiply()`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.multiply.html) 方法计算逐元素相乘例如对于上面定义的 matrix `a` 和 `b`，有：

```python
a * b
# matrix([[19, 22],
#         [43, 50]])
np.dot(a, b)
# matrix([[19, 22],
#         [43, 50]]
np.multiply(a, b)
# matrix([[ 5, 12],
#         [21, 32]])
```

#### 2.2. ndarray

对于 ndarray，使用 NumPy 或者 ndarray 的 [`dot()`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.dot.html) 方法计算矩阵乘法，使用 运算符 `*` 或 Numpy 的 `multiply()` 方法计算逐元素相乘。例如对于上面定义的 ndarray `x` 和 `y`，有：

```python
x * y
# array([[ 5, 12],
#        [21, 32]])
x.dot(y)
# array([[19, 22]
#        [43, 50]])
np.dot(x, y)
# array([[19, 22],
#        [43, 50]])
```

此外，从 Python 3.5 和 Numpy 1.10 以后，可以使用中缀操作符 `@` 计算 ndarray 间的矩阵乘法，写起来更加方便：

```python
x @ y
# array([[19, 22],
#        [43, 50]])
```

### 3. 转换

#### 3.1. matrix 到 ndarray

可以使用 matrix 的 [`A`](https://docs.scipy.org/doc/numpy-dev/reference/generated/numpy.matrix.A.html) 属性或者 NumPy 的 [`asarray()`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.asarray.html) 方法，将 matrix 转换为 ndarray。如：

```python
d = a.A
type(d) # numpy.ndarray
e = np.asarray(a)
type(e) # numpy.ndarray
```

注意上面两个转换方法不会复制数据，如果修改了原始 matrix（即 `a`），则该修改也会反映到转换后的 ndarray（即 `d`、`e`）中，如：

```python
a = np.mat([[1, 2], [3, 4]])
d = a.A
e = np.asarray(a)
print('before change a[0][0]: \nd = \n{}\ne = \n{}'.format(d, e))
a[0][0] = 10
print('\nafter change a[0][0]: \nd = \n{} \ne = \n{}'.format(d, e))
```

输出为：

```python
before change a[0][0]: 
d = 
[[1 2]
 [3 4]
e = 
[[1 2]
 [3 4]]
after change a[0][0]: 
d = 
[[10 10]
 [ 3  4]] 
e = 
[[10 10]
  [ 3  4]]
```

#### 3.2. ndarray 到 matrix

可以使用 Numpy 的 [`asmatrix()`](https://docs.scipy.org/doc/numpy-1.10.4/reference/generated/numpy.asmatrix.html) 将 ndarray 转换为 matrix。如：

```python
z = np.asmatrix(x)
type(z) # numpy.matrixlib.defmatrix.matrix
```

该转换也不会复制数据，如果修改了原始 ndarray（即 `x`），则该修改也会反映到转换后的 matrix（即 `z`）中。

### 4. 如何选择 ndarray 和 matrix

对于 ndarray 和 matrix 的选择，[scipy.org 给出的建议](https://docs.scipy.org/doc/numpy-dev/user/numpy-for-matlab-users.html#array-or-matrix-which-should-i-use)是使用 ndarray，因为：

> - They are the standard vector/matrix/tensor type of numpy. Many numpy functions return arrays, not matrices.
> - There is a clear distinction between element-wise operations and linear algebra operations.
> - You can have standard vectors or row/column vectors if you like.

# 均值，方差，标准差

```python
import numpy as np 
arr = [1,2,3,4,5,6]
 
# 求均值
arr_mean = np.mean(arr)
 
# 求方差
arr_var = np.var(arr)
 
# 求总体标准差
arr_std_1 = np.std(arr)
 
# 求样本标准差
arr_std_2 = np.std(arr, ddof=1)
 
print("平均值为：%f" % arr_mean)
print("方差为：%f" % arr_var)
print("总体标准差为: %f" % arr_std_1)
print("样本标准差为: %f" % arr_std_2)
```

