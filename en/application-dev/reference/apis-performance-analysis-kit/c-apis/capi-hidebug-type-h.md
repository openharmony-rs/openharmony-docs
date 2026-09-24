# hidebug_type.h

## Overview

Defines the code of the HiDebug module.

**Library**: libohhidebug.so

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Related module**: [HiDebug](capi-hidebug.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [HiDebug_ThreadCpuUsage](capi-hidebug-hidebug-threadcpuusage.md) | HiDebug_ThreadCpuUsage | Defines the struct for the CPU usage of all threads of an application. |
| [HiDebug_SystemMemInfo](capi-hidebug-hidebug-systemmeminfo.md) | HiDebug_SystemMemInfo | Defines a struct for the system memory information. |
| [HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md) | HiDebug_NativeMemInfo | Defines the struct for the local memory information of the application process. |
| [HiDebug_MemoryLimit](capi-hidebug-hidebug-memorylimit.md) | HiDebug_MemoryLimit | Defines the struct for the memory limit of the application process. |
| [OH_HiDebug_RequestTraceConfig](capi-hidebug-oh-hidebug-requesttraceconfig.md) | OH_HiDebug_RequestTraceConfig | Defines a struct for the trace collection configuration. |
| [HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md) | HiDebug_MallocDispatch | Defines the struct types of the replaceable/restorable **HiDebug_MallocDispatch** table of the application process. |
| [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) | HiDebug_JsStackFrame | Defines a struct for the JS stack frame content. |
| [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) | HiDebug_NativeStackFrame | Defines the native stack frame content. |
| [HiDebug_StackFrame](capi-hidebug-hidebug-stackframe.md) | HiDebug_StackFrame | Defines the stack frame content. |
| [HiDebug_GraphicsMemorySummary](capi-hidebug-hidebug-graphicsmemorysummary.md) | HiDebug_GraphicsMemorySummary | Defines a struct for the application graphics memory usage details. |
| [HiDebug_ProcessSamplerConfig](capi-hidebug-hidebug-processsamplerconfig.md) | HiDebug_ProcessSamplerConfig | Defines a struct for sampling configuration. |
| [OH_HiDebug_ProfilingResult](capi-hidebug-oh-hidebug-profilingresult.md) | OH_HiDebug_ProfilingResult | Defines a struct for encapsulating the result of a single resource collection. |
| [OH_HiDebug_ResProfilerConfig](capi-hidebug-oh-hidebug-resprofilerconfig.md) | OH_HiDebug_ResProfilerConfig | Defines a struct for the resource collection configurations. |
| [HiDebug_Backtrace_Object\_\_*](capi-hidebug-hidebug-backtrace-object--8h.md) | HiDebug_Backtrace_Object | Defines an object used for stack backtracing and stack parsing. |
| [HiDebug_ThreadCpuUsage*](capi-hidebug-hidebug-threadcpuusage8h.md) | HiDebug_ThreadCpuUsagePtr | Defines pointer of HiDebug_ThreadCpuUsage. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [HiDebug_ErrorCode](#hidebug_errorcode) | HiDebug_ErrorCode | Enumerates the error codes used in the HiDebug module. |
| [HiDebug_TraceFlag](#hidebug_traceflag) | HiDebug_TraceFlag | Enumerates the thread types for trace collection. |
| [HiDebug_StackFrameType](#hidebug_stackframetype) | HiDebug_StackFrameType | Enumerates the stack frame types. |
| [HiDebug_CrashObjType](#hidebug_crashobjtype) | HiDebug_CrashObjType | Enumerates the data types of debugging information. |
| [OH_HiDebug_ResourceType](#oh_hidebug_resourcetype) | OH_HiDebug_ResourceType | Enumerates the resource profiling types. |
| [OH_HiDebug_MemListenerType](#oh_hidebug_memlistenertype) | OH_HiDebug_MemListenerType | Enumerates the memory listener callback types. You can process the related logic based on the callback type. |

### Macro

| Name | Description |
| -- | -- |
| HIDEBUG_TRACE_TAG_FFRT (1ULL << 13) | FFRT tasks.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_COMMON_LIBRARY (1ULL << 16) | Common library subsystem tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_HDF (1ULL << 18) | HDF subsystem tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_NET (1ULL << 23) | Net tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_NWEB (1ULL << 24) | NWeb tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_AUDIO (1ULL << 27) | Distributed audio tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_FILE_MANAGEMENT (1ULL << 29) | File management tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_OHOS (1ULL << 30) | OHOS generic tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_ABILITY_MANAGER (1ULL << 31) | Ability Manager tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_CAMERA (1ULL << 32) | Camera module tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_MEDIA (1ULL << 33) | Media module tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_IMAGE (1ULL << 34) | Image module tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_AUDIO (1ULL << 35) | Audio module tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_DATA (1ULL << 36) | Distributed data manager module tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_GRAPHICS (1ULL << 38) | Graphics module tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_ARKUI (1ULL << 39) | ARKUI development framework tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_NOTIFICATION (1ULL << 40) | Notification module tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_MISC (1ULL << 41) | MISC module tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_MULTIMODAL_INPUT (1ULL << 42) | Multimodal input module tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_RPC (1ULL << 46) | RPC tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_ARK (1ULL << 47) | ARK tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_WINDOW_MANAGER (1ULL << 48) | Window manager tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_SCREEN (1ULL << 50) | Distributed screen tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_CAMERA (1ULL << 51) | Distributed camera tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_FRAMEWORK (1ULL << 52) | Distributed hardware framework tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_GLOBAL_RESOURCE_MANAGER (1ULL << 53) | Global resource manager tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_DEVICE_MANAGER (1ULL << 54) | Distributed hardware device manager tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_SAMGR (1ULL << 55) | SA tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_POWER_MANAGER (1ULL << 56) | Power manager tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_SCHEDULER (1ULL << 57) | Distributed scheduler tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_INPUT (1ULL << 59) | Distributed input tag.<br>**Since**: 12 |
| HIDEBUG_TRACE_TAG_BLUETOOTH (1ULL << 60) | bluetooth tag.<br>**Since**: 12 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_HiDebug_RequestTraceCallback)(HiDebug_ErrorCode errorCode, const char* filePath)](#oh_hidebug_requesttracecallback) | OH_HiDebug_RequestTraceCallback | Triggered for the trace collection request. |
| [typedef void (\*OH_HiDebug_ProfilingCallback)(OH_HiDebug_ProfilingResult* result)](#oh_hidebug_profilingcallback) | OH_HiDebug_ProfilingCallback | Triggered for the resource profiling. |

### Variable

| Name | Description |
| -- | -- |
| HiDebug_ThreadCpuUsage* HiDebug_ThreadCpuUsagePtr | Defines pointer of HiDebug_ThreadCpuUsage.<br>**Since**: 12 |
| void (*OH_HiDebug_RequestTraceCallback)(HiDebug_ErrorCode errorCode, const char* filePath) | Triggered for the trace collection request.<br>**Since**: 24 |
| void (*OH_HiDebug_ProfilingCallback)(OH_HiDebug_ProfilingResult* result) | Triggered for the resource profiling.<br>**Since**: 24 |

## Enum type description

### HiDebug_ErrorCode

```c
enum HiDebug_ErrorCode
```

**Description**

Enumerates the error codes used in the HiDebug module.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

| Enum item | Description |
| -- | -- |
| HIDEBUG_SUCCESS = 0 | Operation successful. |
| HIDEBUG_INVALID_ARGUMENT = 401 | Invalid parameter. Possible causes: 1. The parameter value is incorrect. 2. The parameter type is incorrect. |
| HIDEBUG_TRACE_CAPTURED_ALREADY = 11400102 | Repeated collection. |
| HIDEBUG_NO_PERMISSION = 11400103 | No file write permission. |
| HIDEBUG_TRACE_ABNORMAL = 11400104 | Internal system error. |
| HIDEBUG_NO_TRACE_RUNNING = 11400105 | No trace task is running. |
| OH_HIDEBUG_TRACE_STORAGE_LIMIT = 11400120 |  |
| HIDEBUG_INVALID_SYMBOLIC_PC_ADDRESS = 11400200 |  |
| HIDEBUG_NOT_SUPPORTED = 11400300 |  |
| HIDEBUG_UNDER_SAMPLING = 11400301 |  |
| HIDEBUG_RESOURCE_UNAVAILABLE = 11400302 |  |
| HIDEBUG_RES_PROF_SUCCESS = 11400400 |  |
| HIDEBUG_RES_PROF_INVALID_ARG = 11400410 |  |
| HIDEBUG_RES_PROF_INVALID_MAX_DURATION = 11400411 |  |
| HIDEBUG_RES_PROF_INVALID_FILTER_SIZE = 11400412 |  |
| HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH = 11400413 |  |
| HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL = 11400414 |  |
| HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL = 11400415 |  |
| HIDEBUG_RES_PROF_INVALID_RESOURCE_TYPE = 11400416 |  |
| HIDEBUG_RES_PROF_PERMISSION_DENIED = 11400420 |  |
| HIDEBUG_RES_PROF_ALREADY_STARTED = 11400421 |  |
| HIDEBUG_RES_PROF_NOT_STARTED = 11400422 |  |
| HIDEBUG_RES_PROF_PROCESS_OVERLIMIT = 11400423 |  |
| HIDEBUG_RES_PROF_CONFLICT = 11400424 |  |
| HIDEBUG_RES_PROF_AUTO_STOPPED_BY_DURATION = 11400425 |  |
| HIDEBUG_RES_PROF_DAILY_QUOTA_EXCEEDED = 11400426 |  |
| HIDEBUG_RES_PROF_CPU_OVERLOADED = 11400427 |  |
| HIDEBUG_RES_PROF_MEM_PRESSURE_CRITICAL = 11400428 |  |
| HIDEBUG_RES_PROF_STORAGE_PRESSURE_CRITICAL = 11400429 |  |
| HIDEBUG_RES_PROF_FAILURE = 11400430 |  |
| HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_NESTING_DEPTH = 11400431 | Invalid maximum asynchronous nesting depth.<br>**Since**: 26.0.1 |
| HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_TASK_STACK_DEPTH = 11400432 | Invalid maximum asynchronous task stack depth.<br>**Since**: 26.0.1 |

### HiDebug_TraceFlag

```c
enum HiDebug_TraceFlag
```

**Description**

Enumerates the thread types for trace collection.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

| Enum item | Description |
| -- | -- |
| HIDEBUG_TRACE_FLAG_MAIN_THREAD = 1 | Only the main thread of the current application. |
| HIDEBUG_TRACE_FLAG_ALL_THREADS = 2 | All threads of the application. |

### HiDebug_StackFrameType

```c
enum HiDebug_StackFrameType
```

**Description**

Enumerates the stack frame types.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

| Enum item | Description |
| -- | -- |
| HIDEBUG_STACK_FRAME_TYPE_JS = 1 | JS stack frame. |
| HIDEBUG_STACK_FRAME_TYPE_NATIVE = 2 | Native stack frame. |

### HiDebug_CrashObjType

```c
enum HiDebug_CrashObjType
```

**Description**

Enumerates the data types of debugging information.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 23

| Enum item | Description |
| -- | -- |
| HIDEBUG_CRASHOBJ_STRING = 0 | String. |
| HIDEBUG_CRASHOBJ_MEMORY_64B = 1 | 64-byte memory block. |
| HIDEBUG_CRASHOBJ_MEMORY_256B = 2 | 256-byte memory block. |
| HIDEBUG_CRASHOBJ_MEMORY_1024B = 3 | 1024-byte memory block. |
| HIDEBUG_CRASHOBJ_MEMORY_2048B = 4 | 2048-byte memory block. |
| HIDEBUG_CRASHOBJ_MEMORY_4096B = 5 | 4096-byte memory block. |

### OH_HiDebug_ResourceType

```c
enum OH_HiDebug_ResourceType
```

**Description**

Enumerates the resource profiling types.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_RES_TYPE_FD |  |
| OH_RES_TYPE_THREAD |  |
| OH_RES_TYPE_NATIVE |  |
| OH_RES_TYPE_GPU |  |
| OH_RES_TYPE_GLOBAL_HANDLE |  |
| OH_RES_TYPE_DMA | DMA memory.<br>**Since**: 26.0.1 |
| OH_RES_TYPE_ASHMEM | Anonymous Shared Memory.<br>**Since**: 26.0.1 |
| OH_RES_TYPE_COMPOSITE_HEAP | Composite heap.<br>**Since**: 26.0.1 |

### OH_HiDebug_MemListenerType

```c
enum OH_HiDebug_MemListenerType
```

**Description**

Enumerates the memory listener callback types. You can process the related logic based on the callback type.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_HIDEBUG_DO_NOTHING = 0 |  |
| OH_HIDEBUG_RUNNING_GC = 1 |  |
| OH_HIDEBUG_DUMP_SNAPSHOT = 2 |  |


## Function description

### OH_HiDebug_RequestTraceCallback()

```c
typedef void (*OH_HiDebug_RequestTraceCallback)(HiDebug_ErrorCode errorCode, const char* filePath)
```

**Description**

Triggered for the trace collection request.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode) errorCode | Result code. For details, see [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode). |
| const char\* filePath | Pointer to the collected trace file. If the operation fails, a null pointer may be returned. |

### OH_HiDebug_ProfilingCallback()

```c
typedef void (*OH_HiDebug_ProfilingCallback)(OH_HiDebug_ProfilingResult* result)
```

**Description**

Triggered for the resource profiling.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiDebug_ProfilingResult](capi-hidebug-oh-hidebug-profilingresult.md)\* result | Pointer to the parameters of the resource profiling callback function. |


