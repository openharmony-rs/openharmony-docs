# TransientTask

## 概述

Provide C interface for the Transient task management.

**起始版本：** 13

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [transient_task_api.h](capi-transient-task-api-h.md) | 提供短时任务申请、查询、取消功能。<br> 短时任务允许应用在后台获得有限的时间延长以完成关键操作。 系统为每个应用分配每日配额限制，超时前通过回调通知应用，超时后系统会挂起应用。 |
| [transient_task_type.h](capi-transient-task-type-h.md) | 定义短时任务的错误码和结构体。 |
