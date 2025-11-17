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

The **setEventConfig** API cannot automatically stop the sampling stack when the main thread timeout event ends. Since API Version 22, the **configEventPolicy** API is provided to automatically stop the sampling stack when the main thread timeout event ends.

### setEventConfig

| API| Description|
| -------- | -------- |
| setEventConfig(name: string, config: Record&lt;string, ParamType>): Promise&lt;void> | Sets the parameters of the main thread jank event that triggers the stack sampling. Currently, only the **MAIN_THREAD_JANK** event parameter can be customized. Therefore, the value of **name** is **MAIN_THREAD_JANK**. |

### Parameters of setEventConfig

You can use the API provided by HiAppEvent to customize the parameters for collecting the **MAIN_THREAD_JANK** event in **Record<string, ParamType>**.

> **NOTE**
>
> **log_type** is mandatory. When **log_type** is set to 0 or 2, do not set other parameters.
>
> When **log_type** is set to **1**, configure the following parameters: **sample_interval**, **ignore_startup_time**, **sample_count**, and **report_times_per_app**.

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| log_type | string | Yes| Type of MAIN_THREAD_JANK event logs to collect.<br>**log_type=0**: When the main thread experiences two consecutive timeouts between 150 ms and 450 ms, a call stack capture is triggered. When the timeout exceeds 450 ms, a trace capture is triggered. This is the default value.<br>**log_type=1**: Only the call stack is captured, and the threshold for triggering the detection is customized.<br>**log_type=2**: Only the trace data is captured.|
| sample_interval | string | No| Interval for the main thread jank event detection and sampling, in milliseconds.<br>The default value is **150**. The value range is [50, 500].<br>The system performs the check based on the custom interval and uses the interval for the periodic check.|
| ignore_startup_time | string | No| Time window after thread startup during which no checks are performed, in seconds. The minimum value is **3** and the default value is **10**.<br>Do not perform timeout detection within a specified period of time after the thread is started. For the process that takes time to start, it is not necessary to capture the full stack. You can set this parameter to prevent the check from being performed within the custom startup time.|
| sample_count | string | No| Number of samplings for the main thread jank event. After detecting that the main thread processing time exceeds the threshold, the system starts periodic stack sampling for **sample_count** times.<br>Default value: **10**.<br>The minimum value is 1. The maximum value can be calculated based on the custom value of **sample_interval** as follows: <br>**sample_count** ≤ (2500/**sample_interval** - 4)|
| report_times_per_app | string | No| Number of sampling reporting times for the main thread jank event of the processes with the same PID of an application. This parameter can be set only once for the processes with the same PID.<br>Default value: **1**<br>When the **Developer options** is enabled, the value range is [1, 3] per hour.<br>When the **Developer options** is disabled, the value range is [1, 3] per day.|

1. **sample_count**:

   (1) The value **2500** (ms) indicates the maximum time allowed for a main thread jank event to be reported after being detected. Therefore, the value of **sample_count** cannot be greater than the maximum value calculated based on the formula.

   (2) The value **4** indicates the number of check intervals, that is, the first check interval, the twice second check intervals, and the interval for collecting and reporting stack information.

   (3) You need to set the parameters as required.

2.  
   
   The **log_type** parameter in the **setEventConfig** API can be set to **0**, **1**, or **2**.

   (1) Set **log_type** to **0** to sample the stack or trace.

   ```ts
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

   ```ts
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

   ```ts
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

### configEventPolicy

| API| Description|
| -------- | -------- |
| [configEventPolicy(policy : EventPolicy): Promise&lt;void>](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#hiappeventconfigeventpolicy22) | Sets the parameters of the main thread jank event that triggers the stack sampling. Sampling automatically stops when the timeout ends.|

### Parameters of configEventPolicy

You can use the APIs provided by HiAppEvent to configure the parameters of the sampling stack API in **EventPolicy**.

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mainThreadJankPolicy | MainThreadJankPolicy | Yes| Configuration policy for the main thread jank event.|

Definition of the main thread timeout event configuration policy.

> **NOTE**
>
> All parameters are optional. If they are not set or are left empty, the default values are used.
>
> When **logType** is set to **0**, the default values of other parameters are used regardless of whether the parameters exist. When **logType** is set to **2**, the values of other parameters do not take effect.

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| logType | number | No| Type of logs to collect. Default value: **0**<br>**logType = 0**: The default values of other parameters are used. When the main thread experiences two consecutive timeouts between 150 ms and 450 ms, a call stack capture is triggered. When the timeout exceeds 450 ms, a trace capture is triggered.<br>**logType=1**: Only the call stack is captured, and the threshold for triggering the detection is customized.<br>**logType=2**: Only traces are captured.|
| ignoreStartupTime | number | No| Interval for the main thread jank event detection ignored during application startup, in seconds. The default value is **10** and the minimum value is 3.|
| sampleInterval | number | No| Interval for the main thread jank event detection and sampling, in milliseconds. The default value is **150**. The value range is [50, 500].|
| sampleCount | number | No| Number of samplings for the main thread jank event. The default value is **10**. The minimum value is 1.<br>The maximum value is calculated using the following formula: **sampleCount** ≤ (2500/**sampleInterval** - 4).|
| reportTimesPerApp | number | No| Number of sampling reporting times for the main thread jank event of the processes with the same PID of an application. This parameter can be set only once for the processes with the same PID.<br>The default value is **1**.<br>When **Developer options** is enabled, the number of reporting times per hour ranges from 1 to 3.<br>When **Developer options** is disabled, the number of reporting times per minute ranges from 1 to 3.|
| autoStopSampling | boolean | No| Whether to automatically stop sampling the main thread stack when the main thread jank event ends.<br>The value **true** means to stop sampling when the main thread jank event ends or the number of samplings reaches the specified value.<br>The value **false** means to stop sampling when the number of samplings reaches the specified value.<br>The default value is **false**.|

1. **sampleCount**:

   (1) The value **2500** (ms) indicates the maximum time allowed for a main thread jank event to be reported after being detected. Therefore, the value of **sampleCount** cannot be greater than the maximum value calculated based on the formula.

   (2) The value **4** indicates the number of check intervals, that is, the first check interval, the twice second check intervals, and the interval for collecting and reporting stack information.

   (3) You need to set the parameters as required.

2.  

   The **logType** parameter in the **configEventPolicy** API can be set to **0**, **1**, or **2**.

   (1) Set **logType** to **0** to sample the stack or trace.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

   let policy: hiAppEvent.EventPolicy = {
     "mainThreadJankPolicy" : {
       "logType": 0,
       "ignoreStartupTime": 11,
       "sampleInterval": 70,
       "sampleCount": 20,
       "reportTimesPerApp": 3,
       "autoStopSampling": true
     }
   };
   hiAppEvent.configEventPolicy(policy).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Setting default value successfully.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set default value. Code: ${err.code}, message: ${err.message}`);
   });
   ```

   (2) Set **logType** to **1** to collect only the call stack.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

   let policy: hiAppEvent.EventPolicy = {
     "mainThreadJankPolicy" : {
       "logType": 1,
       "ignoreStartupTime": 11,
       "sampleInterval": 70,
       "sampleCount": 20,
       "reportTimesPerApp": 3,
       "autoStopSampling": true
     }
   };
   hiAppEvent.configEventPolicy(policy).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Successfully set sampling stack parameters.`);
   }).catch((err: BusinessError) => {
   hilog.error(0x0000, 'hiAppEvent', `Failed to set sample stack value. Code: ${err.code}, message: ${err.message}`);
   });
   ```

   (3) Set **logType** to **2** to collect only the trace.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

   let policy: hiAppEvent.EventPolicy = {
     "mainThreadJankPolicy" : {
       "logType": 2
     }
   };
   hiAppEvent.configEventPolicy(policy).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Set to only collect trace successfully.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set only collect trace. code: ${err.code}, message: ${err.message}`);
   });
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
