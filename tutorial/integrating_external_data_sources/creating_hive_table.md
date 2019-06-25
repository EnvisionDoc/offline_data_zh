# Unit 2. Creating a Target Hive Table

Before synchronizing data from external data sources, you need to create a target Hive table. In this unit, create a Hive table named *employee* with the required columns defined.

1. In the EnOS Console, click **Data Explorer** from the left navigation panel.

2. On the **Data Explorer** page, click the **New Note** button.

3. In the **Name** field, enter `Demo/employee` as the name of the note, which means that a hive table with the name `employee` is created under the `Demo/` directory.

4. In the **Type** drop-down list, select **hive** as the note type.

5. Click **OK** to save the note.

   .. image:: media/new_note.png

6. Click the **Enter note** icon |Enter_note| from the **Operation** column of the created note to open the notebook.

7. In the notebook, enter the following script for creating the Hive table:

   ```
   %hive
   use db_demomanager;
   create table employee (serial_id int, birthday date, first_name string, last_name string, gender string, onboard_date date);
   comment 'table for employee info';
   ```

   .. note:: In this example, *db_demomanager* is the database name of the organization. You will need to replace it with that of your own organization. The fields *serial_id*, *birthday*, *first_name*, *last_name*, *gender*, and *onboard_date* are the column headers of the created Hive table. Ensure that the data type of the fields matches with that of the fields in the source data.

8. Click the **Run this paragraph** icon |Run_this_paragraph|. You will see the Hive table named *employee* created successfully, as shown in the following screen capture:

   .. image:: media/created_hive.png

9. Run the following query script to test the result:

   ```
   %hive
   select * from employee limit 100
   ```

   The columns of the Hive table will be displayed, as shown in the following screen capture:

   .. image:: media/query_result.png

## Next Unit

[Creating a Data Integration Task](creating_data_integration_task)

.. |Enter_note| image:: media/enter_note.png

.. |Run_this_paragraph| image:: media/run.png

<!--end-->
