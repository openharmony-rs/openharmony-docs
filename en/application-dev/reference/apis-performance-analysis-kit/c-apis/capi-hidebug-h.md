# hidebug.h

## Overview

Defines the APIs for debugging.

**Library**: libohhidebug.so

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Related module**: [HiDebug](capi-hidebug.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) | OH_HiDebug_ProfilerOptions | Forward declaration for resource profiler options. |

### Macro

| Name | Description |
| -- | -- |
| HIVIEWDFX_HIDEBUG_H | Defines the APIs for debugging.<br>**Since**: 12<br>**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [double OH_HiDebug_GetSystemCpuUsage()](#oh_hidebug_getsystemcpuusage) | - | Obtains the CPU usage of the system. Note that this API involves cross-process communication and takes a long time. Therefore, you are advised not to call this API in the main thread. |
| [double OH_HiDebug_GetAppCpuUsage()](#oh_hidebug_getappcpuusage) | - | Obtains the CPU usage of an application. Note that this API involves cross-process communication and takes a long time. Therefore, you are advised not to call this API in the main thread. |
| [HiDebug_ThreadCpuUsagePtr OH_HiDebug_GetAppThreadCpuUsage()](#oh_hidebug_getappthreadcpuusage) | - | Obtains the CPU usage of all threads of an application. Note that this API involves cross-process communication and takes a long time. Therefore, you are advised not to call this API in the main thread. |
| [void OH_HiDebug_FreeThreadCpuUsage(HiDebug_ThreadCpuUsagePtr *threadCpuUsage)](#oh_hidebug_freethreadcpuusage) | - | Releases the **HiDebug_ThreadCpuUsagePtr**. |
| [void OH_HiDebug_GetSystemMemInfo(HiDebug_SystemMemInfo *systemMemInfo)](#oh_hidebug_getsystemmeminfo) | - | Obtains system memory information. |
| [void OH_HiDebug_GetAppNativeMemInfo(HiDebug_NativeMemInfo *nativeMemInfo)](#oh_hidebug_getappnativememinfo) | - | Obtains the memory information of an application process. Note that this API needs to read the **\/proc/{pid}/ smaps_rollup** node information, which takes a long time. Therefore, you are advised not to call this API in the main thread. |
| [void OH_HiDebug_GetAppNativeMemInfoWithCache(HiDebug_NativeMemInfo *nativeMemInfo, bool forceRefresh)](#oh_hidebug_getappnativememinfowithcache) | - | Obtains the memory information of an application process. This API has a cache mechanism to improve its performance. The cache value is valid for 5 minutes. Note that this API needs to read the **\/proc/{pid}/ smaps_rollup** node information, which takes a long time. Therefore, you are advised not to call this API in the main thread. |
| [void OH_HiDebug_GetAppMemoryLimit(HiDebug_MemoryLimit *memoryLimit)](#oh_hidebug_getappmemorylimit) | - | Obtains the memory limit of an application process. |
| [HiDebug_ErrorCode OH_HiDebug_StartAppTraceCapture(HiDebug_TraceFlag flag, uint64_t tags, uint32_t limitSize, char* fileName, uint32_t length)](#oh_hidebug_startapptracecapture) | - | Starts application trace collection. |
| [HiDebug_ErrorCode OH_HiDebug_StopAppTraceCapture()](#oh_hidebug_stopapptracecapture) | - | Stops application trace collection. |
| [HiDebug_ErrorCode OH_HiDebug_RequestTrace(OH_HiDebug_RequestTraceConfig *config, OH_HiDebug_RequestTraceCallback callback)](#oh_hidebug_requesttrace) | - | Requests trace collection based on the configured collection settings. |
| [HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemory(uint32_t *value)](#oh_hidebug_getgraphicsmemory) | - | Obtains the size of the GPU memory. Note that this API involves multiple cross-process communications and may take more than 1 second. Therefore, you are advised not to call this API in the main thread. |
| [HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemorySummary(uint32_t interval, HiDebug_GraphicsMemorySummary *summary)](#oh_hidebug_getgraphicsmemorysummary) | - | Obtains the detailed GPU memory usage of an application. |
| [HiDebug_ErrorCode OH_HiDebug_SetMallocDispatchTable(struct HiDebug_MallocDispatch *dispatchTable)](#oh_hidebug_setmallocdispatchtable) | - | Sets the **MallocDispatch** table in the basic C library to temporarily replace the original memory operation functions (such as **malloc**, **free**, **calloc**, **realloc**, **mmap**, and **munmap**) with the custom memory operation functions. The **MallocDispatch** table is a struct that encapsulates memory operation functions such as **<br>malloc**, **calloc**, **realloc**, and **free** in the basic C library. **HiDebug_MallocDispatch** is only a part of the **MallocDispatch** struct. |
| [HiDebug_MallocDispatch* OH_HiDebug_GetDefaultMallocDispatchTable(void)](#oh_hidebug_getdefaultmallocdispatchtable) | - | Obtains the default MallocDispatch table of the system C library. You can call [OH_HiDebug_RestoreMallocDispatchTable](capi-hidebug-h.md#oh_hidebug_restoremallocdispatchtable) to restore the table. |
| [void OH_HiDebug_RestoreMallocDispatchTable(void)](#oh_hidebug_restoremallocdispatchtable) | - | Restores the MallocDispatch table of the system C library. |
| [int OH_HiDebug_BacktraceFromFp(HiDebug_Backtrace_Object object, void* startFp, void** pcArray, int size)](#oh_hidebug_backtracefromfp) | - | Performs stack back-tracing based on the given fp address. This function is async-signal-safe. |
| [typedef void (\*OH_HiDebug_SymbolicAddressCallback)(void* pc, void* arg, const HiDebug_StackFrame* frame)](#oh_hidebug_symbolicaddresscallback) | OH_HiDebug_SymbolicAddressCallback | If the [OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress) API is successfully called, the parsed stack information is returned to the caller through this function. Note: This API involves multiple I/O operations and takes a long time. Therefore, you are advised not to call this API in the main thread. |
| [HiDebug_ErrorCode OH_HiDebug_SymbolicAddress(HiDebug_Backtrace_Object object, void* pc, void* arg, OH_HiDebug_SymbolicAddressCallback callback)](#oh_hidebug_symbolicaddress) | - | Obtains detailed symbol information based on the specified PC address. This function is not asyn-signal-safe. |
| [HiDebug_Backtrace_Object OH_HiDebug_CreateBacktraceObject(void)](#oh_hidebug_createbacktraceobject) | - | Creates an object for stack backtracing and parsing. This function is not asyn-signal-safe. |
| [void OH_HiDebug_DestroyBacktraceObject(HiDebug_Backtrace_Object object)](#oh_hidebug_destroybacktraceobject) | - | Destroys the object created by [OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject) to release the resources applied for during stack backtracing and parsing. This function is not asyn-signal-safe. |
| [uint64_t OH_HiDebug_SetCrashObj(HiDebug_CrashObjType type, void* addr)](#oh_hidebug_setcrashobj) | - | Adds debugging information to the crash logs. This function is used together with [OH_HiDebug_ResetCrashObj](capi-hidebug-h.md#oh_hidebug_resetcrashobj). If a program crashes between **OH_HiDebug_SetCrashObj** and **<br>OH_HiDebug_ResetCrashObj**, the debugging information set by **OH_HiDebug_SetCrashObj** is added to the crash logs. |
| [void OH_HiDebug_ResetCrashObj(uint64_t crashObj)](#oh_hidebug_resetcrashobj) | - | Resets the debugging information object to the state before **OH_HiDebug_SetCrashObj** is used. |
| [typedef void (\*OH_HiDebug_ThreadLiteSamplingCallback)(const char* stacks)](#oh_hidebug_threadlitesamplingcallback) | OH_HiDebug_ThreadLiteSamplingCallback | Triggered for the lightweight Perf sampling stack content. Note: The sampling data is valid only during the execution of this callback. If you need to use the data outside the function, deep copy the sampling stack content. |
| [HiDebug_ErrorCode OH_HiDebug_RequestThreadLiteSampling(HiDebug_ProcessSamplerConfig* config, OH_HiDebug_ThreadLiteSamplingCallback stacksCallback)](#oh_hidebug_requestthreadlitesampling) | - |  |
| [HiDebug_ErrorCode OH_HiDebug_StartProfiler(OH_HiDebug_ResourceType type, OH_HiDebug_ResProfilerConfig* config, OH_HiDebug_ProfilingCallback callback)](#oh_hidebug_startprofiler) | - | Asynchronously starts the resource profiler for the current process. <br>The callback function is called only when the collection is stopped (including when the system automatically stops the collection). It carries the resource type and file path to be collected. <br>If the collection is abnormal, the file path is **NULL**. |
| [HiDebug_ErrorCode OH_HiDebug_StopProfiler(void)](#oh_hidebug_stopprofiler) | - | Stops resource profiler for the current process. This API can be called after the [OH_HiDebug_StartProfiler](capi-hidebug-h.md#oh_hidebug_startprofiler) API and the call duration must be within the maximum duration. |
| [typedef bool (\*OH_HiDebug_MemDumpListener)(int32_t fd, OH_HiDebug_MemListenerType tag, bool mayReportToOEM, const char* arg)](#oh_hidebug_memdumplistener) | OH_HiDebug_MemDumpListener | Callback triggered for listening. You can use FDs to write memory data in your app so that you can export the data using the hidumper command. |
| [HiDebug_ErrorCode OH_HiDebug_RegisterMemDumpListener(const char* name, OH_HiDebug_MemDumpListener listener)](#oh_hidebug_registermemdumplistener) | - | Registers a memory dump listener. When the memory usage of an application is high or the memory information is exported using the {@link hidumper command}, the system automatically calls the registered callback function. <br>The third-party application framework or developer can use this function to dump the internal memory information of the application to hidumper or upload the information to the OEM vendor through commercial grayscale release. <br>You can use [OH_HiDebug_UnregisterMemDumpListener](capi-hidebug-h.md#oh_hidebug_unregistermemdumplistener) to unregister the listener. |
| [HiDebug_ErrorCode OH_HiDebug_UnregisterMemDumpListener(const char* name)](#oh_hidebug_unregistermemdumplistener) | - | Unregisters a memory dump listener that has been successfully registered. |
| [uint64_t OH_HiDebug_AcquireAsyncContext()](#oh_hidebug_acquireasynccontext) | - | Obtains an **AsyncContext** for subsequent use. This API is an auxiliary API of the profiler. You can use [OH_HiDebug_ReleaseAsyncContext](capi-hidebug-h.md#oh_hidebug_releaseasynccontext) to release the context. |
| [void OH_HiDebug_PushAsyncContext(uint64_t ctx)](#oh_hidebug_pushasynccontext) | - | Pushes an **AsyncContext** into the running context stack. This API is an auxiliary API of the profiler. |
| [void OH_HiDebug_PopAsyncContext(uint64_t ctx)](#oh_hidebug_popasynccontext) | - | Pops an **AsyncContext** from the running context stack. This API is an auxiliary API of the profiler. |
| [void OH_HiDebug_ReleaseAsyncContext(uint64_t ctx)](#oh_hidebug_releaseasynccontext) | - | Releases an **AsyncContext** to the system. This API is an auxiliary API of the profiler. |
| [OH_HiDebug_ProfilerOptions *OH_HiDebug_CreateProfilerOptions(void)](#oh_hidebug_createprofileroptions) | - | Create Profiler Options. |
| [HiDebug_ErrorCode OH_HiDebug_DestroyProfilerOptions(OH_HiDebug_ProfilerOptions *opts)](#oh_hidebug_destroyprofileroptions) | - | Destroy Profiler Options. |
| [HiDebug_ErrorCode OH_HiDebug_SetMaxAsyncNestingDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)](#oh_hidebug_setmaxasyncnestingdepth) | - | Sets the maximum nesting depth for asynchronous invocations. |
| [HiDebug_ErrorCode OH_HiDebug_SetMaxAsyncTaskStackDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)](#oh_hidebug_setmaxasynctaskstackdepth) | - | Sets the maximum stack depth for each asynchronous task function. |
| [HiDebug_ErrorCode OH_HiDebug_SetSampleIntervalBytes(OH_HiDebug_ProfilerOptions *opts, uint32_t bytes)](#oh_hidebug_setsampleintervalbytes) | - | Sets the sampling interval in bytes. |
| [HiDebug_ErrorCode OH_HiDebug_SetStatisticsIntervalSec(OH_HiDebug_ProfilerOptions *opts, uint32_t seconds)](#oh_hidebug_setstatisticsintervalsec) | - | Sets the statistics interval in seconds. |
| [HiDebug_ErrorCode OH_HiDebug_SetMaxStackDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)](#oh_hidebug_setmaxstackdepth) | - | Sets the maximum backtrace stack depth. |
| [HiDebug_ErrorCode OH_HiDebug_SetFilterSize(OH_HiDebug_ProfilerOptions *opts, uint32_t size)](#oh_hidebug_setfiltersize) | - | Sets the filter size for allocations. |
| [HiDebug_ErrorCode OH_HiDebug_SetMaxDurationSec(OH_HiDebug_ProfilerOptions *opts, uint32_t seconds)](#oh_hidebug_setmaxdurationsec) | - | Sets the maximum profiling duration in seconds. |
| [HiDebug_ErrorCode OH_HiDebug_StartProfilerWithOptions(OH_HiDebug_ResourceType type, OH_HiDebug_ProfilerOptions *opts, OH_HiDebug_ProfilingCallback callback)](#oh_hidebug_startprofilerwithoptions) | - | Starts the profiler with the specified options and resource type. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_HiDebug_SymbolicAddressCallback)(void* pc, void* arg, const HiDebug_StackFrame* frame) | If the [OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress) API is successfully called, the parsed stack information is returned to the caller through this function. Note: This API involves multiple I/O operations and takes a long time. Therefore, you are advised not to call this API in the main thread.<br>**Since**: 20 |
| void (*OH_HiDebug_ThreadLiteSamplingCallback)(const char* stacks) | Triggered for the lightweight Perf sampling stack content. Note: The sampling data is valid only during the execution of this callback. If you need to use the data outside the function, deep copy the sampling stack content.<br>**Since**: 22 |
| bool (*OH_HiDebug_MemDumpListener)(int32_t fd, OH_HiDebug_MemListenerType tag, bool mayReportToOEM, const char* arg) | Callback triggered for listening. You can use FDs to write memory data in your app so that you can export the data using the hidumper command.<br>**Since**: 26.0.0 |

## Function description

### OH_HiDebug_GetSystemCpuUsage()

```c
double OH_HiDebug_GetSystemCpuUsage()
```

**Description**

Obtains the CPU usage of the system. Note that this API involves cross-process communication and takes a long time. Therefore, you are advised not to call this API in the main thread.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| double | Returns the system CPU usage if the operation is successful. Returns 0 if the operation fails. |

### OH_HiDebug_GetAppCpuUsage()

```c
double OH_HiDebug_GetAppCpuUsage()
```

**Description**

Obtains the CPU usage of an application. Note that this API involves cross-process communication and takes a long time. Therefore, you are advised not to call this API in the main thread.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| double | Application CPU usage obtained if the operation is successful. If 0 is returned, the CPU usage of the      current application is too low. |

### OH_HiDebug_GetAppThreadCpuUsage()

```c
HiDebug_ThreadCpuUsagePtr OH_HiDebug_GetAppThreadCpuUsage()
```

**Description**

Obtains the CPU usage of all threads of an application. Note that this API involves cross-process communication and takes a long time. Therefore, you are advised not to call this API in the main thread.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ThreadCpuUsagePtr | CPU usage of all threads. For details, see {@link HiDebug_ThreadCpuUsagePtr}.      <br>If null is returned, the thread data may not be obtained. |

### OH_HiDebug_FreeThreadCpuUsage()

```c
void OH_HiDebug_FreeThreadCpuUsage(HiDebug_ThreadCpuUsagePtr *threadCpuUsage)
```

**Description**

Releases the **HiDebug_ThreadCpuUsagePtr**.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_ThreadCpuUsagePtr *threadCpuUsage | Pointer to the available CPU buffer of all threads of the application. For details, see {@link HiDebug_ThreadCpuUsagePtr}. The input parameter is obtained by **OH_HiDebug_GetAppThreadCpuUsage()**. |

### OH_HiDebug_GetSystemMemInfo()

```c
void OH_HiDebug_GetSystemMemInfo(HiDebug_SystemMemInfo *systemMemInfo)
```

**Description**

Obtains system memory information.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_SystemMemInfo *systemMemInfo | Pointer to [HiDebug_SystemMemInfo](capi-hidebug-hidebug-systemmeminfo.md). If the struct data is empty after the function is called, the calling fails. |

### OH_HiDebug_GetAppNativeMemInfo()

```c
void OH_HiDebug_GetAppNativeMemInfo(HiDebug_NativeMemInfo *nativeMemInfo)
```

**Description**

Obtains the memory information of an application process. Note that this API needs to read the **\/proc/{pid}/ smaps_rollup** node information, which takes a long time. Therefore, you are advised not to call this API in the main thread.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_NativeMemInfo *nativeMemInfo | Pointer to [HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md). If the struct data is empty after the function is called, the calling fails. |

### OH_HiDebug_GetAppNativeMemInfoWithCache()

```c
void OH_HiDebug_GetAppNativeMemInfoWithCache(HiDebug_NativeMemInfo *nativeMemInfo, bool forceRefresh)
```

**Description**

Obtains the memory information of an application process. This API has a cache mechanism to improve its performance. The cache value is valid for 5 minutes. Note that this API needs to read the **\/proc/{pid}/ smaps_rollup** node information, which takes a long time. Therefore, you are advised not to call this API in the main thread.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_NativeMemInfo *nativeMemInfo | Pointer to [HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md). If the struct data is empty after the function is called, the calling fails. |
| bool forceRefresh | Whether to ignore the cache validity and forcibly update the cache value. <br>The value **true** means to directly obtain the current memory data and update the cache value. <br>The value **false** means to directly return the cache value if the cache is valid and obtain the current memory data and update the cache value if the cache is invalid. |

### OH_HiDebug_GetAppMemoryLimit()

```c
void OH_HiDebug_GetAppMemoryLimit(HiDebug_MemoryLimit *memoryLimit)
```

**Description**

Obtains the memory limit of an application process.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_MemoryLimit *memoryLimit | Pointer to [HiDebug_MemoryLimit](capi-hidebug-hidebug-memorylimit.md). If the struct data is empty after the function is called, the calling fails. |

### OH_HiDebug_StartAppTraceCapture()

```c
HiDebug_ErrorCode OH_HiDebug_StartAppTraceCapture(HiDebug_TraceFlag flag, uint64_t tags, uint32_t limitSize, char* fileName, uint32_t length)
```

**Description**

Starts application trace collection.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_TraceFlag flag | Type of the thread (the main thread or all threads of the application) to trace. |
| uint64_t tags | Modules or subsystems to trace. |
| uint32_t limitSize | Maximum size of the trace file (in bytes), which is 500 MB. |
| char* fileName | Buffer for the output trace file. |
| uint32_t length | Length of the buffer for the output trace file. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | 0 - The operation is successful.      <br>[HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode) 401 - The fileName parameter is a null pointer, the input length      parameter is too small, or the limitSize parameter is less than or equal to 0.      <br>11400102 - A trace is already started.      <br>11400103 - You do not have the permission to start the trace function.      <br>11400104 - An internal system error occurs. |

### OH_HiDebug_StopAppTraceCapture()

```c
HiDebug_ErrorCode OH_HiDebug_StopAppTraceCapture()
```

**Description**

Stops application trace collection.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | 0 - The operation is successful.      <br>11400104 - An internal system error occurs.      <br>11400105 - No trace collection is running. |

### OH_HiDebug_RequestTrace()

```c
HiDebug_ErrorCode OH_HiDebug_RequestTrace(OH_HiDebug_RequestTraceConfig *config, OH_HiDebug_RequestTraceCallback callback)
```

**Description**

Requests trace collection based on the configured collection settings.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_HiDebug_RequestTraceConfig *config | Parameters for trace collection. For details, see [OH_HiDebug_RequestTraceConfig](capi-hidebug-oh-hidebug-requesttraceconfig.md). |
| OH_HiDebug_RequestTraceCallback callback | Callback function for trace collection. For details, see [OH_HiDebug_RequestTraceCallback](capi-hidebug-type-h.md#oh_hidebug_requesttracecallback). |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <br>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode): The collection is successful.      <br>[HIDEBUG_TRACE_ABNORMAL](capi-hidebug-type-h.md#hidebug_errorcode): The remote service or status is abnormal.      <br>[OH_HIDEBUG_TRACE_STORAGE_LIMIT](capi-hidebug-type-h.md#hidebug_errorcode): The number of stored trace files reaches the upper limit. If the      number of trace files stored in the directory is greater than or equal to 3, a failure message is returned.      <br>[HIDEBUG_RESOURCE_UNAVAILABLE](capi-hidebug-type-h.md#hidebug_errorcode): The collection resources are unavailable. |

### OH_HiDebug_GetGraphicsMemory()

```c
HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemory(uint32_t *value)
```

**Description**

Obtains the size of the GPU memory. Note that this API involves multiple cross-process communications and may take more than 1 second. Therefore, you are advised not to call this API in the main thread.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t *value | Pointer to the variable that stores the size (in KB) of the obtained GPU memory. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | 0 - The API is obtained successfully.      <br>401 - The parameter is a null pointer, which is invalid.      <br>11400104 - An internal system error occurs. |

### OH_HiDebug_GetGraphicsMemorySummary()

```c
HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemorySummary(uint32_t interval, HiDebug_GraphicsMemorySummary *summary)
```

**Description**

Obtains the detailed GPU memory usage of an application.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t interval | Interval that the cached GPU memory data exists, in seconds. If the duration exceeds the value of interval, the API obtains the latest data and updates the buffer. Otherwise, the API directly returns the cached data. <br>The value range of interval is [2, 3600]. If the passed-in interval is out of the range, **300** is used as the default value. |
| HiDebug_GraphicsMemorySummary *summary | Pointer to [HiDebug_GraphicsMemorySummary](capi-hidebug-hidebug-graphicsmemorysummary.md). |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | For details, see [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode).      <br>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode): The GPU memory information of the application is obtained successfully.      <br>[HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode): Invalid parameter.      <br>[HIDEBUG_TRACE_ABNORMAL](capi-hidebug-type-h.md#hidebug_errorcode): Internal system error. |

### OH_HiDebug_SetMallocDispatchTable()

```c
HiDebug_ErrorCode OH_HiDebug_SetMallocDispatchTable(struct HiDebug_MallocDispatch *dispatchTable)
```

**Description**

Sets the **MallocDispatch** table in the basic C library to temporarily replace the original memory operation functions (such as **malloc**, **free**, **calloc**, **realloc**, **mmap**, and **munmap**) with the custom memory operation functions. The **MallocDispatch** table is a struct that encapsulates memory operation functions such as **<br>malloc**, **calloc**, **realloc**, and **free** in the basic C library. **HiDebug_MallocDispatch** is only a part of the **MallocDispatch** struct.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct HiDebug_MallocDispatch *dispatchTable | Pointer to the [HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md) struct that contains the custom memory operation functions. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | For details, see [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode).      <br>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode): The custom memory operation function is set successfully.      <br>[HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode): Invalid parameter. |

### OH_HiDebug_GetDefaultMallocDispatchTable()

```c
HiDebug_MallocDispatch* OH_HiDebug_GetDefaultMallocDispatchTable(void)
```

**Description**

Obtains the default MallocDispatch table of the system C library. You can call [OH_HiDebug_RestoreMallocDispatchTable](capi-hidebug-h.md#oh_hidebug_restoremallocdispatchtable) to restore the table.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_MallocDispatch* | Pointer to the default [HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md) struct of the current C library. |

### OH_HiDebug_RestoreMallocDispatchTable()

```c
void OH_HiDebug_RestoreMallocDispatchTable(void)
```

**Description**

Restores the MallocDispatch table of the system C library.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

### OH_HiDebug_BacktraceFromFp()

```c
int OH_HiDebug_BacktraceFromFp(HiDebug_Backtrace_Object object, void* startFp, void** pcArray, int size)
```

**Description**

Performs stack back-tracing based on the given fp address. This function is async-signal-safe.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_Backtrace_Object object | Object obtained by the [OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject) API for stack backtracing. |
| void* startFp | Start frame pointer for stack backtracing. |
| void** pcArray | Array of PC addresses obtained from stack backtracing. |
| int size | Length of the PC address array obtained by stack backtracing. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Number of stack frames that are successfully backtraced and written to pcArray. If 0 is returned, stack      backtracing may fail. |

### OH_HiDebug_SymbolicAddressCallback()

```c
typedef void (*OH_HiDebug_SymbolicAddressCallback)(void* pc, void* arg, const HiDebug_StackFrame* frame)
```

**Description**

If the [OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress) API is successfully called, the parsed stack information is returned to the caller through this function. Note: This API involves multiple I/O operations and takes a long time. Therefore, you are advised not to call this API in the main thread.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void\* pc | PC address transferred to the [OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress) API for parsing. |
| void\* arg | arg value of the [OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress) API. |
| const HiDebug_StackFrame\* frame | Pointer to [HiDebug_StackFrame](capi-hidebug-hidebug-stackframe.md), which is obtained by parsing the PC address passed to the [OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress) API. What the pointer points to is valid only in the function scope. |

### OH_HiDebug_SymbolicAddress()

```c
HiDebug_ErrorCode OH_HiDebug_SymbolicAddress(HiDebug_Backtrace_Object object, void* pc, void* arg, OH_HiDebug_SymbolicAddressCallback callback)
```

**Description**

Obtains detailed symbol information based on the specified PC address. This function is not asyn-signal-safe.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_Backtrace_Object object | Object created by the [OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject) API. |
| void* pc | PC address obtained through the [OH_HiDebug_BacktraceFromFp](capi-hidebug-h.md#oh_hidebug_backtracefromfp) API. |
| void* arg | Reserved custom parameter. After the symbol is successfully parsed, this parameter is passed to [OH_HiDebug_SymbolicAddressCallback](capi-hidebug-h.md#oh_hidebug_symbolicaddresscallback). |
| [OH_HiDebug_SymbolicAddressCallback](capi-hidebug-h.md#oh_hidebug_symbolicaddresscallback) callback | Callback used to return the parsed stack information. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | For details, see [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode).      <br>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode): The detailed stack information is successfully obtained, and the callback input by      the function is called.      <br>[HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode): Invalid parameter.      <br>[HIDEBUG_INVALID_SYMBOLIC_PC_ADDRESS](capi-hidebug-type-h.md#hidebug_errorcode): Failed to find the corresponding symbol based on the input PC      address. |

### OH_HiDebug_CreateBacktraceObject()

```c
HiDebug_Backtrace_Object OH_HiDebug_CreateBacktraceObject(void)
```

**Description**

Creates an object for stack backtracing and parsing. This function is not asyn-signal-safe.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_Backtrace_Object | Pointer to the created object. If the object fails to be created, NULL is returned. |

### OH_HiDebug_DestroyBacktraceObject()

```c
void OH_HiDebug_DestroyBacktraceObject(HiDebug_Backtrace_Object object)
```

**Description**

Destroys the object created by [OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject) to release the resources applied for during stack backtracing and parsing. This function is not asyn-signal-safe.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_Backtrace_Object object | Object to destroy. |

### OH_HiDebug_SetCrashObj()

```c
uint64_t OH_HiDebug_SetCrashObj(HiDebug_CrashObjType type, void* addr)
```

**Description**

Adds debugging information to the crash logs. This function is used together with [OH_HiDebug_ResetCrashObj](capi-hidebug-h.md#oh_hidebug_resetcrashobj). If a program crashes between **OH_HiDebug_SetCrashObj** and **<br>OH_HiDebug_ResetCrashObj**, the debugging information set by **OH_HiDebug_SetCrashObj** is added to the crash logs.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_CrashObjType type | Data type of the debugging information. For details, see [HiDebug_CrashObjType](capi-hidebug-type-h.md#hidebug_crashobjtype). |
| void* addr | Address of the debugging information. The address must be valid when a crash occurs. |

**Returns**:

| Type | Description |
| -- | -- |
| uint64_t | Object of the debugging information that was set last time. If no debugging information is set last time,      the value is 0. |

### OH_HiDebug_ResetCrashObj()

```c
void OH_HiDebug_ResetCrashObj(uint64_t crashObj)
```

**Description**

Resets the debugging information object to the state before **OH_HiDebug_SetCrashObj** is used.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t crashObj | Return value of the **OH_HiDebug_SetCrashObj** function. |

### OH_HiDebug_ThreadLiteSamplingCallback()

```c
typedef void (*OH_HiDebug_ThreadLiteSamplingCallback)(const char* stacks)
```

**Description**

Triggered for the lightweight Perf sampling stack content. Note: The sampling data is valid only during the execution of this callback. If you need to use the data outside the function, deep copy the sampling stack content.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char\* stacks | Content of the sampling call stack. |

### OH_HiDebug_RequestThreadLiteSampling()

```c
HiDebug_ErrorCode OH_HiDebug_RequestThreadLiteSampling(HiDebug_ProcessSamplerConfig* config, OH_HiDebug_ThreadLiteSamplingCallback stacksCallback)
```

**Description**

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| HiDebug_ProcessSamplerConfig* config | Pointer to the [HiDebug_ProcessSamplerConfig](capi-hidebug-hidebug-processsamplerconfig.md) struct. |
| [OH_HiDebug_ThreadLiteSamplingCallback](capi-hidebug-h.md#oh_hidebug_threadlitesamplingcallback) stacksCallback | Callback used to return the sampling result when the sampling is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <br>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode): Sampling successful.      <br>[HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode): Invalid parameter.      <br>[HIDEBUG_NOT_SUPPORTED](capi-hidebug-type-h.md#hidebug_errorcode): Perf sampling not supported.      <br>[HIDEBUG_UNDER_SAMPLING](capi-hidebug-type-h.md#hidebug_errorcode): A sampling task is in progress.      <br>[HIDEBUG_RESOURCE_UNAVAILABLE](capi-hidebug-type-h.md#hidebug_errorcode): Sampling resources are insufficient or the upper call limit is reached. |

### OH_HiDebug_StartProfiler()

```c
HiDebug_ErrorCode OH_HiDebug_StartProfiler(OH_HiDebug_ResourceType type, OH_HiDebug_ResProfilerConfig* config, OH_HiDebug_ProfilingCallback callback)
```

**Description**

Asynchronously starts the resource profiler for the current process. <br>The callback function is called only when the collection is stopped (including when the system automatically stops the collection). It carries the resource type and file path to be collected. <br>If the collection is abnormal, the file path is **NULL**.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_HiDebug_ResourceType type | Resource profiling type. |
| OH_HiDebug_ResProfilerConfig* config | Configuration parameters of the resource profiler. |
| OH_HiDebug_ProfilingCallback callback | Result callback function of resource profiling. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <br>[HIDEBUG_RES_PROF_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode): Resource profiler started successfully.      <br>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode): Invalid resource profiler argument.      <br>[HIDEBUG_RES_PROF_INVALID_MAX_DURATION](capi-hidebug-type-h.md#hidebug_errorcode): Invalid maximum duration.      <br>[HIDEBUG_RES_PROF_INVALID_FILTER_SIZE](capi-hidebug-type-h.md#hidebug_errorcode): Invalid filter size.      <br>[HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH](capi-hidebug-type-h.md#hidebug_errorcode): Invalid maximum stack depth.      <br>[HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode): Invalid statistics interval.      <br>[HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode): Invalid sampling interval.      <br>[HIDEBUG_RES_PROF_INVALID_RESOURCE_TYPE](capi-hidebug-type-h.md#hidebug_errorcode): Invalid resource type.      <br>[HIDEBUG_RES_PROF_PERMISSION_DENIED](capi-hidebug-type-h.md#hidebug_errorcode): Insufficient resource profiling permission. The target process      for resource profiling can only be the process that calls this API.      <br>[HIDEBUG_RES_PROF_ALREADY_STARTED](capi-hidebug-type-h.md#hidebug_errorcode): Resource profiler already started.      <br>[HIDEBUG_RES_PROF_PROCESS_OVERLIMIT](capi-hidebug-type-h.md#hidebug_errorcode): The number of resource profiling processes exceeds 4.      <br>[HIDEBUG_RES_PROF_CONFLICT](capi-hidebug-type-h.md#hidebug_errorcode): Resource profiling conflicts with CLI tools or system profiling tasks.      <br>[HIDEBUG_RES_PROF_DAILY_QUOTA_EXCEEDED](capi-hidebug-type-h.md#hidebug_errorcode): The daily quota for resource profiling exceeds 10 times.      <br>[HIDEBUG_RES_PROF_CPU_OVERLOADED](capi-hidebug-type-h.md#hidebug_errorcode): The system CPU is overloaded, with the CPU usage exceeding 70%.      <br>[HIDEBUG_RES_PROF_MEM_PRESSURE_CRITICAL](capi-hidebug-type-h.md#hidebug_errorcode): The available memory space is less than 15%.      <br>[HIDEBUG_RES_PROF_STORAGE_PRESSURE_CRITICAL](capi-hidebug-type-h.md#hidebug_errorcode): The available storage space is less than 15%.      <br>[HIDEBUG_RES_PROF_FAILURE](capi-hidebug-type-h.md#hidebug_errorcode): Failed to start resource profiler. |

### OH_HiDebug_StopProfiler()

```c
HiDebug_ErrorCode OH_HiDebug_StopProfiler(void)
```

**Description**

Stops resource profiler for the current process. This API can be called after the [OH_HiDebug_StartProfiler](capi-hidebug-h.md#oh_hidebug_startprofiler) API and the call duration must be within the maximum duration.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <br>[HIDEBUG_RES_PROF_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode): Resource profiler stopped successfully.      <br>[HIDEBUG_RES_PROF_NOT_STARTED](capi-hidebug-type-h.md#hidebug_errorcode): Failed to stop resource profiler because it is not started.      <br>[HIDEBUG_RES_PROF_FAILURE](capi-hidebug-type-h.md#hidebug_errorcode): Failed to stop resource profiler. |

### OH_HiDebug_MemDumpListener()

```c
typedef bool (*OH_HiDebug_MemDumpListener)(int32_t fd, OH_HiDebug_MemListenerType tag, bool mayReportToOEM, const char* arg)
```

**Description**

Callback triggered for listening. You can use FDs to write memory data in your app so that you can export the data using the hidumper command.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t fd | FD used to write memory data in the app. |
| OH_HiDebug_MemListenerType tag | Callback type. You can process the related logic based on the callback type. |
| bool mayReportToOEM | Whether the data will be uploaded to the OEM. If the value is true, the data will be uploaded to the OEM. Pay attention to data privacy and security issues. |
| const char\* arg | Callback argument. You can pass different arguments based on the value of type. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether the operation is successful. |

### OH_HiDebug_RegisterMemDumpListener()

```c
HiDebug_ErrorCode OH_HiDebug_RegisterMemDumpListener(const char* name, OH_HiDebug_MemDumpListener listener)
```

**Description**

Registers a memory dump listener. When the memory usage of an application is high or the memory information is exported using the {@link hidumper command}, the system automatically calls the registered callback function. <br>The third-party application framework or developer can use this function to dump the internal memory information of the application to hidumper or upload the information to the OEM vendor through commercial grayscale release. <br>You can use [OH_HiDebug_UnregisterMemDumpListener](capi-hidebug-h.md#oh_hidebug_unregistermemdumplistener) to unregister the listener.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* name | Pointer to the name of the listener, which uniquely identifies the listener to be registered. The same name must be passed during listener underegistration. <br>A listener with the same name can be registered only once. If you attempt to register a listener with the same name again, **HIDEBUG_INVALID_ARGUMENT** will be returned. To update a listener, unregister the original listener first. |
| [OH_HiDebug_MemDumpListener](capi-hidebug-h.md#oh_hidebug_memdumplistener) listener | Callback triggered for listening. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <br>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode): Operation succeeded.      <br>[HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode): Invalid parameter. |

### OH_HiDebug_UnregisterMemDumpListener()

```c
HiDebug_ErrorCode OH_HiDebug_UnregisterMemDumpListener(const char* name)
```

**Description**

Unregisters a memory dump listener that has been successfully registered.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* name | Pointer to the unique name of the listener. The value must be the same as the **name** passed during registration. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <br>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode): Operation succeeded.      <br>[HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode): Invalid parameter. |

### OH_HiDebug_AcquireAsyncContext()

```c
uint64_t OH_HiDebug_AcquireAsyncContext()
```

**Description**

Obtains an **AsyncContext** for subsequent use. This API is an auxiliary API of the profiler. You can use [OH_HiDebug_ReleaseAsyncContext](capi-hidebug-h.md#oh_hidebug_releaseasynccontext) to release the context.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| uint64_t | AsyncContext, which is the asynchronous thread context information. |

### OH_HiDebug_PushAsyncContext()

```c
void OH_HiDebug_PushAsyncContext(uint64_t ctx)
```

**Description**

Pushes an **AsyncContext** into the running context stack. This API is an auxiliary API of the profiler.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t ctx | Asynchronous thread context obtained by [OH_HiDebug_AcquireAsyncContext()](capi-hidebug-h.md#oh_hidebug_acquireasynccontext()). |

### OH_HiDebug_PopAsyncContext()

```c
void OH_HiDebug_PopAsyncContext(uint64_t ctx)
```

**Description**

Pops an **AsyncContext** from the running context stack. This API is an auxiliary API of the profiler.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t ctx | Asynchronous thread context obtained by [OH_HiDebug_AcquireAsyncContext()](capi-hidebug-h.md#oh_hidebug_acquireasynccontext()). |

### OH_HiDebug_ReleaseAsyncContext()

```c
void OH_HiDebug_ReleaseAsyncContext(uint64_t ctx)
```

**Description**

Releases an **AsyncContext** to the system. This API is an auxiliary API of the profiler.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t ctx | Asynchronous thread context obtained by [OH_HiDebug_AcquireAsyncContext()](capi-hidebug-h.md#oh_hidebug_acquireasynccontext()). |

### OH_HiDebug_CreateProfilerOptions()

```c
OH_HiDebug_ProfilerOptions *OH_HiDebug_CreateProfilerOptions(void)
```

**Description**

Create Profiler Options.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Returns**:

| Type | Description |
| -- | -- |
| [OH_HiDebug_ProfilerOptions *](capi-hidebug-oh-hidebug-profileroptions.md) | Pointer to the OH_HiDebug_ProfilerOptions structure. |

### OH_HiDebug_DestroyProfilerOptions()

```c
HiDebug_ErrorCode OH_HiDebug_DestroyProfilerOptions(OH_HiDebug_ProfilerOptions *opts)
```

**Description**

Destroy Profiler Options.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] Pointer to the OH_HiDebug_ProfilerOptions structure. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <ul><li>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) Success.</li>      <li>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode) opts is a null pointer.</li></ul> |

### OH_HiDebug_SetMaxAsyncNestingDepth()

```c
HiDebug_ErrorCode OH_HiDebug_SetMaxAsyncNestingDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)
```

**Description**

Sets the maximum nesting depth for asynchronous invocations.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] Pointer to the OH_HiDebug_ProfilerOptions structure. It must not be NULL. |
| uint32_t depth | [in] Maximum asynchronous nesting depth allowed. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <ul><li>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) Success.</li>      <li>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode) opts is a null pointer.</li>      <li>[HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_NESTING_DEPTH](capi-hidebug-type-h.md#hidebug_errorcode) Invalid maximum nesting depth.</li></ul> |

### OH_HiDebug_SetMaxAsyncTaskStackDepth()

```c
HiDebug_ErrorCode OH_HiDebug_SetMaxAsyncTaskStackDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)
```

**Description**

Sets the maximum stack depth for each asynchronous task function.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] Pointer to the OH_HiDebug_ProfilerOptions structure. It must not be NULL. |
| uint32_t depth | [in] Maximum asynchronous task stack depth. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <ul><li>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) Success.</li>      <li>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode) opts is a null pointer.</li>      <li>[HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_TASK_STACK_DEPTH](capi-hidebug-type-h.md#hidebug_errorcode) Invalid maximum asynchronous      task stack depth.</li></ul> |

### OH_HiDebug_SetSampleIntervalBytes()

```c
HiDebug_ErrorCode OH_HiDebug_SetSampleIntervalBytes(OH_HiDebug_ProfilerOptions *opts, uint32_t bytes)
```

**Description**

Sets the sampling interval in bytes.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] Pointer to the OH_HiDebug_ProfilerOptions structure. It must not be NULL. |
| uint32_t bytes | [in] Sample interval in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <ul><li>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) Success.</li>      <li>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode) opts is a null pointer.</li>      <li>[HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode) Invalid sampling interval.</li></ul> |

### OH_HiDebug_SetStatisticsIntervalSec()

```c
HiDebug_ErrorCode OH_HiDebug_SetStatisticsIntervalSec(OH_HiDebug_ProfilerOptions *opts, uint32_t seconds)
```

**Description**

Sets the statistics interval in seconds.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] Pointer to the OH_HiDebug_ProfilerOptions structure. It must not be NULL. |
| uint32_t seconds | [in] Statistics interval in seconds. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <ul><li>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) Success.</li>      <li>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode) opts is a null pointer.</li>      <li>[HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode) Invalid statistics interval.</li></ul> |

### OH_HiDebug_SetMaxStackDepth()

```c
HiDebug_ErrorCode OH_HiDebug_SetMaxStackDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)
```

**Description**

Sets the maximum backtrace stack depth.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] Pointer to the OH_HiDebug_ProfilerOptions structure. It must not be NULL. |
| uint32_t depth | [in] Maximum backtrace stack depth. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <ul><li>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) Success.</li>      <li>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode) opts is a null pointer.</li>      <li>[HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH](capi-hidebug-type-h.md#hidebug_errorcode) Invalid maximum backtrace stack depth.</li></ul> |

### OH_HiDebug_SetFilterSize()

```c
HiDebug_ErrorCode OH_HiDebug_SetFilterSize(OH_HiDebug_ProfilerOptions *opts, uint32_t size)
```

**Description**

Sets the filter size for allocations.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] Pointer to the OH_HiDebug_ProfilerOptions structure. It must not be NULL. |
| uint32_t size | [in] Filter size threshold in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <ul><li>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) Success.</li>      <li>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode) opts is a null pointer.</li>      <li>[HIDEBUG_RES_PROF_INVALID_FILTER_SIZE](capi-hidebug-type-h.md#hidebug_errorcode) Invalid filter size.</li></ul> |

### OH_HiDebug_SetMaxDurationSec()

```c
HiDebug_ErrorCode OH_HiDebug_SetMaxDurationSec(OH_HiDebug_ProfilerOptions *opts, uint32_t seconds)
```

**Description**

Sets the maximum profiling duration in seconds.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] Pointer to the OH_HiDebug_ProfilerOptions structure. It must not be NULL. |
| uint32_t seconds | [in] Maximum duration in seconds. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <ul><li>[HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) Success.</li>      <li>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode) opts is a null pointer.</li>      <li>[HIDEBUG_RES_PROF_INVALID_MAX_DURATION](capi-hidebug-type-h.md#hidebug_errorcode) Invalid maximum duration.</li></ul> |

### OH_HiDebug_StartProfilerWithOptions()

```c
HiDebug_ErrorCode OH_HiDebug_StartProfilerWithOptions(OH_HiDebug_ResourceType type, OH_HiDebug_ProfilerOptions *opts, OH_HiDebug_ProfilingCallback callback)
```

**Description**

Starts the profiler with the specified options and resource type.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_HiDebug_ResourceType type | [in] The resource type to be profiled (OH_HiDebug_ResourceType). |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] Pointer to the configured OH_HiDebug_ProfilerOptions structure. It must not be NULL. |
| OH_HiDebug_ProfilingCallback callback | [in] Callback function to receive profiling results. |

**Returns**:

| Type | Description |
| -- | -- |
| HiDebug_ErrorCode | Result code.      <ul><li>[HIDEBUG_RES_PROF_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) Profiler started successfully.</li>      <li>[HIDEBUG_RES_PROF_INVALID_ARG](capi-hidebug-type-h.md#hidebug_errorcode) opts or callback is a null pointer.</li>      <li>[HIDEBUG_RES_PROF_INVALID_MAX_DURATION](capi-hidebug-type-h.md#hidebug_errorcode) Maximum duration is invalid.</li>      <li>[HIDEBUG_RES_PROF_INVALID_FILTER_SIZE](capi-hidebug-type-h.md#hidebug_errorcode) FilterSize is invalid.</li>      <li>[HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH](capi-hidebug-type-h.md#hidebug_errorcode) Maximum stack depth is invalid.</li>      <li>[HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode) StatisticsInterval is invalid.</li>      <li>[HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode) Sample interval is invalid.</li>      <li>[HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_NESTING_DEPTH](capi-hidebug-type-h.md#hidebug_errorcode) Maximum asynchronous nesting depth      is invalid.</li>      <li>[HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_TASK_STACK_DEPTH](capi-hidebug-type-h.md#hidebug_errorcode) Maximum asynchronous task stack depth      is invalid.</li>      <li>[HIDEBUG_RES_PROF_INVALID_RESOURCE_TYPE](capi-hidebug-type-h.md#hidebug_errorcode) ResourceType is invalid.</li>      <li>[HIDEBUG_RES_PROF_PERMISSION_DENIED](capi-hidebug-type-h.md#hidebug_errorcode) Permission denied.</li>      <li>[HIDEBUG_RES_PROF_ALREADY_STARTED](capi-hidebug-type-h.md#hidebug_errorcode) Profiler has already been started.</li>      <li>[HIDEBUG_RES_PROF_PROCESS_OVERLIMIT](capi-hidebug-type-h.md#hidebug_errorcode) Process exceeds the limit.</li>      <li>[HIDEBUG_RES_PROF_CONFLICT](capi-hidebug-type-h.md#hidebug_errorcode) Conflict.</li>      <li>[HIDEBUG_RES_PROF_DAILY_QUOTA_EXCEEDED](capi-hidebug-type-h.md#hidebug_errorcode) Daily quota exceeded.</li>      <li>[HIDEBUG_RES_PROF_CPU_OVERLOADED](capi-hidebug-type-h.md#hidebug_errorcode) CPU overloaded.</li>      <li>[HIDEBUG_RES_PROF_MEM_PRESSURE_CRITICAL](capi-hidebug-type-h.md#hidebug_errorcode) Memory pressure is critical.</li>      <li>[HIDEBUG_RES_PROF_STORAGE_PRESSURE_CRITICAL](capi-hidebug-type-h.md#hidebug_errorcode) Storage pressure is critical.</li>      <li>[HIDEBUG_RES_PROF_FAILURE](capi-hidebug-type-h.md#hidebug_errorcode) Failed to start the resource profiler.</li></ul> |


