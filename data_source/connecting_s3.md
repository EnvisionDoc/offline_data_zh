# Configuring an Amazon S3 data source

This topic instructs how to configure the connection to an Amazon S3  data source.


## About this task
To retrieve data from an external Amazon S3 database for analysis, Create a data source configuration that specifies the cloud region where the database sits in AWS, the credentials to use to access the S3 database, and other information about the data source.

## Procedure

1. In the EnOS Console, click **Data Source** from the left navigation panel.

2. In the **Data Source** panel, click **Add Data Source**.

3. In the **Data Source** window, provide the following settings:

   - **Data source name**:  the name of the data source. The name can be a combination of the following characters:
     - Chinese characters
     - a through z
     - A through Z
     - 0 through 9
     - _ (underscore)  
     The maximum length of the data source name is 50 characters.
   - **Data source type**: S3
   - **Region**: the cloud region of the S3 database.
   - **Access key ID**: the access key ID of the S3 database.
   - **Secret access key**: the access key to use to sign the requests sent to the S3 database.
   - **Data source description**: a description of the data source.

4. Click **OK** to save the configuration.


## Results

After the connection is created, the data source item is shown in the **Data Source** table.

## What to do next

When the connection is successfully established, EnOS retrieves the data from the external data source to the EnOS internal Hive database. You must create the Hive table to store the retrived data. For more information, see [Creating Hive table](https://docs.envisioniot.com/docs/analysis-report/en/latest/data_explorer/creating_hivetable.html) in *Data Analysis and Report*.

You can then configure a data integration workflow to synchronize data from the data source to the target table in EnOS. For more information, see [Data Integration](../data_integration/index).
