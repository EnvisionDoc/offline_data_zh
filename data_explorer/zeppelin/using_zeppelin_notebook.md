# 快速入门

使用 Zeppelin Notebook 进行数据分析的典型流程如下：

## 步骤1：创建note

1. 在 Zeppelin Notebook 首页，点击 **Create new note**。

2. 在新窗口中，输入note的名称或带路径的名称，选择默认解释器类型，然后点击 **Create** 完成note创建。

   .. image:: ../media/zeppelin_note.png

3. 在新建的note窗口中输入注释并开始工作。

   .. image:: ../media/creating_hive_table.png

## 步骤2：使用解释器编程并运行代码

在note窗口中输入 `%<interpreter_name>`（百分比）调用解释器。下表列出了 Zeppelin Notebook 支持的解释器以及其调用参数。

.. note:: 系统会根据步骤1中选择的默认解释器类型自动关联相应的解释器，无需再次使用百分号调用解释器。但是，如果要调用除步骤1中选择的解释器之外的其他解释器，则可以使用下表中显示的语法。

.. list-table::
   :widths: auto

   * - 解释器
     - `%<interpreter_name>`
   * - hive
     - %hive
   * - spark
     - %livy.spark
   * - pyspark
     - %livy.pyspark
   * - markdown
     - %md
   * - mysql
     - %mysql_report
   * - python
     - %python
   * - shell
     - %sh

使用解释器编程并运行代码的示例如下：

.. image:: ../media/gettingstarted_2.gif

有关解释器的详细介绍，参考 [支持的解释器](supported_interpreter)。

## 步骤3：可视化数据

选择内置的图表类型可视化数据，以帮助你分析数据。下图为一个饼图示例，该示例展示了一组人的教育程度的比例。你也可以切换其他分组标准，例如 **工作** 或 **年龄** 或 **婚姻**。

.. image:: ../media/data_explorer_pic_2.png

## 步骤4：保存代码

Zeppelin代码默认自动保存在EnOS内部存储，除非删除沙箱环境，否则代码会一直保留。

删除沙箱环境与停止沙箱环境不同，停止沙箱环境仅释放计算资源，沙箱不可用，但代码不会丢失，重启沙箱环境后代码仍然可见。删除沙箱环境会同时释放计算和存储资源，沙箱环境彻底销毁不可再用，保存的代码和数据也一并销毁。如需再次使用沙箱环境，需要使用其它的沙箱环境或重新申请沙箱环境。

在删除沙箱环境前，你可以通过以下2种方法保存代码：

1. 导出 notebook 并保存到本地目录；需要使用时，再导入 notebook。
2. 将代码上传到GitLab仓库。使用shell解析器将代码重定向为文件后，通过Git命令将notebook上传至GitLab仓库。

<!--end-->