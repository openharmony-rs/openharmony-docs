# trace.h


## Overview

Defines APIs of the HiTraceMeter module for performance trace.

The vertical bar (|) is used as the separator in user-mode trace format. Therefore, the string parameters passed by the HiTraceMeter APIs must exclude this character to avoid trace parsing exceptions.

The maximum length of a user-mode trace is 512 characters. Excess characters will be truncated.

**Library**: libhitrace_ndk.z.so

**File to include**: <hitrace/trace.h>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10

**Related module**: [HiTrace](_hitrace.md)


## Summary


### Structs

| Name| Description| 
| -------- | -------- |
| struct&nbsp;&nbsp;[HiTraceId](_hi_trace_id.md) | Defines a **HiTraceId** instance. | 


### Types

| Name| Description| 
| -------- | -------- |
| typedef enum [HiTraceId_Valid](_hitrace.md#hitraceid_valid) [HiTraceId_Valid](_hitrace.md#hitraceid_valid) | Defines an enum for whether **HiTraceId** is valid. | 
| typedef enum [HiTrace_Version](_hitrace.md#hitrace_version) [HiTrace_Version](_hitrace.md#hitrace_version) | Defines an enum for the HiTrace versions. | 
| typedef enum [HiTrace_Flag](_hitrace.md#hitrace_flag) [HiTrace_Flag](_hitrace.md#hitrace_flag) | Defines an enum for the HiTrace flags. | 
| typedef enum [HiTrace_Tracepoint_Type](_hitrace.md#hitrace_tracepoint_type) [HiTrace_Tracepoint_Type](_hitrace.md#hitrace_tracepoint_type) | Defines an enum for the HiTrace tracepoint types. | 
| typedef enum [HiTrace_Communication_Mode](_hitrace.md#hitrace_communication_mode) [HiTrace_Communication_Mode](_hitrace.md#hitrace_communication_mode) | Defines an enum for the communication modes. | 
| typedef enum [HiTrace_Output_Level](_hitrace.md#hitrace_output_level) [HiTrace_Output_Level](_hitrace.md#hitrace_output_level) | Defines an enum for the HiTrace output levels. | 
|  typedef struct [HiTraceId](_hi_trace_id.md)**HiTraceId** |  | 


### Enums

| Name| Description| 
| -------- | -------- |
| [HiTraceId_Valid](_hitrace.md#hitraceid_valid) {<br>HITRACE_ID_INVALID = 0, <br>HITRACE_ID_VALID = 1<br>} | Enumerates whether a **HiTraceId** instance is valid. | 
| [HiTrace_Version](_hitrace.md#hitrace_version) {<br>HITRACE_VER_1 = 0<br>} | Enumerates the HiTrace versions. | 
| [HiTrace_Flag](_hitrace.md#hitrace_flag) {<br>HITRACE_FLAG_DEFAULT = 0, <br>HITRACE_FLAG_INCLUDE_ASYNC = 1 &lt;&lt; 0, <br>HITRACE_FLAG_DONOT_CREATE_SPAN = 1 &lt;&lt; 1, <br>HITRACE_FLAG_TP_INFO = 1 &lt;&lt; 2,<br>HITRACE_FLAG_NO_BE_INFO = 1 &lt;&lt; 3, <br>HITRACE_FLAG_DONOT_ENABLE_LOG = 1 &lt;&lt; 4, <br>HITRACE_FLAG_FAULT_TRIGGER = 1 &lt;&lt; 5, <br>HITRACE_FLAG_D2D_TP_INFO = 1 &lt;&lt; 6<br>} | Enumerates the HiTrace flags. | 
| [HiTrace_Tracepoint_Type](_hitrace.md#hitrace_tracepoint_type) {<br>HITRACE_TP_CS = 0, <br>HITRACE_TP_CR = 1, <br>HITRACE_TP_SS = 2, <br>HITRACE_TP_SR = 3,<br>HITRACE_TP_GENERAL = 4<br>} | Enumerates the HiTrace tracepoint types. | 
| [HiTrace_Communication_Mode](_hitrace.md#hitrace_communication_mode) {<br>HITRACE_CM_DEFAULT = 0, <br>HITRACE_CM_THREAD = 1, <br>HITRACE_CM_PROCESS = 2, <br>HITRACE_CM_DEVICE = 3<br>} | Enumerates the HiTrace communication modes. | 
| [HiTrace_Output_Level](_hitrace.md#hitrace_output_level) {<br>HITRACE_LEVEL_DEBUG = 0, <br>HITRACE_LEVEL_INFO = 1, <br>HITRACE_LEVEL_CRITICAL = 2, <br>HITRACE_LEVEL_COMMERCIAL = 3, <br>HITRACE_LEVEL_MAX = HITRACE_LEVEL_COMMERCIAL<br>} | Enumerates the HiTrace output levels. | 


### Functions

| Name| Description| 
| -------- | -------- |
| [HiTraceId](_hi_trace_id.md) [OH_HiTrace_BeginChain](_hitrace.md#oh_hitrace_beginchain) (const char \*name, int flags) | Starts tracing a process. | 
| void [OH_HiTrace_EndChain](_hitrace.md#oh_hitrace_endchain) () | Stops tracing the process and clears the trace ID of the calling thread if the given trace ID is valid. Otherwise, no operation is performed. | 
| [HiTraceId](_hi_trace_id.md) [OH_HiTrace_GetId](_hitrace.md#oh_hitrace_getid) () | Obtains the trace ID of the calling thread. If the calling thread does not have a trace ID, an invalid trace ID is returned. | 
| void [OH_HiTrace_SetId](_hitrace.md#oh_hitrace_setid) (const [HiTraceId](_hi_trace_id.md) \*id) | Sets the trace ID of the calling thread. If the ID is invalid, no operation is performed. | 
| void [OH_HiTrace_ClearId](_hitrace.md#oh_hitrace_clearid) (void) | Clears the trace ID of the calling thread and invalidates it. | 
| [HiTraceId](_hi_trace_id.md) [OH_HiTrace_CreateSpan](_hitrace.md#oh_hitrace_createspan) (void) | Creates a span ID based on the trace ID of the calling thread. | 
| void [OH_HiTrace_Tracepoint](_hitrace.md#oh_hitrace_tracepoint) ([HiTrace_Communication_Mode](_hitrace.md#hitrace_communication_mode) mode, [HiTrace_Tracepoint_Type](_hitrace.md#hitrace_tracepoint_type) type, const [HiTraceId](_hi_trace_id.md) \*id, const char \*fmt,...) | Prints HiTrace information, including the trace ID. | 
| void [OH_HiTrace_InitId](_hitrace.md#oh_hitrace_initid) ([HiTraceId](_hi_trace_id.md) \*id) | Initializes a **HiTraceId** instance. | 
| void [OH_HiTrace_IdFromBytes](_hitrace.md#oh_hitrace_idfrombytes) ([HiTraceId](_hi_trace_id.md) \*id, const uint8_t \*pIdArray, int len) | Creates a **HiTraceId** instance based on a byte array. | 
| bool [OH_HiTrace_IsIdValid](_hitrace.md#oh_hitrace_isidvalid) (const [HiTraceId](_hi_trace_id.md) \*id) | Checks whether a **HiTraceId** instance is valid. | 
| bool [OH_HiTrace_IsFlagEnabled](_hitrace.md#oh_hitrace_isflagenabled) (const [HiTraceId](_hi_trace_id.md) \*id, [HiTrace_Flag](_hitrace.md#hitrace_flag) flag) | Checks whether the specified trace flag is enabled in a **HiTraceId** instance. | 
| void [OH_HiTrace_EnableFlag](_hitrace.md#oh_hitrace_enableflag) (const [HiTraceId](_hi_trace_id.md) \*id, [HiTrace_Flag](_hitrace.md#hitrace_flag) flag) | Enables the specified trace flag in a **HiTraceId** instance. | 
| int [OH_HiTrace_GetFlags](_hitrace.md#oh_hitrace_getflags) (const [HiTraceId](_hi_trace_id.md) \*id) | Obtains the trace flags in a **HiTraceId** instance. | 
| void [OH_HiTrace_SetFlags](_hitrace.md#oh_hitrace_setflags) ([HiTraceId](_hi_trace_id.md) \*id, int flags) | Sets trace flags in a **HiTraceId** instance. | 
| uint64_t [OH_HiTrace_GetChainId](_hitrace.md#oh_hitrace_getchainid) (const [HiTraceId](_hi_trace_id.md) \*id) | Obtains a trace chain ID. | 
| void [OH_HiTrace_SetChainId](_hitrace.md#oh_hitrace_setchainid) ([HiTraceId](_hi_trace_id.md) \*id, uint64_t chainId) | Sets the trace chain ID in a **HiTraceId** instance. | 
| uint64_t [OH_HiTrace_GetSpanId](_hitrace.md#oh_hitrace_getspanid) (const [HiTraceId](_hi_trace_id.md) \*id) | Obtains the span ID in a **HiTraceId** instance. | 
| void [OH_HiTrace_SetSpanId](_hitrace.md#oh_hitrace_setspanid) ([HiTraceId](_hi_trace_id.md) \*id, uint64_t spanId) | Sets the span ID in a **HiTraceId** instance. | 
| uint64_t [OH_HiTrace_GetParentSpanId](_hitrace.md#oh_hitrace_getparentspanid) (const [HiTraceId](_hi_trace_id.md) \*id) | Obtains the parent span ID in a **HiTraceId** instance. | 
| void [OH_HiTrace_SetParentSpanId](_hitrace.md#oh_hitrace_setparentspanid) ([HiTraceId](_hi_trace_id.md) \*id, uint64_t parentSpanId) | Sets the **ParentSpanId** in a **HiTraceId** instance. | 
| int [OH_HiTrace_IdToBytes](_hitrace.md#oh_hitrace_idtobytes) (const [HiTraceId](_hi_trace_id.md) \*id, uint8_t \*pIdArray, int len) | Converts a **HiTraceId** instance into a byte array for caching or transfer. | 
| void [OH_HiTrace_StartTrace](_hitrace.md#oh_hitrace_starttrace) (const char \*name) | Marks the start of a synchronous trace. | 
| void [OH_HiTrace_FinishTrace](_hitrace.md#oh_hitrace_finishtrace) (void) | Marks the end of a synchronous trace. | 
| void [OH_HiTrace_StartAsyncTrace](_hitrace.md#oh_hitrace_startasynctrace) (const char \*name, int32_t taskId) | Marks the start of an asynchronous trace. | 
| void [OH_HiTrace_FinishAsyncTrace](_hitrace.md#oh_hitrace_finishasynctrace) (const char \*name, int32_t taskId) | Marks the end of an asynchronous trace. | 
| void [OH_HiTrace_CountTrace](_hitrace.md#oh_hitrace_counttrace) (const char \*name, int64_t count) | Traces the value change of an integer variable based on its name. | 
| void [OH_HiTrace_StartTraceEx](_hitrace.md#oh_hitrace_starttraceex) ([HiTrace_Output_Level](_hitrace.md#hitrace_output_level) level, const char \*name, const char \*customArgs) | Marks the start of a synchronous trace task with the trace output level specified. | 
| void [OH_HiTrace_FinishTraceEx](_hitrace.md#oh_hitrace_finishtraceex) ([HiTrace_Output_Level](_hitrace.md#hitrace_output_level) level) | Marks the end of a synchronous trace task with the trace output level specified. | 
| void [OH_HiTrace_StartAsyncTraceEx](_hitrace.md#oh_hitrace_startasynctraceex) ([HiTrace_Output_Level](_hitrace.md#hitrace_output_level) level, const char \*name, int32_t taskId, const char \*customCategory, const char \*customArgs) | Marks the start of an asynchronous trace task with the trace output level specified. | 
| void [OH_HiTrace_FinishAsyncTraceEx](_hitrace.md#oh_hitrace_finishasynctraceex) ([HiTrace_Output_Level](_hitrace.md#hitrace_output_level) level, const char \*name, int32_t taskId) | Marks the end of an asynchronous trace task with the trace output level specified. | 
| void [OH_HiTrace_CountTraceEx](_hitrace.md#oh_hitrace_counttraceex) ([HiTrace_Output_Level](_hitrace.md#hitrace_output_level) level, const char \*name, int64_t count) | Marks an integer variable trace task with the trace output level specified. | 
| bool [OH_HiTrace_IsTraceEnabled](_hitrace.md#oh_hitrace_istraceenabled) (void) | Checks whether trace capture is enabled for an application. If not, HiTraceMeter performance tracing is invalid. | 
