# 多图关联

在图表配置的**高级**标签页中，可以配置多图表之间的联动查询。

**前置条件**

创建报表，至少添加两个可以支持多图关联的图表，并分别完成数据配置。

下面以柱图和饼图为例，说明如何配置多图关联。

1. 登录 **控制台**，选择 **数据报表**，然后选择 **报表**。点击 **新建报表**，进入报表编辑页面。

2. 双击柱图图标 |bar_icon| ，柱图的图例会自动显示在报表展示区。在数据标签页，完成数据配置。

3. 双击饼图图标 |pie_icon| ，饼图的图例会自动显示在报表展示区。在数据标签页，完成数据配置。

4. 选中柱图，在 **高级** 标签页中，选择需要 **被关联** 的目标图表。以饼图为例，在柱图的高级标签页中，选中饼图的维度字段。此时，即完成高级关联。

   .. image:: ../media/multi_correlation.png

.. note:: 请注意，配置多图关联时，主动发起关联的图表（柱图）的维度字段将作为源字段，与被关联的图表（饼图）的维度字段进行关联，此时源字段的值将作为过滤条件，过滤被关联图表中维度值等于过滤值的数据。在本例中，当在柱图中选择某个维度值时，该维度的值将作为过滤条件，筛选被关联图表中等于相同维度值的数据。

**效果说明**

1. 以柱图为主动关联图表，源字段为维度，以饼图为被关联图表，被关联字段为月份，完成数据及多图关联配置。

   .. image:: ../media/multi_correlation_before.png

2. 在柱图中，点击2017-12，饼图中将自动查询出2017-12的数据，此时即实现多图联动查询的效果。

   .. image:: ../media/multi_correlation_after.png


.. |bar_icon| image:: ../media/bar_icon.png

.. |pie_icon| image:: ../media/pie_icon.png

<!--end-->
