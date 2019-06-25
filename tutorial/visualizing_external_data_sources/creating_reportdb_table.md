# Unit 1. Creating a Target Table in Report Database

The first step of processing and visualizing data is to create a target table in the EnOS Report Database. In this unit, create a table named *report* with the required columns defined.

1. In the EnOS Console, click **Data Explorer** from the left navigation panel.

2. On the **Data Explorer** page, click the **New Note** button to create a note or create a note under an existing file.

3. In the **Name** field, enter `Demo/report` as the name of the note, which means that a MySQL table with the name `report` is created under the `Demo/` directory.

4. In the **Type** drop-down list, select **mysql_report** as the note type.

5. Click **OK** to save the note.

   .. image:: media/new_note.png

6. Click the **Enter note** icon |Enter_note| from the **Operation** column of the created note to open the notebook.

7. In the notebook, enter the following script for creating the Report Database table:

   ```
   CREATE TABLE `report` (
   `serial_id` int(11) NOT NULL,
   `birthday` date NOT NULL,
   `first_name` varchar(14) NOT NULL,
   `last_name` varchar(16) NOT NULL,
   `gender` enum('M','F') NOT NULL,
   `onboard_date` date NOT NULL,
   PRIMARY KEY (`serial_id`)
   )
   ```

   .. note:: In this example, the fields *serial_id*, *birthday*, *first_name*, *last_name*, *gender*, and *onboard_date* are the column headers of the created table. The data type of the fields must match with that of the Hive table fields.

8. Click the **Run this paragraph** icon |Run_this_paragraph|. You will see the Report Database table named *report* created successfully, as shown in the following screen capture:

   .. image:: media/created_table.png

9. Run the following query script to test the result:

   ```
   select * from report limit 100
   ```

   The columns of the Report Database table will be displayed, as shown in the following screen capture:

   .. image:: media/query_result.png

## Next Unit

[Synchronizing Data to the Report Database](synchronizing_data_to_reportdb) 

.. |Enter_note| image:: media/enter_note.png

.. |Run_this_paragraph| image:: media/run.png

<!--end-->
