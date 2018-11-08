# Supported system variables

You can use variables in path and parameter settings, you can also use variables directly in your SHELL script.


## Business-related variables

Before you start to use the service-related variables, note the following key concepts:

**Triggering time**： The time when a workflow is triggered. It can be the time when you manually trigger the workflow, or when the workflow is automatically triggered according to scheduling settings.

**Business date**: The date from which the data starts to be  processed by the workflow. Service date is generated based on the triggering time by deducting one day from the triggering time (because the batch job is performed against the data of yesterday by default). For example, when the triggering time is `2017-05-27 13:50:00`, and the scheduled cycle is one day. Then the business date is `2017-05-26`, meaning the data on `2017-05-26` will be processed at the triggering time of `2017-05-27 13:50:00`. With that said, if you want to process the data of the date 2018-03-01, you must set the triggering time to some time on 2018-03-02.

The following table explains the system variables by using `2017-05-27 13:50:00` as the example triggering time.

<body>
<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td width="113" valign="top"><p align="center"><strong>Variable</strong></p ></td>
    <td width="203" valign="top"><p align="center"><strong>Description</strong></p ></td>
    <td valign="top"><p align="center"><strong>Format</strong></p ></td>
    <td valign="top"><p align="center"><strong>Business Date</strong></p ></td>
    <td valign="top"><p align="center"><strong>Variable Value</strong></p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${last_week8}</p ></td>
    <td width="203" valign="top"><p align="left">- Using   triggering time as the basis, indicates&nbsp;<strong>Last week</strong>。<br>
      - Using business date as the basis, indicates business date minus 6 days.</p ></td>
    <td valign="top"><p align="left">YYYYMMDD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">20170520</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${last_week10}</p ></td>
    <td width="203" valign="top"><p align="left">- Using   triggering time as the basis, indicates&nbsp;<strong>Last week</strong>。<br>
      - Using business date as the basis, indicates business date minus 6 days.</p ></td>
    <td valign="top"><p align="left">YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">2017-05-20</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${cal_dt}</p ></td>
    <td width="203" valign="top"><p align="left">- Using   triggering time as the basis, indicates&nbsp;<strong>yesterday</strong>。<br>
      - Using business date as the basis, indicates today.</p ></td>
    <td valign="top"><p align="left">YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${cal_dt8}</p ></td>
    <td width="203" valign="top"><p align="left">- Using   triggering time as the basis, indicates&nbsp;<strong>yesterday</strong>。<br>
      - Using business date as the basis, indicates today.</p ></td>
    <td valign="top"><p align="left">YYYYMMDD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">20170526</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${ncal_dt}</p ></td>
    <td width="203" valign="top"><p align="left">Using   triggering time as the basis, indicates&nbsp;<strong>today</strong>。<br>
      Using business date as the basis, indicates today+1.<br>
      Format: YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">2017-05-27</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${ncal_dt8}</p ></td>
    <td width="203" valign="top"><p align="left">Using   triggering time as the basis, indicates&nbsp;<strong>today</strong>.<br>
      Using business date as the basis, indicates today+1.<br>
      Format: YYYYMMDD</p ></td>
    <td valign="top"><p align="left">YYYYMMDD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">20170527</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${end_day_this_month8}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>last day of this month.</strong></p ></td>
    <td valign="top"><p align="left">YYYYMMDD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">20170531</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${end_day_this_month10}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>last day of this month.</strong></p ></td>
    <td valign="top"><p align="left">YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">2017-05-31</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${first_day_this_month8}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>first day of this month</strong>。 </p ></td>
    <td valign="top"><p align="left">YYYYMMDD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">20170501</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${first_day_this_month10}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>first day of this month</strong>。 </p ></td>
    <td valign="top"><p align="left">YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">2017-05-01</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${first_day_last_month8}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>first day of last month</strong>。 </p ></td>
    <td valign="top"><p align="left">YYYYMMDD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">20170401</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${first_day_last_month10}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>first day of last month</strong>。 </p ></td>
    <td valign="top"><p align="left">YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">2017-04-01</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${last_day_last_month8}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>last day of last month</strong>。 </p ></td>
    <td valign="top"><p align="left">YYYYMMDD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">2017-04-30</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${last_day_last_month10}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>last day of last month</strong>。 </p ></td>
    <td valign="top"><p align="left">YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">201704-30</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${monday_next_week8}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>next Monday</strong>。 </p ></td>
    <td valign="top"><p align="left">YYYYMMDD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">20170529</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${monday_next_week10}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>next Monday</strong>。 </p ></td>
    <td valign="top"><p align="left">Format:   YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">2017-05-29</p ></td>
  </tr>
  <tr>
    <td width="113" valign="top"><p align="left">${30days_cal_dt}</p ></td>
    <td width="203" valign="top"><p align="left">Using business   date as the basis, indicates&nbsp;<strong>30 days ago</strong>。 </p ></td>
    <td valign="top"><p align="left">Format:   YYYY-MM-DD</p ></td>
    <td valign="top"><p align="left">2017-05-26</p ></td>
    <td valign="top"><p align="left">2017-0</p ></td>
  </tr>
</table>
</body>


## Time related variables

The following table explains the time-related variables by using `2017-05-27 13:50:00` as the example triggering time.

<body>
<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top"><p align="center"><strong>Variable</strong></p ></td>
    <td valign="top"><p align="center"><strong>Description</strong></p ></td>
    <td valign="top"><p align="center"><strong>Value</strong></p ></td>
  </tr>
  <tr>
    <td valign="top"><p>${this_hour}</p ></td>
    <td valign="top"><p>The hour when the workflow is triggered</p ></td>
    <td valign="top"><p>2017-05-27 13:00:00</p ></td>
  </tr>
  <tr>
    <td valign="top"><p>${unix_timestamp}</p ></td>
    <td valign="top"><p>Unix time corresponding to the triggering   time</p ></td>
    <td valign="top"><p>1495864241</p ></td>
  </tr>
</table>
</body>

## Non-time related variables

<body>
<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top"><p align="center"><strong>Variable</strong></p ></td>
    <td valign="top"><p align="center"><strong>Description</strong></p ></td>
    <td valign="top"><p align="center"><strong>Example</strong></p ></td>
  </tr>
  <tr>
    <td valign="top"><p>${task_id}</p ></td>
    <td valign="top"><p>Task ID of the current instance</p ></td>
    <td valign="top"><p>2017-05-27 13:00:00</p ></td>
  </tr>
  <tr>
    <td valign="top"><p>${instance_id}</p ></td>
    <td valign="top"><p>Current instance ID</p ></td>
    <td valign="top"><p>1495864241</p ></td>
  </tr>
  <tr>
    <td valign="top"><p>${env.APP_CUSTOMER}</p ></td>
    <td valign="top"><p>The group account who generated the   instance</p ></td>
    <td valign="top"><p>CLP</p ></td>
  </tr>
  <tr>
    <td valign="top"><p>${env.APP_ID}</p ></td>
    <td valign="top"><p>The App ID that the instance belongs to</p ></td>
    <td valign="top"><p>a22b94f9-3b9d-40f6-9bd8-4d66b304d930</p ></td>
  </tr>
</table>
</body>
