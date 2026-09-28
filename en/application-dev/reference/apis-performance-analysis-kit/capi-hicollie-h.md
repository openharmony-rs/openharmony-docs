# hicollie.h

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=325a101029ad09501d4d8294a812c2f4976c5510 translatedAt=2026-09-16T10:19:16.062Z pushedAt=2026-09-20T09:01:52.231Z -->

## Overview

The **HiCollie** module provides the capabilities of detecting business thread freeze and jank, and reporting freeze events.

**File to include**: <hicollie/hicollie.h>

**Library**: libohhicollie.so

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 12

**Related module**: [HiCollie](capi-hicollie.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [HiCollie_DetectionParam](capi-hicollie-hicollie-detectionparam.md) | HiCollie_DetectionParam | Parameters related to detecting business thread jank, which can be used in scenarios such as application thread jank detection and analysis. Note that it is supported since API version 12. |
| [HiCollie_SetTimerParam](capi-hicollie-hicollie-settimerparam.md) | HiCollie_SetTimerParam | Input parameters of the **OH_HiCollie_SetTimer** function, used to set the name of the timer monitoring task, the task timeout duration threshold, the timeout callback function, and the execution action flag.<br> Usage scenario: suitable for scenarios that require monitoring task execution time, helping developers monitor and handle task timeout issues. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [HiCollie_ErrorCode](#hicollie_errorcode) | HiCollie_ErrorCode | Enumerates the error codes used in the HiCollie module.|
| [HiCollie_Flag](#hicollie_flag) | HiCollie_Flag | Enumerates the actions to be performed when a function times out.|
| [OH_HiCollie_Freeze_Type](#oh_hicollie_freeze_type) | OH_HiCollie_Freeze_Type | Enumerates the freeze types returned by **FreezeCallback**.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*OH_HiCollie_Task)(void)](#oh_hicollie_task) | OH_HiCollie_Task | Checks whether a service thread is stuck.<br> This function is called by HiCollie every 3 seconds in a service thread.<br> For example, this function can be used to send a message to a service thread and set a flag after the service thread receives the message. Then the flag is checked to determine whether the service thread is stuck.|
| [typedef void (\*OH_HiCollie_BeginFunc)(const char* eventName)](#oh_hicollie_beginfunc) | OH_HiCollie_BeginFunc | Records the start time when a business thread begins event handling in the jank event detection.<br> HiCollie checks the execution time of the event. If the time exceeds the threshold (default threshold: 150 ms), a jank event is reported.<br> This function is inserted before each event is handled and is used together with [OH_HiCollie_EndFunc](capi-hicollie-h.md#oh_hicollie_endfunc). |
| [typedef void (\*OH_HiCollie_EndFunc)(const char* eventName)](#oh_hicollie_endfunc) | OH_HiCollie_EndFunc | Records the end time when a business thread finishes event handling and checks whether the business thread is janky in handling the event.<br> HiCollie checks the execution time of the event. If the time exceeds the threshold (default threshold: 150 ms), a jank event is reported.<br> This function is inserted after each event is handled and is used together with [OH_HiCollie_BeginFunc](capi-hicollie-h.md#oh_hicollie_beginfunc). |
| [HiCollie_ErrorCode OH_HiCollie_Init_StuckDetection(OH_HiCollie_Task task)](#oh_hicollie_init_stuckdetection) | - | Registers a periodic detection task for the freeze of a registered application's business thread. HiCollie periodically invokes the user-implemented callback function in the business thread to check whether the business thread can respond normally, thereby determining whether the thread is frozen.<br> The user implements the callback function to periodically detect the freeze of the business thread.<br> **Note:**<br> - Default detection time: a **BUSSINESS_THREAD_BLOCK_3S** alarm event is reported at 3s, and a **BUSSINESS_THREAD_BLOCK_6S** freeze event is reported at 6s.<br> - This API uses the default detection times of 3s and 6s. To customize the detection time, use the **OH_HiCollie_Init_StuckDetectionWithTimeout** API.<br> - This API can be called only in a non-main thread. |
| [HiCollie_ErrorCode OH_HiCollie_Init_StuckDetectionWithTimeout(OH_HiCollie_Task task, uint32_t stuckTimeout)](#oh_hicollie_init_stuckdetectionwithtimeout) | - | Registers a periodic detection task for the freeze of a registered application's business thread. The user implements the callback function to periodically detect the freeze of the business thread.<br> Developers can set the freeze detection time. The configurable range is [3, 15], in seconds.<br>**Note:**<br> - If the default detection times of 3s and 6s do not meet actual business requirements, use this API to customize the freeze detection time; otherwise, use the **OH_HiCollie_Init_StuckDetection** API.<br> - This API can be called only in a non-main thread. |
| [HiCollie_ErrorCode OH_HiCollie_Init_JankDetection(OH_HiCollie_BeginFunc* beginFunc, OH_HiCollie_EndFunc* endFunc, HiCollie_DetectionParam param)](#oh_hicollie_init_jankdetection) | - | Registers the callback functions for jank detection of a registered application's business thread.<br> The thread jank monitoring feature requires developers to implement two jank detection callback functions, which are placed before and after the business thread handles an event. As instrumentation functions, they monitor the execution of event handling by the business thread.<br> **Note:** <br> This API can be called only in a non-main thread. |
| [HiCollie_ErrorCode OH_HiCollie_Report(bool* isSixSecond)](#oh_hicollie_report) | - | Reports a freeze event of the application's business thread, generates a freeze fault log, and assists in locating application freeze issues.<br> First call OH_HiCollie_Init_StuckDetection or **OH_HiCollie_Init_StuckDetectionWithTimeout** to initialize the detection task.<br> If the task times out, call OH_HiCollie_Report to report the freeze event based on the business logic.<br> **Note:**<br> - This API can be called only in a non-main thread.<br> - This API takes effect only for [release version applications](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-release-version).<br> - This API does not take effect for [debug version applications](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-debug-version). |
| [HiCollie_ErrorCode OH_HiCollie_ReportInputBlock()](#oh_hicollie_reportinputblock) | - | Reports an input unresponsiveness event of the application, generates a freeze fault log, and assists in locating application freeze issues.<br> On PCs or tablets, a dialog box is also displayed to prompt the user to continue waiting or close the application. On other devices, no dialog box is displayed. The following two methods are recommended for using this API.<br> Method 1 (recommended):<br> Use this API together with **OH_HiCollie_Report**, **OH_HiCollie_Init_StuckDetection**, or **OH_HiCollie_Init_StuckDetectionWithTimeout**. The business thread periodically detects its own freeze through the preceding APIs.<br> Call **OH_HiCollie_ReportInputBlock** only when the business thread is frozen and an input event (such as a screen tap, mouse click, or keyboard input) occurs.<br> Method 2: The business thread can also detect its own freeze without using **OH_HiCollie_Report**, **OH_HiCollie_Init_StuckDetection**, or **OH_HiCollie_Init_StuckDetectionWithTimeout**. In this case, the application calls **OH_HiCollie_ReportInputBlock** based on the freeze status of the business thread and the input event.<br> **Note:**<br> - This API can be used in the main thread. For example, an input event must first pass through the main thread before being encapsulated and passed to the business thread for processing. When the business thread is frozen, a status flag is maintained, and the main thread calls this API based on the freeze status flag of the business thread and the input event.<br> - This API takes effect only for [release version applications](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-release-version).<br> - This API does not take effect for [debug version applications](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-debug-version). |
| [typedef void (\*OH_HiCollie_Callback)(void*)](#oh_hicollie_callback) | OH_HiCollie_Callback | Triggered when [OH_HiCollie_CancelTimer](capi-hicollie-h.md#oh_hicollie_canceltimer) is not called within the custom task timeout period after [OH_HiCollie_SetTimer](capi-hicollie-h.md#oh_hicollie_settimer) is called.|
| [HiCollie_ErrorCode OH_HiCollie_SetTimer(HiCollie_SetTimerParam param, int *id)](#oh_hicollie_settimer) | - | Registers a timer to detect whether the execution of a function or code block exceeds a custom duration.<br> This API creates a timer. If **OH_HiCollie_CancelTimer** is not called to cancel the timer within the specified timeout duration, the callback function is triggered to execute the preset action.<br> Use this API together with **OH_HiCollie_CancelTimer**, and call it before invoking a time-consuming function. |
| [void OH_HiCollie_CancelTimer(int id)](#oh_hicollie_canceltimer) | - | Cancels a timer based on the ID.<br> This API is used together with the **OH_HiCollie_SetTimer** API. It must be used after the function or code block is executed.<br> If a timer is not canceled within the custom time, a callback function is executed to generate fault logs for the specified timeout event.|
| [typedef size_t (\*OH_HiCollie_FreezeCallback)(OH_HiCollie_Freeze_Type type, void* buffer, size_t size)](#oh_hicollie_freezecallback) | OH_HiCollie_FreezeCallback | Triggered for freeze events [OH_HiCollie_SetFreezeCallback](capi-hicollie-h.md#oh_hicollie_setfreezecallback). |
| [void* OH_HiCollie_SetFreezeCallback(OH_HiCollie_FreezeCallback callback)](#oh_hicollie_setfreezecallback) | - | Sets the freeze event callback in the system. The system calls this function when a freeze event occurs.|
| [HiCollie_ErrorCode OH_HiCollie_AssociateProcessReport(bool isFreezeEvent)](#oh_hicollie_associateprocessreport) | - | Reports a freeze event of a process. In this case, a **HiAppEvent** event of the **APP_HICOLLIE** type is generated.|

## Enum Description

### HiCollie_ErrorCode

```c
enum HiCollie_ErrorCode
```

**Description**

Enumerates the error codes used in the HiCollie module.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| HICOLLIE_SUCCESS  = 0 | The operation is successful.|
| HICOLLIE_INVALID_ARGUMENT  = 401 | The parameter is invalid.|
| HICOLLIE_WRONG_THREAD_CONTEXT = 29800001 | The API is called in the wrong thread. |
| HICOLLIE_REMOTE_FAILED = 29800002 | The remote call fails.|
| HICOLLIE_INVALID_TIMER_NAME = 29800003 | The timer name is invalid.<br>**Since**: 18|
| HICOLLIE_INVALID_TIMEOUT_VALUE = 29800004 | The function execution timeout value is invalid.<br>**Since**: 18                 |
| HICOLLIE_WRONG_PROCESS_CONTEXT = 29800005 | The process to be accessed is incorrect.<br>**Since**: 18                |
| HICOLLIE_WRONG_TIMER_ID_OUTPUT_PARAM = 29800006 | The pointer used to save the returned timer ID must not be NULL.<br>**Since version:** 18         |
| OH_HICOLLIE_REACH_REPORT_LIMIT = 29800007 | The reporting frequency exceeds the limit.<br>**Since**: 24        |

### HiCollie_Flag

```c
enum HiCollie_Flag
```

**Description**

Enumerates the actions to be performed when a function times out.

**Since**: 18

| Enum Item| Description|
| -- | -- |
| HICOLLIE_FLAG_DEFAULT = (~0) | Generates logs and recovers the function. This is the default action.|
| HICOLLIE_FLAG_NOOP = (0) | Executes only the callback.|
| HICOLLIE_FLAG_LOG = (1 << 0) | Generates logs.|
| HICOLLIE_FLAG_RECOVERY = (1 << 1) | Recovers the function.|

### OH_HiCollie_Freeze_Type

```c
enum OH_HiCollie_Freeze_Type
```

**Description**

Enumerates the freeze event types returned by **FreezeCallback**.

**Since**: 24

| Enum Item| Description|
| -- | -- |
| OH_THREAD_BLOCK_3S | The main thread times out for one cycle. |
| OH_THREAD_BLOCK_6S | The main thread times out for two cycles. |
| OH_LIFECYCLE_HALF_TIMEOUT | The Ability lifecycle times out for one cycle. |
| OH_LIFECYCLE_TIMEOUT | The Ability lifecycle times out for two cycles. |
| OH_APP_INPUT_BLOCK | The input event times out. |
| OH_BUSINESS_THREAD_BLOCK_3S | A 3S freeze event is reported through [OH_HiCollie_Report](capi-hicollie-h.md#oh_hicollie_report). |
| OH_BUSINESS_THREAD_BLOCK_6S | A 6S freeze event is reported through [OH_HiCollie_Report](capi-hicollie-h.md#oh_hicollie_report). |
| OH_BUSINESS_INPUT_BLOCK | A freeze event is reported through [OH_HiCollie_ReportInputBlock](capi-hicollie-h.md#oh_hicollie_reportinputblock). |


## Function Description

### OH_HiCollie_Task()

```c
typedef void (*OH_HiCollie_Task)(void)
```

**Description**

Checks whether a service thread is stuck.<br> This function is called by HiCollie every 3 seconds in a service thread.<br> For example, this function can be used to send a message to a service thread and set a flag after the service thread receives the message. Then the flag is checked to determine whether the service thread is stuck.

**Since**: 12

### OH_HiCollie_BeginFunc()

```c
typedef void (*OH_HiCollie_BeginFunc)(const char* eventName)
```

**Description**

Records the start time when a business thread begins event handling in the jank detection.<br> HiCollie checks the execution time of the event. If the time exceeds the threshold (default threshold: 150 ms), a jank event is reported.<br> This function is inserted before each event handling and is used together with [OH_HiCollie_EndFunc](capi-hicollie-h.md#oh_hicollie_endfunc).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char\* eventName | Name of the event handled by the business thread, in string type. It is used to identify the unique name of the event and should be consistent with the name in [OH_HiCollie_EndFunc](capi-hicollie-h.md#oh_hicollie_endfunc). |

### OH_HiCollie_EndFunc()

```c
typedef void (*OH_HiCollie_EndFunc)(const char* eventName)
```

**Description**

Records the end time when a business thread finishes event handling and checks whether the business thread is janky in handling the event.<br> HiCollie checks the execution time of the event. If the time exceeds the threshold (default threshold: 150 ms), a jank event is reported.<br> This function is inserted after each event handling and is used together with [OH_HiCollie_BeginFunc](capi-hicollie-h.md#oh_hicollie_beginfunc).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char\* eventName | Name of the event handled by the business thread, in string type. It is used to identify the unique name of the event and should be consistent with the name in [OH_HiCollie_BeginFunc](capi-hicollie-h.md#oh_hicollie_beginfunc). |

### OH_HiCollie_Init_StuckDetection()

```c
HiCollie_ErrorCode OH_HiCollie_Init_StuckDetection(OH_HiCollie_Task task)
```

**Description**

Registers a periodic detection task for the thread freeze of a registered application. HiCollie periodically invokes the user-implemented callback function in the business thread to check whether the business thread can respond normally, thereby determining whether the thread is frozen.<br>The user implements the callback function to periodically detect the thread freeze of the business thread.

> **NOTE**
>
> - Default detection time: The **BUSSINESS_THREAD_BLOCK_3S** alarm event is reported at 3s, and the **BUSSINESS_THREAD_BLOCK_6S** freeze event is reported at 6s.
>
> - This API uses the default detection time of 3s and 6s. To customize the detection time, use the **OH_HiCollie_Init_StuckDetectionWithTimeout** API.
>
> - Use this API in non-main threads only.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_HiCollie_Task](capi-hicollie-h.md#oh_hicollie_task) task | Periodic detection task with an execution interval of 3 seconds, used to detect whether the business thread is frozen. |

**Returns**

| Type| Description|
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | <ul><br>         <li> HICOLLIE_SUCCESS 0 - Success.</li><br>         <li> HICOLLIE_WRONG_THREAD_CONTEXT 29800001 - Wrong calling thread. This function can only be called in a non-main thread.</li><br>         </ul> |

### OH_HiCollie_Init_StuckDetectionWithTimeout()

```c
HiCollie_ErrorCode OH_HiCollie_Init_StuckDetectionWithTimeout(OH_HiCollie_Task task, uint32_t stuckTimeout)
```

**Description**

Registers a periodic detection task for the thread freeze of a registered application. The user implements the callback function to periodically detect the thread freeze of the business thread.<br> You can set the freeze detection time. The settable range is [3, 15], in seconds.

> **NOTE**
>
> - If the default detection time of 3s and 6s does not meet your actual service requirements, use this API to customize the freeze detection time. Otherwise, use the **OH_HiCollie_Init_StuckDetection** API.
>
> - Use this API in non-main threads only.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_HiCollie_Task](capi-hicollie-h.md#oh_hicollie_task) task | Periodic detection task that is executed every **stuckTimeout** time to check whether a service thread is stuck.|
| uint32_t stuckTimeout | Detection time for business thread freeze. If a task runs longer than stuckTimeout, a freeze alarm event is reported; if a task runs longer than stuckTimeout * 2, a freeze event is reported.<br> Unit: s. Specification: maximum 15s, minimum 3s. If the value exceeds the range, the API call fails. |

**Returns**

| Type| Description|
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | <ul><br>         <li> HICOLLIE_SUCCESS 0 - Success.</li><br>         <li> HICOLLIE_INVALID_ARGUMENT 401 - The jank detection time is set incorrectly.</li><br>         <li> HICOLLIE_WRONG_THREAD_CONTEXT 29800001 - The calling thread is incorrect. This function can be called only in a non-main thread.</li><br>         </ul> |

### OH_HiCollie_Init_JankDetection()

```c
HiCollie_ErrorCode OH_HiCollie_Init_JankDetection(OH_HiCollie_BeginFunc* beginFunc, OH_HiCollie_EndFunc* endFunc, HiCollie_DetectionParam param)
```

**Description**

Registers the callback function for jank detection of a registered application's business thread.<br> To monitor business thread jank, the developer needs to implement two jank detection callback functions, which are placed before and after the business thread handles an event. As instrumentation functions, they monitor the execution of the business thread's event handling.

> **NOTE**
>
> Use this API in non-main threads only.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_HiCollie_BeginFunc](capi-hicollie-h.md#oh_hicollie_beginfunc)* beginFunc | Callback function invoked before the business thread executes a task. Function pointer type. It must be called before the business thread handles each event to record the start time of event handling. |
| [OH_HiCollie_EndFunc](capi-hicollie-h.md#oh_hicollie_endfunc)* endFunc | Callback function invoked after the business thread executes a task. Function pointer type. It must be called after the business thread handles each event to record the end time of event handling and check whether the business thread is janky when handling the event. |
| [HiCollie_DetectionParam](capi-hicollie-hicollie-detectionparam.md) param | Extended parameter reserved for future use. It is not used currently. Pass the default value 0. |

**Returns**

| Type| Description|
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | <ul><br>         <li> **HICOLLIE_SUCCESS** 0 - Success.</li><br>         <li> **HICOLLIE_INVALID_ARGUMENT** 401 - Both the start function and the end function must have values or be empty; otherwise, this error value is returned.</li><br>         <li> **HICOLLIE_WRONG_THREAD_CONTEXT** 29800001 - Calling thread error. This function can be called only in a non-main thread.</li><br>         </ul> |

### OH_HiCollie_Report()

```c
HiCollie_ErrorCode OH_HiCollie_Report(bool* isSixSecond)
```

**Description**

Reports the thread freeze event of a reporting application's business thread, generates a freeze fault log, and assists in locating application freeze issues.<br> First call **OH_HiCollie_Init_StuckDetection** or **OH_HiCollie_Init_StuckDetectionWithTimeout** to initialize the detection task.<br> If the task times out, call **OH_HiCollie_Report** based on the business logic to report the freeze event.

> **NOTE**
>
> - This API can be called only in a non-main thread.
>
> - This API takes effect only for [release version application](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-release-version).
>
> - This API does not take effect for [debug version application](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-debug-version).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| **bool\* isSixSecond** | Boolean pointer. The Boolean value it points to indicates the thread freeze duration. The value is **true** if the thread is stuck for 6 seconds, and **false** if it is stuck for 3 seconds. |

**Returns**

| Type| Description|
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | <ul><br>         <li> HICOLLIE_SUCCESS 0 - Success.</li><br>         <li> HICOLLIE_INVALID_ARGUMENT 401 - Invalid argument. The input parameter isSixSecond cannot be a null pointer.</li><br>         <li> HICOLLIE_WRONG_THREAD_CONTEXT 29800001 - Wrong calling thread. This function can be called only in a non-main thread.</li><br>         <li> HICOLLIE_REMOTE_FAILED 29800002 - Remote call error. Failed to request the IPC remote service.</li><br>         </ul> |

### OH_HiCollie_ReportInputBlock()

```c
HiCollie_ErrorCode OH_HiCollie_ReportInputBlock()
```

**Description**

Reports an application input unresponsive event and generates a freeze fault log to help locate application freeze issues.<br> On a PC or tablet, a dialog box is displayed, prompting the user to continue waiting or close the application; on other devices, no dialog box is displayed. The following two methods are recommended for using this API.<br> Method 1 (recommended):<br> Use this API together with **OH_HiCollie_Report**, **OH_HiCollie_Init_StuckDetection**, or **OH_HiCollie_Init_StuckDetectionWithTimeout**. The business thread periodically detects its own freeze status through the preceding APIs.<br> Call **OH_HiCollie_ReportInputBlock** only when the business thread is frozen and an input event (such as a screen tap, mouse click, or keyboard input) occurs.<br> Method 2: The business thread can detect its own freeze status without using **OH_HiCollie_Report**, **OH_HiCollie_Init_StuckDetection**, or **OH_HiCollie_Init_StuckDetectionWithTimeout**. In this case, the application calls **OH_HiCollie_ReportInputBlock** based on the business thread freeze status and the input event.

> **NOTE**
>
> - This API can be used in the main thread. For example, an input event needs to be processed by the main thread before being encapsulated and passed to the business thread for processing. When the business thread is frozen, a status flag is maintained, and the main thread calls this API based on the business thread freeze status flag and the input event.
>
> - This API takes effect only for [release version application](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-release-version).
>
> - This API does not take effect for [debug version application](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-debug-version).

**Since**: 24

**Returns**

| Type| Description|
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | <ul><br>         <li> HICOLLIE_SUCCESS 0 - Success.</li><br>         <li> HICOLLIE_REMOTE_FAILED 29800002 - Remote call error. Failed to request the IPC remote service.</li><br>         </ul> |

### OH_HiCollie_Callback()

```c
typedef void (*OH_HiCollie_Callback)(void*)
```

**Description**

Triggered when [OH_HiCollie_CancelTimer](capi-hicollie-h.md#oh_hicollie_canceltimer) is not called within the custom task timeout period after [OH_HiCollie_SetTimer](capi-hicollie-h.md#oh_hicollie_settimer) is called.

**Since**: 18

### OH_HiCollie_SetTimer()

```c
HiCollie_ErrorCode OH_HiCollie_SetTimer(HiCollie_SetTimerParam param, int *id)
```

**Description**

Registers a timer to detect whether the execution of a function or code block exceeds a custom duration.<br> This API creates a timer. If **OH_HiCollie_CancelTimer** is not called to cancel the timer within the specified timeout duration, the callback function is triggered to execute the preset action.<br> Use this API together with **OH_HiCollie_CancelTimer**, and call it before invoking a time-consuming function.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [HiCollie_SetTimerParam](capi-hicollie-hicollie-settimerparam.md) param | Timer configuration parameter, of the structure type.<br> This API is used to define configuration information such as the timer name, timeout duration, and callback function. For details about the API, see [HiCollie_SetTimerParam](capi-hicollie-hicollie-settimerparam.md). |
| int *id | Output parameter. The pointer to the returned timer ID must not be NULL. It is used to receive the timer identifier returned by the function. This ID can be used later to call **OH_HiCollie_CancelTimer** to cancel the timer. |

**Returns**

| Type| Description|
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | <ul><br>         <li> [HICOLLIE_SUCCESS](capi-hicollie-h.md#hicollie_errorcode) 0 - Success.</li><br>         <li> [HICOLLIE_INVALID_TIMER_NAME](capi-hicollie-h.md#hicollie_errorcode) 29800003 - Invalid timer name, which must not be NULL or an empty string.</li><br>         <li> [HICOLLIE_INVALID_TIMEOUT_VALUE](capi-hicollie-h.md#hicollie_errorcode) 29800004 - Invalid timeout value.</li><br>         <li> [HICOLLIE_WRONG_PROCESS_CONTEXT](capi-hicollie-h.md#hicollie_errorcode) 29800005 - Invalid process context for detection access. This API cannot be called in the appspawn or nativespawn process.</li><br>         <li> [HICOLLIE_WRONG_TIMER_ID_OUTPUT_PARAM](capi-hicollie-h.md#hicollie_errorcode) 29800006 - The pointer used to store the returned timer ID must not be NULL.</li><br>         </ul> |

### OH_HiCollie_CancelTimer()

```c
void OH_HiCollie_CancelTimer(int id)
```

**Description**

Cancels a timer based on the ID.<br> This API is used together with the **OH_HiCollie_SetTimer** API. It must be used after the function or code block is executed.<br> If a timer is not canceled within the custom time, a callback function is executed to generate fault logs for the specified timeout event.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| int id | Timer ID updated after the [OH_HiCollie_SetTimer](capi-hicollie-h.md#oh_hicollie_settimer) function is executed. |

### OH_HiCollie_FreezeCallback()

```c
typedef size_t (*OH_HiCollie_FreezeCallback)(OH_HiCollie_Freeze_Type type, void* buffer, size_t size)
```

**Description**

Pointer to the freeze event callback function, set through [OH_HiCollie_SetFreezeCallback](capi-hicollie-h.md#oh_hicollie_setfreezecallback).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| OH_HiCollie_Freeze_Type type | Frozen screen event type. For details, see [OH_HiCollie_Freeze_Type](capi-hicollie-h.md#oh_hicollie_freeze_type). |
| void\* buffer | System-provided log buffer, a byte array pointer.<br>          Used to write custom log information in the freeze callback. The written content is migrated to the APP_FREEZE or APP_HICOLLIE event. Data must be written in byte array format. |
| size_t size | Available buffer size, with a maximum of 64 KB. Exceeding the limit may cause the application to crash. |

**Returns**

| Type| Description|
| -- | -- |
| size_t | Size of the used buffer, in bytes.|

> **NOTE**
>
> If the return value exceeds 64 KB, the log content may be empty.

### OH_HiCollie_SetFreezeCallback()

```c
void* OH_HiCollie_SetFreezeCallback(OH_HiCollie_FreezeCallback callback)
```

**Description**

Sets the freeze event callback in the system. The system calls this function when a freeze event occurs.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_HiCollie_FreezeCallback](capi-hicollie-h.md#oh_hicollie_freezecallback) callback | Frozen screen event callback function, a function pointer type. It is called when the system detects a freeze event. |

**Returns**

| Type| Description|
| -- | -- |
| void* | Callback function previously set for this process. Returns NULL if this is the first call. |

### OH_HiCollie_AssociateProcessReport()

```c
HiCollie_ErrorCode OH_HiCollie_AssociateProcessReport(bool isFreezeEvent)
```

**Description**

Reports a freeze event of a process. In this case, a **HiAppEvent** event of the **APP_HICOLLIE** type is generated.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| bool isFreezeEvent | Type of the reported event. **true**: A 6s freeze event. **false**: A 3s freeze event.|


> **NOTE**
>
> **BUSINESS_THREAD_BLOCK_3S** and **BUSINESS_THREAD_BLOCK_6S** are equivalent to **BUSSINESS_THREAD_BLOCK_3S** and **BUSSINESS_THREAD_BLOCK_6S**, respectively.

**Returns**

| Type| Description|
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | <ul><br>         <li> HICOLLIE_SUCCESS 0 - Success.</li><br>         <li> OH_HICOLLIE_REACH_REPORT_LIMIT 29800007 - Reporting frequency is too high. A freeze event can be reported at most once per minute.</li><br>         </ul> |

> **NOTE**
>
> The event can be reported only once within 1 minute.
