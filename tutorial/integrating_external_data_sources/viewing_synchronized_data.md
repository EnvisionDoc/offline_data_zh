# Unit 5. Viewing Synchronized Data

When the data synchronization task runs successfully, view the synchronized data in the Hive table.

1. In the EnOS Console, click **Data Explorer** from the left navigation panel.

2. In the **Data Explorer** panel, find the **employee** note that is created in [Unit 2](creating_hive_table), and click the **Enter note** icon |Enter_note| to open the note.

3. In the note, enter the following command to view the synchronized data to the Hive table:

   ```
   %hive
   select * from employee limit 100
   ```

4. Click the **Run this paragraph** icon |Run_this_paragraph|. You will see the employee data that has been synchronized to the Hive table.

   .. image:: media/synchronized_data.png

## What to Do Next

The synchronized data can be further processed by data analytics tools for analysis and visualization. For more information, see [Data IDE](/docs/offline-data/en/2.0.9/data_ide/index.html) and [Data Report](/docs/analysis-report/en/2.0.9/report_overview.html).

.. |Enter_note| image:: media/enter_note.png

.. |Run_this_paragraph| image:: media/run.png

<!--end-->
