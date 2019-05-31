# 场景

数据集成包括以下两种典型的场景。

## 同步所有数据<syncalldata>

同步所有数据通常使用在初次集成数据时，你可以一次性同步数据源中的完整数据至EnOS。更多信息，参考[创建从外部数据库同步数据到Hive库的手动调度的任务](creating_scratch_onetime)。

## 同步增量数据<syncadditiondata>

同步增量数据场景通常运用于初次集成之后，此时你只需定期同步新数据或更新数据。你可以通过`where`语句指定要同步的增量数据。更多信息，参考[创建从外部数据库同步数据到Hive库的周期调度的任务](creating_scratch_periodic)。

## 同步文件

将文件从外部源数据库同步至EnOS文件存储HDFS。更多信息，参考[从外部数据库同步文件到文件存储HDFS](creating_scratch_blob2hdfs)。

