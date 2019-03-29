# 数据探索快速入门

将数据探索进行数据分析的典型流程如下：

## 步骤1：创建新笔记<createnote>

1. 在EnOS控制面板中选择 **数据探索**。

2. 单击 **新建笔记**。

3. 在 **新建笔记** 窗口中，提供笔记的名称并选择笔记类型，然后点击 **确认** 完成创建。

4. 单击刚创建笔记后的 |enter_note| 。

5. 在弹出窗口中提供注释并开始工作。

   .. image:: media/gettingstarted_1.gif

## 步骤2：使用解释器编程并运行代码<developcode>

在窗口中输入`%<interpreter_name>`（百分比）调用解释器。下表列出了支持的解释器以及其调用参数。

.. note:: 系统会根据步骤1中选择的笔记类型自动关联相应的解释器，无需再次使用百分号调用解释器。但是，如果要调用除步骤1中选择的解释器之外的其他解释器，则可以使用下表中显示的语法。

.. list-table::
   :widths: auto

   * - 解释器</th>
     - `%<interpreter_name>`
   * - hive</td>
     - %hive</td>
   * - spark</td>
     - %livy.spark</td>
   * - pyspark</td>
     - %livy.pyspark</td>
   * - markdown</td>
     - %md</td>
   * - mysql</td>
     - %mysql_report</td>
   * - python</td>
     - %python</td>
   * - shell</td>
     - %sh</td>

.. image:: media/gettingstarted_2.gif

## 步骤3：可视化数据<visualizedata>

选择内置的图表类型可视化数据，以帮助你分析数据。

以下截图为一个饼图示例，该示例展示了一组人的教育程度的比例。

你也可以切换其他分组标准，例如 **工作** 或 **年龄** 或 **婚姻**。

.. image:: media/data_explorer_pic_2.png

.. |enter_note| image:: media/enter_note.png

<!--end-->
