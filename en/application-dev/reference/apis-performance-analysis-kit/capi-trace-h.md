# trace.h

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @qq_437963121-->
<!--Designer: @kutcherzhou1; @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Defines the APIs of the HiTraceMeter and HiTraceChain modules. The APIs implement performance measurement and distributed tracing.<br>The user-mode trace format uses vertical bars (|) as separators. Therefore, the string parameters passed through the HiTraceMeter APIs must not contain vertical bars (|) to prevent trace parsing exceptions.<br>The maximum length of a user-mode trace is 512 characters. Excess characters will be truncated.

**File to include**: <hitrace/trace.h>

**Library**: libhitrace_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10

**Related module**: [HiTrace](capi-hitrace.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) | HiTraceId | Defines a **HiTraceId** instance.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [HiTraceId_Valid](#hitraceid_valid) | HiTraceId_Valid | Enumerates whether a **HiTraceId** instance is valid.|
| [HiTrace_Version](#hitrace_version) | HiTrace_Version | Enumerates the HiTrace versions.|
| [HiTrace_Flag](#hitrace_flag) | HiTrace_Flag | Enumerates the HiTrace trace flags.|
| [HiTrace_Tracepoint_Type](#hitrace_tracepoint_type) | HiTrace_Tracepoint_Type | Enumerates the trace point types.|
| [HiTrace_Communication_Mode](#hitrace_communication_mode) | HiTrace_Communication_Mode | Enumerates the trace communication types.|
| [HiTrace_Output_Level](#hitrace_output_level) | HiTrace_Output_Level | Enumerates the HiTrace output levels. The trace output level lower than the threshold does not take effect. The log version threshold is **HITRACE_LEVEL_INFO**, and the nolog version threshold is **HITRACE_LEVEL_COMMERCIAL**.|

### Functions

| Name| Description|
| -- | -- |
| [HiTraceId OH_HiTrace_BeginChain(const char *name, int flags)](#oh_hitrace_beginchain) | Starts tracing.<br> If the thread local storage (TLS) of the current thread does not contain a valid HiTrace ID, this function generates a valid HiTrace ID, sets it to the TLS of the current thread, and returns the HiTrace ID.<br> If the TLS of the current thread already contains a valid HiTrace ID, no new tracing is started, and an invalid HiTrace ID with all attribute values being 0 is returned.<br>|
| [void OH_HiTrace_EndChain()](#oh_hitrace_endchain) | Ends tracing.<br> Ends tracing and sets the HiTrace ID in the TLS of the current thread to invalid.<br>|
| [HiTraceId OH_HiTrace_GetId()](#oh_hitrace_getid) | Obtains the trace ID.<br> Obtains the HiTrace ID in the TLS of the current thread.<br>|
| [void OH_HiTrace_SetId(const HiTraceId *id)](#oh_hitrace_setid) | Sets the trace ID.<br> Sets the given HiTrace ID to the TLS of the current thread. If the given HiTrace ID is invalid, no operation is performed.<br>|
| [void OH_HiTrace_ClearId(void)](#oh_hitrace_clearid) | Clears the trace ID.<br> Sets the HiTrace ID in the TLS of the current thread to invalid.<br>|
| [HiTraceId OH_HiTrace_CreateSpan(void)](#oh_hitrace_createspan) | Creates a trace span.<br> Specifically, create a **HiTraceId**, use the **chainId** and **spanId** in the Thread-Local Storage (TLS) of the current thread to initialize the **chainId** and **parentSpanId** of the **HiTraceId**, generate a new **spanId** for the **HiTraceId**, and return the **HiTraceId**.<br>|
| [void OH_HiTrace_Tracepoint(HiTrace_Communication_Mode mode, HiTrace_Tracepoint_Type type, const HiTraceId *id, const char *fmt, ...)](#oh_hitrace_tracepoint) | Adds a tracing point to HiTraceMeter.<br>If type is set to CS (client sends) or SC (server receives), HiTraceMeter starts tracing.<br>If type is set to CC (client receives) or SS (server sends), HiTraceMeter stops tracing.<br>If type is set to GENERAL, HiTraceMeter does not trace.<br>If type is set to CS or CC, the information tracing points must be used together.<br>If type is set to SC or SS, the information tracing points must be used together.<br>Otherwise, the start and end tracing points of HiTraceMeter cannot match.|
| [void OH_HiTrace_InitId(HiTraceId *id)](#oh_hitrace_initid) | Initializes a **HiTraceId**.|
| [void OH_HiTrace_IdFromBytes(HiTraceId *id, const uint8_t *pIdArray, int len)](#oh_hitrace_idfrombytes) | Creates a **HiTraceId** based on a byte array.|
| [bool OH_HiTrace_IsIdValid(const HiTraceId *id)](#oh_hitrace_isidvalid) | Checks whether HiTraceId is valid.|
| [bool OH_HiTrace_IsFlagEnabled(const HiTraceId *id, HiTrace_Flag flag)](#oh_hitrace_isflagenabled) | Checks whether the tracing flag is enabled for HiTraceId.|
| [void OH_HiTrace_EnableFlag(const HiTraceId *id, HiTrace_Flag flag)](#oh_hitrace_enableflag) | Enables the trace flag specified in **HiTraceId**.|
| [int OH_HiTrace_GetFlags(const HiTraceId *id)](#oh_hitrace_getflags) | Obtains the trace flag set in **HiTraceId**.|
| [void OH_HiTrace_SetFlags(HiTraceId *id, int flags)](#oh_hitrace_setflags) | Sets the trace flag to HiTraceId.|
| [uint64_t OH_HiTrace_GetChainId(const HiTraceId *id)](#oh_hitrace_getchainid) | Obtains the trace chain ID in **HiTraceId**.|
| [void OH_HiTrace_SetChainId(HiTraceId *id, uint64_t chainId)](#oh_hitrace_setchainid) | Sets the trace chain ID in **HiTraceId**.|
| [uint64_t OH_HiTrace_GetSpanId(const HiTraceId *id)](#oh_hitrace_getspanid) | Obtains the branch ID in HiTraceId.|
| [void OH_HiTrace_SetSpanId(HiTraceId *id, uint64_t spanId)](#oh_hitrace_setspanid) | Sets the span ID in **HiTraceId**.|
| [uint64_t OH_HiTrace_GetParentSpanId(const HiTraceId *id)](#oh_hitrace_getparentspanid) | Obtains the parent branch ID in HiTraceId.|
| [void OH_HiTrace_SetParentSpanId(HiTraceId *id, uint64_t parentSpanId)](#oh_hitrace_setparentspanid) | Sets the **ParentSpanId** in a **HiTraceId** instance.|
| [int OH_HiTrace_IdToBytes(const HiTraceId* id, uint8_t* pIdArray, int len)](#oh_hitrace_idtobytes) | Converts HiTraceId to a byte array for cache or communication.|
| [void OH_HiTrace_StartTrace(const char *name)](#oh_hitrace_starttrace) | Marks the start of a synchronous trace.<br> This API is used with **OH_HiTrace_FinishTrace()** in pairs.<br> The two APIs can be nested. The stack data structure is used for matching during trace parsing.<br> Since API version 19, you are advised to use the **OH_HiTrace_StartTraceEx()** API to specify the trace output level.<br>|
| [void OH_HiTrace_FinishTrace(void)](#oh_hitrace_finishtrace) | Marks the end of a synchronous trace.<br> This API must be used with **OH_HiTrace_StartTrace()** in pairs. During trace parsing, the system matches it with the **OH_HiTrace_StartTrace()** API recently invoked in the service process.<br> Since API version 19, you are advised to use the **OH_HiTrace_FinishTraceEx()** API to specify the trace output level.<br>|
| [void OH_HiTrace_StartAsyncTrace(const char *name, int32_t taskId)](#oh_hitrace_startasynctrace) | Marks the start of an asynchronous trace.<br> This API is used to start tracing before an asynchronous operation. The start and end of an asynchronous trace do not occur in sequence. Therefore, a unique task ID is required to identify them.<br> It must be used with **OH_HiTrace_FinishAsyncTrace()** in pairs. The start and end identified by the same name and task ID constitute an asynchronous trace task.<br> If multiple tasks with the same name need to be traced or the same task needs to be traced for multiple times and the tasks are executed at the same time, the taskId of each call must be different.<br> If the trace tasks with the same name are not performed at the same time, the same **taskId** can be used.<br> Since API version 19, you are advised to use the **OH_HiTrace_StartAsyncTraceEx()** API to specify the trace output level and category.<br>|
| [void OH_HiTrace_FinishAsyncTrace(const char *name, int32_t taskId)](#oh_hitrace_finishasynctrace) | Marks the end of an asynchronous trace.<br> This API is called in the callback function after an asynchronous trace is complete.<br> It is used with **OH_HiTrace_StartAsyncTrace()** in pairs. Its name and task ID must be the same as those of **OH_HiTrace_StartAsyncTrace()**.<br> Since API version 19, you are advised to use the **OH_HiTrace_FinishAsyncTraceEx()** API to specify the trace output level.<br>|
| [void OH_HiTrace_CountTrace(const char *name, int64_t count)](#oh_hitrace_counttrace) | Traces the value change of an integer variable based on its name.<br> This API can be executed for multiple times to trace the value change of a given integer variable at different time points.<br> Since API version 19, you are advised to use the **OH_HiTrace_CountTraceEx()** API to specify the trace output level.<br>|
| [void OH_HiTrace_StartTraceEx(HiTrace_Output_Level level, const char *name, const char *customArgs)](#oh_hitrace_starttraceex) | Marks the start of a synchronous trace task with the trace output level specified.<br> This API is used with **OH_HiTrace_FinishTraceEx()** in pairs.<br> The two APIs can be nested. The stack data structure is used for matching during trace parsing.<br>|
| [void OH_HiTrace_FinishTraceEx(HiTrace_Output_Level level)](#oh_hitrace_finishtraceex) | Marks the end of a synchronous trace task with the trace output level specified.<br> It must be used with **OH_HiTrace_StartTraceEx()** in pairs. Its level must be the same as those of **OH_HiTrace_StartTraceEx()**.<br> During trace data parsing, the system matches it with the **OH_HiTrace_StartTraceEx()** API recently invoked in the service process.<br>|
| [void OH_HiTrace_StartAsyncTraceEx(HiTrace_Output_Level level, const char *name, int32_t taskId, const char *customCategory, const char *customArgs)](#oh_hitrace_startasynctraceex) | Marks the start of an asynchronous trace task with the trace output level specified.<br> This API is used to start tracing before an asynchronous operation. The start and end of an asynchronous trace do not occur in sequence. Therefore, a unique task ID is required to identify them.<br> It is used with **OH_HiTrace_FinishAsyncTraceEx()** in pairs. The start and end identified by the same name and task ID constitute an asynchronous trace task.<br> If multiple trace tasks with the same name need to be performed at the same time or a trace task needs to be performed multiple times concurrently, different task IDs must be specified.<br> If the trace tasks with the same name are not performed at the same time, the same **taskId** can be used.<br> Task IDs of different processes does not interfere with each other.<br>|
| [void OH_HiTrace_FinishAsyncTraceEx(HiTrace_Output_Level level, const char *name, int32_t taskId)](#oh_hitrace_finishasynctraceex) | Marks the end of an asynchronous trace task with the trace output level specified.<br> This API is used to stop tracing after an asynchronous operation is complete, for example, in a callback function.<br> It is used with **OH_HiTrace_StartAsyncTraceEx()** in pairs. Its level, name and task ID must be the same as those of **OH_HiTrace_StartAsyncTraceEx()**.<br>|
| [void OH_HiTrace_CountTraceEx(HiTrace_Output_Level level, const char *name, int64_t count)](#oh_hitrace_counttraceex) | Marks an integer variable trace task with the trace output level specified.|
| [bool OH_HiTrace_IsTraceEnabled(void)](#oh_hitrace_istraceenabled) | Checks whether trace capture is enabled for an application.|

## Enum Description

### HiTraceId_Valid

```
enum HiTraceId_Valid
```

**Description**

Enumerates whether a **HiTraceId** instance is valid.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Enum Item| Description|
| -- | -- |
| HITRACE_ID_INVALID = 0 | Invalid **HiTraceId**.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_ID_VALID = 1 | Valid **HiTraceId**.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|

### HiTrace_Version

```
enum HiTrace_Version
```

**Description**

Enumerates the HiTrace versions.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Enum Item| Description|
| -- | -- |
| HITRACE_VER_1 = 0 | Version 1.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|

### HiTrace_Flag

```
enum HiTrace_Flag
```

**Description**

Enumerates the HiTrace flags.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Enum Item| Description|
| -- | -- |
| HITRACE_FLAG_DEFAULT = 0 | Default flag.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_FLAG_INCLUDE_ASYNC = 1 << 0 | Asynchronous call flag.<br>     If this flag is set, both synchronous and asynchronous calls are traced. By default, only synchronous calls are traced.<br><br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_FLAG_DONOT_CREATE_SPAN = 1 << 1 | No span flag.<br>     If this flag is set, no branch information is created. By default, branch information is created.<br><br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_FLAG_TP_INFO = 1 << 2 | Trace point flag.<br>     In the debugging scenario, if this flag is set, tracing point information is recorded in HiLog logs when the tracing point API OH_HiTrace_Tracepoint() is called. By default, tracing point information is not recorded in HiLog logs.<br><br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_FLAG_NO_BE_INFO = 1 << 3 | No begin/end flag.<br>     In the debugging scenario, if this flag is set, start and end tracing information is recorded in HiLog logs when the tracing start API OH_HiTrace_BeginChain() and tracing end API OH_HiTrace_EndChain() are called. By default, start and end tracing information is not recorded in HiLog logs.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_FLAG_DONOT_ENABLE_LOG = 1 << 4 | Log association flag.<br>     If this flag is set, HiTraceId information is not attached to HiLog logs. By default, HiTraceId information is attached to HiLog logs.<br><br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_FLAG_FAULT_TRIGGER = 1 << 5 | Failure trigger flag. This is a preset flag, which is not used currently.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_FLAG_D2D_TP_INFO = 1 << 6 | Device-to-device trace point flag. This is a subset of HITRACE_FLAG_TP_INFO and is used in the debugging scenario.<br>     If the HITRACE_FLAG_TP_INFO flag is set, the HITRACE_FLAG_D2D_TP_INFO flag does not take effect.<br> If the HITRACE_FLAG_TP_INFO flag is not set, set the HITRACE_FLAG_D2D_TP_INFO flag. In this case, the OH_HiTrace_Tracepoint() API is called to print hilog logs of the tracing point only when the mode parameter is set to HITRACE_CM_DEVICE.<br><br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|

### HiTrace_Tracepoint_Type

```
enum HiTrace_Tracepoint_Type
```

**Description**

Enumerates tracing point types.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Enum Item| Description|
| -- | -- |
| HITRACE_TP_CS = 0 | CS trace point.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_TP_CR = 1 | CR trace point.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_TP_SS = 2 | SS trace point.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_TP_SR = 3 | SR trace point.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_TP_GENERAL = 4 | General tracing point type, which indicates the tracing points except HITRACE_TP_CS, HITRACE_TP_CR, HITRACE_TP_SS, and HITRACE_TP_SR.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|

### HiTrace_Communication_Mode

```
enum HiTrace_Communication_Mode
```

**Description**

Enumerates communication types.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Enum Item| Description|
| -- | -- |
| HITRACE_CM_DEFAULT = 0 | Default communication.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_CM_THREAD = 1 | Inter-thread communication.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_CM_PROCESS = 2 | Inter-process communication (IPC).<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|
| HITRACE_CM_DEVICE = 3 | Inter-device communication.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiTrace|

### HiTrace_Output_Level

```
enum HiTrace_Output_Level
```

**Description**

Enumerates the HiTrace output levels. The trace output level lower than the threshold does not take effect. The log version threshold is **HITRACE_LEVEL_INFO**, and the nolog version threshold is **HITRACE_LEVEL_COMMERCIAL**.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 19

| Enum Item| Description|
| -- | -- |
| HITRACE_LEVEL_DEBUG = 0 | Level used only for debugging, which has the lowest priority.<br>**Since**: 19               |
| HITRACE_LEVEL_INFO = 1 | Level for the log version.<br>**Since**: 19                        |
| HITRACE_LEVEL_CRITICAL = 2 | Level for the log version, which has a higher priority than **INFO**.<br>**Since**: 19|
| HITRACE_LEVEL_COMMERCIAL = 3 | Level for the nolog version, which has the highest priority.<br>**Since**: 19                |
| HITRACE_LEVEL_MAX = HITRACE_LEVEL_COMMERCIAL | The maximum output level.<br>**Since**: 19                            |


## Function Description

### OH_HiTrace_BeginChain()

```
HiTraceId OH_HiTrace_BeginChain(const char *name, int flags)
```

**Description**

Starts tracing.<br> If no valid HiTraceId exists in the thread local storage (TLS) of the current thread, a valid HiTraceId is generated and set to the TLS of the current thread. The HiTraceId is returned.<br> If a valid HiTraceId exists in the TLS of the current thread, tracing is not started, and an invalid HiTraceId with all attribute values being 0 is returned.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const char *name | Name of the traced service.|
| int flags | Trace flag combination. For details, see [HiTrace_Flag](capi-trace-h.md#hitrace_flag).|

**Returns**

| Type| Description|
| -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) | [HiTraceId](capi-hitrace-hitraceid.md) structure.|

### OH_HiTrace_EndChain()

```
void OH_HiTrace_EndChain()
```

**Description**

Ends tracing.<br> Ends tracing and sets the HiTraceId in the TLS of the current thread to invalid.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

### OH_HiTrace_GetId()

```
HiTraceId OH_HiTrace_GetId()
```

**Description**

Obtains the trace ID.<br> Obtains the HiTraceId in the TLS of the current thread.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) | [HiTraceId](capi-hitrace-hitraceid.md) structure.|

### OH_HiTrace_SetId()

```
void OH_HiTrace_SetId(const HiTraceId *id)
```

**Description**

Sets the trace ID.<br> Sets the given HiTraceId to the TLS of the current thread. If the given HiTraceId is invalid, no operation is performed.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) to be set.|

### OH_HiTrace_ClearId()

```
void OH_HiTrace_ClearId(void)
```

**Description**

Clears the trace ID.<br> Sets the HiTraceId in the TLS of the current thread to invalid.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

### OH_HiTrace_CreateSpan()

```
HiTraceId OH_HiTrace_CreateSpan(void)
```

**Description**

Creates a trace span.<br> Specifically, create a **HiTraceId**, use the **chainId** and **spanId** in the Thread-Local Storage (TLS) of the current thread to initialize the **chainId** and **parentSpanId** of the **HiTraceId**, generate a new **spanId** for the **HiTraceId**, and return the **HiTraceId**.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) | [HiTraceId](capi-hitrace-hitraceid.md) structure.|

### OH_HiTrace_Tracepoint()

```
void OH_HiTrace_Tracepoint(HiTrace_Communication_Mode mode, HiTrace_Tracepoint_Type type, const HiTraceId *id, const char *fmt, ...)
```

**Description**

Adds a trace point for the HiTraceMeter logging.<br>If type is set to CS (client sends) and SC (server receives), the HiTraceMeter tracing point is added at the start.<br>If type is set to CC (client receives) and SS (server sends), the HiTraceMeter tracing point is added at the end.<br>If type is set to GENERAL, the HiTraceMeter tracing point is not added.<br>The information about CS (client sends) and CC (client receives) must match when type is set to CS (client sends) and CC (client receives).<br>The information about SC (server receives) and SS (server sends) must match when type is set to SC (server receives) and SS (server sends).<br>Otherwise, the start and end dotting of HiTraceMeter cannot be matched.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [HiTrace_Communication_Mode](capi-trace-h.md#hitrace_communication_mode) mode | Trace communication mode. For details, see [HiTrace_Communication_Mode](capi-trace-h.md#hitrace_communication_mode).|
| [HiTrace_Tracepoint_Type](capi-trace-h.md#hitrace_tracepoint_type) type | Trace information type. For details, see [HiTrace_Tracepoint_Type](capi-trace-h.md#hitrace_tracepoint_type).|
| [const HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) for implementing information dotting.|
| const char *fmt | Formatted string of the trace description information passed to HiTraceMeter.|

### OH_HiTrace_InitId()

```
void OH_HiTrace_InitId(HiTraceId *id)
```

**Description**

Initializes HiTraceId.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) to initialize.|

### OH_HiTrace_IdFromBytes()

```
void OH_HiTrace_IdFromBytes(HiTraceId *id, const uint8_t *pIdArray, int len)
```

**Description**

Creates HiTraceId based on the byte array.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) to create.|
| const uint8_t *pIdArray | Byte array.|
| int len | Length of the byte array.|

### OH_HiTrace_IsIdValid()

```
bool OH_HiTrace_IsIdValid(const HiTraceId *id)
```

**Description**

Checks whether the **HiTraceId** is valid.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) to be checked.|

**Returns**

| Type| Description|
| -- | -- |
| bool | true: The [HiTraceId](capi-hitrace-hitraceid.md) is valid. false: The [HiTraceId](capi-hitrace-hitraceid.md) is invalid.|

### OH_HiTrace_IsFlagEnabled()

```
bool OH_HiTrace_IsFlagEnabled(const HiTraceId *id, HiTrace_Flag flag)
```

**Description**

Checks whether the trace flag is enabled for the HiTraceId.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) that needs to determine whether the specified trace flag is enabled.|
| [HiTrace_Flag](capi-trace-h.md#hitrace_flag) flag | Specified trace flag. For details, see [HiTrace_Flag](capi-trace-h.md#hitrace_flag).|

**Returns**

| Type| Description|
| -- | -- |
| bool | true: [HiTraceId](capi-hitrace-hitraceid.md) is enabled. false: [HiTraceId](capi-hitrace-hitraceid.md) is disabled.|

### OH_HiTrace_EnableFlag()

```
void OH_HiTrace_EnableFlag(const HiTraceId *id, HiTrace_Flag flag)
```

**Description**

Enables the trace flag specified in **HiTraceId**.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) that needs to enable the specified trace flag.|
| [HiTrace_Flag](capi-trace-h.md#hitrace_flag) flag | Trace flag. For details, see [HiTrace_Flag](capi-trace-h.md#hitrace_flag).|

### OH_HiTrace_GetFlags()

```
int OH_HiTrace_GetFlags(const HiTraceId *id)
```

**Description**

Obtains the trace flag set in HiTraceId.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) whose trace flag bit needs to be obtained.|

**Returns**

| Type| Description|
| -- | -- |
| int | Trace flag field set in [HiTraceId](capi-hitrace-hitraceid.md).|

### OH_HiTrace_SetFlags()

```
void OH_HiTrace_SetFlags(HiTraceId *id, int flags)
```

**Description**

Sets the trace flag bit to [HiTraceId](capi-hitrace-hitraceid.md).

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) that needs to be set.|
| int flags | Trace flag. For details, see [HiTrace_Flag](capi-trace-h.md#hitrace_flag).|

### OH_HiTrace_GetChainId()

```
uint64_t OH_HiTrace_GetChainId(const HiTraceId *id)
```

**Description**

Obtains the trace chain ID in **HiTraceId**.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) whose trace chain ID needs to be obtained.|

**Returns**

| Type| Description|
| -- | -- |
| uint64_t | Trace chain ID.|

### OH_HiTrace_SetChainId()

```
void OH_HiTrace_SetChainId(HiTraceId *id, uint64_t chainId)
```

**Description**

Sets the trace chain ID in **HiTraceId**.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) to which the trace chain ID is to be set.|
| uint64_t chainId | Trace chain ID to set.|

### OH_HiTrace_GetSpanId()

```
uint64_t OH_HiTrace_GetSpanId(const HiTraceId *id)
```

**Description**

Obtains the branch ID in the current HiTraceId.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) whose branch ID needs to be obtained.|

**Returns**

| Type| Description|
| -- | -- |
| uint64_t | Span ID set in [HiTraceId](capi-hitrace-hitraceid.md).|

### OH_HiTrace_SetSpanId()

```
void OH_HiTrace_SetSpanId(HiTraceId *id, uint64_t spanId)
```

**Description**

Sets the span ID to HiTraceId.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) whose span ID needs to be set.|
| uint64_t spanId | Span ID to set.|

### OH_HiTrace_GetParentSpanId()

```
uint64_t OH_HiTrace_GetParentSpanId(const HiTraceId *id)
```

**Description**

Obtains the parent span ID in the current HiTraceId.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) whose parent span ID needs to be obtained.|

**Returns**

| Type| Description|
| -- | -- |
| uint64_t | Parent span ID set in [HiTraceId](capi-hitrace-hitraceid.md).|

### OH_HiTrace_SetParentSpanId()

```
void OH_HiTrace_SetParentSpanId(HiTraceId *id, uint64_t parentSpanId)
```

**Description**

Sets the **ParentSpanId** in a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [HiTraceId](capi-hitrace-hitraceid.md) *id | [HiTraceId](capi-hitrace-hitraceid.md) for which the parent span ID needs to be set.|
| uint64_t parentSpanId | Parent span ID to set.|

### OH_HiTrace_IdToBytes()

```
int OH_HiTrace_IdToBytes(const HiTraceId* id, uint8_t* pIdArray, int len)
```

**Description**

Converts HiTraceId to a byte array for cache or communication.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const HiTraceId](capi-hitrace-hitraceid.md)* id | [HiTraceId](capi-hitrace-hitraceid.md) to be converted.|
| uint8_t* pIdArray | Byte array.|
| int len | Length of the byte array.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns the length of the byte array after conversion.|

### OH_HiTrace_StartTrace()

```
void OH_HiTrace_StartTrace(const char *name)
```

**Description**

Marks the start of a synchronous trace.<br> The synchronous tracing logging APIs OH_HiTrace_StartTrace() and OH_HiTrace_FinishTrace() must be used in pairs.<br> The two APIs can be nested. The stack data structure is used for matching during trace parsing.<br> Since API version 19, you are advised to use the **OH_HiTrace_StartTraceEx()** API to specify the trace output level.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| const char *name | Name of a synchronous trace.|

### OH_HiTrace_FinishTrace()

```
void OH_HiTrace_FinishTrace(void)
```

**Description**

Marks the end of a synchronous trace.<br> This API must be used with **OH_HiTrace_StartTrace()** in pairs. During trace parsing, the system matches it with the **OH_HiTrace_StartTrace()** API recently invoked in the service process.<br> Since API version 19, you are advised to use the **OH_HiTrace_FinishTraceEx()** API to specify the trace output level.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10

### OH_HiTrace_StartAsyncTrace()

```
void OH_HiTrace_StartAsyncTrace(const char *name, int32_t taskId)
```

**Description**

Marks the start of an asynchronous trace.<br> This API is used to start tracing before an asynchronous operation. The start and end of an asynchronous trace do not occur in sequence. Therefore, a unique task ID is required to identify them.<br> It must be used with **OH_HiTrace_FinishAsyncTrace()** in pairs. The start and end identified by the same name and task ID constitute an asynchronous trace task.<br> If multiple trace tasks with the same name need to be performed at the same time or a trace task needs to be performed multiple times concurrently, different task IDs must be specified.<br> If the trace tasks with the same name are not performed at the same time, the same **taskId** can be used.<br> Since API version 19, you are advised to use the **OH_HiTrace_StartAsyncTraceEx()** API to specify the trace output level and category.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| const char *name | Name of the asynchronous trace.|
| int32_t taskId | ID of the asynchronous trace. The start and end of an asynchronous trace task do not occur in sequence. Therefore, the start and end of an asynchronous trace need to be matched based on the task name and the unique task ID together.|

### OH_HiTrace_FinishAsyncTrace()

```
void OH_HiTrace_FinishAsyncTrace(const char *name, int32_t taskId)
```

**Description**

Marks the end of an asynchronous trace.<br> This API is called in the callback function after an asynchronous trace is complete.<br> It is used with **OH_HiTrace_StartAsyncTrace()** in pairs. Its name and task ID must be the same as those of **OH_HiTrace_StartAsyncTrace()**.<br> Since API version 19, you are advised to use the **OH_HiTrace_FinishAsyncTraceEx()** API to specify the trace output level.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| const char *name | Name of the asynchronous trace.|
| int32_t taskId | ID of the asynchronous trace. The start and end of an asynchronous trace task do not occur in sequence. Therefore, the start and end of an asynchronous trace need to be matched based on the task name and the unique task ID together.|

### OH_HiTrace_CountTrace()

```
void OH_HiTrace_CountTrace(const char *name, int64_t count)
```

**Description**

Traces the value change of an integer variable based on its name.<br> This API can be executed for multiple times to trace the value change of a given integer variable at different time points.<br> Since API version 19, you are advised to use the **OH_HiTrace_CountTraceEx()** API to specify the trace output level.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| const char *name | Name of the integer variable. It does not need to be the same as the real variable name.|
| int64_t count | Integer value.|

### OH_HiTrace_StartTraceEx()

```
void OH_HiTrace_StartTraceEx(HiTrace_Output_Level level, const char *name, const char *customArgs)
```

**Description**

Marks the start of a synchronous trace task with the trace output level specified.<br> This API is used with **OH_HiTrace_FinishTraceEx()** in pairs.<br> The two APIs can be nested. The stack data structure is used for matching during trace parsing.<br>

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [HiTrace_Output_Level](capi-trace-h.md#hitrace_output_level) level | Trace output level.|
| const char *name | Name of a synchronous trace.|
| const char *customArgs | Key-value pair. Use commas (,) to separate multiple key-value pairs, for example, "key1=value1,key2=value2".|

### OH_HiTrace_FinishTraceEx()

```
void OH_HiTrace_FinishTraceEx(HiTrace_Output_Level level)
```

**Description**

Marks the end of a synchronous trace task with the trace output level specified.<br> It must be used with **OH_HiTrace_StartTraceEx()** in pairs. Its level must be the same as those of **OH_HiTrace_StartTraceEx()**.<br> During trace data parsing, the system matches it with the **OH_HiTrace_StartTraceEx()** API recently invoked in the service process.<br>

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [HiTrace_Output_Level](capi-trace-h.md#hitrace_output_level) level | Trace output level.|

### OH_HiTrace_StartAsyncTraceEx()

```
void OH_HiTrace_StartAsyncTraceEx(HiTrace_Output_Level level, const char *name, int32_t taskId, const char *customCategory, const char *customArgs)
```

**Description**

Marks the start of an asynchronous trace task with the trace output level specified.<br> This API is used to start tracing before an asynchronous operation. The start and end of an asynchronous trace do not occur in sequence. Therefore, a unique task ID is required to identify them.<br> It is used with **OH_HiTrace_FinishAsyncTraceEx()** in pairs. The start and end identified by the same name and task ID constitute an asynchronous trace task.<br> If multiple trace tasks with the same name need to be performed at the same time or a trace task needs to be performed multiple times concurrently, different task IDs must be specified.<br> If the trace tasks with the same name are not performed at the same time, the same **taskId** can be used.<br> Task IDs of different processes does not interfere with each other.<br>

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [HiTrace_Output_Level](capi-trace-h.md#hitrace_output_level) level | Trace output level.|
| const char *name | Name of the asynchronous trace.|
| int32_t taskId | ID of the asynchronous trace.|
| const char *customCategory | Custom category name, which is used to collect asynchronous trace data of the same type.|
| const char *customArgs | Key-value pair. Use commas (,) to separate multiple key-value pairs, for example, "key1=value1,key2=value2".|

### OH_HiTrace_FinishAsyncTraceEx()

```
void OH_HiTrace_FinishAsyncTraceEx(HiTrace_Output_Level level, const char *name, int32_t taskId)
```

**Description**

Marks the end of an asynchronous trace task with the trace output level specified.<br> This API is used to stop tracing after an asynchronous operation is complete, for example, in a callback function.<br> It is used with **OH_HiTrace_StartAsyncTraceEx()** in pairs. Its level, name and task ID must be the same as those of **OH_HiTrace_StartAsyncTraceEx()**.<br>

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [HiTrace_Output_Level](capi-trace-h.md#hitrace_output_level) level | Trace output level.|
| const char *name | Name of the asynchronous trace.|
| int32_t taskId | ID of the asynchronous trace.|

### OH_HiTrace_CountTraceEx()

```
void OH_HiTrace_CountTraceEx(HiTrace_Output_Level level, const char *name, int64_t count)
```

**Description**

Marks an integer variable trace task with the trace output level specified.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [HiTrace_Output_Level](capi-trace-h.md#hitrace_output_level) level | Trace output level.|
| const char *name | Name of the integer variable. It does not need to be the same as the actual variable name.|
| int64_t count | Integer value.|

### OH_HiTrace_IsTraceEnabled()

```
bool OH_HiTrace_IsTraceEnabled(void)
```

**Description**

Checks whether trace capture is enabled for an application.

**Since**: 19

**Returns**

| Type| Description|
| -- | -- |
| bool | When it is enabled, **true** is returned;<br> when it is disabled or stopped, **false** is returned. In this case, calling the HiTraceMeter API does not take effect.|
