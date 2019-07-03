# 创建Hive表

本章节描述了如何通过数据探索创建Hive表。


## 关于任务<description>

从外部数据源获取的数据需要存储为Hive表，以供其他EnOS数据处理功能使用。你需要在数据探索中创建所需的Hive表。


## 步骤<procedure>

1. 在EnOS控制台中选择 **数据探索**。

2. 导入或创建笔记。

   - 如果你已经创建了包含表创建脚本的笔记，点击 **导入笔记**。
   - 如果要创建新笔记，点击 **新建笔记**。

3. 如果你选择新建笔记，则在弹出窗口中设置笔记的名称，然后选择 **hive** 作为笔记类型。例如，如果你输入`yourname/hive/tablename`作为笔记的名称，则会在`yourname/hive`目录下创建名为`tablename`的Hive表。

4. 点击刚刚新建的笔记后 |enter_note| 进入笔记编辑模式。在笔记中，提供用于创建表的命令。例如，

   ```
   create table if not exists dpdw_dim_site_full(
	   site_id string,
	   site_name string,
	   capacity string,
	   equipment_amount string,
	   air_denity string,
	   area string,
	   state_name string
   ) comment 'wind domain dimension table'
   ```

   更多有关命令的信息，参考 [Apache Hive documentation on table creation](https://cwiki.apache.org/confluence/display/Hive/LanguageManual+DDL#LanguageManualDDL-CreateTable)。


5. 点击 |run| 运行段落。下图显示了表已创建成功：

   .. image:: media/create_hive.png

## 结果<result>
表创建完成后，你可以通过运行查询来测试结果。

```
%hive
select * from dw_meter_1h_demo limit 2
```

如果运行成功，你将得到如下反馈：

.. image:: media/test_query.png

## 后续操作<followup>

如果要将刚创建的Hive表作为存储外部数据源的数据库，需要将Hive表指定为目标表，并通过数据集成功能将数据源中的列映射到目标。详细信息，参考 [数据集成](../data_integration/index.html)。

.. |enter_note| image:: media/enter_note.png

.. |run| image:: media/run.png

<!--end-->