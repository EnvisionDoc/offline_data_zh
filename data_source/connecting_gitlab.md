# 配置GitLab数据源

本文描述了如何配置与GitLab数据源的连接。


## 关于任务<description>

要从外部GitLab数据源检索数据，首先需要配置与GitLab数据源的连接信息。

## 步骤<procedure>

1. 登录EnOS控制台，从导航栏中选择 **外部源连接**。

2. 点击 **新增数据源**。

3. 在 **数据源** 窗口中，完成以下配置：

   - **数据源名称**：输入数据源的名称。数据源名称的最大长度为50个字符，名称可以是以下字符的组合：
     - 中文
     - a - z
     - A - Z
     - 0 - 9
     - _ （下划线）
   - **数据源类型**：选择GITLAB。
   - **Token**：输入用于访问GitLab仓库的Access Token。获取Access Token的步骤如下：
     - 登录GitLab，点击页面右上角 **User** 下拉菜单，选择 **Settings**。
     - 在 **User Settings** 页面左侧导航栏中，选择 **Access Tokens**。
     - 输入需要创建 Access Token 的名称，选择 Token 的有效期，选择 `api`, `read_user`, `read_repository` 三项权限，点击 **Create personal access token**。
     - 在 **Your New Personal Access Token** 字段中，复制生成的 Access Token。
   - **Git URL**：输入GitLab项目的地址，格式为 `http://git.{domain-name}.com`。
   - **数据源描述**：输入对数据源的描述。

4. 点击 **测试** 按钮，测试数据源的连通性。

   .. image:: ../media/gitlab_connection.png

5. 点击 **确定** 保存配置。

## 结果<result>

连接创建后，该数据源项将显示在 **外部源连接** 的列表中。


## 后续操作<followup>

成功建立连接后，即可将数据从外部数据源提取到EnOS内部的Hive数据库。你必须创建Hive表存储已提取到的数据。更多信息，参考[创建Hive表](/docs/offline-data/zh_CN/latest/data_explorer/creating_hivetable.html)。

<!--

接着，你可以配置一个数据集成任务流，将数据从数据源同步到EnOS中的目标表。更多信息，参考[数据集成](../data_integration/index)。

-->
