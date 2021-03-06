# 饼图

饼图显示的是一个数据系列，每个数据系列具有唯一的颜色或图案。饼图可用来展示数据中各项的大小与各项总和的比例，比如不同品牌风机占比。

饼图是由一个个扇区构成的，每个扇区的标签由数据的维度决定，每个扇区的大小由数据的度量决定。

## 任务描述

**饼图需要选择1个维度，1个度量**。

创建报表之前，需要先准备数据集。假设已经完成数据集创建，下面介绍饼图的使用方法。

1. 登录 **控制台**，选择 **数据报表**，然后选择 **报表**。点击 **新建报表**，进入报表编辑页面。

2. 双击 **饼图** 图标 |pie_icon| ，饼图的图例会自动显示在报表展示区。

3. 在数据标签中，点击 **选择数据集**，在下拉列表中选择目标数据集。

4. 点击 **选择字段**，下拉列表中将展示所选数据集的全部维度及度量字段。

5. 在下拉列表中，选择扇区标签（维度）及扇区角度（度量）字段。

6. 点击 **更新**，系统自动更新图表。

   .. note:: 请注意，配置图表的数据时，只有点击 **更新**，数据配置才会生效。

7. 若需要设置过滤器，请参考[设置过滤器](filter)使用说明。

8. 在 **自动刷新** 一栏中，输入数据自动刷新的频率。支持的最小值为5秒。

   .. image:: ../media/pie_data.png

9. 完成数据配置后，可以选择样式标签，设置饼图的样式。包括通用及设计两类。样式设置实时生效，具体说明如下:

   - 是否显示标题

   - 是否显示边框

   - 选择饼图样式，默认或空心。若选择空心，即环状图的效果。

   - 选择标签样式，包括无，标题，百分比，标题，值（百分比），标题以及标题，值

   - 设置显示图例的位置，支持上方、下方、左侧、右侧显示

   - 是否显示Tooltip

     .. image:: ../media/pie_style.png

10. 完成样式配置后，可以选择高级标签，配置多图关联。具体使用方法，请参考 **多图关联** 的使用说明。

11. 在报表展示区，点击饼图的图例，可以设置是否显示维度值。

    .. image:: ../media/pie_legend.png

12. 若需要查看图表对应的数据，并将数据下载到本地，或删除所选图表。需要先选中图表，然后点击标题栏右上角的 |chart_spread| 。在下拉菜单中选择 **查看数据** 并 **下载** 到本地。或者选择 **删除**，删除所选图表。

13. 配置完成后，点击工具栏中的 **保存**。

.. |pie_icon| image:: ../media/pie_icon.png

.. |chart_spread| image:: ../media/chart_spread.png

<!--end-->
