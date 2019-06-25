# Unit 4. Running the Data Integration Task

In this unit, start running the data integration task to synchronize data from the external MySQL database to EnOS Hive. 

## Step 1: Pre-run the task

1. Open the data integration task created in [Unit 3](creating_data_integration_task).

2. Click **Pre-run** on the configuration panel.

   .. image:: media/pre-run_task.png

3. Specify a triggering time and click **OK** to test running the data integration task.

   .. image:: media/trigger_time.png

4. A workflow instance will be created for the data integration task. Check the running status and result of the task on the **Workflow Operation** page.

## Step 2: View the pre-run result

For a pre-running task, a manual instance will be created.

1. Click **Workflow Operation > Manual Instance** from the navigation panel.

2. Find the task name in the **Instance Name** column, and check the running status of the data integration task.

   .. image:: media/pre-running_status.png

3. When the data integration task is completed, check the running result of the task.

   .. image:: media/pre-running_success.png

## Step 3: View the status of periodic instances

According to the configuration, the *MySQL2Hive* data integration task will be running every hour. Updated data in the source database will be synchronized to EnOS Hive table incrementally.

1. From the navigation panel, click **Workflow Operation** > **Periodic Scheduling**. Check the status of the data integration task. 

   .. image:: media/workflow_list.png

2. Click **Periodic Instance** from the menu, check the list of scheduled data integration tasks and their running status and result.

   .. image:: media/preiodic_instances.png

## Next Unit

[Viewing the Synchronized Data](viewing_synchronized_data)