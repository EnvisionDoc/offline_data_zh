# Unit 3. Configuring a Data Integration Task

In this unit, create and configure a data integration task for synchronizing the employee data from the external MySQL database to EnOS Hive.

## Step 1: Create a data integration task

1. Log in EnOS Console, click **Data Integration** from the left navigation tree, and click the **+** icon to create a data integration task.

2. In the **New Data Integration Task** window, complete the basic settings for the task.

   - **Mode**: Select **Create** to create a task from scratch.
   - **Name**: Name of the data integration task (for example, *MySQL2Hive*).
   - **Sync Type**: Select **Data synchronization**.
   - **Scheduling Type**: Select **Periodic scheduling**, which supports synchronizing data periodically.
   - **Description**: Short description about the data integration task.
   - **Select Dir**: Directory to save the task configuration.

3. Click **OK** to create the data integration task.

   .. image:: media/create_data_sync_task.png

## Step 2: Select the data source

1. Complete the following settings for the external data source.

   - **Data Source Type**: Select **MySQL**.

   - **Data Sources**: Select the **employee_data** data source that has been configured in [Unit 1](configuring_data_connection).

   - **Source Table**: Select the **employees** table in the source that will be synchronized. See the following screen capture:

     .. image:: media/selecting_source.png

   - **Data Filter** (optional): If you want to filter the data to be synchronized, provide the SQL query script.

   - **Data Preview** (optional): Click it to preview the filtered data to synchronize.

     .. image:: media/data_preview.png

2. Click **Next**.


## Step 3: Select the target table

1. Complete the following settings for the target Hive table.

   - **Data Source Type**: Select **Hive**.
   - **Table Name**: Select the **employee** Hive table that is created in [Unit 2](creating_hive_table). Note that if the created Hive table is partitioned, the partition of the Hive table will be automatically loaded.
   - **Partition** (optional): If the Hive table has partitions, select the corresponding partition type and enter the value.
   - **Data Writing Rule**: Specify whether to overwrite the existing data in the target table, or append the data behind the existing data records.

2. Click **Next**.

   .. image:: media/selecting_target.png

## Step 4: Configure field mapping between source and target

When both the data source and target table are selected, map the source fields to the target fields. Then, data in the source database will be synchronized to the specified fields in the source table.

1. For each field in the **Target Field** column, click a source field from the **Source Field** column to map the source fields with the target fields.

   .. image:: media/mapping_data.png

   .. note:: Data of the matched fields must be of the same data type.


2. When finishing mapping the fields, click **Next**.

## Step 5: Configure task scheduling

1. Click the **Scheduling Config** tab from the right edge of the configuration panel.

2. Complete the settings of the scheduling attribute:

   - **Activation Date**: Specify when the task starts to take effect.
   - **Scheduling Cycle**: Specify the frequency to run the task. In this tutorial, select **Hour** for the task to run every hour.
   - **Specific Time**: Based on the scheduling cycle, specify the exact time in a cycle to run the task. In this tutorial, select **00 min** for the task to run at every hour.
   - **Timeout**: Specify the timeout value for the task.
   - **Retry Times**: Specify the number of reconnection attempts to try after timeout.
   - **Retry Interval**: Specify the interval between each reconnection attempt.
   - **Allow Referenced**: Specify whether this task can be referenced by another task.

3. Click the **Scheduling Config** tab from the right edge of the configuration panel again, the scheduling configuration will be saved.

   .. image:: media/scheduling_config.png

## Step 6: Configure concurrency

Select the number of concurrent connections to establish and click **Next**.

In this tutorial, select 1 connection.

.. image:: media/concurrency.png


## Step 7: Review and save the task configuration

1. Preview the settings of the data integration task and click the **Edit** button to make changes if needed.

2. Click **Done** to complete the data synchronization configuration.

3. Click **Save** on configuration panel to save the data integration task.

   .. image:: media/saving_task.png

## Next Unit

[Running the Data Integration Task](running_data_integration_task)
