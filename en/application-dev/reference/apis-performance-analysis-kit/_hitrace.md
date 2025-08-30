# Hitrace


## Overview

HiTraceMeter provides APIs for system performance tracing.

You can call the APIs provided by HiTraceMeter in your own service logic to effectively track service processes and check the system performance.

HiTraceChain provides APIs for cross-thread and cross-process distributed tracing.

HiTraceChain generates a unique chain ID for a service process and passes it to various information (including application events, system events, and logs) specific to the service process. During debugging and fault locating, you can use the unique chain ID to quickly correlate various information related to the service process.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10


## Summary


### Files

| Name| Description| 
| -------- | -------- |
| [trace.h](trace_8h.md) | Defines APIs of the HiTraceMeter module for performance trace. | 


### Structs

| Name| Description| 
| -------- | -------- |
| struct&nbsp;&nbsp;[HiTraceId](_hi_trace_id.md) | Defines a **HiTraceId** instance. | 


### Types

| Name| Description| 
| -------- | -------- |
| typedef enum [HiTraceId_Valid](#hitraceid_valid) [HiTraceId_Valid](#hitraceid_valid) | Defines an enum for whether **HiTraceId** is valid. | 
| typedef enum [HiTrace_Version](#hitrace_version) [HiTrace_Version](#hitrace_version) | Defines an enum for the HiTrace versions. | 
| typedef enum [HiTrace_Flag](#hitrace_flag) [HiTrace_Flag](#hitrace_flag) | Defines an enum for the HiTrace flags. | 
| typedef enum [HiTrace_Tracepoint_Type](#hitrace_tracepoint_type) [HiTrace_Tracepoint_Type](#hitrace_tracepoint_type) | Defines an enum for the HiTrace tracepoint types. | 
| typedef enum [HiTrace_Communication_Mode](#hitrace_communication_mode) [HiTrace_Communication_Mode](#hitrace_communication_mode) | Defines an enum for the HiTrace communication modes. |
| typedef enum [HiTrace_Output_Level](#hitrace_output_level)[HiTrace_Output_Level](#hitrace_output_level) | Defines an enum for the HiTrace output levels. |  
| typedef struct [HiTraceId](_hi_trace_id.md) [HiTraceId](_hi_trace_id.md) | Defines a struct for the HiTrace ID.| 


### Enums

| Name| Description| 
| -------- | -------- |
| [HiTraceId_Valid](#hitraceid_valid) { HITRACE_ID_INVALID = 0, HITRACE_ID_VALID = 1 } | Enumerates whether a **HiTraceId** instance is valid. | 
| [HiTrace_Version](#hitrace_version) { HITRACE_VER_1 = 0 } | Enumerates the HiTrace versions. | 
| [HiTrace_Flag](#hitrace_flag) {<br>HITRACE_FLAG_DEFAULT = 0, HITRACE_FLAG_INCLUDE_ASYNC = 1 &lt;&lt; 0, HITRACE_FLAG_DONOT_CREATE_SPAN = 1 &lt;&lt; 1, HITRACE_FLAG_TP_INFO = 1 &lt;&lt; 2,<br>HITRACE_FLAG_NO_BE_INFO = 1 &lt;&lt; 3, HITRACE_FLAG_DONOT_ENABLE_LOG = 1 &lt;&lt; 4, HITRACE_FLAG_FAULT_TRIGGER = 1 &lt;&lt; 5, HITRACE_FLAG_D2D_TP_INFO = 1 &lt;&lt; 6<br>} | Enumerates the HiTrace flags. | 
| [HiTrace_Tracepoint_Type](#hitrace_tracepoint_type) {<br>HITRACE_TP_CS = 0, HITRACE_TP_CR = 1, HITRACE_TP_SS = 2, HITRACE_TP_SR = 3,<br>HITRACE_TP_GENERAL = 4<br>} | Enumerates the HiTrace tracepoint types. | 
| [HiTrace_Communication_Mode](#hitrace_communication_mode) { HITRACE_CM_DEFAULT = 0, HITRACE_CM_THREAD = 1, HITRACE_CM_PROCESS = 2, HITRACE_CM_DEVICE = 3 } | Enumerates the HiTrace communication modes. | 
| [HiTrace_Output_Level](#hitrace_output_level) {<br>HITRACE_LEVEL_DEBUG = 0, HITRACE_LEVEL_INFO = 1, HITRACE_LEVEL_CRITICAL = 2, HITRACE_LEVEL_COMMERCIAL = 3,<br>HITRACE_LEVEL_MAX = HITRACE_LEVEL_COMMERCIAL<br>} | Enumerates the HiTrace output levels. | 


### Functions

| Name| Description| 
| -------- | -------- |
| [HiTraceId](_hi_trace_id.md) [OH_HiTrace_BeginChain](#oh_hitrace_beginchain) (const char \*name, int flags) | Starts tracing a process. | 
| void [OH_HiTrace_EndChain](#oh_hitrace_endchain) () | Stops tracing the process and clears the trace ID of the calling thread if the given trace ID is valid. Otherwise, no operation is performed. | 
| [HiTraceId](_hi_trace_id.md) [OH_HiTrace_GetId](#oh_hitrace_getid) () | Obtains the trace ID of the calling thread. If the calling thread does not have a trace ID, an invalid trace ID is returned. | 
| void [OH_HiTrace_SetId](#oh_hitrace_setid) (const [HiTraceId](_hi_trace_id.md) \*id) | Sets the trace ID of the calling thread. If the ID is invalid, no operation is performed. | 
| void [OH_HiTrace_ClearId](#oh_hitrace_clearid) (void) | Clears the trace ID of the calling thread and invalidates it. | 
| [HiTraceId](_hi_trace_id.md) [OH_HiTrace_CreateSpan](#oh_hitrace_createspan) (void) | Creates a span ID based on the trace ID of the calling thread. | 
| void [OH_HiTrace_Tracepoint](#oh_hitrace_tracepoint) ([HiTrace_Communication_Mode](#hitrace_communication_mode) mode, [HiTrace_Tracepoint_Type](#hitrace_tracepoint_type) type, const [HiTraceId](_hi_trace_id.md) \*id, const char \*fmt,...) | Prints HiTrace information, including the trace ID. | 
| void [OH_HiTrace_InitId](#oh_hitrace_initid) ([HiTraceId](_hi_trace_id.md) \*id) | Initializes a **HiTraceId** instance. | 
| void [OH_HiTrace_IdFromBytes](#oh_hitrace_idfrombytes) ([HiTraceId](_hi_trace_id.md) \*id, const uint8_t \*pIdArray, int len) | Creates a **HiTraceId** instance based on a byte array. | 
| bool [OH_HiTrace_IsIdValid](#oh_hitrace_isidvalid) (const [HiTraceId](_hi_trace_id.md) \*id) | Checks whether a **HiTraceId** instance is valid. | 
| bool [OH_HiTrace_IsFlagEnabled](#oh_hitrace_isflagenabled) (const [HiTraceId](_hi_trace_id.md) \*id, [HiTrace_Flag](#hitrace_flag) flag) | Checks whether the specified trace flag is enabled in a **HiTraceId** instance. | 
| void [OH_HiTrace_EnableFlag](#oh_hitrace_enableflag) (const [HiTraceId](_hi_trace_id.md) \*id, [HiTrace_Flag](#hitrace_flag) flag) | Enables the specified trace flag in a **HiTraceId** instance. | 
| int [OH_HiTrace_GetFlags](#oh_hitrace_getflags) (const [HiTraceId](_hi_trace_id.md) \*id) | Obtains the trace flags in a **HiTraceId** instance. | 
| void [OH_HiTrace_SetFlags](#oh_hitrace_setflags) ([HiTraceId](_hi_trace_id.md) \*id, int flags) | Sets trace flags in a **HiTraceId** instance. | 
| uint64_t [OH_HiTrace_GetChainId](#oh_hitrace_getchainid) (const [HiTraceId](_hi_trace_id.md) \*id) | Obtains a trace chain ID. | 
| void [OH_HiTrace_SetChainId](#oh_hitrace_setchainid) ([HiTraceId](_hi_trace_id.md) \*id, uint64_t chainId) | Sets the trace chain ID in a **HiTraceId** instance. | 
| uint64_t [OH_HiTrace_GetSpanId](#oh_hitrace_getspanid) (const [HiTraceId](_hi_trace_id.md) \*id) | Obtains the span ID in a **HiTraceId** instance. | 
| void [OH_HiTrace_SetSpanId](#oh_hitrace_setspanid) ([HiTraceId](_hi_trace_id.md) \*id, uint64_t spanId) | Sets the span ID in a **HiTraceId** instance. | 
| uint64_t [OH_HiTrace_GetParentSpanId](#oh_hitrace_getparentspanid) (const [HiTraceId](_hi_trace_id.md) \*id) | Obtains the parent span ID in a **HiTraceId** instance. | 
| void [OH_HiTrace_SetParentSpanId](#oh_hitrace_setparentspanid) ([HiTraceId](_hi_trace_id.md) \*id, uint64_t parentSpanId) | Sets the **ParentSpanId** in a **HiTraceId** instance. | 
| int [OH_HiTrace_IdToBytes](#oh_hitrace_idtobytes) (const [HiTraceId](_hi_trace_id.md) \*id, uint8_t \*pIdArray, int len) | Converts a **HiTraceId** instance into a byte array for caching or transfer. | 
| void [OH_HiTrace_StartTrace](#oh_hitrace_starttrace) (const char \*name) | Marks the start of a synchronous trace. | 
| void [OH_HiTrace_FinishTrace](#oh_hitrace_finishtrace) (void) | Marks the end of a synchronous trace. | 
| void [OH_HiTrace_StartAsyncTrace](#oh_hitrace_startasynctrace) (const char \*name, int32_t taskId) | Marks the start of an asynchronous trace. | 
| void [OH_HiTrace_FinishAsyncTrace](#oh_hitrace_finishasynctrace) (const char \*name, int32_t taskId) | Marks the end of an asynchronous trace. | 
| void [OH_HiTrace_CountTrace](#oh_hitrace_counttrace) (const char \*name, int64_t count) | Traces the value change of an integer variable based on its name. | 
| void [OH_HiTrace_StartTraceEx](#oh_hitrace_starttraceex) ([HiTrace_Output_Level](#hitrace_output_level) level, const char \*name, const char \*customArgs) | Marks the start of a synchronous trace task with the trace output level specified. | 
| void [OH_HiTrace_FinishTraceEx](#oh_hitrace_finishtraceex) ([HiTrace_Output_Level](#hitrace_output_level) level) | Marks the end of a synchronous trace task with the trace output level specified. | 
| void [OH_HiTrace_StartAsyncTraceEx](#oh_hitrace_startasynctraceex) ([HiTrace_Output_Level](#hitrace_output_level) level, const char \*name, int32_t taskId, const char \*customCategory, const char \*customArgs) | Marks the start of an asynchronous trace task with the trace output level specified. | 
| void [OH_HiTrace_FinishAsyncTraceEx](#oh_hitrace_finishasynctraceex) ([HiTrace_Output_Level](#hitrace_output_level) level, const char \*name, int32_t taskId) | Marks the end of an asynchronous trace task with the trace output level specified. | 
| void [OH_HiTrace_CountTraceEx](#oh_hitrace_counttraceex) ([HiTrace_Output_Level](#hitrace_output_level) level, const char \*name, int64_t count) | Marks an integer variable trace task with the trace output level specified. | 
| bool [OH_HiTrace_IsTraceEnabled](#oh_hitrace_istraceenabled) (void) | Checks whether trace capture is enabled for an application. If not, HiTraceMeter performance tracing is invalid. | 


## Type Description


### HiTrace_Communication_Mode

```
typedef enum HiTrace_Communication_ModeHiTrace_Communication_Mode
```
**Description**
Defines an enum for the HiTrace communication modes.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


### HiTrace_Flag

```
typedef enum HiTrace_FlagHiTrace_Flag
```
**Description**
Defines an enum for the HiTrace flags.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


### HiTrace_Output_Level

```
typedef enum HiTrace_Output_Level HiTrace_Output_Level
```
**Description**
Defines an enum for the HiTrace output levels.

The trace output level lower than the threshold does not take effect. The log version threshold is **HITRACE_LEVEL_INFO**, and the nolog version threshold is **HITRACE_LEVEL_COMMERCIAL**.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 19


### HiTrace_Tracepoint_Type

```
typedef enum HiTrace_Tracepoint_Type HiTrace_Tracepoint_Type
```
**Description**
Defines an enum for the HiTrace tracepoint types.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


### HiTrace_Version

```
typedef enum HiTrace_Version HiTrace_Version
```
**Description**
Defines an enum for the HiTrace versions.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


### HiTraceId_Valid

```
typedef enum HiTraceId_Valid HiTraceId_Valid
```
**Description**
Defines an enum for whether a **HiTraceId** instance is valid.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


## Enum Description


### HiTrace_Communication_Mode

```
enum HiTrace_Communication_Mode
```
**Description**
Enumerates the HiTrace communication modes.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Value| Description| 
| -------- | -------- |
| HITRACE_CM_DEFAULT | Unspecified.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_CM_THREAD | Inter-thread communication.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_CM_PROCESS | Inter-process communication (IPC).<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_CM_DEVICE | Inter-device communication.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 


### HiTrace_Flag

```
enum HiTrace_Flag
```
**Description**
Enumerates the HiTrace flags.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Value| Description| 
| -------- | -------- |
| HITRACE_FLAG_DEFAULT | Default value.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_FLAG_INCLUDE_ASYNC | Both synchronous and asynchronous calls are traced. By default, only synchronous calls are traced.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_FLAG_DONOT_CREATE_SPAN | Do not create a child span. By default, a child span is created.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_FLAG_TP_INFO | Trace points are automatically added to spans. By default, no trace point is added.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_FLAG_NO_BE_INFO | Information about the start and end of the trace task is not printed. By default, information about the start and end of the trace task is printed.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_FLAG_DONOT_ENABLE_LOG | The ID is not added to the log. By default, the ID is added to the log.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_FLAG_FAULT_TRIGGER | Tracing is triggered by faults.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_FLAG_D2D_TP_INFO | Trace points are added only for call chain trace between devices. By default, device-to-device trace points are not added.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 


### HiTrace_Output_Level

```
enum HiTrace_Output_Level
```
**Description**
Enumerates the HiTrace output levels.

The trace output level lower than the threshold does not take effect. The log version threshold is **HITRACE_LEVEL_INFO**, and the nolog version threshold is **HITRACE_LEVEL_COMMERCIAL**.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 19

| Value| Description| 
| -------- | -------- |
| HITRACE_LEVEL_DEBUG  | Level used only for debugging, which has the lowest priority.| 
| HITRACE_LEVEL_INFO  | Level for the log version.| 
| HITRACE_LEVEL_CRITICAL  | Level for the log version, which has a higher priority than **INFO**.| 
| HITRACE_LEVEL_COMMERCIAL  | Level for the nolog version, which has the highest priority.| 
| HITRACE_LEVEL_MAX  | The maximum output level.| 


### HiTrace_Tracepoint_Type

```
enum HiTrace_Tracepoint_Type
```
**Description**
Enumerates the HiTrace tracepoint types.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Value| Description| 
| -------- | -------- |
| HITRACE_TP_CS | CS trace point<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_TP_CR | CR trace point<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_TP_SS | SS trace point<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_TP_SR | SR trace point<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_TP_GENERAL | General trace point<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 


### HiTrace_Version

```
enum HiTrace_Version
```
**Description**
Enumerates the HiTrace versions.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Value| Description| 
| -------- | -------- |
| HITRACE_VER_1 | Version 1.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 


### HiTraceId_Valid

```
enum HiTraceId_Valid
```
**Description**
Enumerates whether a **HiTraceId** instance is valid.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

| Value| Description| 
| -------- | -------- |
| HITRACE_ID_INVALID | Invalid **HiTraceId**.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 
| HITRACE_ID_VALID | Valid **HiTraceId**.<br>SysCap:<br>SystemCapability.HiviewDFX.HiTrace | 


## Function Description


### OH_HiTrace_BeginChain()

```
HiTraceId OH_HiTrace_BeginChain (const char * name, int flags )
```
**Description**
Starts tracing a process.

This API starts tracing, creates a **HiTraceId** instance, and sets it to the TLS of the calling thread. This API works only when it is called for the first time.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| name | Name of the traced service. | 
| flags | Flags of the tracing. For details, see [HiTrace_Flag](#hitrace_flag). | 

**Return value**

Returns the generated **HitraceId**. For details, see [HiTraceId](_hi_trace_id.md).


### OH_HiTrace_ClearId()

```
void OH_HiTrace_ClearId (void )
```
**Description**
Clears the trace ID of the calling thread and invalidates it.

This API clears the **HiTraceId** instance in the TLS of the calling thread.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


### OH_HiTrace_CountTrace()

```
void OH_HiTrace_CountTrace (const char * name, int64_t count )
```
**Description**
Traces the value change of an integer variable based on its name.

This API can be executed for multiple times to trace the value change of a given integer variable at different time points.

Since API version 19, you are advised to use the **OH_HiTrace_CountTraceEx** API to specify the trace output level.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10

**Parameters**

| Name| Description| 
| -------- | -------- |
| name | Name of the integer variable. It does not need to be the same as the real variable name. | 
| count | Integer value.| 


### OH_HiTrace_CountTraceEx()

```
void OH_HiTrace_CountTraceEx(HiTrace_Output_Level level, const char *name, int64_t count)
```
**Description**
Marks an integer variable trace task with the trace output level specified.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Since**: 19

**Parameters**

| Name| Description| 
| -------- | -------- |
| level | Trace output level. | 
| name | Name of the integer variable. It does not need to be the same as the actual variable name. | 
| count | Integer value.| 


### OH_HiTrace_CreateSpan()

```
HiTraceId OH_HiTrace_CreateSpan (void )
```
**Description**
Creates a span ID based on the trace ID of the calling thread.

This API generates a new span and corresponding **HiTraceId** instance based on the **HiTraceId** instance in the TLS of the calling thread.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Return value**

Returns a valid span trace ID. For details, see [HiTraceId](_hi_trace_id.md). If the span ID cannot be created, the ID of the calling thread is traced.


### OH_HiTrace_EnableFlag()

```
void OH_HiTrace_EnableFlag (const HiTraceId * id, HiTrace_Flag flag )
```
**Description**
Enables the specified trace flag in a **HiTraceId** instance.

 

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | Trace ID for which the flag needs to be enabled. For details, see [HiTraceId](_hi_trace_id.md). | 
| flag | Specified trace flag needs to be enabled in the trace ID. For details, see [HiTrace_Flag](#hitrace_flag).| 


### OH_HiTrace_EndChain()

```
void OH_HiTrace_EndChain ()
```
**Description**
Stops tracing the process and clears the trace ID of the calling thread if the given trace ID is valid. Otherwise, no operation is performed.

 

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12


### OH_HiTrace_FinishAsyncTrace()

```
void OH_HiTrace_FinishAsyncTrace (const char * name, int32_t taskId )
```
**Description**
Marks the end of an asynchronous trace.

This API is called in the callback function after an asynchronous trace is complete.

It is used with **OH_HiTrace_StartAsyncTrace** in pairs. Its name and task ID must be the same as those of **OH_HiTrace_StartAsyncTrace**.

Since API version 19, you are advised to use the **OH_HiTrace_FinishAsyncTraceEx** API to specify the trace output level.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10

**Parameters**

| Name| Description| 
| -------- | -------- |
| name | Name of the asynchronous trace. | 
| taskId | ID of the asynchronous trace. The start and end of an asynchronous trace task do not occur in sequence. Therefore, the start and end of an asynchronous trace need to be matched based on the task name and the unique task ID together.| 


### OH_HiTrace_FinishAsyncTraceEx()

```
void OH_HiTrace_FinishAsyncTraceEx(HiTrace_Output_Level level, const char *name, int32_t taskId)
```
**Description**
Marks the end of an asynchronous trace task with the trace output level specified.

This API is used to stop tracing after an asynchronous operation is complete, for example, in a callback function.

It is used with **OH_HiTrace_StartAsyncTraceEx** in pairs. Its level, name and task ID must be the same as those of **OH_HiTrace_StartAsyncTraceEx**.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Since**: 19

**Parameters**

| Name| Description| 
| -------- | -------- |
| level | Trace output level. | 
| name | Name of the asynchronous trace. | 
| taskId | ID of the asynchronous trace.| 


### OH_HiTrace_FinishTrace()

```
void OH_HiTrace_FinishTrace(void)
```
**Description**
Marks the end of a synchronous trace.

This API must be used with **OH_HiTrace_StartTrace** in pairs. During trace parsing, the system matches it with the **OH_HiTrace_StartTrace** API recently invoked in the service process.

Since API version 19, you are advised to use the **OH_HiTrace_FinishTraceEx** API to specify the trace output level.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10


### OH_HiTrace_FinishTraceEx()

```
void OH_HiTrace_FinishTraceEx(HiTrace_Output_Level level)
```
**Description**
Marks the end of a synchronous trace task with the trace output level specified.

It must be used with **OH_HiTrace_StartTraceEx** in pairs. Its level must be the same as those of **OH_HiTrace_StartTraceEx**.

During trace data parsing, the system matches it with the **OH_HiTrace_StartTraceEx** API recently invoked in the service process.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Since**: 19

**Parameters**

| Name| Description| 
| -------- | -------- |
| level | Trace output level.| 


### OH_HiTrace_GetChainId()

```
uint64_t OH_HiTrace_GetChainId (const HiTraceId * id)
```
**Description**
Obtains a trace chain ID.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance for which you want to obtain the trace chain ID. For details, see [HiTraceId](_hi_trace_id.md).| 

**Return value**

Returns the trace chain ID of the specified **HiTraceId** instance.


### OH_HiTrace_GetFlags()

```
int OH_HiTrace_GetFlags (const HiTraceId * id)
```
**Description**
Obtains the trace flags in a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance for which you want to obtain the flag. For details, see [HiTraceId](_hi_trace_id.md).| 

**Return value**

Returns the trace flags set in the specified **HiTraceId** instance.


### OH_HiTrace_GetId()

```
HiTraceId OH_HiTrace_GetId ()
```
**Description**
Obtains the trace ID in TLS of the calling thread. If the calling thread does not have a trace ID, an invalid trace ID is returned.

 

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Return value**

Returns the [HiTraceId](_hi_trace_id.md) of the calling thread. Returns an invalid **HiTraceId** if the calling thread does not have a **HiTraceId**.


### OH_HiTrace_GetParentSpanId()

```
uint64_t OH_HiTrace_GetParentSpanId (const HiTraceId * id)
```
**Description**
Obtains the parent span ID in a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance for which you want to obtain the parent span ID. For details, see [HiTraceId](_hi_trace_id.md).| 

**Return value**

Returns the parent span ID in the specified **HiTraceId** instance.


### OH_HiTrace_GetSpanId()

```
uint64_t OH_HiTrace_GetSpanId (const HiTraceId * id)
```
**Description**
Obtains the span ID in a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance for which you want to obtain the span ID. For details, see [HiTraceId](_hi_trace_id.md).| 

**Return value**

Returns the span ID in the specified **HiTraceId** instance.


### OH_HiTrace_IdFromBytes()

```
void OH_HiTrace_IdFromBytes (HiTraceId * id, const uint8_t * pIdArray, int len )
```
**Description**
Creates a **HiTraceId** instance based on a byte array.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **[HiTraceId](_hi_trace_id.md)** instance to create. | 
| pIdArray | Byte array. | 
| len | Length of the byte array.| 


### OH_HiTrace_IdToBytes()

```
int OH_HiTrace_IdToBytes (const HiTraceId * id, uint8_t * pIdArray, int len )
```
**Description**
Converts a **HiTraceId** instance into a byte array for caching or transfer.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance to convert. For details, see [HiTraceId](_hi_trace_id.md). | 
| pIdArray | Byte array. | 
| len | Length of the byte array.| 

**Return value**

Returns the length of the byte array after conversion.


### OH_HiTrace_InitId()

```
void OH_HiTrace_InitId (HiTraceId * id)
```
**Description**
Initializes a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **[HiTraceId](_hi_trace_id.md)** instance to initialize.| 


### OH_HiTrace_IsFlagEnabled()

```
bool OH_HiTrace_IsFlagEnabled (const HiTraceId * id, HiTrace_Flag flag )
```
**Description**
Checks whether the specified trace flag is enabled in a **HiTraceId** instance.

* 

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance to check. For details, see [HiTraceId](_hi_trace_id.md). | 
| flag | Specified trace flag. For details, see [HiTrace_Flag](#hitrace_flag). | 

**Return value**

Returns **true** if the specified trace flag is enabled; returns **false** otherwise.


### OH_HiTrace_IsIdValid()

```
bool OH_HiTrace_IsIdValid (const HiTraceId * id)
```
**Description**
Checks whether a **HiTraceId** instance is valid.

* 

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance to check. For details, see [HiTraceId](_hi_trace_id.md). | 

**Return value**

Returns **true** if the **HiTraceId** instance is valid; returns **false** otherwise.


### OH_HiTrace_IsTraceEnabled()

```
bool OH_HiTrace_IsTraceEnabled()
```
**Description**
Checks whether trace capture is enabled for an application. If not, HiTraceMeter performance tracing is invalid.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Since**: 19

**Return value**

Returns **true** if the application trace capture is enabled and the HiTraceMeter performance tracing takes effect;

returns **false** otherwise.


### OH_HiTrace_SetChainId()

```
void OH_HiTrace_SetChainId (HiTraceId * id, uint64_t chainId )
```
**Description**
Sets the trace chain ID in a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance. For details, see [HiTraceId](_hi_trace_id.md). | 
| chainId | Trace chain ID to set.| 


### OH_HiTrace_SetFlags()

```
void OH_HiTrace_SetFlags (HiTraceId * id, int flags )
```
**Description**
Sets trace flags in a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance. For details, see [HiTraceId](_hi_trace_id.md). | 
| flags | Trace flag to set. For details, see [HiTrace_Flag](#hitrace_flag).| 


### OH_HiTrace_SetId()

```
void OH_HiTrace_SetId (const HiTraceId * id)
```
**Description**
Sets the trace ID of the calling thread. If the ID is invalid, no operation is performed.

This API sets a **HiTraceId** instance to the TLS of the calling thread.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | Trace ID of the calling thread. For details, see [HiTraceId](_hi_trace_id.md).| 


### OH_HiTrace_SetParentSpanId()

```
void OH_HiTrace_SetParentSpanId (HiTraceId * id, uint64_t parentSpanId )
```
**Description**
Sets the **ParentSpanId** in a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance. For details, see [HiTraceId](_hi_trace_id.md). | 
| parentSpanId | Parent span ID to set.| 


### OH_HiTrace_SetSpanId()

```
void OH_HiTrace_SetSpanId (HiTraceId * id, uint64_t spanId )
```
**Description**
Sets the span ID in a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| id | **HiTraceId** instance. | 
| spanId | Span ID to set.| 


### OH_HiTrace_StartAsyncTrace()

```
void OH_HiTrace_StartAsyncTrace (const char * name, int32_t taskId )
```
**Description**
Starts an asynchronous trace.

This API is used to start tracing before an asynchronous operation. The start and end of an asynchronous trace do not occur in sequence. Therefore, a unique task ID is required to identify them.

It must be used with **OH_HiTrace_FinishAsyncTrace** in pairs. The start and end identified by the same name and task ID constitute an asynchronous trace task.

If multiple trace tasks with the same name need to be performed at the same time or a trace task needs to be performed multiple times concurrently, different task IDs must be specified.

If the trace tasks with the same name are not performed at the same time, the same **taskId** can be used.

Since API version 19, you are advised to use the **OH_HiTrace_StartAsyncTraceEx** API to specify the trace output level and category.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10

**Parameters**

| Name| Description| 
| -------- | -------- |
| name | Name of the asynchronous trace. | 
| taskId | ID of the asynchronous trace. The start and end of an asynchronous trace task do not occur in sequence. Therefore, the start and end of an asynchronous trace need to be matched based on the task name and the unique task ID together.| 


### OH_HiTrace_StartAsyncTraceEx()

```
void OH_HiTrace_StartAsyncTraceEx(HiTrace_Output_Level level, const char *name, int32_t taskId, const char *customCategory, const char *customArgs)
```
**Description**
Marks the start of an asynchronous trace task with the trace output level specified.

This API is used to start tracing before an asynchronous operation. The start and end of an asynchronous trace do not occur in sequence. Therefore, a unique task ID is required to identify them.

It is used with **OH_HiTrace_FinishAsyncTraceEx** in pairs. The start and end identified by the same name and task ID constitute an asynchronous trace task.

If multiple trace tasks with the same name need to be performed at the same time or a trace task needs to be performed multiple times concurrently, different task IDs must be specified.

If the trace tasks with the same name are not performed at the same time, the same **taskId** can be used.

Task IDs of different processes does not interfere with each other.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Since**: 19

**Parameters**

| Name| Description| 
| -------- | -------- |
| level | Trace output level. | 
| name | Name of the asynchronous trace. | 
| taskId | ID of the asynchronous trace. | 
| customCategory | Custom category name, which is used to collect asynchronous trace data of the same type. | 
| customArgs | Key-value pair. Use commas (,) to separate multiple key-value pairs, for example, "key1=value1,key2=value2".| 


### OH_HiTrace_StartTrace()

```
void OH_HiTrace_StartTrace(const char *name)
```
**Description**
Marks the start of a synchronous trace.

This API is used with **OH_HiTrace_FinishTrace** in pairs.

The two APIs can be nested. The stack data structure is used for matching during trace parsing.

Since API version 19, you are advised to use the **OH_HiTrace_StartTraceEx** API to specify the trace output level.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10

**Parameters**

| Name| Description| 
| -------- | -------- |
| name | Name of a synchronous trace.| 


### OH_HiTrace_StartTraceEx()

```
void OH_HiTrace_StartTraceEx(HiTrace_Output_Level level, const char *name, const char *customArgs)
```
**Description**
Marks the start of a synchronous trace task with the trace output level specified.

This API is used with **OH_HiTrace_FinishTraceEx** in pairs.

The two APIs can be nested. The stack data structure is used for matching during trace parsing.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Since**: 19

**Parameters**

| Name| Description| 
| -------- | -------- |
| level | Trace output level. | 
| name | Name of a synchronous trace. | 
| customArgs | Key-value pair. Use commas (,) to separate multiple key-value pairs, for example, "key1=value1,key2=value2".| 


### OH_HiTrace_Tracepoint()

```
void OH_HiTrace_Tracepoint (HiTrace_Communication_Mode mode, HiTrace_Tracepoint_Type type, const HiTraceId * id, const char * fmt,  ... )
```
**Description**
Prints HiTrace information, including the trace ID.

This API prints trace point information, including the communication mode, trace point type, timestamp, and span.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Parameters**

| Name| Description| 
| -------- | -------- |
| mode | Communication mode for the trace point. For details, see [HiTrace_Communication_Mode](#hitrace_communication_mode). | 
| type | Trace point type. For details, see [HiTrace_Tracepoint_Type](#hitrace_tracepoint_type). | 
| id | Trace ID. For details, see [HiTraceId](_hi_trace_id.md). | 
| fmt | Custom information to print.| 


## Variable Description


### chainId

```
uint64_t HiTraceId::chainId
```
**Description**
Chain ID of **HiTraceId**.


### flags

```
uint64_t HiTraceId::flags
```
**Description**
Flag of **HiTraceId**.


### parentSpanId

```
uint64_t HiTraceId::parentSpanId
```
**Description**
Parent span ID of **HiTraceId**.


### spanId

```
uint64_t HiTraceId::spanId
```
**Description**
Span ID of **HiTraceId**.


### valid

```
uint64_t HiTraceId::valid
```
**Description**
Whether a **HiTraceId** instance is valid.


### ver

```
uint64_t HiTraceId::ver
```
**Description**
Version number of **HiTraceId**.
