# 使用场景

使用数据开发套件进行数据开发的典型用户场景如下：

## 运行内置脚本<builtinscript>

EnOS提供了常用一系列数据处理的内置脚本。例如将主数据从HDFS同步到外部S3数据库，或将列转换为行。有关EnOS提供的内置脚本的相关信息，参考[通用库](common_library)。

运行内置脚本的主要步骤如下：

1. 在EnOS控制面板中选择 **数据开发套件 > 任务开发**。

2. 在通用库中找到要运行的脚本。

3. 双击脚本的版本查看有关脚本的详细信息。

   .. image:: media/scenario_built-in.png

4. 单击右侧的 **使用该方案**。

5. 在弹出窗口中，完成有关任务流的设置。并点击 **确认**。

6. 在配置面板中，完成调度配置。更多信息，参考[从零开始创建一次性任务流](creating_workflow_onetime)或[从零开始创建周期性任务流](creating_workflow_periodic)。

## 运行外部脚本<externalscript>

运行外部脚本的主要步骤如下：

1. 将你的脚本作为资源上传至EnOS。更多信息，参考[创建资源](creating_resource)。

2. 创建由SHELL类型的任务组成的任务流，该任务需调用步骤1中创建的包含外部脚本的资源。更多信息，参考[从零开始创建一次性任务流](creating_workflow_onetime)或[从零开始创建周期性任务流](creating_workflow_periodic)。

EnOS提供了示例代码用以简化配置过程，详细信息，参考[https://github.com/EnvisionBigdata/dataide_external_script](https://github.com/EnvisionBigdata/dataide_external_script).
