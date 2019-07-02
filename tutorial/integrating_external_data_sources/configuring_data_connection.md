# Unit 1. Configuring Source Data Connection

The first step of synchronizing data to EnOS Hive is to register the external data sources in EnOS by configuring a data connection.

In this unit, configure the connection to the MySQL server that hosts the employee data to be synchronized to EnOS Hive.

1. In the EnOS Console, click **Data Connection** from the left navigation panel.

2. On the **Data Connection** page, click the **Add Data Source** button.

3. In the **Data Sources** window, provide the following information:

   - **Data Source**: Name of the data source.
   - **Data Source Type**: Select **MYSQL** from the drop-down list.
   - **Host Name or IP Address**: Host name or IP address of the MySQL server.
   - **Database Name**: Enter a unique name for the database to be connected.
   - **Port**: Port of the MySQL server.
   - **Username**: User name for accessing the database.
   - **Password**: Password of the user name.
   - **Data Source Description**: Short description of the data connection.

4. Click **OK** to save the configuration. See the following data connection sample:

   .. image:: media/data_connection.png

After the data connection is created, the data connection item is shown in the **Data Connection** table.

## Next Unit

[Creating a Target Hive Table](creating_hive_table)
