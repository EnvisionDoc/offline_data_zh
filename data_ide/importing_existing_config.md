# Creating by importing an existing configuration

If you have existing workflow configuration that you want to reuse for the new workflow, import the configuration file.

## Before you begin

You must have a workflow configuration file stored locally. For information about how to export an existing workflow as a configuration file, see [Exporting a workflow](operating_workflow#exporting-a-workflow).

## Procedure

1. Click **+** from above the directory tree.
2. In the **New Workflow** window, provide the following settings and click **OK**.
   - Mode: select **Import from existing**.   
   - Name: Enter the name of workflow.
   - Upload File: In your local file system, browse to and select the configuration file.
   - Description: Provide a descriptive information about the workflow.
   - Select Directory: Select the directy to save the workflow.

3. Click **OK**.
4. Edit the settings that are loaded from the configuration file.
  - If the imported configure file defines a periodic workflow, see [Creating a periodic workflow from scratch](creating_workflow_periodic).
  - If the imported configure file defines a one-time workflow, see [Creating a manual workflow from scratch](creating_workflow_onetime).

## What to do next

Pre-run the workflow to test the result of your configuration.
