# Module 2: Develop periodical workflows with Task Designer

The module aims to develop the tasks performed on daily basis, i.e., daily
synchronization of the master data to the report databases, periodically fetching
data from the original point record forms to generate the data required for
business goals and synchronizing them to the report databases.

.. image:: media/module_7_Cyclical_Workflows.png
   :alt: Fig. periodical Workflows


## Before you start

Create `mdm_sync` and `mdm_hive` resources that will be used in this learning module.

## Step 1: Creating the mdm_sync task

The job aims to synchronize the master data periodically, as described below:

### Creating a periodical workflow

Enter **Data IDE > Task Designer** and create a new workflow,
as described below: ( Please change to the job name of your own when performing
the experiment):

.. image:: media/module_7_Creating_cyclical_jobs.png
   :alt: Fig. Creating periodical jobs

### Creating and configuring the shell nodes

Creating a shell node:

.. image:: media/module_7_shell_node.png

Double click the shell node and configure it. Make sure to save the changes. See
below:

.. image:: media/module_7_shellsave.png

- **Command**:

  `sh run.sh --mdmID=${mdmID} --path=${path} --domain=${domain}`

- **Resources**: `mdm_sync`
- **ResourceVersion**: *V1.0.0*

After saving the configuration, return to the workflow panel, click **Publish** and save all the configurations made.

## Step 2: Creating the mdm_hive task

The task aims to create hive forms and store the synchronized master data, as
described below:

.. image:: media/module_7_Creating_a_shell_node.png
   :alt: Fig. Creating a shell node

.. image:: media/module_7_Configuring_the_shell_node.png
   :alt: Fig. Configuring the shell node

- **Command**: `sh run.sh --overwrite=${overwrite} --path=${path}`
- **Resources**：mdm_hive
- **ResourceVersion**：V1.0.0

After saving the configuration, return to the workflow panel, click **Publish** and save all the configurations made.

## Step 3: Creating meter_1h_demo tasks

The job aims to acquire the data at the hours from periodically from the
pointrecords forms, as described below:

### Writing the shell scripts

Write the shell scripts for achieve the business logics, so as to realize the
following functions:

Processing the meter data of the previous day in the pointrecords table,
calculating the active power (energy) and the maximum active power (max_power)
at the hours, and taking out the corresponding device_id, timestamp and other
fields.

An example of the scripts are shown here, the name of which shall be changed when it is being used:

```
    queue="root.default"
    while getopts:s:e:q:h OPTION
      do

    case $OPTION in

    s)start_date=$OPTARG;;

    e)end_date=$OPTARG;;

    q)queue=$OPTARG;;

    h)echo "sh dw_meter_1m_demo.sh -s <yyyymmdd notnull> -e <yyyymmdd notnull> -q <queue root.default>"&&exit 0;;

      esac

        done

    while [[ $start_date -le $end_date ]]

    do

    next_date=`date -d "+1 day $start_date" +%Y%m%d`

    prev_date=`date -d "-1 day $start_date" +%Y%m%d`

    sql="set mapreduce.job.queuename=$queue;

    insert overwrite table dw_meter_1h_demo partition(yyyymmdd=$start_date)

    select device_id, site_id, floor(time/3600000)*3600000 as ts, (cast(hh as int)+8)%24 as hour,

    max(case when point='EMT.Wp' then value end) - min(case when point='EMT.Wp' then value end) as energy,

    max(case when point='EMT.P' then value end) as max_power from pointrecords

    where (yyyymmdd=$prev_date and hh >= '16') or (yyyymmdd=$start_date and hh < '16') group by device_id, site_id, floor(time/3600000)*3600000, hh"

    echo "$sql" > tmp_hql

    dwexec -f tmp_hql

    if [ $? -ne 0 ];then

    echo "----------execute sql failed!!!--------------"

    exit 1

    fi

    start_date=$next_date

    done

    echo "execute task successfully"
```


.. image:: media/module_7_execute_task_successfully.png

### Creating a new resource to upload the shell scripts

Enter **Data IDE> Resource Manager**, create a new resource and
upload the shell scripts:

.. image:: media/module_7_Create_the_resource_dw_meter_1h_demo.png
   :alt: Fig. Create the resource dw_meter_1h_demo

.. image:: media/module_7_Upload_the_shell_scripts_of_dw_meter_1h_demo.png
   :alt: Fig. Upload the shell scripts of dw_meter_1h_demo

.. image:: media/module_7_Shell_scripts_uploaded_successfully.png
   :alt: Fig. Shell scripts uploaded successfully

### Creating a shell node and linking it to the resources

Enter **Data IDE**> **Task Designer**, create a shell node and configure it:

.. image:: media/module_7_Creating_a_shell_node_2.png
   :alt: Fig. Creating a shell node

.. image:: media/module_7_Related_resources.png
   :alt: Fig. Related resources

- **Command**: `sh dw_meter_1h_demo.sh -s ${start_date} -e ${end_date} -q ${queue}`
- **Resources**: `dw_meter_1h_demo`
- **ResourceVersion**: *V1.0.0*

After saving the configuration, return to the workflow panel, click **Publish** and save all the configurations made.

## Step 4: Create the synchronization job for meter_1h_demo reports

The job aims to synchronize the dw_meter_1h_demo form in the hive to the report
relational databases, as described below:

### Creating a shell node

.. image:: media/module_7_syn_meter_1h_demo.png

### Configure the shell node

.. image:: media/module_7_meter_1h_hive2.png

- **Command**:

  ```
    wormhole HiveDB2ReportDB.xml -E SOURCE_TBALE=dw_meter_1h_demo -E TARGET_TBALE=dw_meter_1h_demo -E SOURCE_QUEUE=${queue} -E START_DATE=${start_date} -E END_DATE=${end_date}
  ```

- **Resources**: `HiveDB2ReportDB`
- **ResourcesVersion**: *V1.0.1*

After saving the configuration, return to the workflow panel, click **Publish** and save all the configurations made.

## Step 5: Creating new site_1h_demo jobs

The job aims to acquire the site data at the hours from the pointrecords forms periodically, as described below:

### Writing the shell scripts

Write the shell scripts for achieve the business logics, so as to realize the following functions:

Processing the meter data of the previous day in the pointrecords table,
calculating the active power of all the devices at the hours (energy), the sum
of the maximum powers at the hours (max_power), and taking out such fields as
corresponding site_ids and timestamps, etc.

An example of the scripts are shown here, the name of which shall be changed when it is being used:

```
    queue="root.default"

    while getopts:s:e:q:h OPTION

    do

    case $OPTION in

    s)start_date=$OPTARG;;

    e)end_date=$OPTARG;;

    q)queue=$OPTARG;;

    h)echo "sh dw_site_1m_demo.sh -s <yyyymmdd notnull> -e <yyyymmdd notnull> -q <queue root.default>"&&exit 0;;

    esac

    done

    while [[ $start_date -le $end_date ]]

    do

    next_date=`date -d "+1 day $start_date" +%Y%m%d`

    prev_date=`date -d "-1 day $start_date" +%Y%m%d`

    sql="set mapreduce.job.queuename=$queue;

    insert overwrite table dw_site_1h_demo partition(yyyymmdd=$start_date)

    select site_id, floor(time/3600000)*3600000 as ts, (cast(hh as int)+8)%24 as hour,

    max(energy) - min(energy) as energy,

    max(power) as max_power

    from (

    select site_id, time, sum(energy) as energy, sum(power) as power, hh from (

    select device_id, site_id, time, hh,

    max(case when point='EMT.Wp' then value end) as energy,

    max(case when point='EMT.P' then value end) as power

    from pointrecords where (yyyymmdd=$prev_date and hh >= '16') or (yyyymmdd=$start_date and hh < '16') group by site_id, device_id, time, hh

     ) a group by site_id, time, hh ) b group by site_id,
    floor(time/3600000)*3600000, hh"

    echo "$sql" > tmp_hql

    dwexec -f tmp_hql

    if [ $? -ne 0 ];then

    echo "----------execute sql failed!!!--------------"

    exit 1

    fi

    start_date=$next_date

    done

    echo "execute task successfully"
```

.. image:: media/module_7_execute_task_successfully_2.png

### Creating a new resource to upload the shall scripts

.. image:: media/module_7_creating_a_new_source_dw_site_1h_domo.png
   :alt: Fig. Creating a new resource dw_site_1h_demo

.. image:: media/module_7_Uploading_the_shell_scripts_for_dw_site_1h_demo.png
   :alt: Fig. Uploading the shell scripts for dw_site_1h_demo

.. image:: media/module_7_Shell_scripts_uploaded_successfully_2.png
   :alt: Fig. Shell scripts uploaded successfully

### Creating a shell node and linking it to the resources

.. image:: media/module_7_Creating_a_shell_node_3.png
   :alt: Fig. Creating a shell node

.. image:: media/module_7_related_resource_site_1h_demo.png
   :alt: Fig. Related resources

- **Command**: `sh dw_site_1h_demo.sh -s ${start_date} -e ${end_date} -q ${queue}`

- **Resources**: `dw_site_1h_demo`

- **ResourceVersion**: *V1.0.0*

After saving the configuration, return to the workflow panel, click **Publish** and save all the configurations made.

## Step 6: Creating a synchronization job for site_1h_demo reports

The job aims to synchronize the dw_site_1h_demo form in the hive to the report relational databases, as described below:

### Creating a shell node

.. image:: media/module_7_Creating_a_shell_node_3.png

### Configure the shell node

.. image:: media/module_7_Configure_the_shell_node_3.png

- **Command**:

  ```
    wormhole HiveDB2ReportDB.xml -E SOURCE_TBALE=dw_site_1h_demo -E
    TARGET_TBALE=dw_site_1h_demo -E SOURCE_QUEUE=${queue} -E
    START_DATE=${start_date} -E END_DATE=${end_date}
  ```

- **Resources**: `HiveDB2ReportDB`

- **ResourcesVersion**: *V1.0.1*

After saving the configuration, return to the workflow panel, click **Publish** and save all the configurations made.

## Step 7: Creating a synchronization job for icat_c6_meter_demo reports

The job aims to synchronize the meter master data to the report relational databases, as described below:

### Creating a shell node

.. image:: media/module_7_Creating_a_shell_node_4.png

### Configure the shell node

.. image:: media/module_7_synchronization_job_for_icat_c6_meter_demo_reports2.png

- **Command**:

  ```
    wormhole HiveDB2ReportDB.xml -E SOURCE_TBALE=icat_c6_meter_demo -E
    TARGET_TBALE=icat_c6_meter_demo -E SOURCE_QUEUE=${queue}
  ```

- **Resources**: `HiveDB2ReportDB`
- **ResourcesVersion**: *V1.0.1*

After saving the configuration, return to the workflow panel, click **Publish** and save all the configurations made.

## Step 8: Configuring the calling parameters and variables

The job aims to configure the calling parameters for the whole workflow (when to
run daily), and define the variables used in the job, as described below:

.. image:: media/module_7_calling_parameters_and_variables.png

- **Scheduling interval**: Day
- **Specific time**: 01:00 (To be noted that the time here is utc+8)
- **Scheduling status**: Do not check "Pause"

.. image:: media/module_7_calling_parameters_and_variables2.png

Parameters:

```
    start_date=${cal_dt8}

    end_date=${cal_dt8}

    queue=root.training

    mdmID=1c750ed055000000

    path=/user/db_owner_enos_training/cim

    domain=198

    overwrite=true
```    

## Step 9: Pre-run the job manually and observe the job status

Scheduled on daily basis, the workflow is launched at 1:00 am and the data of
the previous day is calculated. To facilitate debugging, the job may be started
manually to run at the current time.

This session of the experiment aims to enable you to learn pre-run the jobs
manually, to observe their running statuses and view the relevant logs with the
job monitoring functions.

1. Select your workflow in **Data IDE Suite> Task Designer**, then click **Pre-run** .

2. Find the example workflow you pre-ran just now in Data Operation and **Manual instance > Pre-run**, as described below:

   .. image:: media/module_7_View_the_pre_run_example.png
      :alt: Fig. View the pre-run example

3. Click the name of your pre-run example, where the running status of each job-node can be viewed in the expanded running workflow page, as described below:

   .. image:: media/module_7_View_the_running_status_of_the_pre_run_example.png
      :alt: Fig. View the running status of the pre-run example

   Please note that the latest running status of the jobs can be viewed by clicking the "Refresh the Page" button on the upper left corner, as described below:

   .. image:: media/6dcb80bec9244404260b8d7e3f2aff95.png

   .. image:: media/module_7_View_the_latest_job_status_by_refreshing_the_page.png
      :alt: Fig. View the latest job status by refreshing the page

   You can view the descriptions of a job by clicking a job node, as described below:

   .. image:: media/module_7_View_the_running_status_of_a_job_node.png
      :alt: Fig. View the running status of a job node

<!--end-->
