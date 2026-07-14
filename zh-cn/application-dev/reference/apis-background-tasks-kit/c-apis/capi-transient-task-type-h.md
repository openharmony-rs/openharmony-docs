# transient_task_type.h

## 概述

Defines the data structures for the C APIs of transient task.

**库：** libtransient_task.so

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**起始版本：** 11

**相关模块：** [TransientTask](capi-transienttask.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [TransientTask_DelaySuspendInfo](capi-transienttask-transienttask-delaysuspendinfo.md) | TransientTask_DelaySuspendInfo | 定义短时任务返回信息结构体。用于返回当前短时任务的任务ID和剩余时间。 |
| [TransientTask_TransientTaskInfo](capi-transienttask-transienttask-transienttaskinfo.md) | TransientTask_TransientTaskInfo | 定义所有短时任务信息结构体。用于返回当日剩余总配额和已申请的所有短时任务信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [TransientTask_ErrorCode](#transienttask_errorcode) | TransientTask_ErrorCode | 定义短时任务错误码。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| TRANSIENT_TASK_MAX_NUM 3 | 同一时刻最大短时任务数量。<br>**起始版本：** 20 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*TransientTask_Callback)(void)](#transienttask_callback) | TransientTask_Callback | 定义短时任务超时回调类型。 |

## 枚举类型说明

### TransientTask_ErrorCode

```c
enum TransientTask_ErrorCode
```

**描述**

定义短时任务错误码。

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| ERR_TRANSIENT_TASK_OK = 0 |  |
| ERR_TRANSIENT_TASK_INVALID_PARAM = 401 |  |
| ERR_TRANSIENT_TASK_PARCEL_FAILED = 9800002 |  |
| ERR_TRANSIENT_TASK_TRANSACTION_FAILED = 9800003 |  |
| ERR_TRANSIENT_TASK_SYS_NOT_READY = 9800004 |  |
| ERR_TRANSIENT_TASK_CLIENT_INFO_VERIFICATION_FAILED = 9900001 |  |
| ERR_TRANSIENT_TASK_SERVICE_VERIFICATION_FAILED = 9900002 |  |
| ERR_TRANSIENT_TASK_PARCELABLE_FAILED = 9900003 |  |
| ERR_TRANSIENT_TASK_SERVICE_NOT_READY = 9900004 |  |


## 函数说明

### TransientTask_Callback()

```c
typedef void (*TransientTask_Callback)(void)
```

**描述**

定义短时任务超时回调类型。

**起始版本：** 13


