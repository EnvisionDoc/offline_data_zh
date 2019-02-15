# 通用库

EnO在其通用库中提供各种内置SDK，可帮助你更便捷地访问和处理数据。这些SDK降低了开发成本并提高了开发效率。

## 内置SDK列表<sdk>

.. list-table::
   :widths: auto

   * - SDK名称
     - 描述
   * - SYNC_HDFS_TO_S3
     - 将HDFS中指定路径的数据同步到S3数据库中的指定路径。
   * - COLUMNS_TO_ROWS
     - 将HIVE表的行数据（一行为设备一次收集的所有数据采集点的值）转换为表，表中的每行为单个数据采集点的历史值。
   * - SYNC_MDM
     - 将主数据同步到HDFS。
   * - SYNC_REPORT_DB
     - 将Hive表中的完整数据一次性同步到目标表中。
   * - FLATTEN_POINTS
     - 将EnOS原始点数据（一行为单个数据收集点的历史值）转换为类似sql的行数据（一行为设备的所有数据采集点的值）。
   * - POWER_DATA_INTERPOLATION
     - 插入功率数据，尤其是丢失的生产数据。
   * - SYNC_REPORT_STRUCTURE
     - 将Hive数据库的表结构传输到MySQL报告数据库。
   * - SHORT_TERM_LOAD_FORECAST
     - 对于网格中的不同电力消费者，基于历史数据和可选的天气数据，针对不同级别的时间粒度（15分钟，30分钟，1小时，1天）提供0-6天负荷预测。
   * - HADOOP_FILE_CRUSHER
     - 将多个小文件合并为几个较大的文件。


## 步骤<procedure>

使用内置SDK的主要步骤如下：

1. 在EnOS控制台中选则 **数据开发套件 > 任务开发** ，在通用库中找到你需要的SDK。

2. 双击脚本的版本号查看脚本的详细情况。

   .. image:: media/scenario_built-in.png

3. 点击右栏中的 **使用该方案**。

4. 在弹出窗口中，提供任务流的配置信息。

   .. image:: media/built-in_workflow.png

5. 提供调度配置信息。具体的配置流程，参考[从零开始创建一次性任务流](creating_workflow_onetime)或[从零开始创建周期性任务流](creating_workflow_periodic)。
