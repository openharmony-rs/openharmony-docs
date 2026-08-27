# hidebug.h

## 概述

定义HiDebug模块的调试功能，提供CPU使用率监控、内存信息查询、trace采集、栈回溯、性能采样、内存导出监听、维测信息记录等能力，帮助开发者进行应用性能分析、资源管理和问题诊断。

**库：** libohhidebug.so

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**起始版本：** 12

**相关模块：** [HiDebug](capi-hidebug.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) | OH_HiDebug_ProfilerOptions | 资源采集配置结构体前向声明。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [double OH_HiDebug_GetSystemCpuUsage()](#oh_hidebug_getsystemcpuusage) | - | 获取系统的CPU资源占用情况百分比。注意：由于该接口涉及跨进程通信，耗时较长，建议不要在主线程中直接调用。 |
| [double OH_HiDebug_GetAppCpuUsage()](#oh_hidebug_getappcpuusage) | - | 获取进程的CPU使用率百分比。注意：由于该接口涉及跨进程通信，耗时较长，建议不要在主线程中直接调用。 |
| [HiDebug_ThreadCpuUsagePtr OH_HiDebug_GetAppThreadCpuUsage()](#oh_hidebug_getappthreadcpuusage) | - | 获取应用所有线程CPU使用情况。注意：由于该接口涉及跨进程通信，耗时较长，建议不要在主线程中直接调用。 |
| [void OH_HiDebug_FreeThreadCpuUsage(HiDebug_ThreadCpuUsagePtr *threadCpuUsage)](#oh_hidebug_freethreadcpuusage) | - | 释放线程数据结构。 |
| [void OH_HiDebug_GetSystemMemInfo(HiDebug_SystemMemInfo *systemMemInfo)](#oh_hidebug_getsystemmeminfo) | - | 获取系统内存信息。 |
| [void OH_HiDebug_GetAppNativeMemInfo(HiDebug_NativeMemInfo *nativeMemInfo)](#oh_hidebug_getappnativememinfo) | - | 获取应用程序进程的内存信息。注意：由于该接口需要读取/proc/{pid}/smaps_rollup节点信息，耗时较长，建议不要在主线程中直接调用。 |
| [void OH_HiDebug_GetAppNativeMemInfoWithCache(HiDebug_NativeMemInfo *nativeMemInfo, bool forceRefresh)](#oh_hidebug_getappnativememinfowithcache) | - | 获取应用程序进程的内存信息，该接口存在缓存机制以提高接口性能。缓存值的有效期为5分钟。注意：由于该接口需要读取/proc/{pid}/smaps_rollup节点信息，耗时较长，建议不要在主线程中直接调用。 |
| [void OH_HiDebug_GetAppMemoryLimit(HiDebug_MemoryLimit *memoryLimit)](#oh_hidebug_getappmemorylimit) | - | 获取应用程序进程的内存限制。 |
| [HiDebug_ErrorCode OH_HiDebug_StartAppTraceCapture(HiDebug_TraceFlag flag, uint64_t tags, uint32_t limitSize, char* fileName, uint32_t length)](#oh_hidebug_startapptracecapture) | - | 启动应用trace采集。 |
| [HiDebug_ErrorCode OH_HiDebug_StopAppTraceCapture()](#oh_hidebug_stopapptracecapture) | - | 停止采集应用程序trace。 |
| [HiDebug_ErrorCode OH_HiDebug_RequestTrace(OH_HiDebug_RequestTraceConfig *config, OH_HiDebug_RequestTraceCallback callback)](#oh_hidebug_requesttrace) | - | 根据设置的采集配置请求trace采集。 |
| [HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemory(uint32_t *value)](#oh_hidebug_getgraphicsmemory) | - | 获取应用GPU显存大小。注意：由于该接口涉及多次跨进程通信，其耗时可能超过1秒，建议不要在主线程中直接调用该接口。 |
| [HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemorySummary(uint32_t interval, HiDebug_GraphicsMemorySummary *summary)](#oh_hidebug_getgraphicsmemorysummary) | - | 获取应用显存占用的详细数据。 |
| [HiDebug_ErrorCode OH_HiDebug_SetMallocDispatchTable(struct HiDebug_MallocDispatch *dispatchTable)](#oh_hidebug_setmallocdispatchtable) | - | 通过设置基础库C库中的MallocDispatch表，将原始内存操作函数（例如：malloc/free/calloc/realloc/mmap/munmap）临时替换为开发者自定义的内存操作函数。MallocDispatch表是基础库C库中封装malloc/calloc/realloc/free等内存操作函数的结构体，HiDebug_MallocDispatch只是MallocDispatch结构体的一部分。 |
| [HiDebug_MallocDispatch* OH_HiDebug_GetDefaultMallocDispatchTable(void)](#oh_hidebug_getdefaultmallocdispatchtable) | - | 获取基础库C库当前默认MallocDispatch表，调用[OH_HiDebug_RestoreMallocDispatchTable](capi-hidebug-h.md#oh_hidebug_restoremallocdispatchtable)可恢复。 |
| [void OH_HiDebug_RestoreMallocDispatchTable(void)](#oh_hidebug_restoremallocdispatchtable) | - | 恢复基础库C库MallocDispatch表。 |
| [int OH_HiDebug_BacktraceFromFp(HiDebug_Backtrace_Object object, void* startFp, void** pcArray, int size)](#oh_hidebug_backtracefromfp) | - | 根据给定的fp地址进行栈回溯，该函数异步信号安全。 |
| [typedef void (\*OH_HiDebug_SymbolicAddressCallback)(void* pc, void* arg, const HiDebug_StackFrame* frame)](#oh_hidebug_symbolicaddresscallback) | OH_HiDebug_SymbolicAddressCallback | 若[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口调用成功，将通过该函数将解析后的栈信息返回给调用者。注意：由于该接口涉及多次IO操作，耗时较长，建议不要在主线程中直接调用。 |
| [HiDebug_ErrorCode OH_HiDebug_SymbolicAddress(HiDebug_Backtrace_Object object, void* pc, void* arg, OH_HiDebug_SymbolicAddressCallback callback)](#oh_hidebug_symbolicaddress) | - | 通过给定的pc地址获取详细的符号信息，该函数非异步信号安全。不能在异步信号处理函数中使用。 |
| [HiDebug_Backtrace_Object OH_HiDebug_CreateBacktraceObject(void)](#oh_hidebug_createbacktraceobject) | - | 创建一个用于栈回溯及栈解析的对象，该函数非异步信号安全。 |
| [void OH_HiDebug_DestroyBacktraceObject(HiDebug_Backtrace_Object object)](#oh_hidebug_destroybacktraceobject) | - | 销毁由[OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject)创建的对象，以释放栈回溯及栈解析过程中申请的资源，该函数非异步信号安全。 |
| [uint64_t OH_HiDebug_SetCrashObj(HiDebug_CrashObjType type, void* addr)](#oh_hidebug_setcrashobj) | - | 将维测信息添加到崩溃日志中，与[OH_HiDebug_ResetCrashObj](capi-hidebug-h.md#oh_hidebug_resetcrashobj)配对使用。若程序在OH_HiDebug_SetCrashObj与OH_HiDebug_ResetCrashObj之间发生崩溃，会将OH_HiDebug_SetCrashObj设置的维测信息添加到记录本次崩溃的日志中。 |
| [void OH_HiDebug_ResetCrashObj(uint64_t crashObj)](#oh_hidebug_resetcrashobj) | - | 将维测信息对象还原到使用OH_HiDebug_SetCrashObj之前的状态。 |
| [typedef void (\*OH_HiDebug_ThreadLiteSamplingCallback)(const char* stacks)](#oh_hidebug_threadlitesamplingcallback) | OH_HiDebug_ThreadLiteSamplingCallback | 轻量级Perf采样栈内容的回调函数定义。注意：采样数据仅在该回调函数执行期间有效，若需在函数外使用，务必对采样栈内容进行深拷贝。 |
| [HiDebug_ErrorCode OH_HiDebug_RequestThreadLiteSampling(HiDebug_ProcessSamplerConfig* config, OH_HiDebug_ThreadLiteSamplingCallback stacksCallback)](#oh_hidebug_requestthreadlitesampling) | - |  |
| [HiDebug_ErrorCode OH_HiDebug_StartProfiler(OH_HiDebug_ResourceType type, OH_HiDebug_ResProfilerConfig* config, OH_HiDebug_ProfilingCallback callback)](#oh_hidebug_startprofiler) | - | 异步启动当前进程资源采集功能。<br>回调函数只在终止采集（含系统自动停止采集）时调用，其携带采集资源类型和采集文件路径。<br>若采集异常，则文件路径为NULL。 |
| [HiDebug_ErrorCode OH_HiDebug_StopProfiler(void)](#oh_hidebug_stopprofiler) | - | 停止当前进程资源采集功能。该接口可在[OH_HiDebug_StartProfiler](capi-hidebug-h.md#oh_hidebug_startprofiler)接口调用后使用，且调用间隔不能超过最大持续时间。 |
| [typedef bool (\*OH_HiDebug_MemDumpListener)(int32_t fd, OH_HiDebug_MemListenerType tag, bool mayReportToOEM, const char* arg)](#oh_hidebug_memdumplistener) | OH_HiDebug_MemDumpListener | 触发监听的回调函数。开发者在应用中使用FD来写入内存数据，这样就可以使用hidumper命令导出数据。 |
| [HiDebug_ErrorCode OH_HiDebug_RegisterMemDumpListener(const char* name, OH_HiDebug_MemDumpListener listener)](#oh_hidebug_registermemdumplistener) | - | 注册内存导出监听。当应用的内存占用较高，或通过{@link hidumper命令}手动导出内存信息时，系统会主动调用已注册的回调函数。<br>第三方应用框架或开发者可借此将应用内部内存信息转储到hidumper中，或通过商业灰度上传至OEM厂商。<br>对应的注销函数为：[OH_HiDebug_UnregisterMemDumpListener](capi-hidebug-h.md#oh_hidebug_unregistermemdumplistener)。 |
| [HiDebug_ErrorCode OH_HiDebug_UnregisterMemDumpListener(const char* name)](#oh_hidebug_unregistermemdumplistener) | - | 注销已经注册成功的内存导出监听。 |
| [uint64_t OH_HiDebug_AcquireAsyncContext()](#oh_hidebug_acquireasynccontext) | - | Profiler辅助接口，获取一个AsyncContext供后续使用。对应的释放函数为：[OH_HiDebug_ReleaseAsyncContext](capi-hidebug-h.md#oh_hidebug_releaseasynccontext)。 |
| [void OH_HiDebug_PushAsyncContext(uint64_t ctx)](#oh_hidebug_pushasynccontext) | - | Profiler辅助接口，将AsyncContext压入运行上下文栈表。 |
| [void OH_HiDebug_PopAsyncContext(uint64_t ctx)](#oh_hidebug_popasynccontext) | - | Profiler辅助接口，将AsyncContext从运行上下文栈表中弹出。 |
| [void OH_HiDebug_ReleaseAsyncContext(uint64_t ctx)](#oh_hidebug_releaseasynccontext) | - | Profiler辅助接口，将AsyncContext释放给系统。 |
| [OH_HiDebug_ProfilerOptions *OH_HiDebug_CreateProfilerOptions(void)](#oh_hidebug_createprofileroptions) | - | 创建Profiler选项。 |
| [HiDebug_ErrorCode OH_HiDebug_DestroyProfilerOptions(OH_HiDebug_ProfilerOptions *opts)](#oh_hidebug_destroyprofileroptions) | - | 销毁Profiler配置。 |
| [HiDebug_ErrorCode OH_HiDebug_SetMaxAsyncNestingDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)](#oh_hidebug_setmaxasyncnestingdepth) | - | 设置异步调用最大嵌套深度。 |
| [HiDebug_ErrorCode OH_HiDebug_SetMaxAsyncTaskStackDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)](#oh_hidebug_setmaxasynctaskstackdepth) | - | 设置异步任务函数的最大栈深。 |
| [HiDebug_ErrorCode OH_HiDebug_SetSampleIntervalBytes(OH_HiDebug_ProfilerOptions *opts, uint32_t bytes)](#oh_hidebug_setsampleintervalbytes) | - | 设置采样间隔（单位：字节）。 |
| [HiDebug_ErrorCode OH_HiDebug_SetStatisticsIntervalSec(OH_HiDebug_ProfilerOptions *opts, uint32_t seconds)](#oh_hidebug_setstatisticsintervalsec) | - | 设置统计时间间隔（单位：秒）。 |
| [HiDebug_ErrorCode OH_HiDebug_SetMaxStackDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)](#oh_hidebug_setmaxstackdepth) | - | 设置最大回栈深度。 |
| [HiDebug_ErrorCode OH_HiDebug_SetFilterSize(OH_HiDebug_ProfilerOptions *opts, uint32_t size)](#oh_hidebug_setfiltersize) | - | 设置过滤大小。 |
| [HiDebug_ErrorCode OH_HiDebug_SetMaxDurationSec(OH_HiDebug_ProfilerOptions *opts, uint32_t seconds)](#oh_hidebug_setmaxdurationsec) | - | 设置最大采集持续时间（单位：秒）。 |
| [HiDebug_ErrorCode OH_HiDebug_StartProfilerWithOptions(OH_HiDebug_ResourceType type, OH_HiDebug_ProfilerOptions *opts, OH_HiDebug_ProfilingCallback callback)](#oh_hidebug_startprofilerwithoptions) | - | 根据指定资源类型和配置启动分配栈trace日志采集。 |

## 函数说明

### OH_HiDebug_GetSystemCpuUsage()

```c
double OH_HiDebug_GetSystemCpuUsage()
```

**描述**

获取系统的CPU资源占用情况百分比。注意：由于该接口涉及跨进程通信，耗时较长，建议不要在主线程中直接调用。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| double | 返回系统CPU资源占用情况百分比。如果返回结果为0，可能的原因是获取失败。 |

### OH_HiDebug_GetAppCpuUsage()

```c
double OH_HiDebug_GetAppCpuUsage()
```

**描述**

获取进程的CPU使用率百分比。注意：由于该接口涉及跨进程通信，耗时较长，建议不要在主线程中直接调用。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| double | 返回进程的CPU使用率百分比。如果返回结果为0，可能因当前应用的CPU使用率过低导致。 |

### OH_HiDebug_GetAppThreadCpuUsage()

```c
HiDebug_ThreadCpuUsagePtr OH_HiDebug_GetAppThreadCpuUsage()
```

**描述**

获取应用所有线程CPU使用情况。注意：由于该接口涉及跨进程通信，耗时较长，建议不要在主线程中直接调用。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ThreadCpuUsagePtr | 返回所有线程CPU使用情况，见{@link HiDebug_ThreadCpuUsagePtr}。      <br>若返回结果为null，可能因未获取到线程相关数据所致。 |

### OH_HiDebug_FreeThreadCpuUsage()

```c
void OH_HiDebug_FreeThreadCpuUsage(HiDebug_ThreadCpuUsagePtr *threadCpuUsage)
```

**描述**

释放线程数据结构。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| HiDebug_ThreadCpuUsagePtr *threadCpuUsage | 应用的所有线程可用CPU使用缓冲区指针，见{@link HiDebug_ThreadCpuUsagePtr}。传入的参数是要由OH_HiDebug_GetAppThreadCpuUsage()得到的。传入后该函数将释放指向的线程CPU使用数据结构，释放后该指针不可再被使用。 |

### OH_HiDebug_GetSystemMemInfo()

```c
void OH_HiDebug_GetSystemMemInfo(HiDebug_SystemMemInfo *systemMemInfo)
```

**描述**

获取系统内存信息。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_SystemMemInfo](capi-hidebug-hidebug-systemmeminfo.md) *systemMemInfo | 表示指向[HiDebug_SystemMemInfo](capi-hidebug-hidebug-systemmeminfo.md)。函数调用后，若结构体数据为空，则表明调用失败。 |

### OH_HiDebug_GetAppNativeMemInfo()

```c
void OH_HiDebug_GetAppNativeMemInfo(HiDebug_NativeMemInfo *nativeMemInfo)
```

**描述**

获取应用程序进程的内存信息。注意：由于该接口需要读取/proc/{pid}/smaps_rollup节点信息，耗时较长，建议不要在主线程中直接调用。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md) *nativeMemInfo | 表示指向[HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md)。函数调用后，若结构体数据为空，则表明调用失败。 |

### OH_HiDebug_GetAppNativeMemInfoWithCache()

```c
void OH_HiDebug_GetAppNativeMemInfoWithCache(HiDebug_NativeMemInfo *nativeMemInfo, bool forceRefresh)
```

**描述**

获取应用程序进程的内存信息，该接口存在缓存机制以提高接口性能。缓存值的有效期为5分钟。注意：由于该接口需要读取/proc/{pid}/smaps_rollup节点信息，耗时较长，建议不要在主线程中直接调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md) *nativeMemInfo | 表示指向[HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md)。函数调用后，若结构体数据为空，则表明调用失败。 |
| bool forceRefresh | 是否需要无视缓存有效性，强制更新缓存值。<br>当为true时，直接获取当前内存数据并更新缓存值；<br>当为false时，缓存有效时，直接返回缓存值，缓存失效时，获取当前内存数据并更新缓存值。 |

### OH_HiDebug_GetAppMemoryLimit()

```c
void OH_HiDebug_GetAppMemoryLimit(HiDebug_MemoryLimit *memoryLimit)
```

**描述**

获取应用程序进程的内存限制。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_MemoryLimit](capi-hidebug-hidebug-memorylimit.md) *memoryLimit | 表示指向[HiDebug_MemoryLimit](capi-hidebug-hidebug-memorylimit.md)。函数调用后，若结构体数据为空，则表明调用失败。 |

### OH_HiDebug_StartAppTraceCapture()

```c
HiDebug_ErrorCode OH_HiDebug_StartAppTraceCapture(HiDebug_TraceFlag flag, uint64_t tags, uint32_t limitSize, char* fileName, uint32_t length)
```

**描述**

启动应用trace采集。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| HiDebug_TraceFlag flag | 采集线程trace方式。 |
| uint64_t tags | 采集trace场景标签。 |
| uint32_t limitSize | trace文件的最大大小（以字节为单位），最大为 500MB。 |
| char* fileName | 输出trace文件名缓冲区。 |
| uint32_t length | 输出trace文件名缓冲区长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 0 - 成功。      <br>{@link HIDEBUG_INVALID_ARGUMENT} 401 - fileName参数为空指针或者传入的length参数过小或者limitSize参数小于等于0。      <br>11400102 - 已经开启了一个trace。      <br>11400103 - 没有权限去开启trace。      <br>11400104 - 系统内部错误。 |

### OH_HiDebug_StopAppTraceCapture()

```c
HiDebug_ErrorCode OH_HiDebug_StopAppTraceCapture()
```

**描述**

停止采集应用程序trace。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 0 - 成功。      <br>11400104 - 系统内部错误。      <br>11400105 - 当前没有trace正在运行。 |

### OH_HiDebug_RequestTrace()

```c
HiDebug_ErrorCode OH_HiDebug_RequestTrace(OH_HiDebug_RequestTraceConfig *config, OH_HiDebug_RequestTraceCallback callback)
```

**描述**

根据设置的采集配置请求trace采集。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_RequestTraceConfig](capi-hidebug-oh-hidebug-requesttraceconfig.md) *config | trace采集的采集配置参数，参考[OH_HiDebug_RequestTraceConfig](capi-hidebug-oh-hidebug-requesttraceconfig.md)。 |
| [OH_HiDebug_RequestTraceCallback](capi-hidebug-type-h.md#oh_hidebug_requesttracecallback) callback | trace采集的回调函数，参考[OH_HiDebug_RequestTraceCallback](capi-hidebug-type-h.md#oh_hidebug_requesttracecallback)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回结果码：      <br>{@link HIDEBUG_SUCCESS}：采集成功。      <br>{@link HIDEBUG_TRACE_ABNORMAL}：远程服务异常或状态异常。      <br>{@link OH_HIDEBUG_TRACE_STORAGE_LIMIT}：trace存储达到限制。目录下存储的trace文件大于等于3份时，返回失败。      <br>{@link HIDEBUG_RESOURCE_UNAVAILABLE}：采集资源限制。 |

### OH_HiDebug_GetGraphicsMemory()

```c
HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemory(uint32_t *value)
```

**描述**

获取应用GPU显存大小。注意：由于该接口涉及多次跨进程通信，其耗时可能超过1秒，建议不要在主线程中直接调用该接口。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t *value | 指向用来保存接口获取到的应用显存大小（单位KB）的变量的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 0 - 接口获取成功。      <br>401 - 无效参数，所传递参数为空指针。      <br>11400104 - 系统内部错误。 |

### OH_HiDebug_GetGraphicsMemorySummary()

```c
HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemorySummary(uint32_t interval, HiDebug_GraphicsMemorySummary *summary)
```

**描述**

获取应用显存占用的详细数据。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t interval | 当显存数据缓存值存在时间超过设定间隔interval（单位：秒）时，接口会获取最新的显存数据并更新缓存；否则，接口将直接返回缓存值。<br>interval的取值范围为[2, 3600]，若传入的interval超出取值范围时，将使用300作为默认值。 |
| [HiDebug_GraphicsMemorySummary](capi-hidebug-hidebug-graphicsmemorysummary.md) *summary | 表示指向[HiDebug_GraphicsMemorySummary](capi-hidebug-hidebug-graphicsmemorysummary.md)的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回结果具体可参考{@link HiDebug_ErrorCode}：      <br>{@link HIDEBUG_SUCCESS} 成功获取到应用显存数据。      <br>{@link HIDEBUG_INVALID_ARGUMENT} 无效参数。      <br>{@link HIDEBUG_TRACE_ABNORMAL} 系统内部错误。 |

### OH_HiDebug_SetMallocDispatchTable()

```c
HiDebug_ErrorCode OH_HiDebug_SetMallocDispatchTable(struct HiDebug_MallocDispatch *dispatchTable)
```

**描述**

通过设置基础库C库中的MallocDispatch表，将原始内存操作函数（例如：malloc/free/calloc/realloc/mmap/munmap）临时替换为开发者自定义的内存操作函数。MallocDispatch表是基础库C库中封装malloc/calloc/realloc/free等内存操作函数的结构体，HiDebug_MallocDispatch只是MallocDispatch结构体的一部分。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md) *dispatchTable | 指向开发者自定义内存操作函数[HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md)结构体指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回结果具体可参考{@link HiDebug_ErrorCode}：      <br>{@link HIDEBUG_SUCCESS} 成功设置自定义内存操作函数。      <br>{@link HIDEBUG_INVALID_ARGUMENT} 无效参数。 |

### OH_HiDebug_GetDefaultMallocDispatchTable()

```c
HiDebug_MallocDispatch* OH_HiDebug_GetDefaultMallocDispatchTable(void)
```

**描述**

获取基础库C库当前默认MallocDispatch表，调用[OH_HiDebug_RestoreMallocDispatchTable](capi-hidebug-h.md#oh_hidebug_restoremallocdispatchtable)可恢复。

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [HiDebug_MallocDispatch*](capi-hidebug-hidebug-mallocdispatch.md) | 当前C库默认的[HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md)结构体指针。 |

### OH_HiDebug_RestoreMallocDispatchTable()

```c
void OH_HiDebug_RestoreMallocDispatchTable(void)
```

**描述**

恢复基础库C库MallocDispatch表。

**起始版本：** 20

### OH_HiDebug_BacktraceFromFp()

```c
int OH_HiDebug_BacktraceFromFp(HiDebug_Backtrace_Object object, void* startFp, void** pcArray, int size)
```

**描述**

根据给定的fp地址进行栈回溯，该函数异步信号安全。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_Backtrace_Object](capi-hidebug-hidebug-backtrace-object--8h.md) object | 由[OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject)接口获取到的用来栈回溯的对象。 |
| void* startFp | 栈回溯的起始栈帧地址。 |
| void** pcArray | 保存栈回溯得到的pc地址的数组。 |
| int size | 保存栈回溯得到的pc地址的数组长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功回溯并写入到pcArray中的栈帧数量。如果返回结果为0，原因可能是栈回溯失败。 |

### OH_HiDebug_SymbolicAddressCallback()

```c
typedef void (*OH_HiDebug_SymbolicAddressCallback)(void* pc, void* arg, const HiDebug_StackFrame* frame)
```

**描述**

若[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口调用成功，将通过该函数将解析后的栈信息返回给调用者。注意：由于该接口涉及多次IO操作，耗时较长，建议不要在主线程中直接调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void\* pc | 传入[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口的需要解析的pc地址。 |
| void\* arg | 传入[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口的arg值。 |
| [const HiDebug_StackFrame](capi-hidebug-hidebug-stackframe.md)\* frame | 由传入[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口的pc地址解析后得到栈信息[HiDebug_StackFrame](capi-hidebug-hidebug-stackframe.md)指针，该指针指向内容仅在该函数作用域内有效。 |

### OH_HiDebug_SymbolicAddress()

```c
HiDebug_ErrorCode OH_HiDebug_SymbolicAddress(HiDebug_Backtrace_Object object, void* pc, void* arg, OH_HiDebug_SymbolicAddressCallback callback)
```

**描述**

通过给定的pc地址获取详细的符号信息，该函数非异步信号安全。不能在异步信号处理函数中使用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_Backtrace_Object](capi-hidebug-hidebug-backtrace-object--8h.md) object | 由[OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject)接口创建的对象。 |
| void* pc | 由[OH_HiDebug_BacktraceFromFp](capi-hidebug-h.md#oh_hidebug_backtracefromfp)接口获取到的pc地址。 |
| void* arg | 保留的自定义参数，符号解析成功后系统内部会将该参数传递给回调函数[OH_HiDebug_SymbolicAddressCallback](capi-hidebug-h.md#oh_hidebug_symbolicaddresscallback)。 |
| [OH_HiDebug_SymbolicAddressCallback](capi-hidebug-h.md#oh_hidebug_symbolicaddresscallback) callback | 用于返回解析后栈信息的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回结果具体可参考{@link HiDebug_ErrorCode}：      <br>{@link HIDEBUG_SUCCESS} 成功获取到详细的栈信息，且该函数传入的callback被调用。      <br>{@link HIDEBUG_INVALID_ARGUMENT} 无效参数。      <br>{@link HIDEBUG_INVALID_SYMBOLIC_PC_ADDRESS} 无法根据传入的pc地址找到对应的符号。 |

### OH_HiDebug_CreateBacktraceObject()

```c
HiDebug_Backtrace_Object OH_HiDebug_CreateBacktraceObject(void)
```

**描述**

创建一个用于栈回溯及栈解析的对象，该函数非异步信号安全。

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [HiDebug_Backtrace_Object](capi-hidebug-hidebug-backtrace-object--8h.md) | 返回创建的对象的指针，当创建失败时返回NULL。 |

### OH_HiDebug_DestroyBacktraceObject()

```c
void OH_HiDebug_DestroyBacktraceObject(HiDebug_Backtrace_Object object)
```

**描述**

销毁由[OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject)创建的对象，以释放栈回溯及栈解析过程中申请的资源，该函数非异步信号安全。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_Backtrace_Object](capi-hidebug-hidebug-backtrace-object--8h.md) object | 需要被销毁的对象。 |

### OH_HiDebug_SetCrashObj()

```c
uint64_t OH_HiDebug_SetCrashObj(HiDebug_CrashObjType type, void* addr)
```

**描述**

将维测信息添加到崩溃日志中，与[OH_HiDebug_ResetCrashObj](capi-hidebug-h.md#oh_hidebug_resetcrashobj)配对使用。若程序在OH_HiDebug_SetCrashObj与OH_HiDebug_ResetCrashObj之间发生崩溃，会将OH_HiDebug_SetCrashObj设置的维测信息添加到记录本次崩溃的日志中。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| HiDebug_CrashObjType type | 维测信息的数据类型{@link HiDebug_CrashObjType}。 |
| void* addr | 维测信息的地址，崩溃时该地址必须保持有效。设置后，若程序崩溃，系统将读取该地址指向的维测信息并记录到崩溃日志中。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint64_t | 上次设置的维测信息的对象，如果上次没有设置则为0。 |

### OH_HiDebug_ResetCrashObj()

```c
void OH_HiDebug_ResetCrashObj(uint64_t crashObj)
```

**描述**

将维测信息对象还原到使用OH_HiDebug_SetCrashObj之前的状态。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t crashObj | 函数OH_HiDebug_SetCrashObj的返回值。 |

### OH_HiDebug_ThreadLiteSamplingCallback()

```c
typedef void (*OH_HiDebug_ThreadLiteSamplingCallback)(const char* stacks)
```

**描述**

轻量级Perf采样栈内容的回调函数定义。注意：采样数据仅在该回调函数执行期间有效，若需在函数外使用，务必对采样栈内容进行深拷贝。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char\* stacks | 采样得到的调用栈内容。 |

### OH_HiDebug_RequestThreadLiteSampling()

```c
HiDebug_ErrorCode OH_HiDebug_RequestThreadLiteSampling(HiDebug_ProcessSamplerConfig* config, OH_HiDebug_ThreadLiteSamplingCallback stacksCallback)
```

**描述**

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_ProcessSamplerConfig](capi-hidebug-hidebug-processsamplerconfig.md)* config | 指向Perf采样配置结构体[HiDebug_ProcessSamplerConfig](capi-hidebug-hidebug-processsamplerconfig.md)的指针。配置参数决定了采样的具体行为，如采样频率、目标线程等。 |
| [OH_HiDebug_ThreadLiteSamplingCallback](capi-hidebug-h.md#oh_hidebug_threadlitesamplingcallback) stacksCallback | 采样结束时的回调函数，用于返回采样结果。采样完成后，系统将调用此函数并将采样数据作为参数传递。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回结果码：      <br>{@link HIDEBUG_SUCCESS}：采样成功完成。      <br>{@link HIDEBUG_INVALID_ARGUMENT}：无效参数。      <br>{@link HIDEBUG_NOT_SUPPORTED}：当前设备不支持Perf采样。      <br>{@link HIDEBUG_UNDER_SAMPLING}：已有采样任务正在执行中。      <br>{@link HIDEBUG_RESOURCE_UNAVAILABLE}：采样资源不足或已达调用上限。 |

### OH_HiDebug_StartProfiler()

```c
HiDebug_ErrorCode OH_HiDebug_StartProfiler(OH_HiDebug_ResourceType type, OH_HiDebug_ResProfilerConfig* config, OH_HiDebug_ProfilingCallback callback)
```

**描述**

异步启动当前进程资源采集功能。<br>回调函数只在终止采集（含系统自动停止采集）时调用，其携带采集资源类型和采集文件路径。<br>若采集异常，则文件路径为NULL。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ResourceType](capi-hidebug-type-h.md#oh_hidebug_resourcetype) type | 资源采集类型，决定了采集的具体资源类别（如CPU、内存、IO等）。不同类型对应不同资源采集场景：CPU采集用于分析CPU性能问题，内存采集用于分析内存泄漏和内存使用情况，IO采集用于分析IO性能瓶颈。根据分析需求选择合适的资源类型。 |
| [OH_HiDebug_ResProfilerConfig](capi-hidebug-oh-hidebug-resprofilerconfig.md)* config | 资源采集配置参数。配置参数决定了采集的具体行为，如采样频率、持续时间等。 |
| [OH_HiDebug_ProfilingCallback](capi-hidebug-type-h.md#oh_hidebug_profilingcallback) callback | 资源采集回调结果函数。采集终止时将调用此回调函数，传递采集结果和文件路径。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回结果码：      <br>{@link HIDEBUG_RES_PROF_SUCCESS}：启动资源采集成功。      <br>{@link HIDEBUG_RES_PROF_INVALID_ARG}：资源采集参数无效。      <br>{@link HIDEBUG_RES_PROF_INVALID_MAX_DURATION}：资源采集最大持续时间参数无效。      <br>{@link HIDEBUG_RES_PROF_INVALID_FILTER_SIZE}：资源采集过滤大小参数无效。      <br>{@link HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH}：资源采集最大回栈深度参数无效。      <br>{@link HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL}：资源采集统计间隔参数无效。      <br>{@link HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL}：资源采集采样大小参数无效。      <br>{@link HIDEBUG_RES_PROF_INVALID_RESOURCE_TYPE}：资源采集类型参数无效。      <br>{@link HIDEBUG_RES_PROF_PERMISSION_DENIED}：资源采集权限不足，采集资源的目标进程仅支持调用接口进程本身。      <br>{@link HIDEBUG_RES_PROF_ALREADY_STARTED}：资源采集重复启动。      <br>{@link HIDEBUG_RES_PROF_PROCESS_OVERLIMIT}：资源采集进程数超出 4 个限制。      <br>{@link HIDEBUG_RES_PROF_CONFLICT}：资源采集与命令行工具或系统采集任务冲突。      <br>{@link HIDEBUG_RES_PROF_DAILY_QUOTA_EXCEEDED}：资源采集每日配额超出 10 次限制。      <br>{@link HIDEBUG_RES_PROF_CPU_OVERLOADED}：系统 CPU 处于高负载状态，CPU 占用率超过 70%。      <br>{@link HIDEBUG_RES_PROF_MEM_PRESSURE_CRITICAL}：内存可用空间紧张，可用空间少于 15%。      <br>{@link HIDEBUG_RES_PROF_STORAGE_PRESSURE_CRITICAL}：存储可用空间紧张，可用空间少于 15%。      <br>{@link HIDEBUG_RES_PROF_FAILURE}：启动资源采集失败。 |

### OH_HiDebug_StopProfiler()

```c
HiDebug_ErrorCode OH_HiDebug_StopProfiler(void)
```

**描述**

停止当前进程资源采集功能。该接口可在[OH_HiDebug_StartProfiler](capi-hidebug-h.md#oh_hidebug_startprofiler)接口调用后使用，且调用间隔不能超过最大持续时间。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回结果码：      <br>{@link HIDEBUG_RES_PROF_SUCCESS}：已成功停止资源采集。      <br>{@link HIDEBUG_RES_PROF_NOT_STARTED}：资源采集未启动，停止失败。      <br>{@link HIDEBUG_RES_PROF_FAILURE}：停止资源采集失败。 |

### OH_HiDebug_MemDumpListener()

```c
typedef bool (*OH_HiDebug_MemDumpListener)(int32_t fd, OH_HiDebug_MemListenerType tag, bool mayReportToOEM, const char* arg)
```

**描述**

触发监听的回调函数。开发者在应用中使用FD来写入内存数据，这样就可以使用hidumper命令导出数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fd | 开发者使用FD在应用程序中写入内存数据。 |
| [OH_HiDebug_MemListenerType](capi-hidebug-type-h.md#oh_hidebug_memlistenertype) tag | 回调类型。开发人员根据回调类型处理相关逻辑。 |
| bool mayReportToOEM | 当值为true时告知开发者该数据会上传给OEM厂商请注意数据隐私安全问题 |
| const char\* arg | 回调参数。根据type的值传递不同的参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 操作是否成功。 |

### OH_HiDebug_RegisterMemDumpListener()

```c
HiDebug_ErrorCode OH_HiDebug_RegisterMemDumpListener(const char* name, OH_HiDebug_MemDumpListener listener)
```

**描述**

注册内存导出监听。当应用的内存占用较高，或通过{@link hidumper命令}手动导出内存信息时，系统会主动调用已注册的回调函数。<br>第三方应用框架或开发者可借此将应用内部内存信息转储到hidumper中，或通过商业灰度上传至OEM厂商。<br>对应的注销函数为：[OH_HiDebug_UnregisterMemDumpListener](capi-hidebug-h.md#oh_hidebug_unregistermemdumplistener)。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* name | 监听器的唯一标识。用于标识本次注册的监听，注销时需传入相同的name。<br>相同name只能注册一次，重复注册将返回HIDEBUG_INVALID_ARGUMENT；如需更新，请先注销原监听器。 |
| [OH_HiDebug_MemDumpListener](capi-hidebug-h.md#oh_hidebug_memdumplistener) listener | 触发监听的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回结果码：      <br>{@link HIDEBUG_SUCCESS}：操作成功。      <br>{@link HIDEBUG_INVALID_ARGUMENT}：无效参数。 |

### OH_HiDebug_UnregisterMemDumpListener()

```c
HiDebug_ErrorCode OH_HiDebug_UnregisterMemDumpListener(const char* name)
```

**描述**

注销已经注册成功的内存导出监听。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* name | 监听器的唯一标识。需要与注册时传入的name保持一致。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回结果码：      <br>{@link HIDEBUG_SUCCESS}：操作成功。      <br>{@link HIDEBUG_INVALID_ARGUMENT}：无效参数。 |

### OH_HiDebug_AcquireAsyncContext()

```c
uint64_t OH_HiDebug_AcquireAsyncContext()
```

**描述**

Profiler辅助接口，获取一个AsyncContext供后续使用。对应的释放函数为：[OH_HiDebug_ReleaseAsyncContext](capi-hidebug-h.md#oh_hidebug_releaseasynccontext)。

**起始版本：** 26.0.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint64_t | AsyncContext，异步线程上下文信息。 |

### OH_HiDebug_PushAsyncContext()

```c
void OH_HiDebug_PushAsyncContext(uint64_t ctx)
```

**描述**

Profiler辅助接口，将AsyncContext压入运行上下文栈表。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t ctx | 由[OH_HiDebug_AcquireAsyncContext()](capi-hidebug-h.md#oh_hidebug_acquireasynccontext())获取的异步线程上下文。 |

### OH_HiDebug_PopAsyncContext()

```c
void OH_HiDebug_PopAsyncContext(uint64_t ctx)
```

**描述**

Profiler辅助接口，将AsyncContext从运行上下文栈表中弹出。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t ctx | 由[OH_HiDebug_AcquireAsyncContext()](capi-hidebug-h.md#oh_hidebug_acquireasynccontext())获取的异步线程上下文。 |

### OH_HiDebug_ReleaseAsyncContext()

```c
void OH_HiDebug_ReleaseAsyncContext(uint64_t ctx)
```

**描述**

Profiler辅助接口，将AsyncContext释放给系统。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t ctx | 由[OH_HiDebug_AcquireAsyncContext()](capi-hidebug-h.md#oh_hidebug_acquireasynccontext())获取的异步线程上下文。 |

### OH_HiDebug_CreateProfilerOptions()

```c
OH_HiDebug_ProfilerOptions *OH_HiDebug_CreateProfilerOptions(void)
```

**描述**

创建Profiler选项。

**起始版本：** 26.1.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_HiDebug_ProfilerOptions *](capi-hidebug-oh-hidebug-profileroptions.md) | 指向OH_HiDebug_ProfilerOptions结构体的指针。 |

### OH_HiDebug_DestroyProfilerOptions()

```c
HiDebug_ErrorCode OH_HiDebug_DestroyProfilerOptions(OH_HiDebug_ProfilerOptions *opts)
```

**描述**

销毁Profiler配置。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] 指向OH_HiDebug_ProfilerOptions结构体的指针，该参数须为非空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回码。  <ul><li>{@link HIDEBUG_SUCCESS}成功</li>  <li>{@link HIDEBUG_RES_PROF_INVALID_ARG} opts是一个空指针。</li></ul> |

### OH_HiDebug_SetMaxAsyncNestingDepth()

```c
HiDebug_ErrorCode OH_HiDebug_SetMaxAsyncNestingDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)
```

**描述**

设置异步调用最大嵌套深度。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] 指向OH_HiDebug_ProfilerOptions结构体的指针，该参数须为非空指针。 |
| uint32_t depth | [in] 允许的最大异步嵌套深度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回码。      <ul><li>{@link HIDEBUG_SUCCESS} 成功。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_ARG} opts是一个空指针。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_NESTING_DEPTH} 无效的最大异步嵌套深度。</li></ul> |

### OH_HiDebug_SetMaxAsyncTaskStackDepth()

```c
HiDebug_ErrorCode OH_HiDebug_SetMaxAsyncTaskStackDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)
```

**描述**

设置异步任务函数的最大栈深。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] 指向OH_HiDebug_ProfilerOptions结构体的指针，该参数须为非空指针。 |
| uint32_t depth | [in] 最大异步任务栈深。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回码。      <ul><li>{@link HIDEBUG_SUCCESS} 成功。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_ARG} opts是一个空指针。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_TASK_STACK_DEPTH} 无效的最大异步任务栈深度。</li></ul> |

### OH_HiDebug_SetSampleIntervalBytes()

```c
HiDebug_ErrorCode OH_HiDebug_SetSampleIntervalBytes(OH_HiDebug_ProfilerOptions *opts, uint32_t bytes)
```

**描述**

设置采样间隔（单位：字节）。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] 指向OH_HiDebug_ProfilerOptions结构体的指针，该参数须为非空指针。 |
| uint32_t bytes | [in] 采样间隔。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回码。      <ul><li>{@link HIDEBUG_SUCCESS} 成功。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_ARG} opts是一个空指针。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL} 无效的采样间隔。</li></ul> |

### OH_HiDebug_SetStatisticsIntervalSec()

```c
HiDebug_ErrorCode OH_HiDebug_SetStatisticsIntervalSec(OH_HiDebug_ProfilerOptions *opts, uint32_t seconds)
```

**描述**

设置统计时间间隔（单位：秒）。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] 指向OH_HiDebug_ProfilerOptions结构体的指针，该参数须为非空指针。 |
| uint32_t seconds | [in] 统计时间间隔。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回码。      <ul><li>{@link HIDEBUG_SUCCESS} 成功。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_ARG} opts是一个空指针。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL} 无效的统计间隔。</li></ul> |

### OH_HiDebug_SetMaxStackDepth()

```c
HiDebug_ErrorCode OH_HiDebug_SetMaxStackDepth(OH_HiDebug_ProfilerOptions *opts, uint32_t depth)
```

**描述**

设置最大回栈深度。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] 指向OH_HiDebug_ProfilerOptions结构体的指针，该参数须为非空指针。 |
| uint32_t depth | [in] 最大回栈深度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回码。      <ul><li>{@link HIDEBUG_SUCCESS} 成功。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_ARG} opts是一个空指针。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH} 无效的最大栈深度。</li></ul> |

### OH_HiDebug_SetFilterSize()

```c
HiDebug_ErrorCode OH_HiDebug_SetFilterSize(OH_HiDebug_ProfilerOptions *opts, uint32_t size)
```

**描述**

设置过滤大小。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] 指向OH_HiDebug_ProfilerOptions结构体的指针，该参数须为非空指针。 |
| uint32_t size | [in] 过滤大小（单位：字节）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回码。      <ul><li>{@link HIDEBUG_SUCCESS} 成功。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_ARG} opts是一个空指针。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_FILTER_SIZE} 无效的过滤大小。</li></ul> |

### OH_HiDebug_SetMaxDurationSec()

```c
HiDebug_ErrorCode OH_HiDebug_SetMaxDurationSec(OH_HiDebug_ProfilerOptions *opts, uint32_t seconds)
```

**描述**

设置最大采集持续时间（单位：秒）。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] 指向OH_HiDebug_ProfilerOptions结构体的指针，该参数须为非空指针。 |
| uint32_t seconds | [in] 最大采集持续时间（单位：秒）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回码。      <ul><li>{@link HIDEBUG_SUCCESS} 成功。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_ARG} opts是一个空指针。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_MAX_DURATION} 无效的最大持续时间。</li></ul> |

### OH_HiDebug_StartProfilerWithOptions()

```c
HiDebug_ErrorCode OH_HiDebug_StartProfilerWithOptions(OH_HiDebug_ResourceType type, OH_HiDebug_ProfilerOptions *opts, OH_HiDebug_ProfilingCallback callback)
```

**描述**

根据指定资源类型和配置启动分配栈trace日志采集。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ResourceType](capi-hidebug-type-h.md#oh_hidebug_resourcetype) type | [in] 指定采集资源类型（OH_HiDebug_ResourceType）。 |
| [OH_HiDebug_ProfilerOptions](capi-hidebug-oh-hidebug-profileroptions.md) *opts | [in] 指向OH_HiDebug_ProfilerOptions资源采集配置结构体的指针，该参数须为非空指针。 |
| [OH_HiDebug_ProfilingCallback](capi-hidebug-type-h.md#oh_hidebug_profilingcallback) callback | [in] 接收采集结果的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| HiDebug_ErrorCode | 返回码。      <ul><li>{@link HIDEBUG_RES_PROF_SUCCESS}启动资源采集成功。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_ARG} opts或callback是一个空指针。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_MAX_DURATION}资源采集最大持续时间参数无效。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_FILTER_SIZE}资源采集过滤大小参数无效。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH}资源采集最大回栈深度参数无效。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL}资源采集统计间隔参数无效。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL}资源采集采样大小参数无效。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_NESTING_DEPTH}最大异步嵌套深度参数无效。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_MAX_ASYNC_TASK_STACK_DEPTH}最大异步任务回栈栈深参数无效。</li>      <li>{@link HIDEBUG_RES_PROF_INVALID_RESOURCE_TYPE}资源类型参数无效。</li>      <li>{@link HIDEBUG_RES_PROF_PERMISSION_DENIED}资源采集权限不足，采集资源的目标进程仅支持调用接口进程本身。</li>      <li>{@link HIDEBUG_RES_PROF_ALREADY_STARTED}资源采集重复启动。</li>      <li>{@link HIDEBUG_RES_PROF_PROCESS_OVERLIMIT}资源采集进程数超出限制。</li>      <li>{@link HIDEBUG_RES_PROF_CONFLICT}资源采集与命令行工具或系统采集任务冲突。</li>      <li>{@link HIDEBUG_RES_PROF_DAILY_QUOTA_EXCEEDED}资源采集每日配额超出限制。</li>      <li>{@link HIDEBUG_RES_PROF_CPU_OVERLOADED}系统CPU高负载，禁止采集。</li>      <li>{@link HIDEBUG_RES_PROF_MEM_PRESSURE_CRITICAL}系统内存可用空间紧张，禁止采集。</li>      <li>{@link HIDEBUG_RES_PROF_STORAGE_PRESSURE_CRITICAL}存储可用空间紧张，禁止采集。</li>     <li>{@link HIDEBUG_RES_PROF_FAILURE}启动资源采集失败。</li></ul> |


