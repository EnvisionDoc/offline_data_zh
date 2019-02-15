# 监控手动任务流

你可以对手动任务流执行以下操作：
- 查看任务流实例
- 预跑手动任务流
- 预跑单个任务

## 查看手动任务流<viewworkflow>

你可以查看任务流的常规信息和任务流中每个任务的详细信息。

执行以下步骤查看手动任务流：

1. 在EnOS控制面板中，单击 **数据运维 > 手动任务**。右侧面板中显示了你可以访问的所有手动任务流。

2. （可选）在表格上方的搜索字段中，输入任务ID或名称过滤表格中显示的结果。

3. 单击需查看详细信息的任务流的名称，将打开任务流面板。

4. 在任务流面板中，双击单个任务节点可查看以下详细信息：

   - **属性**：任务的配置详情。

     .. image:: media/workflow_attributes.png

   - **节点内容**：任务中运行的内容。具体内容因任务类型而异。

     示例1，数据集成任务的内容如下所示：

     .. image:: media/workflow_taskcontents.png

     示例2，SHELL任务的内容如下所示：

     .. image:: media/workflow_taskcontents2.png


## 预跑手动任务流<prerunworkflow>

如需手动触发任务流，点击需预跑的任务流后的 **重跑** 并设置触发时间。

## 预跑单个任务<preruntask>

如需手动触发任务流中的单个任务：

1. 单击需预跑的任务所属的任务流的名称，打开任务流面板。

2. 在任务面板中，右键单击任务框，然后单击 **预跑** 并设置触发时间。