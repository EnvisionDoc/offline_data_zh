# 创建报表

你可以通过所见即所得的方式，拖拽图表的设计布局，自定义报表内容。EnOS 数据报表采用灵活的磁贴式布局来显示报表数据的交互。报表中可以包含多种分析图表和控件，并可进行过滤、多图表关联等高级设置。

## 前置条件

在制作报表之前，需要先完成数据准备，即[创建数据集](creating_dataset)。

## 步骤1：新建报表

1. 从控制台左边导航菜单选择 **数据报表 > 报表**。

2. 点击 **新建报表**，将进入报表编辑页面。在报表编辑页面，可以按需添加多种图表、控件，设置数据过滤、多图表关联等。还支持将报表发布为组织内公开，或者将报表导出为PDF文件等操作。

## 步骤2：添加报表组件

### 添加图表

按需添加所需的图表组件：

- [添加柱状图](charts_controls/bar_chart)
- [添加线状图](charts_controls/line_chart)
- [添加饼状图](charts_controls/pie_chart)
- [添加交叉表](charts_controls/cross_table)
- [添加指示块](charts_controls/indicating_block)
- [添加仪表盘](charts_controls/gauge)
- [添加散点图](charts_controls/scatter_chart)
- [添加高亮表](charts_controls/highlight_table)

不同图表的配置方式及差别如下表所示如下：

.. list-table::
   :widths: auto

   * - 图表名称
     - 维度个数
     - 度量个数
     - 是否支持多图关联
   * - 柱图
     - 1个
     - 1个或多个
     - 是
   * - 线图
     - 1个
     - 1个或多个
     - 是
   * - 饼图
     - 1个
     - 1个
     - 是
   * - 交叉表
     - 0个或多个
     - 0个或多个
     - 否
   * - 指标块
     - 0个或1个
     - 1个或多个
     - 是
   * - 仪表盘
     - 0个
     - 1个
     - 否
   * - 散点图
     - 1个或多个
     - 2个
     - 是
   * - 突出显示表
     - 2个或多个
     - 1个
     - 否

你还可以配置多图表之间的联动查询，详见[多图关联](charts_controls/multiple_chart_interlock)。

若图表的数据量较大，可以设置过滤器，将需要的某一类或某几类数据从数据中过滤出来。详见[设置过滤器](charts_controls/filter)。

### 添加组件

- [添加文本框控件](charts_controls/textbox)
- [添加iframe控件](charts_controls/iframe)
- [添加条件查询控件](charts_controls/conditioned_query)
- [添加图形控件](charts_controls/figure)
