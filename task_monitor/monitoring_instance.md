# Monitoring workflow instances

For a worflow instance, you can perform the following monitoring actions:

- Viewing details and logs of the instance
- Re-running the instance
- Stopping the instance


## Viewing details and logs of the instance

To view an instance of a manual or periodic workflow, do the following steps:

1. From the navigation panel, click **Task Monitor** > **Manual Instance** or **Task Monitor** > **Periodic Instance**. A table of all instances that are generated in the last 24 hours are shown.
2. (Optional) In the search field above the table, enter the instance ID or name to filter the result shown in the table.
3. Click the name of the instance that you want to inspect details for from the table. A workflow panel is shown.
4. For each task node in the workflow, you can double-click the task node to view the following details:
  - Attributes: settings of the task that is defined at the design time
  - Scheduling Log: the log of the instance, and you can download the log for analysis.
  - Task contents: what's run in the task. What's shown in the Task Contents tab varies according to the task type.

## Re-running an instance

When the status of the instance is **success**, **failed**, **canceled** or **skipped**, it can be re-run. In this case, the current task flow instance and its downstream nodes are re-run.

## Stopping an instance

When the status of the instance is **initializing**, **running** or **failed**. you can click **Stop Running** to immediately stop running the current instance. However, instances already submitted for batch data processing can not be stopped.

As long as one node fails to run in a workflow instance, the status of the entire workflow instance fails. However, the workflow instance might not have been completed. In this case, you can stop it manually.
