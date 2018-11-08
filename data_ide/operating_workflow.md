# Operating a workflow

## Pre-running a workflow

After creating a workflow, you can run the **Pre-run** action to check the operations and results of the code.

- In a periodic workflow, pre-run is designed to test code logic.
- In a one-time workflow, each operation needs to be manually triggered, that is, to be realized by pre-run.


1. Click **Pre-run** and specify the workflow triggering time.

   **Note:**
   - If a time before the current system time is selected as the trigger time, the workflow will be executed immediately to generate a running instance (viewable through the workflow monitor. When the workflow instance is running, the trigger time is regarded as the business time and is transmitted to the time parameter for business computing.
   - Only one instance for the same workflow is allowed to run at a time. If the pre-run instance conflicts with the current running instance, the pre-run instance will wait till the completion of the running instance.

2. Click **OK**, and the workflow instance ID will be displayed in the upper right corner of the page.

3. You can then view the instance information in the workflow monitor. For more information, see [Task monitor overview](../task_monitor/taskmonitor_overview).

## Cloning a workflow

From the directory tree, right-click the workflow and click **Clone**.

**Note**: When you clone a workflow, the resources and the upstream references of the original workflow are cloned. However, the downstream references are not cloned.


## Deleting a workflow

From the directory tree, right-click the workflow and click **Delete**.

**Note**: When you delete a workflow, the instances of the workflow are all removed. You can no longer retrieve the instance details through **Workflow Monitor**.

## Exporting a workflow

To save a workflow configuration for future reuse, export the workflow.

From the directory tree, double-click the workflow and click **Export** in the workflow panel.

A file with the `.workflow` extension is downloaded to your local file system. An exported configuration file contains the configuration information, scheduling information, and resource packages that are used in the workflow.
