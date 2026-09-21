# hicollie.h

## Overview

Defines the interface of the HiCollie module.

**Library**: libohhicollie.so

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 12

**Related module**: [HiCollie](capi-hicollie.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [HiCollie_DetectionParam](capi-hicollie-hicollie-detectionparam.md) | HiCollie_DetectionParam | Defines the parameters of the jank event detection. Note that this struct is supported since API 12. |
| [HiCollie_SetTimerParam](capi-hicollie-hicollie-settimerparam.md) | HiCollie_SetTimerParam | Defines the input parameters of the **OH_HiCollie_SetTimer** function. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [HiCollie_ErrorCode](#hicollie_errorcode) | HiCollie_ErrorCode | Enumerates the error codes used in the HiCollie module. |
| [HiCollie_Flag](#hicollie_flag) | HiCollie_Flag | Enumerates the actions to be performed when a function times out. |
| [OH_HiCollie_Freeze_Type](#oh_hicollie_freeze_type) | OH_HiCollie_Freeze_Type | Enumerates the freeze event types returned by **FreezeCallback**. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_HiCollie_Task)(void)](#oh_hicollie_task) | OH_HiCollie_Task | Checks whether a service thread is stuck. This function is called by HiCollie every 3 seconds in a service thread. For example, this function can be used to send a message to a service thread and set a flag after the service thread receives the message. Then the flag is checked to determine whether the service thread is stuck. |
| [typedef void (\*OH_HiCollie_BeginFunc)(const char* eventName)](#oh_hicollie_beginfunc) | OH_HiCollie_BeginFunc | In jank scenario, you need to insert two stub functions before and after each event processing of your business thread. By checking these two function executing timestamp, HiCollie will know consuming time for every event. If it exceeds the preset threshold, a jank event will be reported. This is the stub function inserted before each event processing. |
| [typedef void (\*OH_HiCollie_EndFunc)(const char* eventName)](#oh_hicollie_endfunc) | OH_HiCollie_EndFunc | Records the end time when a service thread processes an event. This function is used in the jank event detection. HiCollie checks the execution time of the event. If the duration exceeds the preset threshold, a jank event is reported. This is the stub function inserted after each event processing. |
| [HiCollie_ErrorCode OH_HiCollie_Init_StuckDetection(OH_HiCollie_Task task)](#oh_hicollie_init_stuckdetection) | - | Registers a callback used to periodically detect service thread stuck events. By default, the **BUSSINESS_THREAD_BLOCK_3S** event is reported when the thread is blocked for 3s and the **<br>BUSSINESS_THREAD_BLOCK_6S** event is reported when the thread is blocked for 6s. |
| [HiCollie_ErrorCode OH_HiCollie_Init_StuckDetectionWithTimeout(OH_HiCollie_Task task, uint32_t stuckTimeout)](#oh_hicollie_init_stuckdetectionwithtimeout) | - | Registers a callback used to periodically detect service thread stuck events. You can set the interval for the stuck event detection. The value range is [3, 15], in seconds. |
| [HiCollie_ErrorCode OH_HiCollie_Init_JankDetection(OH_HiCollie_BeginFunc* beginFunc, OH_HiCollie_EndFunc* endFunc, HiCollie_DetectionParam param)](#oh_hicollie_init_jankdetection) | - | Registers a callback used to detect service thread jank events. To monitor service thread jank events, you can implement two callbacks as instrumentation functions, placing them before and after the service thread event. |
| [HiCollie_ErrorCode OH_HiCollie_Report(bool* isSixSecond)](#oh_hicollie_report) | - | Reports a service thread stuck event and generates logs to help locate application stuck issues. Call **OH_HiCollie_Init_StuckDetection()** or **OH_HiCollie_Init_StuckDetectionWithTimeout()** to initialize the detection task. If the task times out, call **OH_HiCollie_Report()** to report the stuck event based on the service logic. |
| [HiCollie_ErrorCode OH_HiCollie_ReportInputBlock()](#oh_hicollie_reportinputblock) | - | Reports an application input unresponsive event and generates logs to help locate application freeze issues. On a PC or tablet, a dialog box is displayed, prompting the user to wait or close the application. On other devices, no dialog box is displayed. You are advised to use this API in either of the following ways: Method 1 (recommended): Use this API together with **OH_HiCollie_Report**, **OH_HiCollie_Init_StuckDetection**, or **<br>OH_HiCollie_Init_StuckDetectionWithTimeout**. The service thread periodically checks whether it is frozen through the preceding APIs. When the service thread is frozen and an input event (such as screen tapping, mouse clicking, or keyboard input) occurs, the service thread calls **OH_HiCollie_ReportInputBlock**. Method 2: If the service thread can detect its own freeze without using the **OH_HiCollie_Report**, **<br>OH_HiCollie_Init_StuckDetection**, or **OH_HiCollie_Init_StuckDetectionWithTimeout** API, the application calls the *<br>*OH_HiCollie_ReportInputBlock** API based on the service thread freeze and input event. |
| [typedef void (\*OH_HiCollie_Callback)(void*)](#oh_hicollie_callback) | OH_HiCollie_Callback | Triggered when [OH_HiCollie_CancelTimer](capi-hicollie-h.md#oh_hicollie_canceltimer) is not called within the custom task timeout period after [OH_HiCollie_SetTimer](capi-hicollie-h.md#oh_hicollie_settimer) is called. |
| [HiCollie_ErrorCode OH_HiCollie_SetTimer(HiCollie_SetTimerParam param, int *id)](#oh_hicollie_settimer) | - | Registers a timer to check whether the execution time of a function or code block exceeds the custom time. This API is used together with the **OH_HiCollie_CancelTimer** API. |
| [void OH_HiCollie_CancelTimer(int id)](#oh_hicollie_canceltimer) | - | Cancels a timer based on the ID. This API is used together with the **OH_HiCollie_SetTimer** API. It must be used after the function or code block is executed. If a timer is not canceled within the custom time, a callback function is executed to generate fault logs for the specified timeout event. |
| [typedef size_t (\*OH_HiCollie_FreezeCallback)(OH_HiCollie_Freeze_Type type, void* buffer, size_t size)](#oh_hicollie_freezecallback) | OH_HiCollie_FreezeCallback | the freeze callback used in [OH_HiCollie_SetFreezeCallback](capi-hicollie-h.md#oh_hicollie_setfreezecallback) |
| [void* OH_HiCollie_SetFreezeCallback(OH_HiCollie_FreezeCallback callback)](#oh_hicollie_setfreezecallback) | - | Sets the freeze event callback in the system. The system calls this function when a freeze event occurs. |
| [HiCollie_ErrorCode OH_HiCollie_AssociateProcessReport(bool isFreezeEvent)](#oh_hicollie_associateprocessreport) | - | Reports a freeze event of a process. In this case, a **HiAppEvent** event of the **APP_HICOLLIE** type is generated. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_HiCollie_Task)(void) | Checks whether a service thread is stuck. This function is called by HiCollie every 3 seconds in a service thread. For example, this function can be used to send a message to a service thread and set a flag after the service thread receives the message. Then the flag is checked to determine whether the service thread is stuck.<br>**Since**: 12 |
| void (*OH_HiCollie_BeginFunc)(const char* eventName) | In jank scenario, you need to insert two stub functions before and after each event processing of your business thread. By checking these two function executing timestamp, HiCollie will know consuming time for every event. If it exceeds the preset threshold, a jank event will be reported. This is the stub function inserted before each event processing.<br>**Since**: 12 |
| void (*OH_HiCollie_EndFunc)(const char* eventName) | Records the end time when a service thread processes an event. This function is used in the jank event detection. HiCollie checks the execution time of the event. If the duration exceeds the preset threshold, a jank event is reported. This is the stub function inserted after each event processing.<br>**Since**: 12 |
| void (*OH_HiCollie_Callback)(void*) | Triggered when [OH_HiCollie_CancelTimer](capi-hicollie-h.md#oh_hicollie_canceltimer) is not called within the custom task timeout period after [OH_HiCollie_SetTimer](capi-hicollie-h.md#oh_hicollie_settimer) is called.<br>**Since**: 18 |
| size_t (*OH_HiCollie_FreezeCallback)(OH_HiCollie_Freeze_Type type, void* buffer, size_t size) | the freeze callback used in [OH_HiCollie_SetFreezeCallback](capi-hicollie-h.md#oh_hicollie_setfreezecallback)<br>**Since**: 24 |

## Enum type description

### HiCollie_ErrorCode

```c
enum HiCollie_ErrorCode
```

**Description**

Enumerates the error codes used in the HiCollie module.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 12

| Enum item | Description |
| -- | -- |
| HICOLLIE_SUCCESS = 0 |  |
| HICOLLIE_INVALID_ARGUMENT = 401 |  |
| HICOLLIE_WRONG_THREAD_CONTEXT = 29800001 |  |
| HICOLLIE_REMOTE_FAILED = 29800002 |  |
| HICOLLIE_INVALID_TIMER_NAME = 29800003 |  |
| HICOLLIE_INVALID_TIMEOUT_VALUE = 29800004 |  |
| HICOLLIE_WRONG_PROCESS_CONTEXT = 29800005 |  |
| HICOLLIE_WRONG_TIMER_ID_OUTPUT_PARAM = 29800006 |  |
| OH_HICOLLIE_REACH_REPORT_LIMIT = 29800007 |  |

### HiCollie_Flag

```c
enum HiCollie_Flag
```

**Description**

Enumerates the actions to be performed when a function times out.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 18

| Enum item | Description |
| -- | -- |
| HICOLLIE_FLAG_DEFAULT = (~0) |  |
| HICOLLIE_FLAG_NOOP = (0) |  |
| HICOLLIE_FLAG_LOG = (1 << 0) |  |
| HICOLLIE_FLAG_RECOVERY = (1 << 1) |  |

### OH_HiCollie_Freeze_Type

```c
enum OH_HiCollie_Freeze_Type
```

**Description**

Enumerates the freeze event types returned by **FreezeCallback**.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_THREAD_BLOCK_3S | The main thread times out for one period.<br>**Since**: 24 |
| OH_THREAD_BLOCK_6S | The main thread times out for two periods.<br>**Since**: 24 |
| OH_LIFECYCLE_HALF_TIMEOUT | The ability lifecycle times out for one period.<br>**Since**: 24 |
| OH_LIFECYCLE_TIMEOUT | The ability lifecycle times out for two periods.<br>**Since**: 24 |
| OH_APP_INPUT_BLOCK | Input event processing timeout.<br>**Since**: 24 |
| OH_BUSINESS_THREAD_BLOCK_3S | A 3s freeze event is reported through [OH_HiCollie_Report](capi-hicollie-h.md#oh_hicollie_report).<br>**Since**: 24 |
| OH_BUSINESS_THREAD_BLOCK_6S | A 6s freeze event is reported through [OH_HiCollie_Report](capi-hicollie-h.md#oh_hicollie_report).<br>**Since**: 24 |
| OH_BUSINESS_INPUT_BLOCK | A freeze event is reported through [OH_HiCollie_ReportInputBlock](capi-hicollie-h.md#oh_hicollie_reportinputblock).<br>**Since**: 24 |


## Function description

### OH_HiCollie_Task()

```c
typedef void (*OH_HiCollie_Task)(void)
```

**Description**

Checks whether a service thread is stuck. This function is called by HiCollie every 3 seconds in a service thread. For example, this function can be used to send a message to a service thread and set a flag after the service thread receives the message. Then the flag is checked to determine whether the service thread is stuck.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 12

### OH_HiCollie_BeginFunc()

```c
typedef void (*OH_HiCollie_BeginFunc)(const char* eventName)
```

**Description**

In jank scenario, you need to insert two stub functions before and after each event processing of your business thread. By checking these two function executing timestamp, HiCollie will know consuming time for every event. If it exceeds the preset threshold, a jank event will be reported. This is the stub function inserted before each event processing.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char\* eventName | Business thread processing event name. |

### OH_HiCollie_EndFunc()

```c
typedef void (*OH_HiCollie_EndFunc)(const char* eventName)
```

**Description**

Records the end time when a service thread processes an event. This function is used in the jank event detection. HiCollie checks the execution time of the event. If the duration exceeds the preset threshold, a jank event is reported. This is the stub function inserted after each event processing.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char\* eventName | Name of the service thread event. |

### OH_HiCollie_Init_StuckDetection()

```c
HiCollie_ErrorCode OH_HiCollie_Init_StuckDetection(OH_HiCollie_Task task)
```

**Description**

Registers a callback used to periodically detect service thread stuck events. By default, the **BUSSINESS_THREAD_BLOCK_3S** event is reported when the thread is blocked for 3s and the **<br>BUSSINESS_THREAD_BLOCK_6S** event is reported when the thread is blocked for 6s.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiCollie_Task](capi-hicollie-h.md#oh_hicollie_task) task | A periodic detection task that is executed every 3 seconds to check whether a service thread is stuck. |

**Returns**:

| Type | Description |
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | [HICOLLIE_SUCCESS](capi-hicollie-h.md#hicollie_errorcode) 0 - Operation successful.  [HICOLLIE_WRONG_THREAD_CONTEXT](capi-hicollie-h.md#hicollie_errorcode) 29800001 - Incorrect calling thread. This function should be called in a non-  main thread.  For details, see [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode). |

### OH_HiCollie_Init_StuckDetectionWithTimeout()

```c
HiCollie_ErrorCode OH_HiCollie_Init_StuckDetectionWithTimeout(OH_HiCollie_Task task, uint32_t stuckTimeout)
```

**Description**

Registers a callback used to periodically detect service thread stuck events. You can set the interval for the stuck event detection. The value range is [3, 15], in seconds.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiCollie_Task](capi-hicollie-h.md#oh_hicollie_task) task | Periodic detection task that is executed every **stuckTimeout** time to check whether a service thread is stuck. |
| uint32_t stuckTimeout | Threshold for reporting a service thread stuck event, in seconds. When the task execution time exceeds the value of **stuckTimeout**, a stuck warning event is reported. When the task execution time exceeds twice the value of **stuckTimeout**, a stuck event is reported. The maximum value is **15s** and the minimum value is **3s**. |

**Returns**:

| Type | Description |
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | [HICOLLIE_SUCCESS](capi-hicollie-h.md#hicollie_errorcode) 0 - Operation successful.  [HICOLLIE_INVALID_ARGUMENT](capi-hicollie-h.md#hicollie_errorcode) 401 - Invalid detection time.  [HICOLLIE_WRONG_THREAD_CONTEXT](capi-hicollie-h.md#hicollie_errorcode) 29800001 - Incorrect calling thread. This function should be called in a non-  main thread.  For details, see [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode). |

### OH_HiCollie_Init_JankDetection()

```c
HiCollie_ErrorCode OH_HiCollie_Init_JankDetection(OH_HiCollie_BeginFunc* beginFunc, OH_HiCollie_EndFunc* endFunc, HiCollie_DetectionParam param)
```

**Description**

Registers a callback used to detect service thread jank events. To monitor service thread jank events, you can implement two callbacks as instrumentation functions, placing them before and after the service thread event.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiCollie_BeginFunc](capi-hicollie-h.md#oh_hicollie_beginfunc)* beginFunc | Function used before the service thread event detection. |
| [OH_HiCollie_EndFunc](capi-hicollie-h.md#oh_hicollie_endfunc)* endFunc | Function used after the service thread event detection. |
| [HiCollie_DetectionParam](capi-hicollie-hicollie-detectionparam.md) param | Extended parameter for future use. |

**Returns**:

| Type | Description |
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | [HICOLLIE_SUCCESS](capi-hicollie-h.md#hicollie_errorcode) 0 - Operation successful.  [HICOLLIE_INVALID_ARGUMENT](capi-hicollie-h.md#hicollie_errorcode) 401 - The begin and end functions are not both set or both unset; they must either  both have valid values or both be empty.  [HICOLLIE_WRONG_THREAD_CONTEXT](capi-hicollie-h.md#hicollie_errorcode) 29800001 - Incorrect calling thread. This function should be called in a non-  main thread.  For details, see [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode). |

### OH_HiCollie_Report()

```c
HiCollie_ErrorCode OH_HiCollie_Report(bool* isSixSecond)
```

**Description**

Reports a service thread stuck event and generates logs to help locate application stuck issues. Call **OH_HiCollie_Init_StuckDetection()** or **OH_HiCollie_Init_StuckDetectionWithTimeout()** to initialize the detection task. If the task times out, call **OH_HiCollie_Report()** to report the stuck event based on the service logic.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool* isSixSecond | Pointer to a Boolean value.  If the service thread is stuck for 6s, the value is **true**. If the service thread is stuck for 3s, the value is **false**. |

**Returns**:

| Type | Description |
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | [HICOLLIE_SUCCESS](capi-hicollie-h.md#hicollie_errorcode) 0 - Operation successful.  [HICOLLIE_INVALID_ARGUMENT](capi-hicollie-h.md#hicollie_errorcode) 401 - The begin and end functions are not both set or both unset; they must either  both have valid values or both be empty.  [HICOLLIE_WRONG_THREAD_CONTEXT](capi-hicollie-h.md#hicollie_errorcode) 29800001 - Incorrect calling thread. This function should be called in a non-  main thread.  [HICOLLIE_REMOTE_FAILED](capi-hicollie-h.md#hicollie_errorcode) 29800002 - Remote call error. The IPC remote service fails to be called.  For details, see [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode). |

### OH_HiCollie_ReportInputBlock()

```c
HiCollie_ErrorCode OH_HiCollie_ReportInputBlock()
```

**Description**

Reports an application input unresponsive event and generates logs to help locate application freeze issues. On a PC or tablet, a dialog box is displayed, prompting the user to wait or close the application. On other devices, no dialog box is displayed. You are advised to use this API in either of the following ways: Method 1 (recommended): Use this API together with **OH_HiCollie_Report**, **OH_HiCollie_Init_StuckDetection**, or **<br>OH_HiCollie_Init_StuckDetectionWithTimeout**. The service thread periodically checks whether it is frozen through the preceding APIs. When the service thread is frozen and an input event (such as screen tapping, mouse clicking, or keyboard input) occurs, the service thread calls **OH_HiCollie_ReportInputBlock**. Method 2: If the service thread can detect its own freeze without using the **OH_HiCollie_Report**, **<br>OH_HiCollie_Init_StuckDetection**, or **OH_HiCollie_Init_StuckDetectionWithTimeout** API, the application calls the *<br>*OH_HiCollie_ReportInputBlock** API based on the service thread freeze and input event.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | [HICOLLIE_SUCCESS](capi-hicollie-h.md#hicollie_errorcode) 0 - Operation successful.  [HICOLLIE_REMOTE_FAILED](capi-hicollie-h.md#hicollie_errorcode) 29800002 - Remote call error. The IPC remote service fails to be called.  For details, see [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode). |

### OH_HiCollie_Callback()

```c
typedef void (*OH_HiCollie_Callback)(void*)
```

**Description**

Triggered when [OH_HiCollie_CancelTimer](capi-hicollie-h.md#oh_hicollie_canceltimer) is not called within the custom task timeout period after [OH_HiCollie_SetTimer](capi-hicollie-h.md#oh_hicollie_settimer) is called.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 18

### OH_HiCollie_SetTimer()

```c
HiCollie_ErrorCode OH_HiCollie_SetTimer(HiCollie_SetTimerParam param, int *id)
```

**Description**

Registers a timer to check whether the execution time of a function or code block exceeds the custom time. This API is used together with the **OH_HiCollie_CancelTimer** API.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiCollie_SetTimerParam](capi-hicollie-hicollie-settimerparam.md) param | Input parameters. |
| int *id | Pointer to the returned timer ID, which should not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | [HICOLLIE_SUCCESS](capi-hicollie-h.md#hicollie_errorcode) 0 - Operation successful.  [HICOLLIE_INVALID_TIMER_NAME](capi-hicollie-h.md#hicollie_errorcode) 29800003 - Invalid timer name. The timer name cannot be NULL or an empty string.  [HICOLLIE_INVALID_TIMEOUT_VALUE](capi-hicollie-h.md#hicollie_errorcode) 29800004 - Invalid timeout value.  [HICOLLIE_WRONG_PROCESS_CONTEXT](capi-hicollie-h.md#hicollie_errorcode) 29800005 - Invalid process context for detection. This function cannot be  called in the appspawn and nativespawn processes.  [HICOLLIE_WRONG_TIMER_ID_OUTPUT_PARAM](capi-hicollie-h.md#hicollie_errorcode) 29800006 - The pointer used to save the returned timer ID is NULL.  For details, see [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode). |

### OH_HiCollie_CancelTimer()

```c
void OH_HiCollie_CancelTimer(int id)
```

**Description**

Cancels a timer based on the ID. This API is used together with the **OH_HiCollie_SetTimer** API. It must be used after the function or code block is executed. If a timer is not canceled within the custom time, a callback function is executed to generate fault logs for the specified timeout event.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| int id | Timer ID updated after the [OH_HiCollie_SetTimer](capi-hicollie-h.md#oh_hicollie_settimer) function is executed. |

### OH_HiCollie_FreezeCallback()

```c
typedef size_t (*OH_HiCollie_FreezeCallback)(OH_HiCollie_Freeze_Type type, void* buffer, size_t size)
```

**Description**

the freeze callback used in [OH_HiCollie_SetFreezeCallback](capi-hicollie-h.md#oh_hicollie_setfreezecallback)

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiCollie_Freeze_Type](capi-hicollie-h.md#oh_hicollie_freeze_type) type | Freeze event type in [OH_HiCollie_Freeze_Type](capi-hicollie-h.md#oh_hicollie_freeze_type) |
| void\* buffer | log buffer provided by the system, whose content will be moved to APP_FREEZE or APP_HICOLLIE HiAppEvent |
| size_t size | buffer size can be used |

**Returns**:

| Type | Description |
| -- | -- |
| size_t | used buffer size |

### OH_HiCollie_SetFreezeCallback()

```c
void* OH_HiCollie_SetFreezeCallback(OH_HiCollie_FreezeCallback callback)
```

**Description**

Sets the freeze event callback in the system. The system calls this function when a freeze event occurs.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiCollie_FreezeCallback](capi-hicollie-h.md#oh_hicollie_freezecallback) callback | Callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Callback function passed last time in the current process. |

### OH_HiCollie_AssociateProcessReport()

```c
HiCollie_ErrorCode OH_HiCollie_AssociateProcessReport(bool isFreezeEvent)
```

**Description**

Reports a freeze event of a process. In this case, a **HiAppEvent** event of the **APP_HICOLLIE** type is generated.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool isFreezeEvent | Type of the reported event. **true**: A 6s freeze event. **false**: A 3s freeze event. |

**Returns**:

| Type | Description |
| -- | -- |
| [HiCollie_ErrorCode](capi-hicollie-h.md#hicollie_errorcode) | HICOLLIE_SUCCESS: 0 - The operation is successful.  OH_HICOLLIE_REACH_REPORT_LIMIT: 29800007 - The reporting frequency is too high. |


