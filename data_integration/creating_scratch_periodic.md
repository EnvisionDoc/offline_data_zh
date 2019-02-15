# 创建从外部数据库同步数据到Hive库的周期调度的任务

本文描述了如何从零开始创建从外部数据库同步数据到Hive库的周期调度的任务。


## 开始前准备<beforestart>

你必须已创建用于存放同步数据的目标Hive表。更多信息，参考 **数据分析及报表** 中的[创建Hive表](https://www.envisioniot.com/docs/analysis-report/zh_CN/latest/data_explorer/creating_hivetable.html)。


## 步骤1：创建数据集成任务<createworkflow>

1. 在EnOS控制面板中选择 **数据集成**。

2. 点击目录树上方的 **+** 新建数据集成任务。

3. 在 **新建数据集成任务** 窗口中，提供有关任务的基本设置。

   - 模式：选择 **创建** 以从头开始创建集成任务。如果选择 **导入任务配置**，参考[基于已有任务创建新的集成任务](importing_existing_config)。
   - 名称：输入集成任务的名称。
   - 类型：选择 **周期调度**。
   - 说明：提供有关集成任务的描述性信息。
   - 选择目录：选择保存集成任务的目录。

4. 单击 **确定** 完成创建。

## 步骤2： 选择数据源<selectdatasource>

### SQL、MySQL或Oracle数据库<database>

如选择从SQL、MySQL或Oracle数据库同步数据时，需提供以下设置：

1. 从已有的数据源列表中选择数据源或创建新数据源。更多信息，参考[数据源概述](../data_source/datasource_overview)。

2. 从数据库中选择需要同步的表。

3. （可选）可提供SQL查询脚本筛选需同步的数据。

4. （可选）单击 **数据预览** 预览将同步的数据，如下图所示：

   .. image:: media/sql_source.png

5. 点击 **下一步**。


### FTP、SFTP或S3文本数据库<testdatabase>

1. 从已有的数据源列表中选择数据源或创建新数据源。更多信息，请参阅[数据源概述](../data_source/datasource_overview)。

2. 指定数据源的URL。当目录包含多个文件时，数据记录将被合并。在这种情况下，确保同一目录中的所有数据具有相同的列。

3. 选择文本数据文件中使用的列分隔符，例如，Tab符、逗号、分号、空格或其他分隔符。

4. 选择数据文件的编码格式：UTF-8、GBK或GB2312。

5. 选择数据文件的压缩格式。

6. 选择加载数据时忽略首部的行数。

7. 指定列头的名称。

8. （可选）点击 **数据预览** 预览将同步的数据。
9. 点击 **下一步**。


## 步骤3：选择目标源<selecttarget>

本版本只支持Hive类型的目标源，需提供以下设置。

1. 选择目标源的类型。

2. 如果Hive表已分区，则会自动加载分区。

3. 指定目标分区。可通过以下方法指定分区：

   - 列名：系统将根据该列的每个值创建新分区。例如：例名为日期，列值为`20180501`和`20180502`，则系统会创建两个分区，一天一个分区。
   - 固定值：例如，输入2017-10-11，数据将自动同步到目标表的`2017-10-11`分区。
   - 占位符：你可以使用系统提供或自定义的参数。例如，系统变量`$ {cal_dt}`。有关系统变量用法的更多信息，参考[系统变量列表](../data_ide/system_variables)。

   .. image:: media/sql_target.png

4. 设定数据写入的规则，覆盖目标表中已有数据或将数据添加到已有数据后。

5. 点击 **下一步**。


## 步骤4：配置数据源与目标的映射关系<maprelationship>

本步骤中，将源中的字段映射到目标字段中。

1. 对于 **目标字段** 列中的每个字段，点击左侧框内的 **来源字段**，添加至到右侧框 **来源（配置映射关系）**。

   .. image:: media/sql_mapping.png

2. 完成配置后，点击 **下一步**。


## 步骤5：配置调度<configschedule>

1. 点击配置面板右侧边缘的 **调度配置**。

2. 提供以下配置：

   - **负责人**：负责人可以是本组织中具有访问数据集权利的用户。默认为任务创建者。负责人具有以下事实：
     - 作为创建者，无法删除自己。
     - 可以在同一组织中添加其他负责人。
     - 同一负责人可不再创建具有相同名称的另一个任务。
   - **说明**：（可选）提供说明。
   - **预警方式**：选择告警的方式。邮件为强制选择项。
     - 电子邮件：当实例满足告警条件时，会向负责人发送告警电子邮件。
     - 短信：必须是在用户注册期间通过短信认证的电话号码。当实例满足告警条件时，短信告警仅发送给负责人。

3. 提供调度属性的设置：

   - **生效时间**：指定任务程何时开始生效。
   - **调度周期**：指定调度周期，即运行任务的频率。例如，可以设定每天运行任务流。可选择使用CronTab表达式。
   - **具体时间**：根据选择的周期，设置运行工作程的确切时间。例如，可以设置在每天上午9:00运行任务。如果选择使用CronTab语法，请按7个字符的CronTab表达式输入。例如，值`59 59 23 * * ? *`表示任务在每天23:59:59运行。有关CronTab的更多信息，参考[http://cron.qqe2.com/](http://cron.qqe2.com/)。
   - **超时时间**：指定认定任务超时的时长。
   - **重试次数**：指定超时后尝试重新连接的次数。
   - **重试间隔**：指定每次重新连接尝试之间的时长。
   - **可否被依赖**：设置该任务可否被其他任务引用。

## 步骤6：配置参数<configparameter>

为配置数据源和目标中使用的参数指定参数值。你可以为参数指定常量，系统变量或自定义变量。步骤如下：

1. 点击配置面板右侧边缘的 **参数配置**。

2. 在 **参数** 中，为每个使用到的参数指定参数值。

   例如，你可以为S3数据源设置如下URL：：`s3://history/log_solar_dt_change_inverter/${test_list}.each_value`。

   `test_list`为参数，你可以为该参数设置值：`test_list=Array[20170515,20170516,20170517,20170518,20170519,20170520]`。

   EnOS将同步设置中指定的目录中的所有数据。

   你可以将参数值设定为系统变量。更多信息，参考[系统变量列表](../data_ide/system_variables)。


## 步骤7：配置并发数<configconcurrency>

选择要建立的并发连接数，然后点击 **下一步**。

如设置高并发数，数据库会承受更大的负载，当总传输速率固定时，单个连接的速率会变小。

## 步骤8：预览并保存配置<preview>

预览设置，如有需要进行再编辑，然后点击 **保存** 完成配置。

## 后续操作<followup>

单击 **预跑** 测试任务。

示例将在运行任务后产生。接着，你可在数据运维中跟踪有关实例的详细信息。更多信息，参考[数据运维](../task_monitor/index)。

从数据源同步数据后，你可以根据数据设置其他处理任务。更多信息，参考[数据开发套件](../data_ide/dataide_overview)。