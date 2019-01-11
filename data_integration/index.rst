数据集成
=========

数据集成功能实现了在多种异构数据源之间的数据同步。主要运用于帮助数据开发人员将源数据库中的结构化数据同步到EnOS™ 中的Hive库。

数据集成任务是一种特定类型的任务流。数据集成任务的本质是集合单一数据集成任务类型的任务流。

数据集成功能仅支持结构化数据的同步，即可作为二维表抽象的数据。如需集成非结构化数据，如MP3。可在任务中设置SHELL类型的任务来同步非结构化数据。有关同步非结构化数据的信息，参考 `数据开发套件 <../data_ide/index>`__ 。

.. toctree::
  :maxdepth: 1
  :caption: 概述

  dataintegration_overview
  scenarios

.. toctree::
  :maxdepth: 1
  :caption: 操作

  creating_scratch_onetime
  creating_scratch_periodic
  creating_scratch_hive2mysql
  importing_existing_config
  setting_parameters

.. toctree::
  :maxdepth: 1
  :caption: 参考信息

  ../data_ide/system_variables
