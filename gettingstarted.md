# 数据分析快速入门
使用EnOS数据分析服务分析历史数据的典型流程如下：

.. image:: media/getting_started.png


## 步骤1：准备数据源和目标数据库<preparedatasource>

1. 准备数据源

   - 如果数据源来自外部的，首先需要设置与源数据的连接。EnOS支持同步 MYSQL，SQL Server，Oracle，FTP，SFTP，Amazon S3，Azure Blob，和 GitLab 数据源的数据。有关如何连接到数据库的信息，参考 [外部源连接](data_source/index)。
   - 如果处理和分析的数据位于EnOS云端，例如，设备主数据累加并存储到EnOS中，可跳过此步骤。

2. 准备目标源

   在EnOS上创建用于存储从数据源同步来的数据的配置单元表（Hive）。更多信息，参考 [创建Hive表](data_explorer/creating_hivetable.html)。

## 步骤2: 从数据源同步数据至EnOS<synchronizetoenos>

对于外部数据源，可以从零开始创建数据集成任务或导入已有的任务配置文件，同步数据或文件。数据集成任务可根据你的需求设置为手动调度或周期调度。更多信息，参考 [数据集成](data_integration/index)。

对于主数据同步，可以使用大数据开发套件功能创建使用 `SYNC_MDM` 程序的任务流。更多信息，参考 [数据开发套件](data_ide/index)。

## 步骤3：处理数据<process>

使用数据开发套件处理数据，例如，将列转换为行。EnOS提供了丰富的数据处理SDK通用库。更多信息，参考 [数据开发套件](data_ide/index)。


## 步骤4：探索数据<explorerdata>

EnOS数据探索帮助你执行交互式数据分析和可视化，并将这些数据用于数据可视化和商业智能等目的。更多信息，参考 [数据探索](data_explorer/index)。
