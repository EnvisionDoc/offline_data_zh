# 支持的解释器

## `%hive`

以下代码块提供的示例介绍了如何使用SQL查询原始数据表。

```sql
%hive
select * from bank limit 10;
```

单击 |run_note| 运行代码段落，你将得到类似于以下所示的结果。

.. image:: media/data_explorer_pic_3.png

## `%livy.spark`

以下代码块提供的示例介绍了如何读取文件`bank.csv`并计算行数。

```
%livy.spark
val bank = sc.textFile("/user/data_explore_product_db/spark/input/bank.csv")
bank.count
```

单击 |run_note| 运行代码段落，你将得到类似于以下所示的结果。

.. image:: media/data_explorer_pic_4.png

## `%livy.pyspark`

以下代码块提供的示例介绍了读取表文件`bank.csv`，以及计算除第一行之外的行数并显示前十行数据。

```python
%livy.pyspark
from pyspark import SparkContext
from pyspark.sql import SQLContext
spark = SparkSession \
    .builder \
    .appName("PySparkTest") \
    .getOrCreate()
sc = spark.sparkContext
sc.setLogLevel("INFO")

sqlContext = SQLContext(sc)
df=sqlContext.read.format('com.databricks.spark.csv').options(header='true', inferschema='true').load("/user/data_explore_product_db/pyspark/input/bank.csv")

print df.count()
df.show(10)
```

单击 |run_note| 运行代码段落，你将得到类似于以下所示的结果。

.. image:: media/data_explorer_pic_5.png

## `%md`

以下代码块提供了markdown的示例：

```markdown
%md
# hello world
- **hello world**
```
单击 |run_note| 运行代码段落，你将得到类似于以下所示的结果。

.. image:: media/data_explorer_pic_6.png

## `%mysql_report`

以下代码块提供的示例介绍了如何从EnOS数据报表的数据库中检索数据：

```sql
%mysql_report
select * from bank limit 10;
```

单击 |run_note| 运行代码段落，你将得到类似于以下所示的结果。

.. image:: media/data_explorer_pic_7.png

以下代码块提供的示例介绍了如何使用复杂的SQL语句查询检索数据：

```sql
%mysql_report
select ${group_by}, count(1)as count, avg(balance)as balance_avg
from bank
where marital="${marital=single,single|divorced|married}" and age < ${maxAge=50}
group by ${group_by=education,education|job|age|marital};
```

单击 |run_note| 运行代码段落，你将得到类似于以下所示的结果。

.. image:: media/data_explorer_pic_8.png

## `%python`

以下代码块提供的示例介绍了python的基本操作，即如何使用python标记两个坐标点。

```python
%python
import matplotlib.pyplot as plt
z.configure_mpl(width=400, height=300, fmt='svg')
plt.plot([1,2,3,4], [1,4,9,16], 'ro')
```

单击 |run_note| 运行代码段落，你将得到类似于以下所示的结果。

.. image:: media/data_explorer_pic_9.png

## `%sh`

以下代码块提供的示例介绍了shell的基本操作。

```
%sh
whoami
hadoop fs -ls /user
```

单击 |run_note| 运行代码段落，你将得到类似于以下所示的结果。

.. image:: media/data_explorer_pic_10.png

.. |run_note| image:: media/run_note.png


<!--end-->
