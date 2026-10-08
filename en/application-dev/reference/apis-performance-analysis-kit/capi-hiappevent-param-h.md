# hiappevent_param.h

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @jiangwenhao-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=a77786e77c1e5d30b8a9141947c9f6691210aaf7 translatedAt=2026-09-21T02:22:40.694Z pushedAt=2026-09-22T01:29:30.366Z -->

## Overview

Defines the names of all predefined parameters. You can use specific predefined parameter names for logging or set custom parameter specifications for system events.

For details about how to use the following macro definitions, see [Parameters of OH_HiAppEvent_SetEventConfig](../../dfx/hiappevent-watcher-mainthreadjank-events.md#parameters-of-oh_hiappevent_seteventconfig) for subscribing to main thread timeout events and [OH_HiAppEvent_SetEventConfig Parameter Settings](../../dfx/hiappevent-watcher-crash-events.md#oh_hiappevent_seteventconfig-parameter-settings) for subscribing to crash events.

**File to include**: <hiappevent/hiappevent_param.h>

**Library**: libhiappevent_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 8

**Related module**: [HiAppEvent](capi-hiappevent.md)

## Summary

### Macros

| Name| Description|
| -- | -- |
| [PARAM_USER_ID](#param_user_id) "user_id"                                                        | User ID. Can be used for predefined event logging.<br>**Since:** 8  |
| [PARAM_DISTRIBUTED_SERVICE_NAME](#param_distributed_service_name) "ds_name"                      | Distributed service name. Can be used for predefined event logging.<br>**Since:** 8   |
| [PARAM_DISTRIBUTED_SERVICE_INSTANCE_ID](#param_distributed_service_instance_id) "ds_instance_id" | Distributed service instance ID. Can be used for predefined event logging.<br>**Since:** 8 |
| [MAIN_THREAD_JANK_PARAM_LOG_TYPE](#main_thread_jank_param_log_type) "log_type" | Type of the log collected by the main thread jank event detection. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|
| [MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL](#main_thread_jank_param_sample_interval) "sample_interval" | Used for the **MAIN_THREAD_JANK_V2** event, the main thread jank event detection interval and sampling interval. Unit: ms.<br>**Since:** 22 |
| [MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME](#main_thread_jank_param_ignore_startup_time) "ignore_startup_time" | Used for the **MAIN_THREAD_JANK_V2** event, the time during which main thread jank event detection is ignored during application startup. Unit: s.<br>**Since:** 22 |
| [MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT](#main_thread_jank_param_sample_count) "sample_count" | Number of stack samplings of the main thread jank event detection. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|
| [MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP](#main_thread_jank_param_report_times_per_app) "report_times_per_app" | Number of sampling reporting times of the main thread jank event detection within a single lifecycle of an application PID, which can only be set once in a lifecycle. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|
| [MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING](#main_thread_jank_param_auto_stop_sampling) "auto_stop_sampling" | Whether to stop sampling the main thread stack when the main thread jank event ends. This macro is used for **MAIN_THREAD_JANK_V2** events.<br>**Since**: 22|
| [OH_APP_CRASH_PARAM_EXTEND_PC_LR_PRINTING](#oh_app_crash_param_extend_pc_lr_printing) "extend_pc_lr_printing"                                                        | Used to set the log specifications of the **CPP_CRASH** type in the **APP_CRASH** event, that is, whether to print the memory contents of the extended byte ranges of the PC and LR.<br>**Since**: 24 |
| [OH_APP_CRASH_PARAM_LOG_FILE_CUTOFF_SZ_BYTES](#oh_app_crash_param_log_file_cutoff_sz_bytes) "log_file_cutoff_sz_bytes"                                                        | Used to set the log specifications of the **CPP_CRASH** type in the **APP_CRASH** event, that is, truncate **CPP_CRASH** logs based on the configured parameter value.<br>**Since**: 24 |
| [OH_APP_CRASH_PARAM_SIMPLIFY_VMA_PRINTING](#oh_app_crash_param_simplify_vma_printing) "simplify_vma_printing"                                                        | Used to set the log specifications of the **CPP_CRASH** type in the **APP_CRASH** event, that is, whether to print only the VMA mapping information of the address in the crash log to reduce the size of the **CPP_CRASH** log file.<br>**Since**: 24 |
| [OH_APP_CRASH_PARAM_MERGE_CPPCRASH_APP_LOG](#oh_app_crash_param_merge_cppcrash_app_log) "merge_cppcrash_app_log"                                                        | Used to set the log specifications of the **CPP_CRASH** type in the **APP_CRASH** event, that is, whether to combine the logs of the specified file in the application sandbox in the **CPP_CRASH** scenario.<br>**Since**: 24 |
| [OH_APP_CRASH_PARAM_COLLECT_MINIDUMP](#oh_app_crash_param_collect_minidump) "collect_minidump"  | <!--RP1-->Used for the **APP_CRASH** event, whether to enable minidump.<!--RP1End--><br>**Since:** 26.0.0  |


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

Number of stack samplings of the main thread jank event detection. This macro is used for **MAIN_THREAD_JANK_V2** events.

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

### OH_APP_CRASH_PARAM_EXTEND_PC_LR_PRINTING

```c
#define OH_APP_CRASH_PARAM_EXTEND_PC_LR_PRINTING "extend_pc_lr_printing"
```

**Description**

Used to set the log specifications of the **CPP_CRASH** type in the **APP_CRASH** event, that is, whether to print the memory contents of the extended byte ranges of the PC and LR.

**Since**: 24

### OH_APP_CRASH_PARAM_LOG_FILE_CUTOFF_SZ_BYTES

```c
#define OH_APP_CRASH_PARAM_LOG_FILE_CUTOFF_SZ_BYTES "log_file_cutoff_sz_bytes"
```

**Description**

Used to set the log specifications of the **CPP_CRASH** type in the **APP_CRASH** event, that is, truncate **CPP_CRASH** logs based on the configured parameter value.

**Since**: 24

### OH_APP_CRASH_PARAM_SIMPLIFY_VMA_PRINTING

```c
#define OH_APP_CRASH_PARAM_SIMPLIFY_VMA_PRINTING "simplify_vma_printing"
```

**Description**

Used to set the log specifications of the **CPP_CRASH** type in the **APP_CRASH** event, that is, whether to print only the VMA mapping information of the address in the crash log to reduce the size of the **CPP_CRASH** log file.

**Since**: 24

### OH_APP_CRASH_PARAM_MERGE_CPPCRASH_APP_LOG

```c
#define OH_APP_CRASH_PARAM_MERGE_CPPCRASH_APP_LOG "merge_cppcrash_app_log"
```

**Description**

Used to set the log specifications of the **CPP_CRASH** type in the **APP_CRASH** event, that is, whether to combine the logs of the specified file in the application sandbox in the **CPP_CRASH** scenario.

**Since**: 24

### OH_APP_CRASH_PARAM_COLLECT_MINIDUMP

```c
#define OH_APP_CRASH_PARAM_COLLECT_MINIDUMP "collect_minidump"
```

**Description**

Used for the **APP_CRASH** event to specify whether to enable minidump.

**Since:** 26.0.0
