# Tutorial Overview

## Scenario

In this tutorial, synchronize data from an external MySQL database (with some employee information) to EnOS Hive periodically, so that the employee data can be further processed and analyzed with data analytics tools provided by EnOS.

The scenario is depicted in the following chart:

.. image:: media/integrating_external_data.png

This tutorial walks you through a typical path of integrating external data sources into EnOS, which is:

- Configuring data connection for the external data source
- Creating a target Hive table to receive the synchronized data
- Creating a data integration task with periodic scheduling
- Running the data integration task
- Viewing the synchronized data in the hive table

### [Start >](configuring_data_connection)

## Prerequisites

You have data stored in an external MySQL database, which is ready to be integrated into EnOS Hive table.

## Units

This tutorial includes the following units:

> [Unit 1. Configuring Source Data Connection](configuring_data_connection)
>
> 10 minutes

> [Unit 2. Creating a Target Hive Table](creating_hive_table)
>
> 20 minutes

> [Unit 3. Creating a Data Integration Task](creating_data_integration_task)
>
> 20 minutes

> [Unit 4. Running the Data Integration Task](running_data_integration_task)
>
> 20 minutes

> [Unit 5. Viewing the Synchronized Data](viewing_synchronized_data)
>
> 5 minutes
