# Pandas

## `read_csv`

对‘LogiReg_data.txt‘中的数据进行逻辑回归分析。完成下列工作：
读取数据并转换为DataFrame格式，将第一列的列标签设置为‘参数1’，第二列的列标签设置为‘参数2’，第三列的列标签设置为‘y’，其中‘y’值为分类标签。

```python
path = 'data/LogiReg_data.txt'
df = pd.read_csv(path, header=None, names=['参数1', '参数2', 'y'])
print(df)
```

## pandas中提取DataFrame某些列的一些方法

df格式为：

|      | Name    | course1 | course2 | course3 | fruit  | sport      |
| :--- | :------ | :------ | :------ | :------ | :----- | :--------- |
| 1    | Anna    | 85      | 90      | 82      | apple  | basketball |
| 2    | Betty   | 83      | 85      | 86      | banana | volleyball |
| 3    | Richard | 90      | 83      | 81      | apple  | football   |
| 4    | Philip  | 84      | 88      | 91      | orange | basketball |
| 5    | Paul    | 85      | 84      | 85      | peach  | baseball   |

### 1. `df[columns]`

选择一列：`df['course2']`

选择多列`df[['course','fruit]]`

可以用 `column_list=df.columns[start:end] `的方式选择连续列，start 和 end 均为数字，不包括 end 列。例如：

```python
select_cols=df.columns[1:4]
df[select_cols]
```

### 2. `df.loc[]`：用 label （行名或列名）做索引。

择多列 [:, column_list]，括号中第一个: 表示选择全部行。例如：

```python
df.loc[:,['course2','fruit']]
```

选择连续多列 [:,start_col: end_col]，注意：包括 end_col。例如：

```python
df.loc[:,'course2':'fruit']
```

选择多行和多列，例如：

```python
df.loc[1:3,'course2':'fruit']
```

与 df[ ]类似，df.loc[ ]括号内也可以输入判断语句，结果是对行做筛选。例如：

```python
df.loc[df['course1']>84]
#注：输入df[df['course1']>84]，输出结果相同
```

## Dataframe中插入一列

### `insert`方法

`insert`方法：

```python
insert(loc, column, value, allow_duplicates=False)
```

* loc： 插入列的索引。第一列是 0。
* column： 赋予新列的名称。
* value： 新列的值数组。
* allow_duplicates： 是否允许新列名匹配现有列名。默认值为假。

第一个参数指定插入列的位置，第二个参数指定插入列的列名，第三个参数指定插入列的数据

```python
data.insert(0,'add',1)
```

或者插入指定数据：

```python
player_vals = ['A', 'B', 'C', 'D', 'E']
df.insert(0, 'player', player_vals)
```

