# Creating by importing an existing configuration

If you have existing workflow configuration that you want to reuse for the new data integration workflow, import the configuration file.

## Before you begin

You must have a workflow configuration file stored locally. For information about how to export an existing workflow as a configuration file, see [Exporting a workflow](../data_ide/operating_workflow#exporting-a-workflow).

## Procedure

1. Click **Data Integration** from the left navigation tree and click **New Data Integration Workflow**.
2. In the **New Data Integration Workflow** window, provide the following settings.
   - Mode: select **Import from existing**.
   - Upload File: In your local file system, browse to and select the configuration file.
   - Name: Enter the name of workflow.
   - Type: Select whether to create a periodic workflow that is run automatically based on scheduling parameters, or a one-time workflow that is run only when manually triggered.
   - Description: Provide descriptive information about the workflow.
   - Select Directory: Select the directy to save the workflow.

3. Click **OK**.
4. Edit the settings that are loaded from the configuration file.
  - If you selected to create a periodic workflow in step 2, see [Creating a periodic synchronization workflow from scratch](creating_scratch_periodic).
  - If you selected to create a one-time workflow in step 2, see [Creating a one-time synchronization workflow from scratch](creating_scratch_onetime).

## What to do next

Click **Pre-run** to trigger the workflow.

After a workflow is run, an instance is generated. You can then trace the details about the instance through the task monitor. For more information, see [Task monitor](../task_monitor/index).

After the data is synchronized from the data source, you can schedule other processing tasks against the data. For more information, see [Data IDE](../data_ide/dataide_overview).
