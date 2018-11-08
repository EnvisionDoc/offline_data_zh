# Creating a periodic workflow from scratch

How to create a periodic workflow that is run automatically based on the scheduling parameters.

## Before you begin

Ensure that you've registered the codes and scripts to run against the data as resources. For more information, see [Creating a resource](creating_resource).

**Note**: A periodic workflow cannot be changed to one-time workflow after creation.

## Step 1: Create a workflow
1. Click **+** from above the directory tree.
2. In the **New Workflow** window, provide the following settings and click **OK**.
   - Mode: choose whether to create a workflow from scratch or by importing a configuration file.
   - Name: Enter the name of workflow.
   - Type: Select **Periodic**.
   - Select Dir: select the directory to store the workflow.

## Step 2: (Optional) Add references
If the workflow is dependent on another workflow or task, add a reference as the root node.
- To reference a workflow, drag the **Workflow Premise** type of reference into the workflow panel, select the workflow, and click **OK**.
- To reference a task, drag the **Task Premise** type of reference into the workflow panel, select the task, and click **OK**.
Repeat if the workflow depends on multiple references.

## Step 3: Add task nodes
1. From the **Component** panel, drag the **SHELL** type of task node into the workflow panel.
2. In the **New Task Node** window, enter the name and optionally a description of the task. Note that task is unique within the same workflow.
3. Click **Create**.
4. Double click the node that you just created.
5. Enter the command to run, select the resource, and the resource version.
6. Click **Node Scheduling Settings** from the right edge of the configuration panel and provide the scheduling settings:
   - The exact time to run the task in the 7-character CronTab syntax. For example, the value `59 59 23 * * ? *` indicates that the task is to run at 23:59:59 every day. For more information about CronTab, see [http://cron.qqe2.com/](http://cron.qqe2.com/).
   - The timeout value.
   - The number of reconnection attempts to try after timeout.
   -The interval between each reconnection attempt.
   - Specify whether this task can be referenced by another workflow.

7. When parameters are used in the task, click **Parameter Settings** from the right edge to specify parameter values. You can specify constants, system variables, or custom variables for a parameter. For more information, see [Setting parameters](setting_parameters).
8. Click **Save** and click **Back to Workflow Panel**.

Repeat 1 to 8 to add more task nodes as you need.
## Step 4: Add relations
**Note**: References must always be the root node.

1. Click **Relation**.
2. Click the upstream task and an arrowhead is shown, drag the arrowhead and drop at the downstream task.
3. Repeat 1 to 2 till you finish connecting all nodes according to your design.

## Step 5: Configure scheduling settings
1. Click **Scheduling Settings** from the right edge of the configuration panel.
2. Provide the basic settings:
   - **Owner**: Select the workflow owner from the list of users in the organization who have access to data integration. It is the workflow creator by default. As the creator, you cannot delete yourself. You can add othher owners, however, in the same organization.
   - **Description**: (Optional) Provide a description.
   - **Alert Mode**: Select how to alert the workflow owner. Email is always selected.
      - E-mail: an alert e-mail is sent to the owner when an instance meets the alert conditions. When the task fails, a copy of the alert is also sent to the affected downstream task owner, if there is.
      - SMS: A phone number must be verified during user registration for use of SMS alert. The SMS alert is sent to only the owner when an instance meets the alert conditions.

3. Provide the scheduling settings:
   - Specify when the workflow starts to take effect.
   - Specify the scheduling cycle, that is, how frequent to run the workflow. For example, you can specify to run the workflow on a daily basis.
   - Based the cycle you select, specify the exact time in a cycle to run the workflow. For example, you can specify to run the workflow at 9:00 am everyday.
   - Specify the timeout value.
   - Specify the number of reconnection attempts to try after timeout.
   - Specify the internal between each reconnection attempt.
   - Specify whether this workflow can be referenced by another workflow.

## Step 6: Specify parameters

When parameters are used when you configure the data source and target, specify parameter values. For more information, see [Setting parameters](setting_parameters).

## What to do next

Click **Pre-run** to test the result of the workflow.

After a workflow is run, an instance is generated. You can then trace the details about the instance through the task monitor. For more information, see [Monitoring periodic workflows](../task_monitor/monitoring_workflow_periodic).

After the data is synchronized from the data source, you can schedule other processing tasks against the data. For more information, see [Data IDE](../data_ide/dataide_overview).
