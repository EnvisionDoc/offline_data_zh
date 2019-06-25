# Unit 1. Configuring Source Data Connection

The first step of synchronizing data to EnOS Hive is to register the external data sources in EnOS by configuring a data connection.

In this unit, configure the connection to the MySQL server that hosts the employee data to be synchronized to EnOS Hive.

1. In the EnOS Console, click **Data Connection** from the left navigation panel.

2. On the **Data Connection** page, click the **Add Data Source** button.

3. In the **Data Sources** window, provide the following information:

   - **Data source**: Enter a name for the data source.
   - **Data source type**: Select **MYSQL** from the drop-down list.
   - **Host Name or IP Address**: Enter the host name or IP address of the MySQL server.
   - **Database Name**: Enter the name that uniquely identifies to the database to be connected.
   - **Port**: Enter the port of the MySQL server.
   - **Username**: Enter the user name for accessing the database.
   - **Password**: Enter the password of the user name.
   - **Data Source Description**: Enter a short description of the data connection.

4. Click **OK** to save the configuration. See the following data connection sample:

   .. image:: media/data_connection.png

After the data connection is created, the data connection item is shown in the **Data Connection** table.

## Next Unit

[Creating a Target Hive Table](creating_hive_table)
