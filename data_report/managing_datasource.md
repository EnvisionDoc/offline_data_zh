# 数据源管理

在EnOS<sup>TM</sup> IoT平台中，为每个开通数据报表模块的组织，默认自动创建一个数据库Report DB。不同组织之间，数据库隔离，以保证数据安全。您可以使用数据探索工具，在Report DB中创建数据源表。然后使用数据集成工具，将Hive中的数据同步至目标数据源表。

## 操作步骤

1. 添加数据源

   登录 **控制台**，从左边的导航菜单选择 **外部源连接**，完成数据源信息配置。有关EnOS支持的数据源类型及如何配置连接至数据源，参见 [外部源连接](/docs/offline-data/zh_CN/2.0.9/data_source/datasource_overview.html)。

2. 创建目标表

   从左边的导航菜单选择 **数据探索**，参见 [创建Hive表](/docs/offline-data/zh_CN/2.0.9/data_explorer/creating_hivetable.html) 创建目标表。若目标表已存在，则可以跳过这一步。

3. 创建数据集成任务

   从左边的导航菜单选择 **数据集成**，点击新建任务流，创建数据集成任务，并完成任务流配置。根据业务需要，可以通过数据过滤，同步部分数据。详细任务流配置，参见 [数据集成](/docs/offline-data/zh_CN/2.0.9/data_integration/index.html)。

4. （可选）创建数据开发任务

   若数据ETL开发逻辑比较复杂，可以选择 **数据开发套件 > 数据开发**。点击新建任务流，创建任务流。详细任务流配置，参见[数据开发套件](/docs/offline-data/zh_CN/2.0.9/data_ide/dataide_overview.html)。

5. 运行任务并查看监控

   点击 **预跑**，然后到 **任务监控**，查看任务流运行情况。详见 [任务流运维](/docs/offline-data/zh_CN/2.0.9/task_monitor/taskmonitor_overview.html)。

6. 查询数据导入结果

   任务成功后，进入 **数据探索**，查询导入到Hive表的数据。

7. 在Report DB中创建目标表

   选择 **数据探索**，新建mysql_report类型的工作簿，在Report DB中创建目标表。若目标表已存在，则可以跳过这一步。

8. 同步表数据到Report DB

   选择 **数据集成**，点击新建任务流，创建数据集成任务。数据源选择Hive类型，目标表选择Report DB，并完成任务流配置。点击预跑，然后到 **任务监控** 模块查看任务状态。

## 后续操作

数据同步完成后，可以通过单表模式或SQL模式，创建数据集。详见 [创建数据集](creating_dataset)。
