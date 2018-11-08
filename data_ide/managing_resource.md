# Managing resources

After a resource is created, you can manage the different versions of resource by performs tasks such as updating, deleting, and downloading.

To manage a resource, double-click the resource from the resource directory tree to show the resource information panel.

## Updating a resource

When a resource is updated, the tasks that reference the resource are automatically updated.

To update the generic information such as the resource name and description, click **Edit Resource**.

To update a resource version, click **Update** from the **Operations** column. Upload the new resource bundle, modify the version number and description according to your needs.

## Tracing workflows that reference a resource version

To trace the usage of a resource version, you can view the workflows and task nodes that reference the resource by clicking **Reference** from the **Operations** column.

## Deleting a resource version or entire resource

You can delete a resource version or an entire resource when it is no longer needed.

**Note**: The following rules apply when you delete a resource or a resource version:

- To delete a resource version, ensure that the version of resource is not referenced by any workflow. Otherwise, the current resource version cannot be deleted. To determine which workflow or task node is referencing the resource version, click **Reference** from the **Operations** column.

- To delete an entire resource, you must first delete all versions under the resource. Otherwise, you cannot delete the entire resource.

To delete a resource version, click **Delete** from the **Operations** column.

To delete an entire resource, right-click the resource from the directory tree and click **Delete** from the menu.


## Downloading a resource version

You may want to download a resource file for secondary development. To download a resource file to your local system, click the file name from the **Resource File** column.
