# 使用EnOS™Data IDE运行外部Python脚本

你可使用`external_service.sh`脚本运行非EnOS内置的脚本。示例代码描述了如何使用EnOS 的`external_service.sh`脚本来运行外部Python脚本。

## 开始前准备<beforestart>

1. 将示例文件从GitHub库 <https://github.com/EnvisionBigdata/dataide_external_script>克隆到本地。

2. 在本地打开您克隆的目录。

3. 用你自己的文件替换脚本和引用的文件。

4. 将目录中所有的文件压缩为`.zip`文件。例如`external_service.zip`。

## 关于任务<description>

此任务使用示例来描述了如何使用`external_service.sh`脚本调用主脚本文件[`example-conda.sh`](example-conda.sh)。

存储库中的示例代码的说明如下：
- 调用的脚本文件`example-conda.sh`，是通过在原始脚本文件`example.sh`中通过添加以下代码来生成的。此代码安装了运行引用的Python脚本所需的Python包。

  ```
   source ~/.bash_profile
   envName=codeExample
   if [[ `conda create -y -n $envName python=2.7` ]]; then
     source activate $envName
     conda install -y pytz
     conda install -y pandas
     conda install -y boto3
     source deactivate
   fi
   source activate $envName

   ...
   ...

   source deactivate
  ```

- `inputFiles`目录中的文件是示例输入文件，包含非标准数据格式和结构，因此需要重组和转换。

- `example-conda.sh`中调用的Python脚本完成处理数据并将数据上传到S3数据库的任务。

- `outputFiles`目录下的文件为符合EnOS数据的输出的示例文件。

- `config`目录下的文件包含了运行Python脚本所需的配置。


## 步骤1：将zip文件上传到EnOS（创建资源）<uploadscript>

你可通过以下过程中将`.zip`文件作为EnOS的资源上传：

1. 在EnOS控制台中选择 **数据开发套件 > 资源管理**。

2. 点击资源目录树上方的 **+** 创建资源。

3. 在 **新建资源** 窗口中，提供有关资源的基本设置。然后单击 **确定**。

    - 名称：输入资源名称。
    - 描述：提供有关资源的描述性信息。
    - 选择目录：选择保存资源的目录d。

4. 双击刚刚新建的资源打开资源概述。

5. 单击 **新建版本** 并上传`external_service.zip`文件，其设置如下图所示：

   .. image:: media/resource.png

## 步骤2：创建一个引用本资源的任务流<createworkflow>

1. 在EnOS控制台中选择 **数据开发套件 > 任务开发**。

2. 点击目录树上方的 **+** 创建任务流。

3. 在 **新建任务流** 窗口中，按下列信息设置任务流，然后单击 **确定**。

   - **模式**：新建。
   - **名称**：external_script_sample
   - **类型**：手动调度
   - **选择目录**：要存储任务流的目录。

   .. image:: media/new_workflow.png

4. 双击刚刚新建的任务流。

5. 在配置面板中，将任务节点 **SHELL** 拖曳至配置面板中。

6. 在 **新建任务节点** 窗口中，提供任务的名称和描述。然后点击 **创建**。

   .. image:: media/new_task.png

7. 双击刚刚创建的任务节点，根据下列信息设置任务节点：

   -  **命令**：输入以下命令：

      ```
      sh external_service.sh $ {service_url} $ {instance_id} $ {command}
      ```

      其中，`service_url`和`command`为需要在右侧边缘的**参数配置**中设置的参数。` instance_id`为系统变量，是任务流实例的标识符。

   - 选择在步骤3中上载的资源和资源版本。   

8. 单击配置面板右边缘的 **参数配置**，并提供以下设置：

   ```
   SERVICE_URL = “http://172.20.101.141:8185/uploadservice”
   command =“python example-conda.py”
   ```

   .. note:: `command`的值为主脚本文件的名称。

   下图为示例中的任务配置。

   .. image:: media/task.png

9. 单击 **返回工作流面板**，然后单击 **发布** 以发布工作流程。

10. 单击 **预跑** 运行任务流。

##步骤3: 验证结果<verify>

预跑任务流后，将生成任务流的实例。然后，你可以在数据运维中跟踪有关实例的详细信息。

1. 在EnOS控制台中选择 **数据运维**。

2. 单击 **预跑实例**，然后通过任务流的名称找到实例。任务流实例如下图所示：

   .. image:: media/instance.png

3. 单击表中的实例名称，然后从配置面板中双击该任务。

4. 单击 **调查运行日志** 选项卡查看日志。

   .. image:: media/log.png

<!--end-->
