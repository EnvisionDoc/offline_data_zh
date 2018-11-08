## Scenarios

The typical scenarios of data integration are as follows.

### Synchronization of full-load of data

Synchronization of full-load of data usually happens at the initial stage of data integration. In this scenario, you synchronize full-load of data from the data source at one-time. To achieve this scenario, see [Creating a one-time synchronization workflow](creating_scratch_onetime).

### Synchronization of incremental data

Synchronization of incremental data usually happens after the initial stage, when you only want to synchronize the new or updated data periodically. In this scenario, you usually select the incremental data to synchronize through a `where` clause when you configure the synchronization workflow. To achieve this scenario, see [Creating a periodic synchronization workflow](creating_scratch_periodic).
