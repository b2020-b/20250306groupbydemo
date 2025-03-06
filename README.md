# 20250306groupbydemo
pytho案例:使用Pandas 进行数据分组GroupBy 的实战 操作
## 引言
本篇文章将介绍如何使用 `pandas` 处理 Excel 数据，并进行分组统计。

## 1. 数据准备
首先，我们需要创建一个销售数据集，并保存到 Excel 文件中。

```python
import pandas as pd

# 创建示例数据
data = {
    '销售员': ['张三', '李四', '王五', '张三', '李四', '王五', '张三', '李四', '王五'],
    '地区': ['北京', '上海', '广州', '北京', '上海', '广州', '北京', '上海', '广州'],
    '销售额': [5000, 7000, 8000, 6000, 9000, 7500, 5500, 6500, 8200]
}

# 创建DataFrame
df = pd.DataFrame(data)

# 保存到Excel文件
df.to_excel('sales_data.xlsx', index=False)
```

这段代码创建了一个简单的销售数据集，并将其保存为 `sales_data.xlsx`。

## 2. 读取 Excel 数据
有了 Excel 文件后，我们可以使用 `pandas` 读取数据。

```python
# 读取Excel数据
df = pd.read_excel('sales_data.xlsx')
```

## 3. 数据分组统计
### 3.1 按销售员统计销售总额
我们可以使用 `groupby` 按销售员进行数据分组，并计算总销售额。

```python
grouped_sales = df.groupby('销售员')['销售额'].sum().reset_index()
print("按销售员统计销售总额:")
print(grouped_sales)
```

### 3.2 按销售员和地区统计销售额
有时，我们需要细化分组，例如按销售员和地区统计销售额。

```python
grouped_sales_region = df.groupby(['销售员', '地区'])['销售额'].sum().reset_index()
print("\n按销售员和地区统计销售额:")
print(grouped_sales_region)
```

### 3.3 计算销售员的平均销售额
我们还可以计算销售员的平均销售额。

```python
grouped_avg_sales = df.groupby('销售员')['销售额'].mean().reset_index()
print("\n按销售员统计平均销售额:")
print(grouped_avg_sales)
```

### 3.4 按地区计算销售总额
最后，我们按地区统计销售总额。

```python
grouped_region_sales = df.groupby('地区')['销售额'].sum().reset_index()
print("\n按地区统计销售总额:")
print(grouped_region_sales)
```

## 4. 运行结果示例
假设我们运行上述代码，可能得到如下结果：

**按销售员统计销售总额**

| 销售员 | 销售总额 |
|--------|---------|
| 张三  | 16500   |
| 李四  | 22500   |
| 王五  | 23700   |

**按销售员和地区统计销售额**

| 销售员 | 地区 | 销售额 |
|--------|------|-------|
| 张三  | 北京 | 16500  |
| 李四  | 上海 | 22500  |
| 王五  | 广州 | 23700  |

**按销售员统计平均销售额**

| 销售员 | 平均销售额 |
|--------|---------|
| 张三  | 5500   |
| 李四  | 7500   |
| 王五  | 7900   |

**按地区统计销售总额**

| 地区 | 销售总额 |
|------|---------|
| 北京 | 16500   |
| 上海 | 22500   |
| 广州 | 23700   |

