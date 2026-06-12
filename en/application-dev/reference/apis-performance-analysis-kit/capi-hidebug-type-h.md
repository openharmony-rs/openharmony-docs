# hidebug_type.h

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

## Overview

Defines the structs of the HiDebug module.

**File to include**: <hidebug/hidebug_type.h>

**Library**: libohhidebug.so

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Related module**: [HiDebug](capi-hidebug.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [HiDebug_ThreadCpuUsage](capi-hidebug-hidebug-threadcpuusage.md) | HiDebug_ThreadCpuUsage | Defines the CPU usage of all threads in an application.|
| [HiDebug_SystemMemInfo](capi-hidebug-hidebug-systemmeminfo.md) | HiDebug_SystemMemInfo | Defines the system memory information.|
| [HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md) | HiDebug_NativeMemInfo | Defines the local memory information of an application process.|
| [HiDebug_MemoryLimit](capi-hidebug-hidebug-memorylimit.md) | HiDebug_MemoryLimit | Defines the memory limit of an application process.|
| [OH_HiDebug_RequestTraceConfig](capi-hidebug-oh-hidebug-requesttraceconfig.md) | OH_HiDebug_RequestTraceConfig | Defines the trace collection configuration.|
| [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) | HiDebug_JsStackFrame | Defines the JS stack frame content.|
| [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) | HiDebug_NativeStackFrame | Defines the native stack frame content.|
| [HiDebug_StackFrame](capi-hidebug-hidebug-stackframe.md) | HiDebug_StackFrame | Defines the stack frame content.|
| [HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md) | HiDebug_MallocDispatch | Defines the struct types of the replaceable/restorable **HiDebug_MallocDispatch** table of the application process.|
| [HiDebug_GraphicsMemorySummary](capi-hidebug-hidebug-graphicsmemorysummary.md) | HiDebug_GraphicsMemorySummary | Defines the application graphics memory usage details.|
| [HiDebug_ProcessSamplerConfig](capi-hidebug-hidebug-processsamplerconfig.md) | HiDebug_ProcessSamplerConfig | Defines the sampling configuration.|
| [HiDebug_Backtrace_Object__*](capi-hidebug-hidebug-backtrace-object--8h.md) | HiDebug_Backtrace_Object | Defines the object used for stack backtracing and stack parsing.|
| [HiDebug_ThreadCpuUsage*](capi-hidebug-hidebug-threadcpuusage.md) | HiDebug_ThreadCpuUsagePtr | Defines the pointer to **HiDebug_ThreadCpuUsage**.|
| [OH_HiDebug_ResProfilerConfig](capi-hidebug-oh-hidebug-resprofilerconfig.md) | OH_HiDebug_ResProfilerConfig | Defines the resource profiling configurations.|
| [OH_HiDebug_ProfilingResult](capi-hidebug-oh-hidebug-profilingresult.md) | OH_HiDebug_ProfilingResult | Define the encapsulated result of a single resource profiling.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [HiDebug_ErrorCode](#hidebug_errorcode) | HiDebug_ErrorCode | Enumerates the error codes used in the HiDebug module.|
| [HiDebug_TraceFlag](#hidebug_traceflag) | HiDebug_TraceFlag | Enumerates the thread types for trace collection.|
| [HiDebug_StackFrameType](#hidebug_stackframetype) | HiDebug_StackFrameType | Enumerates the stack frame types.|
| [HiDebug_CrashObjType](#hidebug_crashobjtype) | HiDebug_CrashObjType | Enumerates the data types of debugging information.|
| [OH_HiDebug_ResourceType](#oh_hidebug_resourcetype) | OH_HiDebug_ResourceType | Enumerates the resource profiling types.|
| [OH_HiDebug_MemListenerType](#oh_hidebug_memlistenertype) | OH_HiDebug_MemListenerType | Enumerates the memory listener callback types. You can process the related logic based on the callback type.|

### Macros

| Name| Description|
| -- | -- |
| [HIDEBUG_TRACE_TAG_FFRT](#hidebug_trace_tag_ffrt) (1ULL << 13)                                                               | Indicates a function flow runtime (FFRT) task.<br>**Since**: 12     |
| [HIDEBUG_TRACE_TAG_COMMON_LIBRARY](#hidebug_trace_tag_common_library) (1ULL << 16)                                           | Indicates the common library subsystem.<br>**Since**: 12         |
| [HIDEBUG_TRACE_TAG_HDF](#hidebug_trace_tag_hdf) (1ULL << 18)                                                                 | Indicates the HDF subsystem.<br>**Since**: 12         |
| [HIDEBUG_TRACE_TAG_NET](#hidebug_trace_tag_net) (1ULL << 23)                                                                 | Indicates the Network.<br>**Since**: 12             |
| [HIDEBUG_TRACE_TAG_NWEB](#hidebug_trace_tag_nweb) (1ULL << 24)                                                               | Indicates the NWeb.<br>**Since**: 12           |
| [HIDEBUG_TRACE_TAG_DISTRIBUTED_AUDIO](#hidebug_trace_tag_distributed_audio) (1ULL << 27)                                     | Indicates the distributed audio.<br>**Since**: 12          |
| [HIDEBUG_TRACE_TAG_FILE_MANAGEMENT](#hidebug_trace_tag_file_management) (1ULL << 29)                                         | Indicates the file management.<br>**Since**: 12           |
| [HIDEBUG_TRACE_TAG_OHOS](#hidebug_trace_tag_ohos) (1ULL << 30)                                                               | Indicates the OpenHarmony OS.<br>**Since**: 12         |
| [HIDEBUG_TRACE_TAG_ABILITY_MANAGER](#hidebug_trace_tag_ability_manager) (1ULL << 31)                                         | Indicates the Ability Manager.<br>**Since**: 12|
| [HIDEBUG_TRACE_TAG_CAMERA](#hidebug_trace_tag_camera) (1ULL << 32)                                                           | Indicates the camera module.<br>**Since**: 12           |
| [HIDEBUG_TRACE_TAG_MEDIA](#hidebug_trace_tag_media) (1ULL << 33)                                                             | Indicates the media module.<br>**Since**: 12           |
| [HIDEBUG_TRACE_TAG_IMAGE](#hidebug_trace_tag_image) (1ULL << 34)                                                             | Indicates the image module.<br>**Since**: 12           |
| [HIDEBUG_TRACE_TAG_AUDIO](#hidebug_trace_tag_audio) (1ULL << 35)                                                             | Indicates the audio module.<br>**Since**: 12           |
| [HIDEBUG_TRACE_TAG_DISTRIBUTED_DATA](#hidebug_trace_tag_distributed_data) (1ULL << 36)                                       | Indicates the distributed data management.<br>**Since**: 12     |
| [HIDEBUG_TRACE_TAG_GRAPHICS](#hidebug_trace_tag_graphics) (1ULL << 38)                                                       | Indicates the graphics module.<br>**Since**: 12           |
| [HIDEBUG_TRACE_TAG_ARKUI](#hidebug_trace_tag_arkui) (1ULL << 39)                                                             | Indicates the ArkUI development framework.<br>**Since**: 12      |
| [HIDEBUG_TRACE_TAG_NOTIFICATION](#hidebug_trace_tag_notification) (1ULL << 40)                                               | Indicates the notification module.<br>**Since**: 12           |
| [HIDEBUG_TRACE_TAG_MISC](#hidebug_trace_tag_misc) (1ULL << 41)                                                               | Indicates the MISC module.<br>**Since**: 12         |
| [HIDEBUG_TRACE_TAG_MULTIMODAL_INPUT](#hidebug_trace_tag_multimodal_input) (1ULL << 42)                                       | Indicates the multimodal input module.<br>**Since**: 12        |
| [HIDEBUG_TRACE_TAG_RPC](#hidebug_trace_tag_rpc) (1ULL << 46)                                                                 | Indicates a remote procedure call (RPC).<br>**Since**: 12            |
| [HIDEBUG_TRACE_TAG_ARK](#hidebug_trace_tag_ark) (1ULL << 47)                                                                 | Indicates a JavaScript virtual machine (JSVM).<br>**Since**: 12        |
| [HIDEBUG_TRACE_TAG_WINDOW_MANAGER](#hidebug_trace_tag_window_manager) (1ULL << 48)                                           | Indicates the window manager.<br>**Since**: 12          |
| [HIDEBUG_TRACE_TAG_DISTRIBUTED_SCREEN](#hidebug_trace_tag_distributed_screen) (1ULL << 50)                                   | Indicates the distributed screen.<br>**Since**: 12          |
| [HIDEBUG_TRACE_TAG_DISTRIBUTED_CAMERA](#hidebug_trace_tag_distributed_camera) (1ULL << 51)                                   | Indicates the distributed camera.<br>**Since**: 12          |
| [HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_FRAMEWORK](#hidebug_trace_tag_distributed_hardware_framework) (1ULL << 52)           | Indicates the distributed hardware framework.<br>**Since**: 12        |
| [HIDEBUG_TRACE_TAG_GLOBAL_RESOURCE_MANAGER](#hidebug_trace_tag_global_resource_manager) (1ULL << 53)                         | Indicates the global resource management.<br>**Since**: 12        |
| [HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_DEVICE_MANAGER](#hidebug_trace_tag_distributed_hardware_device_manager) (1ULL << 54) | Indicates the distributed hardware device management.<br>**Since**: 12     |
| [HIDEBUG_TRACE_TAG_SAMGR](#hidebug_trace_tag_samgr) (1ULL << 55)                                                             | Indicates the Samgr (SA).<br>**Since**: 12             |
| [HIDEBUG_TRACE_TAG_POWER_MANAGER](#hidebug_trace_tag_power_manager) (1ULL << 56)                                             | Indicates the power manager.<br>**Since**: 12          |
| [HIDEBUG_TRACE_TAG_DISTRIBUTED_SCHEDULER](#hidebug_trace_tag_distributed_scheduler) (1ULL << 57)                             | Indicates the distributed scheduler.<br>**Since**: 12        |
| [HIDEBUG_TRACE_TAG_DISTRIBUTED_INPUT](#hidebug_trace_tag_distributed_input) (1ULL << 59)                                     | Indicates the distributed input.<br>**Since**: 12          |
| [HIDEBUG_TRACE_TAG_BLUETOOTH](#hidebug_trace_tag_bluetooth) (1ULL << 60)                                                     | Indicates the Bluetooth.<br>**Since**: 12             |

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*OH_HiDebug_RequestTraceCallback)(HiDebug_ErrorCode errorCode, const char* filePath)](#oh_hidebug_requesttracecallback) | OH_HiDebug_RequestTraceCallback | Triggered for the trace collection request.|
| [typedef void (\*OH_HiDebug_ProfilingCallback)(OH_HiDebug_ProfilingResult* result)](#oh_hidebug_profilingcallback) | OH_HiDebug_ProfilingCallback | Triggered for the resource profiling.|

## Enum Description

### HiDebug_ErrorCode

```c
enum HiDebug_ErrorCode
```

**Description**

Enumerates the error codes used in the HiDebug module.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| HIDEBUG_SUCCESS = 0 | Operation successful.|
| HIDEBUG_INVALID_ARGUMENT = 401 | Invalid parameter. Possible causes: 1. The parameter value is incorrect. 2. The parameter type is incorrect.|
| HIDEBUG_TRACE_CAPTURED_ALREADY = 11400102 | Repeated collection.|
| HIDEBUG_NO_PERMISSION = 11400103 | No file write permission.|
| HIDEBUG_TRACE_ABNORMAL = 11400104 | Internal system error.|
| HIDEBUG_NO_TRACE_RUNNING = 11400105 | No trace task is running.|
| OH_HIDEBUG_TRACE_STORAGE_LIMIT = 11400120 | The trace file storage reaches the upper limit.<br>**Since**: 24|
| HIDEBUG_INVALID_SYMBOLIC_PC_ADDRESS = 11400200 | PC address passed to the symbol parsing function is invalid.<br>**Since**: 20|
| HIDEBUG_NOT_SUPPORTED = 11400300 | Current device is not supported.<br>**Since**: 22|
| HIDEBUG_UNDER_SAMPLING = 11400301 | Current process is being sampled.<br>**Since**: 22|
| HIDEBUG_RESOURCE_UNAVAILABLE = 11400302 | Sampling resources are unavailable.<br>**Since**: 22|
| HIDEBUG_RES_PROF_SUCCESS = 11400400 | Resource profiling started or stopped successfully.<br>**Since**: 24|
| HIDEBUG_RES_PROF_INVALID_ARG = 11400410 | Invalid resource profiling parameter.<br>**Since**: 24|
| HIDEBUG_RES_PROF_INVALID_MAX_DURATION = 11400411 | Invalid maximum duration for resource profiling.<br>**Since**: 24|
| HIDEBUG_RES_PROF_INVALID_FILTER_SIZE = 11400412 | Invalid resource profiling filtering size.<br>**Since**: 24|
| HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH = 11400413 | Invalid maximum stack depth for resource profiling.<br>**Since**: 24|
| HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL = 11400414 | Invalid statistics interval for resource profiling.<br>**Since**: 24|
| HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL = 11400415 | Invalid sampling size for resource profiling.<br>**Since**: 24|
| HIDEBUG_RES_PROF_INVALID_RESOURCE_TYPE = 11400416 | Invalid resource type for resource profiling.<br>**Since**: 24|
| HIDEBUG_RES_PROF_PERMISSION_DENIED = 11400420 | Insufficient resource profiling permission. The target process for resource profiling can only be the process that calls this API.<br>**Since**: 24|
| HIDEBUG_RES_PROF_ALREADY_STARTED = 11400421 | Resource profiling is repeatedly started.<br>**Since**: 24|
| HIDEBUG_RES_PROF_NOT_STARTED = 11400422 | Failed to stop resource profiling because it is not started.<br>**Since**: 24|
| HIDEBUG_RES_PROF_PROCESS_OVERLIMIT = 11400423 | The number of resource profiling processes exceeds 4.<br>**Since**: 24|
| HIDEBUG_RES_PROF_CONFLICT = 11400424 | Resource profiling conflicts with CLI tools or system collection tasks.<br>**Since**: 24|
| HIDEBUG_RES_PROF_AUTO_STOPPED_BY_DURATION = 11400425 | Resource profiling automatically stopped due to the duration limit.<br>**Since**: 24|
| HIDEBUG_RES_PROF_DAILY_QUOTA_EXCEEDED = 11400426 | The daily quota for resource profiling exceeded 10 times.<br>**Since**: 24|
| HIDEBUG_RES_PROF_CPU_OVERLOADED = 11400427 | The system CPU is overloaded, with the CPU usage exceeding 70%.<br>**Since**: 24|
| HIDEBUG_RES_PROF_MEM_PRESSURE_CRITICAL = 11400428 | The available memory space is less than 15%.<br>**Since**: 24|
| HIDEBUG_RES_PROF_STORAGE_PRESSURE_CRITICAL = 11400429 | The available storage space is less than 15%.<br>**Since**: 24|
| HIDEBUG_RES_PROF_FAILURE = 11400430 | Failed to start or stop resource profiling.<br>**Since**: 24|

### HiDebug_TraceFlag

```c
enum HiDebug_TraceFlag
```

**Description**

Enumerates the thread types for trace collection.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| HIDEBUG_TRACE_FLAG_MAIN_THREAD = 1 | Only the main thread of the current application.|
| HIDEBUG_TRACE_FLAG_ALL_THREADS = 2 | All threads of the application.|

### HiDebug_StackFrameType

```c
enum HiDebug_StackFrameType
```

**Description**

Enumerates the stack frame types.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| HIDEBUG_STACK_FRAME_TYPE_JS = 1 | JS stack frame.|
| HIDEBUG_STACK_FRAME_TYPE_NATIVE = 2 | Native stack frame.|

### HiDebug_CrashObjType

```c
enum HiDebug_CrashObjType
```

**Description**

Enumerates the data types of debugging information.

**Since**: 23

| Enum Item| Description|
| -- | -- |
| HIDEBUG_CRASHOBJ_STRING = 0 | String.|
| HIDEBUG_CRASHOBJ_MEMORY_64B = 1 | 64-byte memory block.|
| HIDEBUG_CRASHOBJ_MEMORY_256B = 2 | 256-byte memory block.|
| HIDEBUG_CRASHOBJ_MEMORY_1024B = 3 | 1024-byte memory block.|
| HIDEBUG_CRASHOBJ_MEMORY_2048B = 4 | 2048-byte memory block.|
| HIDEBUG_CRASHOBJ_MEMORY_4096B = 5 | 4096-byte memory block.|

### OH_HiDebug_ResourceType

```c
enum OH_HiDebug_ResourceType
```

**Description**

Enumerates the resource profiling types.

**Since**: 24

| Enum Item| Description|
| -- | -- |
| OH_RES_TYPE_FD | File descriptor.<br>**Since**: 24|
| OH_RES_TYPE_THREAD | Thread.<br>**Since**: 24|
| OH_RES_TYPE_NATIVE | Native memory.<br>**Since**: 24|
| OH_RES_TYPE_GPU | GPU memory.<br>**Since**: 24|
| OH_RES_TYPE_GLOBAL_HANDLE | Global handle.<br>**Since**: 24|

### OH_HiDebug_MemListenerType

```c
enum OH_HiDebug_MemListenerType
```

**Description**

Enumerates the memory listener callback types. You can process the related logic based on the callback type.

**Since:** 26.0.0

| Enum Item| Description|
| -- | -- |
| OH_HIDEBUG_DO_NOTHING = 0 | No specific operation is performed. Only a notification callback is performed.<br>**Since:** 26.0.0|
| OH_HIDEBUG_RUNNING_GC = 1 | Perform garbage collection (GC).<br>**Since:** 26.0.0|
| OH_HIDEBUG_DUMP_SNAPSHOT = 2 | Export memory snapshot.<br>**Since:** 26.0.0|

## Macro Description

### HIDEBUG_TRACE_TAG_FFRT

```c
#define HIDEBUG_TRACE_TAG_FFRT (1ULL << 13)
```

**Description**

Indicates a function flow runtime (FFRT) task.

**Since**: 12

### HIDEBUG_TRACE_TAG_COMMON_LIBRARY

```c
#define HIDEBUG_TRACE_TAG_COMMON_LIBRARY (1ULL << 16)
```

**Description**

Indicates the common library subsystem.

**Since**: 12

### HIDEBUG_TRACE_TAG_HDF

```c
#define HIDEBUG_TRACE_TAG_HDF (1ULL << 18)
```

**Description**

Indicates the HDF subsystem.

**Since**: 12

### HIDEBUG_TRACE_TAG_NET

```c
#define HIDEBUG_TRACE_TAG_NET (1ULL << 23)
```

**Description**

Indicates the Network.

**Since**: 12

### HIDEBUG_TRACE_TAG_NWEB

```c
#define HIDEBUG_TRACE_TAG_NWEB (1ULL << 24)
```

**Description**

Indicates the NWeb.

**Since**: 12

### HIDEBUG_TRACE_TAG_DISTRIBUTED_AUDIO

```c
#define HIDEBUG_TRACE_TAG_DISTRIBUTED_AUDIO (1ULL << 27)
```

**Description**

Indicates the distributed audio.

**Since**: 12

### HIDEBUG_TRACE_TAG_FILE_MANAGEMENT

```c
#define HIDEBUG_TRACE_TAG_FILE_MANAGEMENT (1ULL << 29)
```

**Description**

Indicates the file management.

**Since**: 12

### HIDEBUG_TRACE_TAG_OHOS

```c
#define HIDEBUG_TRACE_TAG_OHOS (1ULL << 30)
```

**Description**

Indicates the OpenHarmony OS.

**Since**: 12

### HIDEBUG_TRACE_TAG_ABILITY_MANAGER

```c
#define HIDEBUG_TRACE_TAG_ABILITY_MANAGER (1ULL << 31)
```

**Description**

Indicates the Ability Manager.

**Since**: 12

### HIDEBUG_TRACE_TAG_CAMERA

```c
#define HIDEBUG_TRACE_TAG_CAMERA (1ULL << 32)
```

**Description**

Indicates the camera module.

**Since**: 12

### HIDEBUG_TRACE_TAG_MEDIA

```c
#define HIDEBUG_TRACE_TAG_MEDIA (1ULL << 33)
```

**Description**

Indicates the media module.

**Since**: 12

### HIDEBUG_TRACE_TAG_IMAGE

```c
#define HIDEBUG_TRACE_TAG_IMAGE (1ULL << 34)
```

**Description**

Indicates the image module.

**Since**: 12

### HIDEBUG_TRACE_TAG_AUDIO

```c
#define HIDEBUG_TRACE_TAG_AUDIO (1ULL << 35)
```

**Description**

Indicates the audio module.

**Since**: 12

### HIDEBUG_TRACE_TAG_DISTRIBUTED_DATA

```c
#define HIDEBUG_TRACE_TAG_DISTRIBUTED_DATA (1ULL << 36)
```

**Description**

Indicates the distributed data management.

**Since**: 12

### HIDEBUG_TRACE_TAG_GRAPHICS

```c
#define HIDEBUG_TRACE_TAG_GRAPHICS (1ULL << 38)
```

**Description**

Indicates the graphics module.

**Since**: 12

### HIDEBUG_TRACE_TAG_ARKUI

```c
#define HIDEBUG_TRACE_TAG_ARKUI (1ULL << 39)
```

**Description**

Indicates the ArkUI development framework.

**Since**: 12

### HIDEBUG_TRACE_TAG_NOTIFICATION

```c
#define HIDEBUG_TRACE_TAG_NOTIFICATION (1ULL << 40)
```

**Description**

Indicates the notification module.

**Since**: 12

### HIDEBUG_TRACE_TAG_MISC

```c
#define HIDEBUG_TRACE_TAG_MISC (1ULL << 41)
```

**Description**

Indicates the MISC module.

**Since**: 12

### HIDEBUG_TRACE_TAG_MULTIMODAL_INPUT

```c
#define HIDEBUG_TRACE_TAG_MULTIMODAL_INPUT (1ULL << 42)
```

**Description**

Indicates the multimodal input module.

**Since**: 12

### HIDEBUG_TRACE_TAG_RPC

```c
#define HIDEBUG_TRACE_TAG_RPC (1ULL << 46)
```

**Description**

Indicates a remote procedure call (RPC).

**Since**: 12

### HIDEBUG_TRACE_TAG_ARK

```c
#define HIDEBUG_TRACE_TAG_ARK (1ULL << 47)
```

**Description**

Indicates a JavaScript virtual machine (JSVM).

**Since**: 12

### HIDEBUG_TRACE_TAG_WINDOW_MANAGER

```c
#define HIDEBUG_TRACE_TAG_WINDOW_MANAGER (1ULL << 48)
```

**Description**

Indicates the window manager.

**Since**: 12

### HIDEBUG_TRACE_TAG_DISTRIBUTED_SCREEN

```c
#define HIDEBUG_TRACE_TAG_DISTRIBUTED_SCREEN (1ULL << 50)
```

**Description**

Indicates the distributed screen.

**Since**: 12

### HIDEBUG_TRACE_TAG_DISTRIBUTED_CAMERA

```c
#define HIDEBUG_TRACE_TAG_DISTRIBUTED_CAMERA (1ULL << 51)
```

**Description**

Indicates the distributed camera.

**Since**: 12

### HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_FRAMEWORK

```c
#define HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_FRAMEWORK (1ULL << 52)
```

**Description**

Indicates the distributed hardware framework.

**Since**: 12

### HIDEBUG_TRACE_TAG_GLOBAL_RESOURCE_MANAGER

```c
#define HIDEBUG_TRACE_TAG_GLOBAL_RESOURCE_MANAGER (1ULL << 53)
```

**Description**

Indicates the global resource management.

**Since**: 12

### HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_DEVICE_MANAGER

```c
#define HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_DEVICE_MANAGER (1ULL << 54)
```

**Description**

Indicates the distributed hardware device management.

**Since**: 12

### HIDEBUG_TRACE_TAG_SAMGR

```c
#define HIDEBUG_TRACE_TAG_SAMGR (1ULL << 55)
```

**Description**

Indicates the Samgr (SA).

**Since**: 12

### HIDEBUG_TRACE_TAG_POWER_MANAGER

```c
#define HIDEBUG_TRACE_TAG_POWER_MANAGER (1ULL << 56)
```

**Description**

Indicates the power manager.

**Since**: 12

### HIDEBUG_TRACE_TAG_DISTRIBUTED_SCHEDULER

```c
#define HIDEBUG_TRACE_TAG_DISTRIBUTED_SCHEDULER (1ULL << 57)
```

**Description**

Indicates the distributed scheduler.

**Since**: 12

### HIDEBUG_TRACE_TAG_DISTRIBUTED_INPUT

```c
#define HIDEBUG_TRACE_TAG_DISTRIBUTED_INPUT (1ULL << 59)
```

**Description**

Indicates the distributed input.

**Since**: 12

### HIDEBUG_TRACE_TAG_BLUETOOTH

```c
#define HIDEBUG_TRACE_TAG_BLUETOOTH (1ULL << 60)
```

**Description**

Indicates the Bluetooth.

**Since**: 12

## Function Description

### OH_HiDebug_RequestTraceCallback()

```c
typedef void (*OH_HiDebug_RequestTraceCallback)(HiDebug_ErrorCode errorCode, const char* filePath)
```

**Description**

Triggered for the trace collection request.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| HiDebug_ErrorCode errorCode | Result code. For details, see [HiDebug_ErrorCode](#hidebug_errorcode).|
| const char\* filePath | Pointer to the collected trace file. If the operation fails, a null pointer may be returned.|

### OH_HiDebug_ProfilingCallback()

```c
typedef void (*OH_HiDebug_ProfilingCallback)(OH_HiDebug_ProfilingResult* result)
```

**Description**

Triggered for the resource profiling.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| OH_HiDebug_ProfilingResult\* result | Pointer to the parameters of the resource profiling callback function.|
