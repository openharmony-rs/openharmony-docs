# Main Thread Jank Event Overview

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @rr_cn-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Introduction

When an application's main thread executes a time-consuming task, you may detect that the application freezes. However, the freeze time does not reach the threshold specified by [application freeze detection](appfreeze-guidelines.md). Therefore, no fault log is generated. To better locate and analyze problems, you can use [main thread jank event detection principles](apptask-timeout-guidelines.md#detection-principles) and [main thread jank event log specifications](apptask-timeout-guidelines.md#log-specifications) to proactively analyze the task execution status of the main thread.

## Detection Principles

For details, see [main thread jank event detection principles](apptask-timeout-guidelines.md#detection-principles).

## Available APIs

You can use the APIs provided by HiAppEvent to subscribe to the main thread jank event **hiAppEvent.event.MAIN_THREAD_JANK**. When the system detects a main thread jank event, it captures maintenance and debugging information and sends the callback to the application process through HiAppEvent.

- [Subscribing to Main Thread Jank Events (ArkTS)](hiappevent-watcher-mainthreadjank-events-arkts.md)

- [Subscribing to Main Thread Jank Events (C/C++)](hiappevent-watcher-mainthreadjank-events-ndk.md)

## Custom Parameters

### setEventConfig

| API| Description|
| -------- | -------- |
| [setEventConfig(name: string, config: Record&lt;string, ParamType>): Promise&lt;void>](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#hiappeventseteventconfig15) | Sets the parameters of the main thread jank event that triggers the stack sampling.|

### Parameters of setEventConfig

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Name of the main thread jank event. The value must be the constant **hiappevent.event.MAIN_THREAD_JANK**.|
| config | Record&lt;string, ParamType> | Yes| Configuration parameters for the sampling stack of main thread jank event.|

The following table lists the configuration parameters.

> **NOTE**
>
> **log_type** is mandatory.
>
> If **log_type** is set to **0** or **2**, do not set other parameters.
>
> If **log_type** is set to **1**, all parameters must be set.

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| log_type | string | Yes| Type of MAIN_THREAD_JANK event logs to collect.<br>**log_type=0**: When the main thread experiences two consecutive timeouts between 150 ms and 450 ms, a call stack capture is triggered. When the timeout exceeds 450 ms, a trace capture is triggered. This is the default value.<br>**log_type=1**: Only the call stack data is captured.<br>**log_type=2**: Only the trace data is captured.|
| sample_interval | string | No| Interval for the main thread jank event detection and sampling, in milliseconds.<br>The default value is **150**. The value range is [50, 500].<br>The system determines the jank event based on the custom **sample_interval** and uses this **sample_interval** as the interval for periodic detection.|
| ignore_startup_time | string | No| Time window after thread startup during which no checks are performed, in seconds. The minimum value is **3** and the default value is **10**.<br>Do not perform timeout detection within a specified period of time after the thread is started. For the process that takes time to start, it is not necessary to capture the full stack. You can set this parameter to prevent the check from being performed within the custom startup time.|
| sample_count | string | No| Number of samplings for the main thread jank event. When detecting that the task execution duration of the current main thread reaches the sampling threshold, the system starts to periodically collect stacks, once per interval, for a total of **sample_count** times.<br>Default value: **10**.<br>The minimum value is 1. The maximum value can be calculated based on the custom value of **sample_interval** as follows: <br>**sample_count** ≤ (2500/**sample_interval** - 4)|
| report_times_per_app | string | No| Number of sampling reporting times for the main thread jank event of the processes with the same PID of an application. This parameter can be set only once for the processes with the same PID.<br>Default value: **1**<br>When the **Developer options** is enabled, the value range is [1, 3] per hour.<br>When the **Developer options** is disabled, the value range is [1, 3] per day.|

1. **sample_count**:
   (1) The value **2500** (ms) indicates the maximum time allowed for a main thread jank event to be reported after being detected. Therefore, the value of **sample_count** cannot be greater than the maximum value calculated based on the formula.

   (2) The value **4** indicates the number of check intervals, that is, the first check interval, the twice second check intervals, and the interval for collecting and reporting stack information.

   (3) You need to set the parameters as required.

2.  
   The following examples describe how to configure the triggering conditions for the **MAIN_THREAD_JANK** event using three types of **log_type**.

   (1) Set **log_type** to **0** to sample the stack or trace.

   ```
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';
   let params: Record<string, hiAppEvent.ParamType> = {
     "log_type": "0"
   };
   hiAppEvent.setEventConfig(hiAppEvent.event.MAIN_THREAD_JANK, params).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Setting default value successfully.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set default value. Code: ${err.code}, message: ${err.message}`);
   });
   ```

   (2) Set **log_type** to **1** to collect only the call stack.

   ```
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';
   let params: Record<string, hiAppEvent.ParamType> = {
     "log_type": "1",
     "sample_interval": "100",
     "ignore_startup_time": "11",
     "sample_count": "21",
     "report_times_per_app": "3"
   };
   hiAppEvent.setEventConfig(hiAppEvent.event.MAIN_THREAD_JANK, params).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Successfully set sampling stack parameters.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set sample stack value. Code: ${err.code}, message: ${err.message}`);
   });
   ```

   (3) Set **log_type** to **2** to collect only the trace.

   ```
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';
   let params: Record<string, hiAppEvent.ParamType> = {
     "log_type": "2"
   };
   hiAppEvent.setEventConfig(hiAppEvent.event.MAIN_THREAD_JANK, params).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Set to only collect trace successfully.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set only collect trace. code: ${err.code}, message: ${err.message}`);
   });
   ```

### OH_HiAppEvent_SetEventConfig

| API| Description|
| -------- | -------- |
| [int OH_HiAppEvent_SetEventConfig(const char\* name, HiAppEvent_Config\* config)](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md#oh_hiappevent_seteventconfig) | Sets the parameters of the main thread jank event that triggers the stack sampling.|

### Parameters of OH_HiAppEvent_SetEventConfig

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | const char\* | Yes| Name of the main thread jank event. The value is the predefined macro **EVENT_MAIN_THREAD_JANK**.|
| config | HiAppEvent_Config\* | Yes| Configuration parameters for the sampling stack of main thread jank event. You can use the [OH_HiAppEvent_SetConfigItem](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md#oh_hiappevent_setconfigitem) function to set the configuration items of the **config** parameter.|

The API does not provide the functionality of automatically stoping the sampling stack when the main thread jank event ends. The **config** parameters are configured as follows:

> **NOTE**
> 
> The configuration item names are related strings.
>
> **log_type** is mandatory.
>
> When **log_type** is set to **0** or **2**, no other configuration item is required.
>
> When **log_type** is set to **1**, all configuration items must be set.
>
> The value of each configuration item is a string literal or character pointer that can be converted into an integer.

The following value ranges are described based on the variable types after conversion.

| Item| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| log_type | const char\* | Yes| Type of logs to collect.<br>**"0"**: When the main thread experiences two consecutive timeouts between 150 ms and 450 ms, a call stack capture is triggered. When the timeout exceeds 450 ms, a trace capture is triggered. This is the default value.<br>**"1"**: Only call stacks are captured.<br>**"2"**: Only traces are captured.|
| sample_interval | const char\* | No| Interval for the main thread jank event detection and sampling, in milliseconds.<br>The default value is **150**. The value range is [50, 500].<br>The system determines the jank event based on the custom **sample_interval** and uses this value as the interval for periodic detection.|
| ignore_startup_time | const char\* | No| Time window after thread startup during which no checks are performed, in seconds.<br>The minimum value is **3** and the default value is **10**.<br>Do not perform timeout detection within a specified period of time after the thread is started. For the process that takes time to start, it is not necessary to capture the full stack. You can set this parameter to prevent the check from being performed within the custom startup time.|
| sample_count | const char\* | No| Number of samplings for the main thread jank event. When detecting that the task execution duration of the current main thread reaches the sampling threshold, the system starts to periodically collect stacks, once per interval, for a total of **sample_count** times.<br>Default value: **10**.<br>The minimum value is 1. The maximum value can be calculated based on the custom value of **sample_interval** as follows: <br>**sample_count** ≤ (2500/**sample_interval** - 4)|
| report_times_per_app | const char\* | No| Number of sampling reporting times for the main thread jank event of the processes with the same PID of an application. This parameter can be set only once for the processes with the same PID.<br>Default value: **1**<br>When the **Developer options** is enabled, the value range is [1, 3] per hour.<br>When the **Developer options** is disabled, the value range is [1, 3] per day.|

1. **sample_count**:

   (1) The value **2500** (ms) indicates the maximum time allowed for a main thread jank event to be reported after being detected. Therefore, the value of **sample_count** cannot be greater than the maximum value calculated based on the formula.

   (2) The value **4** indicates the number of check intervals, that is, the first check interval, the twice second check intervals, and the interval for collecting and reporting stack information.

   (3) You need to set the parameters as required.

2.  The following shows examples of setting **log_type** of the **config** parameter in the **OH_HiAppEvent_SetEventConfig** API:
   
   (1) Set **log_type** to **"0"** to sample the stack or trace.

   ```c++
#include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"
   
   #undef LOG_TAG
#define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();    
OH_HiAppEvent_SetConfigItem(config, "log_type", "0");
   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Setting default value successfully.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```
   
   (2) Set **log_type** to **"1"** to collect the call stack.

   ```c++
#include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"
   
   #undef LOG_TAG
#define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, "log_type", "1");
   OH_HiAppEvent_SetConfigItem(config, "sample_interval", "100");
   OH_HiAppEvent_SetConfigItem(config, "ignore_startup_time", "11");
   OH_HiAppEvent_SetConfigItem(config, "sample_count", "21");
   OH_HiAppEvent_SetConfigItem(config, "report_times_per_app", "3");
   
   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK, config);
if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Successfully set sampling stack parameters.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```
   
   (3) Set **log_type** to **"2"** to collect trace data.

   ```c++
#include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"
   
   #undef LOG_TAG
#define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, "log_type", "2");
   
   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK, config);
if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Set to only collect trace successfully");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```

## Event Fields

| Name| Type| Description|
| -------- | -------- | -------- |
| time | number | Event triggering time, in ms.|
| bundle_version | string | Application version.|
| bundle_name | string | Application name.|
| pid | number | Process ID of the application.|
| uid | number | User ID of the application.|
| begin_time | number | Begin time of a task in the main thread.|
| end_time | number | End time of a task in the main thread.|
| external_log | string[] | Path of the generated log files. If the directory files exceed the threshold (for details, see **log_over_limit**), new log files may fail to be written. Therefore, delete the log files immediately after they are processed.|
| log_over_limit | boolean | Whether the size of generated log files and existing log files exceeds the upper limit (10 MB). The value **true** indicates that the upper limit is exceeded and logs fail to be written. The value **false** indicates that the upper limit is not exceeded.|
| app_start_jiffies_time | number | Start time of the task when the main thread jank event occurs. The information is printed in the sampling stack.|
| heaviest_stack | string | Call stack that is generated multiple times in the log file. The information is printed in the sampling stack.|
