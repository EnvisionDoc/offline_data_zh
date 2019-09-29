# 数据探索概述

EnOS数据探索功能旨在支持灵活的数据分析方案，提供数据预处理和数据分析技术，帮助你对数据湖内的数据进行初步研究，以便更好地理解其性质，并通过对数据进行直观的检查来发现数据价值。

本功能基于开源 Apache Zeppelin 和 Jupyter 的数据探索分析功能，支持数据驱动的交互式数据分析任务。你可以对接入或集成到EnOS Cloud内的数据进行在线的、灵活高效的、交互式数据分析和探索，完成数据分析、可视化、模型训练等操作。

## 概述<description>

数据探索可帮助数据工程师、数据科学家、和业务分析人员更有效地处理数据，无需使用复杂的命令行或关注群集实现的细节。


## 主要优势<keybenefits>

- **发现与分析**

  EnOS数据探索深度集成了 Zeppelin Notebook 和 Jupyter Notebook两种当前主流的Notebook数据探索工具，提供基于浏览器的交互式分析环境。你可根据业务需求和使用场景，选择使用 Zeppelin Notebook 和 Jupyter Notebook：

     * **Zeppelin Notebook**：需要使用大数据平台资源（如Hive表和Report DB）进行数据探索和分析。支持hive，spark，python，shell，mysql，和markdown。
     * **Jupyter Notebook**：需要使用Python或R进行数据探索和分析、模型训练及验证等。支持Python 2，Python 3，和R。


- **可视化和协作**

  EnOS数据探索内置了多种图表样式，如柱状图，饼图，折线图和散点图。数据可视化不再仅限于SparkSQL查询，任何语言的输出都可以被识别并可视化。数据分析的过程可以被保存，导入，导出和共享。同时Notebook可使用Markdown格式的富文本中穿插代码，运行代码，然后以文本，表格，图形的方式查看结果。
