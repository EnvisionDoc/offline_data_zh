# 设置集成任务参数

本文描述了如何设配置在集成任务中使用的参数。

## 参数类型<parameters>

参数可设置为常量，系统变量或自定义变量。

有关可以使用的系统变量，参阅[系统变量](../data_ide/system_variables)。


## 步骤<procedure>

步骤如下：

1. 在EnOS控制台中选择 **数据开发套件 > 数据开发**。

2. 在目录树中，双击需要添加参数的集成任务。

3. 在配置面板中，单击面板右边缘的 **参数设置** 。

4. 按 **key=value** 的格式配置你所使用的每个参数的值。如果要定义多个参数，使用 **Enter** 键分隔每个参数。

```
key1=value1
key2=value2
```
可以设置为单个值或者为一组值。
<!--Vivian: @weiwei, please list the syntax how to set value array-->


## 示例: 在URL中使用参数<example>

例如，你可以为S3数据源设置如下URL：

  `s3://history/log_solar_dt_change_inverter/${test_list}.each_value`

`test_list`为参数，你可以为该参数设置值： `test_list=Array[20170515,20170516,20170517,20170518,20170519,20170520,20170521,20170522,20170523,20170524,20170808,20170905,20170906,20170918]`

.. image:: media/parameter_example_URL.png

<!--end-->
