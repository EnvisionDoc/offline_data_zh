# Unit 2. Synchronizing Data to the Report Database

In this unit, create a data integration task for synchronizing the employee data from Hive to the Report Database.

## Step 1: Create the data integration task

1. Log in EnOS Console, click **Data Integration** from the left navigation tree, and click the **+** icon to create a data integration task.

2. In the **New Data Integration Task** window, complete the basic settings for the task.

   - Mode: Select **Create** to create a task from scratch.
   - Name: Enter the name of the data integration task.
   - Sync Type: Select **Data synchronization**.
   - Scheduling Type: Select **Manual scheduling**, which indicates that the data integration task needs to be started manually.
   - Description: Provide descriptive information about the data integration task.
   - Select Directory: Select the directory to save the task configuration.

3. Click **OK** to create the data integration task. See the following screen capture:

   .. image:: media/create_data_sync_task.png

## Step 2: Select the data source

Complete the following settings for the Hive data source:

1. From the **Data Source Type** drop-down list, select **HIVE**.

2. From the **Source Table** drop-down list, select the **employee** Hive table that has been created in [Tutorial - Integrating External Data Sources](/docs/offline-data/en/2.0.9/tutorial/integrating_external_data_sources/creating_hive_table.html), which also has the employee data synchronized from external data source.

   .. image:: media/selecting_source.png

3. (Optional) Click **Data Preview** to preview the data to be synchronized, as shown in the following figure:

   .. image:: media/data_preview.png

4. Click **Next**.


## Step 3: Select the target table

Complete the following settings for the target Report Database table.
1. From the **Data Source Type** drop-down list, select **REPORTDB**.

2. From the **Table Name** drop-down list, select the **report** table that is created in [Unit 1](creating_reportdb_table).

3. For **Data Writing Rule**, specify whether to overwrite the existing data in the target table, or append the data behind the existing data records.

4. Click **Next**. See the following screen capture:

   .. image:: media/selecting_target.png

## Step 4: Configure field mapping between source and target

When both the data source and target table are selected, map the source fields to the target fields. In this way, data in the Hive table will be synchronized to specified fields in the Report Database table.

1. For each field in the **Target Field** column, click a source field from the **Source Field** column to map the source fields with the target fields.

   .. image:: media/mapping_data.png


2. When you finish mapping each field, click **Next**.

## Step 5: Configure concurrency

Select the number of concurrent connections to establish and click **Next**.

In this tutorial, select 1 connection.


## Step 6: Review and save the task configuration

1. Preview the settings of the data integration task, and click the **Edit** button to make changes if needed.

2. Click **Done** to complete the data synchronization configuration.

3. Click **Save** on configuration panel to save the data integration task.

   .. image:: media/saving_task.png

## Step 7: Run the data integration task

1. Open the created data integration task in the above step.

2. Click **Pre-run** on the configuration panel.

   .. image:: media/pre-run_task.png

3. Specify a triggering time and click **OK** to test running the data integration task.

4. A workflow instance will be created for the data integration task. Check the running status and result of the task on the **Workflow Operation** page. For more information on monitoring a data integration task, see [Running the Data Integration Task](/docs/offline-data/en/2.0.9/tutorial/integrating_external_data_sources/running_data_integration_task.html).

## Step 8: View the synchronized data

When the data synchronization task runs successfully, view the synchronized data in the Report Database table.

1. In the EnOS Console, click **Data Explorer** from the left navigation panel.

2. In the **Data Explorer** panel, find the **report** note that is created in [Unit 1](creating_reportdb_table), and click the **Enter note** icon |enter_note| to open the notebook.

3. In the notebook, enter the following command to view the synchronized data to the Hive table:

   ```
   select * from report limit 100
   ```

4. Click the **Run this paragraph** icon |run|. You will see the employee data that has been synchronized to the Report Database table. See the following screen capture:

   .. image:: media/synchronized_data.png

## Next Unit

[Creating Datasets](creating_datasets)

.. |enter_note| image:: media/enter_note.png

.. |run| image:: media/run.png

<!--end-->