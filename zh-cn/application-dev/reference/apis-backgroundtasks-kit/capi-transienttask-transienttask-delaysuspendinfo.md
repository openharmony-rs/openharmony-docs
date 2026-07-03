# TransientTask_DelaySuspendInfo

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

```c
typedef struct TransientTask_DelaySuspendInfo {...} TransientTask_DelaySuspendInfo
```

## 概述

定义短时任务返回信息结构体。用于返回当前短时任务的任务ID和剩余时间。

**起始版本：** 13

**相关模块：** [TransientTask](capi-transienttask.md)

**所在头文件：** [transient_task_type.h](capi-transient-task-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t requestId | 短时任务请求ID。 |
| int32_t actualDelayTime | 剩余时间（单位：ms）。取值范围：[0, 180000]。 |
