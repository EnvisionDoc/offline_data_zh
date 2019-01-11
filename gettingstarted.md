# 批处理快速入门
<!--
The short description should be a single, concise paragraph that contains one or two sentences and no more than 50 words.
Briefly mention what the user's learning goal is and include the following SEO keywords in the title short description: EnOS™, ServiceName, tutorial.
-->

使用EnOS分析历史数据的典型流程如下：

.. image:: media/getting_started.png
   :width: 700px

## 步骤1：准备数据源和目标数据库<preparedatasource>

1. 准备数据源

   - 如果数据源来自外部的，首先需要设置与源数据的连接。EnOS支持同步MYSQL，SQL，Oracle，FTP，SFTP和Amazon S3数据库的数据。有关如何连接到数据库的信息，参考[数据源管理](data_source/index)。
   - 如果处理和分析的数据位于EnOS云端，例如，设备主数据累加并存储到EnOS中。可跳过此步骤。

2. 准备目标源

   在EnOS上创建用于存储从数据源同步来的数据的配置单元表（Hive）。更多信息，参考[创建Hive表](https://docs.envisioniot.com/docs/data-explorer/zh_CN/latest/creating_hivetable.html)。

## 步骤2: 从数据源同步数据至EnOS<synchronizetoenos>

   对于外部数据源，可以从零开始创建或导入已有的任务流同步数据。任务流可根据你的需求设置为手动调度或周期调度。更多信息，参考[数据集成](data_integration/index)。

   对于主数据同步，可以使用大数据开发套件功能创建使用`SYNC_MDM`程序的任务流。更多信息，参考[数据开发套件](data_ide/index)。

## 步骤3：处理数据<process>

   使用数据开发套件处理数据，例如，将列转换为行。EnO提供了丰富的数据处理SDK通用库。

   更多信息，参考[数据开发套件](data_ide/index)。


## 步骤4：（可选）探索数据<explorerdata>

   EnOS数据探索帮助你执行交互式数据分析和可视化，并将这些数据用于数据可视化和商业智能等目的。更多信息，参考[数据探索](https://docs.envisioniot.com/docs/data-explorer/zh_CN/latest/dataexplorer_overview.html)。
