# Module 1: Creating a Hive table and creating workflows

## Step 1: Creating new Hive tables with Data Explorer

This task aims to create the hive forms used to store the data of the meters and sites, as described below:

1. Cick **Data Explorer** from the left navigation tree of EnOS Console, and create a Hive type of note as shown in the following figure:

   .. image:: media/module_6_Create_a_new_worksheet_in_the_Data_Explorer.png
      :alt: Fig. Create a new worksheet in the Data Explorer

2. Enter the note that you created in step 1 and create the `dw_meter_1h` table.

   - The scripts for constructing the new table are as shown in the following example.

   .. note:: Please change the name *dw_meter_1h_demo* to your own table name.

   ```
   %hive
   CREATE TABLE <table_name>(
      device_id string,
      site_id string,
      ts timestamp,
      hour int,
      energy double,
      max_power double)
   PARTITIONED BY (
      yyyymmdd string)
   ROW FORMAT DELIMITED
      FIELDS TERMINATED BY '\t'
   STORED AS ORC
   ```

   After you create the table, you can make a query to the table and make sure the results are successful returned as shown in the figure below:

   .. image:: media/module_6_queries_successful.png

   The following table shows an example query result:

   .. list-table::
      :widths: auto

      * - device_id
        - site_id
        - ts
        - hour
        - energy
        - max_power
        - yyyymmdd
      * - 1c7cd59561002000
        - 1c7cd5955e000000
        - 2018-08-10 00:00:00.0
        - 0
        - 75.8
        - 81
        - 20180810


3. CREATE the `dw_site_1h` table.

   - The scripts for creating the table are shown in the following example.

   .. note:: If this table name is used, please change the name `dw_meter_1h_demo`，which shall be different from that of the example:

   ```
   DROP TABLE IF EXISTS dw_site_1h_demo;
   CREATE TABLE dw_site_1h_demo(
      site_id string,
      ts timestamp,
      hour int,
      energy double,
      max_power double)
   PARTITIONED BY (
      yyyymmdd string)
   ROW FORMAT DELIMITED
      FIELDS TERMINATED BY '\t'
   STORED AS ORC
   ```

   The following table shows an example query result:

   .. list-table::
      :widths: auto

      * - site_id
        - ts
        - hour
        - energy
        - max_power
        - yyyymmdd
      * - 1c7cd5955e000000
        - 2018-08-10 00:00:00.0
        - 0
        - 638.23
        - 678
        - 20180810

## Step 2: Synchronizing the master data and creating table with Task Designer

The task aims to synchronize the master data of the meters to the hive table that you created in Step 1 and create a corresponding hive table so as to obtain the descriptions of the electrical meters, as described below:

1. Click **Data IDE > Task Designer**, double click **SYNC_MDM** version **V0.1.2**. The Instructions of the SDK are shown as in the following figure:

   .. image:: media/module_6_Instructions_on_the_SDK_for_Main_Data_Synchronization.png
      :alt: Fig. Instructions on the SDK for master data Synchronization

2. Review the instructions and click **Use this program**, enter the name of your task (change the suffix "demo" to your own task name, ensure that the name is not identical with other tasks), select **/Workflow/Practice**, as described below:

   .. image:: media/module_6_select_WorkflowPractice.png

3. The task parameters are configured as described below:

   .. image:: media/module_6_job_parameters.png

    The parameters are as follows:

   ```
   mdmID=<ou_objectID>
   path=/user/db_<owner_name>
   domain=<domain_ID>
   overwrite=true
   ```

   - `ou_objectID` indicates the object ID of the organization unit. You can find the value through clicking **Asset Management > Data Preview** and locating the **objectID** of the organization.
   - `owner_name` indicates the owner name of the current organization.
   - `domain_ID` indicates the ID of domain that you are accesssing data from. You can find this value through clicking **Model Center > Device Models** and locating the `ID` value beside the domain name.
   - `overwrite`: set it to `true` for this training.

4. Click **Release** to publish the workflow and click **Pre-run** to synchronize the master data.

## Synchronize the form structures with Task Designer

The task aims to synchronize the form structures in the hive automatically to the
relational databases for reports using the sdk on the platform for the purpose
of creating new forms, which may avoid creating new forms by writing SQL
statements on your own.

The forms required to be synchronized to the report databases include:

- dw_meter_1h (data sheets for the electrical meters);
- dw_site_1h ( Site data sheets);
- icat_c6_meter (master data sheets for the electrical meters);
- icat_c6_site (Site master data sheets);

.. note:: You'll need to replace the database names with your own.

1. Enter **Data IDE > Task Designer**, double click "SYNC_REPORT_STRUCTURE" V0.1.1, where the roles and application of the SDK are detailed, as described below:

   .. image:: media/module_6_Synchronization_of_report_database_structures.png
      :alt: Fig. Synchronization of report database structures

2. Click **Use this program**, input the name of your program (the suffix "demo" may be changed to your program name, which shall not be identical with that of other programs), select **/Workflow/Practice**, as described below:

   .. image:: media/module_6_select_WorkflowPracticeapplymethod.png

3. Configure the parameters

   .. image:: media/module_6_confi_gramm.png

   The parameters are as follows:

   tablename= dw_meter_1h_demo

   .. note:: Please do fill in your form name here.

   In this example, synchronization of 4 forms are required, one form each time:

   - `dw_meter_1h_demo` ( Data sheets for the electrical meters)
   - `dw_site_1h_demo` (Site data sheets)
   - `icat_c6_meter` (master data sheets for the electrical meters)
   - `icat_c6_site` (Site master data sheets)

4. Publish and pre-run the task.

   Please do repeat the above-mentioned operations and synchronize all the form structures required.

## Adding primary keys for the report databases with Data Explorer

This task aims to add the primary keys for the report databases to avoid repeated
records arising from regular synchronization.

1. Enter the **Data Explorer** module, create a worksheet of mysql_report type, as described below:

   .. image:: media/module_6_Creating_a_new_mysql_report_type_worksheet.png
      :alt: Fig. Creating a new mysql_report type worksheet

2. The primary keys are added to the 4 forms respectively, among which:

   - device_id and ts are used as the primary keys for the form dw_meter_1h_demo;

   - site_id and ts are used as the primary keys for the form dw_site_1h_demo;

   - \_objectid is used as the primary key for the form icat_c6_meter_demo;

   - \_objectid is used as the primary key for the form icat_c6_site_demo;

   Take the primary key codes for the form dw_meter_1h_demo as an example described below:

   ```
   ALTER TABLE dw_meter_1h_demo ADD PRIMARY KEY (device_id,ts)
   ```

   Upon completion, view the descriptions of the form for confirmation, the code example of which are described as follows:

   ```
   desc dw_meter_1h_demo
   ```

   .. image:: media/module_6_Adding_main_keys_to_the_form_dw_meter_1h_demo.png
      :alt: Fig. Adding primary keys to the form dw_meter_1h_demo


<!--end-->
