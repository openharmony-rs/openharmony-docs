# hiappevent_param.h

## Overview

Defines the param names of all predefined events.<br> In addition to custom events associated with specific apps, you can also use predefined events for logging.<br> Sample code: <pre> ParamList list = OH_HiAppEvent_CreateParamList(); OH_HiAppEvent_AddInt32Param(list, PARAM_USER_ID, 123); int res = OH_HiAppEvent_Write("user_domain", EVENT_USER_LOGIN, BEHAVIOR, list); OH_HiAppEvent_DestroyParamList(list); </pre>

**Library**: libhiappevent_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 8

**Related module**: [HiAppEvent](capi-hiappevent.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| HIVIEWDFX_HIAPPEVENT_PARAM_H | Defines the param names of all predefined events.<br> In addition to custom events associated with specific apps, you can also use predefined events for logging.<br> Sample code: <pre> ParamList list = OH_HiAppEvent_CreateParamList(); OH_HiAppEvent_AddInt32Param(list, PARAM_USER_ID, 123); int res = OH_HiAppEvent_Write("user_domain", EVENT_USER_LOGIN, BEHAVIOR, list); OH_HiAppEvent_DestroyParamList(list); </pre><br>**Since**: 8<br>**System capability**: SystemCapability.HiviewDFX.HiAppEvent |
| PARAM_USER_ID "user_id" | Preset param name, user id param.<br>**Since**: 8 |
| PARAM_DISTRIBUTED_SERVICE_NAME "ds_name" | Preset param name, distributed service name param.<br>**Since**: 8 |
| PARAM_DISTRIBUTED_SERVICE_INSTANCE_ID "ds_instance_id" | Preset param name, distributed service instance id param.<br>**Since**: 8 |
| MAIN_THREAD_JANK_PARAM_LOG_TYPE "log_type" | Used in MAIN_THREAD_JANK_V2, type of the log that needs to be collected when main thread jank happened.<br>**Since**: 22 |
| MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL "sample_interval" | Used in MAIN_THREAD_JANK_V2, The timeout detection interval and sampling interval for the main thread. Unit: ms.<br>**Since**: 22 |
| MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME "ignore_startup_time" | Used in MAIN_THREAD_JANK_V2, Ignore main thread timeout detection during startup. Unit: s.<br>**Since**: 22 |
| MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT "sample_count" | Used in MAIN_THREAD_JANK_V2, Number of main thread timeout samples.<br>**Since**: 22 |
| MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP "report_times_per_app" | Used in MAIN_THREAD_JANK_V2, Number of main thread timeout sampling reports per application PID within a single lifecycle.<br>**Since**: 22 |
| MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING "auto_stop_sampling" | Used in MAIN_THREAD_JANK_V2, Stop sampling main thread stack when main thread blockage is resolved.<br>**Since**: 22 |
| OH_APP_CRASH_PARAM_EXTEND_PC_LR_PRINTING "extend_pc_lr_printing" | Print additional memory information near the PC and LR registers<br>**Since**: 24 |
| OH_APP_CRASH_PARAM_LOG_FILE_CUTOFF_SZ_BYTES "log_file_cutoff_sz_bytes" | Used to set the log specifications of the CPP_CRASH type in the APP_CRASH event, that is, truncate CPP_CRASH logs based on the configured parameter value.<br>**Since**: 24 |
| OH_APP_CRASH_PARAM_SIMPLIFY_VMA_PRINTING "simplify_vma_printing" | Only print VMA within the stacktrace of the cppcrash log<br>**Since**: 24 |
| OH_APP_CRASH_PARAM_MERGE_CPPCRASH_APP_LOG "merge_cppcrash_app_log" | Merge the app log into the system cppcrash log and return it via external_log in the APP_CRASH event<br>**Since**: 24 |
| OH_APP_CRASH_PARAM_COLLECT_MINIDUMP "collect_minidump" | Enable minidump in the APP_CRASH event<br>**Since**: 26.0.0 |

