# 配置SQL或MySQL Server数据源

本文描述了如何配置与SQL或MySQL Server数据源的连接。


## 关于任务<description>

要从外部SQL或MySQL数据库检索数据并进行分析，首先配置该数据源的信息以及创建与源数据库的JDBC连接。


## 步骤<procedure>

1. 在EnOS控制面板中选择 **外部源连接**。

2. 点击 **新增数据源**。

3. 在 **数据源** 窗口，完成以下配置：

   - **数据源名称**：数据源的名称。数据源名称的最大长度为50个字符，名称可以是以下字符的组合：
     - 中文
     - a - z
     - A - Z
     - 0 - 9
     - _ （下划线）

   - **数据源类型**：选择MYSQL
   - **主机名或IP地址**：输入数据库的主机名或者IP地址。
   - **数据库名称**：输入数据库的名称，为该数据库的唯一识别码。
   - **端口**：输入用于连接的端口号。EnOS使用数据库地址、数据库名称和端口来建立从EnOS到数据库的JDBC连接。
   - **用户名**：输入用于访问数据库的用户名。
   - **密码**：输入用户名的密码。
   - **数据源描述**：输入对数据源的描述。

4. 点击 **测试** 按钮，测试数据源的连通性。

5. 点击 **确定** 保存配置。

## 结果<result>

连接创建后，该数据源项将显示在 **外部源连接** 的列表中。


## 后续操作<followup>

成功建立连接后，EnOS会将数据从外部数据源提取到EnOS内部的Hive数据库。你必须创建Hive表存储已提取到的数据。更多信息，参考[创建Hive表](/docs/offline-data/zh_CN/latest/data_explorer/creating_hivetable.html)。

接着，你可以配置一个数据集成任务流，将数据从数据源同步到EnOS中的目标表。更多信息，参考[数据集成](../data_integration/index)。
