# hiappevent_param.h

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @junjie_shi-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Defines the names of all predefined event parameters. In addition to custom events associated with specific applications, you can use predefined events for logging.

**File to include**: <hiappevent/hiappevent_param.h>

**Library**: libhiappevent_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 8

**Related module**: [HiAppEvent](capi-hiappevent.md)

## Summary

### Macros

| Name| Description|
| -- | -- |
| [PARAM_USER_ID](#param_user_id) "user_id"                                                        | User ID.<br>**Since**: 8 |
| [PARAM_DISTRIBUTED_SERVICE_NAME](#param_distributed_service_name) "ds_name"                      | Distributed service name.<br>**Since**: 8  |
| [PARAM_DISTRIBUTED_SERVICE_INSTANCE_ID](#param_distributed_service_instance_id) "ds_instance_id" | Distributed service instance ID.<br>**Since**: 8|
| [MAIN_THREAD_JANK_PARAM_LOG_TYPE](#main_thread_jank_param_log_type) "log_type" | Type of the log collected by the main thread jank event detection. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|
| [MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL](#main_thread_jank_param_sample_interval) "sample_interval" | Sampling interval of the main thread jank event detection. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|
| [MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME](#main_thread_jank_param_ignore_startup_time) "ignore_startup_time" | Main thread jank event detection time ignored during application startup. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|
| [MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT](#main_thread_jank_param_sample_count) "sample_count" | Number of stack samplings of the main thread timeout detection. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|
| [MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP](#main_thread_jank_param_report_times_per_app) "report_times_per_app" | Number of sampling reporting times of the main thread jank event detection within a single lifecycle of an application PID, which can only be set once in a lifecycle. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|
| [MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING](#main_thread_jank_param_auto_stop_sampling) "auto_stop_sampling" | Whether to stop sampling the main thread stack when the main thread jank event ends. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|


## Macro Description

### PARAM_USER_ID

```c
#define PARAM_USER_ID "user_id"
```

**Description**

User ID.

**Since**: 8

### PARAM_DISTRIBUTED_SERVICE_NAME

```c
#define PARAM_DISTRIBUTED_SERVICE_NAME "ds_name"
```

**Description**

Distributed service name.

**Since**: 8

### PARAM_DISTRIBUTED_SERVICE_INSTANCE_ID

```c
#define PARAM_DISTRIBUTED_SERVICE_INSTANCE_ID "ds_instance_id"
```

**Description**

Distributed service instance ID.

**Since**: 8

### MAIN_THREAD_JANK_PARAM_LOG_TYPE

```c
#define MAIN_THREAD_JANK_PARAM_LOG_TYPE "log_type"
```

**Description**

Type of the log collected by the main thread jank event detection. This macro is used for **MAIN_THREAD_JANK_V2** events.

**Since**: 22

### MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL

```c
#define MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL "sample_interval"
```

**Description**

Sampling interval of the main thread jank event detection. This macro is used for **MAIN_THREAD_JANK_V2** events.

**Since**: 22

### MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME

```c
#define MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME "ignore_startup_time"
```

**Description**

Main thread jank event detection time ignored during application startup. This macro is used for **MAIN_THREAD_JANK_V2** events.

**Since**: 22

### MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT

```c
#define MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT "sample_count"
```

**Description**

Number of stack samplings of the main thread timeout detection. This macro is used for **MAIN_THREAD_JANK_V2** events.

**Since**: 22

### MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP

```c
#define MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP "report_times_per_app"
```

**Description**

Number of sampling reporting times of the main thread jank event detection within a single lifecycle of an application PID, which can only be set once in a lifecycle. This macro is used for **MAIN_THREAD_JANK_V2** events.

**Since**: 22

### MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING

```c
#define MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING "auto_stop_sampling"
```

**Description**

Whether to stop sampling the main thread stack. This macro is used for **MAIN_THREAD_JANK_V2** events.

**Since**: 22
