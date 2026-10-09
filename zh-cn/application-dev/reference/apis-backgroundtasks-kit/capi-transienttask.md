# TransientTask

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

## 概述

该模块提供短时任务C接口，用于申请、查询和取消短时任务。用于应用进入后台后需要在短时间内执行耗时操作，如状态保存、消息发送等。

**起始版本：** 13
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [transient_task_api.h](capi-transient-task-api-h.md) | 提供短时任务申请、查询、取消功能。 |
| [transient_task_type.h](capi-transient-task-type-h.md) | 定义短时任务的错误码和结构体。 |
