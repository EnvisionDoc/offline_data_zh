# 设置任务流或SHELL类型任务的参数

本文描述了如何设配置在任务流或SHELL类型任务中使用的参数。


## 参数类型<parameter>

参数可设置为常量，系统变量或自定义变量。

有关可以使用的系统变量，参阅[系统变量](/docs/offline-data/zh_CN/latest/system_variables.html)。


## 步骤<procedure>

步骤如下：

1. 在EnOS控制台中选择 **数据开发套件 > 数据开发**。

2. 在目录树中，双击需要添加参数的任务流。

3. 在配置面板中，单击面板右边缘的 **参数设置**。

4. 按 **key=value** 的格式配置你所使用的每个参数的值。如果要定义多个参数，使用 **Enter** 键分隔每个参数。

   ```
   key1=value1
   key2=value2
   ```

值可以为一个值或者为一组值。
<!--Vivian: @weiwei, please list the syntax how to set value array-->

## 示例：在SHELL脚本中使用参数<example>

你可以在SHELL脚本中设置参数，如下所示：

```
java -cp ide.sdk-0.1.3.jar com.envision.dataplatform.C2R.C2RBeelineUtil -i
${inputPath}  -o ${outputPath} -ot ${outputTableName} -ca ${columnAll} -cm
${columnMust} -cs ${columnSelected} -g ${group_name} -h "${HIVE_JDBC}" -u
${unix_timestamp} -z ${time_zone}
```

你可以在参数配置中赋值给参数，如下所示：

```
inputPath=/user/hive/warehouse/xiaoxiao_product_db.db/input
outputPath=/tmp/xiaoxiao/output
outputTableName=2018_07_31
columnAll=projectid,deviceid,updatetime,envi_monitor_pm1,envi_monitor_pm25
columnMust=projectid,deviceid,updatetime,
columnSelected=envi_monitor_pm1,envi_monitor_pm25
time_zone=Asia/Shanghai
```

.. image:: media/parameter_example_shell.png

<!--end-->
