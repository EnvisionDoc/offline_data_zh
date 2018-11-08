# Creating a resource

How to crate a resource and add new versions of the resource.

## Procedure

The procedure to create a resource is as follows:

1. Click **Data IDE > Resource Management** from the left navigation tree and click **Create Resource**.
2. In the **Create Resource** window, provide the basic settings about the resource.
   - Name: Enter the name of resource.
   - Description: Provide a descriptive information about the resource.
   - Select Directory: Select the directy to save the resource.
3. Click **OK**.
4. In the resource details panel, click **New Version** to add a version of resource.
   - Upload: From your local file system, browse to and select the script file.
   - Version: Specify the version of resource in the format of
      ```
      v<version_number>.<release_number>.<modifier_number>
      ```
      For example, v1.0.0.
   - Description: Provide a descriptive information about the version.
5. Click **OK**.  
6. Repeart Step 4 to 5 to add more versions for the resource.

## What to do next

You can then invoke the scripts packaged in the resource through a SHELL-type of task in a workflow.

## Reference information

- [Creating a one-time workflow from scratch](creating_workflow_onetime)
- [Creating a periodic workflow from scratch](creating_workflow_periodic)
