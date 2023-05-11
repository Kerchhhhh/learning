# sql_learning
Record my learning process of SQL


## SQL

### 基础语句

```sql
SELECT column_name(s)
FROM table_name

WHERE column_name IN (SELECT column_name FROM another_table);
WHERE column_name IN (value1, value2, ...)
  AND another_column_name = some_value;

JOIN table2
ON table1.column_name = table2.column_name;

GROUP BY
HAVING 用于从这些计算结果中选择满足特定条件的行

ORDER BY
```



### 条件筛选

```sql
/***
	多种条件筛选 
	· 使用比较运算符（例如 <, >, =, !=, <=, >=）来比较列的值。
	· 使用逻辑运算符（例如 AND, OR, NOT）将多个条件组合在一起。
	· 使用通配符（例如 % 和 _）匹配模式，以查找特定模式或模式的一部分
***/
WHERE column1 = value1
  AND (column2 < value2 OR column3 LIKE '%pattern%')
  AND column4 IN (value3, value4, ...)
  AND column5 NOT IN (SELECT column6 FROM another_table WHERE column7 = value5);
```

```sql
/* 指定计算范围 */
OVER:指定窗口函数（如 ROW_NUMBER, SUM, AVG 等）的计算范围

<window function> OVER (
    PARTITION BY partition_expression, ...
    ORDER BY sort_expression [ASC|DESC], ...
)
```



### 细节处理

#### 时间处理

```sql
extract(year from b2.monthtime)||'年'||extract(month from b2.monthtime)||'月' optime：日期，optime最后一次，放置重复
TRUNC(date, [fmt])：截断日期，YY,DD,MM
```

#### 数据处理

##### 小数数据

```sql
ROUND(number, num_digits)：小数数据存储
TO_CHAR(value, [fmt])：转换的数，转换的格式
```

##### 处理空值

```sql
NVL(expression, default_value)：控制替换
```

##### 提取数据

```sql
SUBSTR(string, start_position, [length])：
```

##### 排序处理

```sql
`ROW_NUMBER` 函数用于为查询结果集中的每行数据分配一个唯一的序号，并返回一个新的结果集。

SELECT staff_name, monthtime, SUM(amount) OVER (PARTITION BY staff_name ORDER BY monthtime) as sales_total 
FROM sales;
```


![企业微信截图_16837735081095](https://github.com/Kerchhhhh/sql_learning/assets/64466119/f0ee7bcf-d354-4917-9568-fd81ee74e068)
