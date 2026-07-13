# ffrt_task_attr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct {...} ffrt_task_attr_t
```

## 概述

任务属性结构体，用于存储任务的属性信息。

**起始版本：** 10

**相关模块：** [FFRT](capi-ffrt.md)

**所在头文件：** [type_def.h](capi-type-def-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t storage[(ffrt_task_attr_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | 任务属性的内部存储。请勿直接访问，通过[ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init)和`ffrt_task_attr_set_*`等接口管理内容。 |
