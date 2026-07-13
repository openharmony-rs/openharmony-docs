# TransientTask_TransientTaskInfo

```c
typedef struct TransientTask_TransientTaskInfo {...} TransientTask_TransientTaskInfo
```

## 概述

定义所有短时任务信息结构体。用于返回当日剩余总配额和已申请的所有短时任务信息。

**起始版本：** 20

**相关模块：** [TransientTask](capi-transienttask.md)

**所在头文件：** [transient_task_type.h](capi-transient-task-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t remainingQuota |  |
| [TransientTask_DelaySuspendInfo](capi-transienttask-transienttask-delaysuspendinfo.md) transientTasks[TRANSIENT_TASK_MAX_NUM] |  |


