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

> **NOTE**
>
> Mainthread jank events can be subscribed to using HiAppEvent in [application clones](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/app-clone) and atomic services. Since API version 22, this feature is also supported for [input method applications](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/inputmethod-application-guide).

## Custom Parameters

The **setEventConfig** API cannot automatically stop the sampling stack when the main thread timeout event ends. Since API Version 22, the **configEventPolicy** API is provided to automatically stop the sampling stack when the main thread timeout event ends.

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
| [configEventPolicy(policy: EventPolicy): Promise&lt;void>](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#hiappeventconfigeventpolicy22) | Sets the parameters of the main thread jank event that triggers the stack sampling. Sampling automatically stops when the timeout ends.|

### Parameters of configEventPolicy

You can use the APIs provided by HiAppEvent to configure the parameters of the sampling stack API in **EventPolicy**.

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mainThreadJankPolicy | MainThreadJankPolicy | Yes| Configuration policy for the main thread jank event.|

Definition of the main thread timeout event configuration policy.

> **NOTE**
>
> All parameters are optional. If they are not set, the default values are used.
>
> When **logType** is set to **0**, you only need to set **autoStopSampling**. Default values are used for other parameters.
>
> When **logType** is set to **2**, other parameters do not take effect and do not need to be set.

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| logType | number | No| Type of logs to collect. Default value: **0**<br>**logType = 0**: The default values of other parameters are used. When the main thread experiences two consecutive timeouts between 150 ms and 450 ms, a call stack capture is triggered. When the timeout exceeds 450 ms, a trace capture is triggered.<br>**logType=1**: Only the call stack is captured, and the threshold for triggering the detection is customized.<br>**logType=2**: Only traces are captured.|
| sampleInterval | number | No| Interval for the main thread jank event detection and sampling, in milliseconds. The default value is **150**. The value range is [50, 500].|
| ignoreStartupTime | number | No| Application startup time for the main thread jank event detection to ignore, in seconds. The default value is **10** and the minimum value is 3.|
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
       "sampleInterval": 70,
       "ignoreStartupTime": 11,
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

### OH_HiAppEvent_SetEventConfig

| API| Description|
| -------- | -------- |
| [int OH_HiAppEvent_SetEventConfig(const char\* name, HiAppEvent_Config\* config)](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md#oh_hiappevent_seteventconfig) | Sets the parameters of the main thread jank event that triggers the stack sampling.|

### Parameters of OH_HiAppEvent_SetEventConfig

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | const char\* | Yes| Name of the main thread jank event. The value is the predefined macro **EVENT_MAIN_THREAD_JANK** or **EVENT_MAIN_THREAD_JANK_V2**.|
| config | HiAppEvent_Config\* | Yes| Configuration parameters for the sampling stack of main thread jank event. You can use the [OH_HiAppEvent_SetConfigItem](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md#oh_hiappevent_setconfigitem) function to set the configuration items of the **config** parameter.|

**name**: **EVENT_MAIN_THREAD_JANK**

The API does not provide the functionality of automatically stoping the sampling stack when the main thread jank event ends. The **config** parameters are configured as follows:

> **NOTE**
>
> **MAIN_THREAD_JANK_PARAM_LOG_TYPE** is mandatory.
>
> When **MAIN_THREAD_JANK_PARAM_LOG_TYPE** is set to **0** or **2**, no other configuration item is required.
>
> When **MAIN_THREAD_JANK_PARAM_LOG_TYPE** is set to **1**, all configuration items must be set.
>
> The value of each configuration item is a string literal or character pointer that can be converted into an integer.

For API version 21 and earlier versions, the configuration item name can contain only related strings.

Since API version 22, predefined macros and related strings can be used as configuration item names. Macros are recommended to avoid unexpected results caused by manually written strings.

The following value ranges are described based on the variable types after conversion.

| Item| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| Macro: **MAIN_THREAD_JANK_PARAM_LOG_TYPE**<br>String: **log_type**| const char\* | Yes| Type of logs to collect.<br>**"0"**: When the main thread experiences two consecutive timeouts between 150 ms and 450 ms, a call stack capture is triggered. When the timeout exceeds 450 ms, a trace capture is triggered. This is the default value.<br>**"1"**: Only call stacks are captured.<br>**"2"**: Only traces are captured.|
| Macro: **MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL**<br>String: **sample_interval**| const char\* | No| Interval for the main thread jank event detection and sampling, in milliseconds.<br>The default value is **150**. The value range is [50, 500].<br>The system determines the jank event based on the custom **MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL** and uses this value as the interval for periodic detection.|
| Macro: **MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME**<br>String: **ignore_startup_time**| const char\* | No| Time window after thread startup during which no checks are performed, in seconds.<br>The minimum value is **3** and the default value is **10**.<br>Do not perform timeout detection within a specified period of time after the thread is started. For the process that takes time to start, it is not necessary to capture the full stack. You can set this parameter to prevent the check from being performed within the custom startup time.|
| Macro: **MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT**<br>String: **sample_count**| const char\* | No| Number of samplings for the main thread jank event. When detecting that the task execution duration of the current main thread reaches the sampling threshold, the system starts to periodically collect stacks, once per interval, for a total of **MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT** times.<br>Default value: **10**.<br>The minimum value is 1. The maximum value can be calculated based on the custom value of **MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL** as follows: <br>**MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT** ≤ (2500/**MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL** - 4)|
| Macro: **MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP**<br>String: **report_times_per_app**| const char\* | No| Number of sampling reporting times for the main thread jank event of the processes with the same PID of an application. This parameter can be set only once for the processes with the same PID.<br>Default value: **1**<br>When the **Developer options** is enabled, the value range is [1, 3] per hour.<br>When the **Developer options** is disabled, the value range is [1, 3] per day.|

1. Description of **MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT**:

   (1) The value **2500** (ms) indicates the maximum time allowed for a main thread jank event to be reported after being detected. Therefore, the value of **MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT** cannot be greater than the maximum value calculated based on the formula.

   (2) The value **4** indicates the number of check intervals, that is, the first check interval, the twice second check intervals, and the interval for collecting and reporting stack information.

   (3) You need to set the parameters as required.

2.  
   
   The following shows examples of setting **MAIN_THREAD_JANK_PARAM_LOG_TYPE** of the **config** parameter in the **OH_HiAppEvent_SetEventConfig** API:

   (1) Set **MAIN_THREAD_JANK_PARAM_LOG_TYPE** to **"0"** to sample the stack or trace.

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"

   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();    
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "0");
   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Setting default value successfully.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```

   (2) Set **MAIN_THREAD_JANK_PARAM_LOG_TYPE** to **"1"** to collect the call stack.

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "1");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL, "100");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME, "11");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT, "21");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP, "3");

   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Successfully set sampling stack parameters.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```

   (3) Set **MAIN_THREAD_JANK_PARAM_LOG_TYPE** to **"2"** to collect trace data.

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "2");

   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Set to only collect trace successfully");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```  

**name**: **EVENT_MAIN_THREAD_JANK_V2**

Since API version 22, you can set name to **EVENT_MAIN_THREAD_JANK_V2**. In this case, the API provides the functionality of automatically stopping the sampling stack when the main thread jank event ends. The configuration of the **config** parameter is as follows:

> **NOTE**
> 
> The configuration item names are predefined macros.
>
> All configuration items of **config** are optional. If the items are not set or left empty, the default values are used.
>
> When **MAIN_THREAD_JANK_PARAM_LOG_TYPE** is set to **"0"**, you only need to set **MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING**. Other configuration items use the default values.
>
> When **MAIN_THREAD_JANK_PARAM_LOG_TYPE** is set to **"2"**, other configuration items do not take effect and do not need to be set.
>
>  If **MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING** is set to **"true"** or **"false"**, the value is converted to the Boolean type. The values of other configuration items are string literals or character pointers that can be converted into integers.

The following value ranges are described based on the variable types after conversion.

| Item| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| MAIN_THREAD_JANK_PARAM_LOG_TYPE | const char\* | No| Type of logs to collect.<br>**"0"**: When the main thread experiences two consecutive timeouts between 150 ms and 450 ms, a call stack capture is triggered. When the timeout exceeds 450 ms, a trace capture is triggered. This is the default value.<br>**"1"**: Only call stacks are captured.<br>**"2"**: Only traces are captured.|
| MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL | const char\* | No| Interval for the main thread jank event detection and sampling, in milliseconds.<br>The default value is **150**. The value range is [50, 500].<br>The system determines the jank event based on the custom **MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL** and uses this value as the interval for periodic detection.|
| MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME | const char\* | No| Time window after thread startup during which no checks are performed, in seconds.<br>The minimum value is **3** and the default value is **10**.<br>Do not perform timeout detection within a specified period of time after the thread is started. For the process that takes time to start, it is not necessary to capture the full stack. You can set this parameter to prevent the check from being performed within the custom startup time.|
| MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT | const char\* | No| Number of samplings for the main thread jank event. When detecting that the task execution duration of the current main thread reaches the sampling threshold, the system starts to periodically collect stacks, once per interval, for a total of **MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT** times.<br>Default value: **10**.<br>The minimum value is 1. The maximum value can be calculated based on the custom value of **MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL** as follows: <br>**MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT** ≤ (2500/**MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL** - 4)|
| MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP | const char\* | No| Number of sampling reporting times for the main thread jank event of the processes with the same PID of an application. This parameter can be set only once for the processes with the same PID.<br>Default value: **1**<br>When the **Developer options** is enabled, the value range is [1, 3] per hour.<br>When the **Developer options** is disabled, the value range is [1, 3] per day.|
| MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING | const char\* | No| Whether to automatically stop sampling the main thread stack when the main thread jank event ends.<br>The value **true** means to stop sampling when the main thread jank event ends or the number of samplings reaches the specified value.<br>The value **false** means to stop sampling when the number of samplings reaches the specified value.<br>The default value is **false**.|

1. Description of **MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT**:

   (1) The value **2500** (ms) indicates the maximum time allowed for a main thread jank event to be reported after being detected. Therefore, the value of **MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT** cannot be greater than the maximum value calculated based on the formula.

   (2) The value **4** indicates the number of check intervals, that is, the first check interval, the twice second check intervals, and the interval for collecting and reporting stack information.

   (3) You need to set the parameters as required.

2.  
   
   The following shows examples of setting **MAIN_THREAD_JANK_PARAM_LOG_TYPE** of the **config** parameter in the **OH_HiAppEvent_SetEventConfig** API:

   (1) Set **MAIN_THREAD_JANK_PARAM_LOG_TYPE** to **"0"** to sample the stack or trace.

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"

   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();    
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "0");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING, "true");
   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK_V2, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Setting default value successfully.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```

   (2) Set **MAIN_THREAD_JANK_PARAM_LOG_TYPE** to **"1"** to collect the call stack.

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "1");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL, "100");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME, "11");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT, "21");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP, "3");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING, "true");

   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK_V2, config);
   if (ret == HIAPPEVENT_SUCCESS) {{
       OH_LOG_INFO(LogType::LOG_APP, "Successfully set sampling stack parameters.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```

   (3) Set **MAIN_THREAD_JANK_PARAM_LOG_TYPE** to **"2"** to collect trace data.

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "2");

   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK_V2, config);
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
