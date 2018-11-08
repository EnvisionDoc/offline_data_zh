# Data integration overview

The data integration function supports synchronizing data between extensive heterogeneous data sources.

The major use case of data integration is to help data developers synchronize structured data from source databases to the Hive Library in EnOS.

A data integration workflow is specific type of workflow. The essence of a data integration workflow is a workflow with a single data-integration type of task.

The data integration function only supports synchronization of structured data, that is data which can be abstracted as two-dimensional tables.

Unstructured data such as MP3 is not supported by data integration. However, you can schedule SHELL-type of tasks in a workflow to synchronize the unstructured data. For information about unstructured data synchronization, see [Data IDE](../data_ide/dataide_overview).
