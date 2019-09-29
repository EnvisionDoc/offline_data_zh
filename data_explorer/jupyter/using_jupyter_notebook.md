# 快速入门

使用 Jupyter Notebook 进行数据分析的典型流程如下：

## 步骤1：添加代码

1. 在 Jupyter Notebook 首页，点击页面右上角的 **New** 下拉菜单，选择需要创建的note（目前支持Python2、Pythone3、和 R）。

2. （可选）在 **New** 下拉菜单中，也可选择需要创建的文件、目录、或Terminal。

   .. image:: ../media/jupyter_note.png

3. 如果选择创建note，在打开的 Jupyter Notebook中，输入注释即可进行数据探索分析。

   .. image:: ../media/jupyter_python.png

## 步骤2：Kernel管理

Jupyter Notebook 提供Kernel管理功能，如下图所示：

.. image:: ../media/kernel_management.png

各项管理操作的功能为：

.. list-table::
   :widths: auto

   * - 操作
     - 功能描述
   * - Interrupt
     - 中断当前服务
   * - Restart
     - 重启服务，所有变量都会丢失
   * - Restart & Clear Output
     - 重启当前内核并清除所有输出，所有变量和输出都将丢失
   * - Restart & Run All
     - 重新启动当前内核并重新执行整个Notebook，所有变量和输出都将丢失 
   * - Reconnect
     - 重新连接Jupyter Server
   * - Shutdown
     - 关闭Jupyter服务，所有变量都会丢失
   * - Change Kernel
     - 可以切换Kernel, 支持Python2，Pyton3，R三种Kernel的任意切换

## 步骤3：Notebook管理

你可以通过步骤2中介绍的Kernel管理操作管理Notebook。如通过Interrupt或Shutdown操作可以停止当前Notebook，通过Restart或Reconnect可以重启内核或重连Server。

直接关闭Notebook页面并没有真正停止Notebook与后台Server的连接，你也可以在Jupyter Notebook管理页面管理Notebook, 可以选择一个或多个Active的Notebook, 点击 **Shutdown** 后统一关闭，如下图所示：

.. image:: ../media/shutdown_note.png

选择一个或多个Active的Notebook, 点击 **Delete** 后统一删除Notebook。

.. note:: Jupyter Notebook的删除操作与Zeppelin Notebook不同，是永久删除，请谨慎操作。

## 步骤4：保存代码

Jupyter代码默认自动保存在EnOS内部存储，除非删除沙箱环境，否则代码会一直保留。

删除沙箱环境与停止沙箱环境不同，停止沙箱环境仅释放计算资源，沙箱不可用，但代码不会丢失，重启沙箱环境后代码仍然可见。删除沙箱环境会同时释放计算和存储资源，沙箱环境彻底销毁不可再用，保存的代码和数据也一并销毁。如需再次使用沙箱环境，需要使用其它的沙箱环境或重新申请沙箱环境。

在删除沙箱环境前，你可以通过以下2种方法保存代码：

1. 导出代码：通过Download方式可以将Notebook导出到本地，需要使用时，可通过Open功能打开使用。

   .. image:: ../media/download_note.png

2. 将代码上传到GitLab仓库：在 **New** 下拉菜单中，选择 Terminal。在启动的Terminal中，通过Git命令将Notebook上传至GitLab。

<!--end-->