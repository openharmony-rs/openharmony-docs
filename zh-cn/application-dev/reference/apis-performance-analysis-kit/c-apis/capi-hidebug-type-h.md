# hidebug_type.h

## 概述

Defines the code of the HiDebug module.

**库：** libohhidebug.so

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**起始版本：** 12

**相关模块：** [HiDebug](capi-hidebug.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [HiDebug_ThreadCpuUsage](capi-hidebug-hidebug-threadcpuusage.md) | HiDebug_ThreadCpuUsage | 当前进程所有线程的CPU使用率结构体定义。<br>使用场景：<br>应用性能监控：获取线程CPU使用率，监控应用的运行状态和性能瓶颈。<br>线程性能优化：分析各线程的CPU占用情况，优化线程调度和资源分配。<br>系统调试：在调试阶段追踪线程的CPU使用情况，定位性能问题。 |
| [HiDebug_SystemMemInfo](capi-hidebug-hidebug-systemmeminfo.md) | HiDebug_SystemMemInfo | 系统内存信息结构类型定义。用于获取系统内存的总量、空闲量、可用量等关键信息，适用于系统性能分析、内存监控、故障诊断等场景，帮助开发者了解系统内存使用状况，优化内存管理策略。 |
| [HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md) | HiDebug_NativeMemInfo | 应用程序进程本机内存信息结构类型定义。 |
| [HiDebug_MemoryLimit](capi-hidebug-hidebug-memorylimit.md) | HiDebug_MemoryLimit | 应用程序进程内存限制结构类型定义。 |
| [OH_HiDebug_RequestTraceConfig](capi-hidebug-oh-hidebug-requesttraceconfig.md) | OH_HiDebug_RequestTraceConfig | 请求trace采集的配置结构类型定义。用于在应用性能分析和调试场景中配置trace采集参数，如定位应用启动慢、UI卡顿、CPU占用高等性能问题。 |
| [HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md) | HiDebug_MallocDispatch | 应用程序进程可替换/恢复的HiDebug_MallocDispatch表结构类型定义。通过该结构体，开发者可以自定义内存管理函数指针，实现对进程内存分配和释放的监控与定制。主要特点包括：支持动态替换和恢复内存管理函数、提供全面的内存操作接口（malloc、calloc、realloc、free、mmap、munmap）、不影响系统默认内存管理行为。使用场景包括：内存泄漏检测、内存使用性能分析、自定义内存分配策略、内存安全监控等。能够帮助开发者及时发现和解决内存问题，提升应用稳定性和性能。 |
| [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) | HiDebug_JsStackFrame | js栈帧内容的定义。用于在性能分析和调试场景中，记录js调用栈的帧信息，包括代码位置、函数名称、映射区域等关键信息。 |
| [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) | HiDebug_NativeStackFrame | native栈帧内容的定义。 |
| [HiDebug_StackFrame](capi-hidebug-hidebug-stackframe.md) | HiDebug_StackFrame | 栈帧内容的定义。该结构体用于表示调试时的栈帧信息，支持获取当前栈的类型以及对应的js栈帧或Native栈帧内容，帮助开发者进行问题定位和调试分析。 |
| [HiDebug_GraphicsMemorySummary](capi-hidebug-hidebug-graphicsmemorysummary.md) | HiDebug_GraphicsMemorySummary | 应用图形显存占用详情的结构定义。 |
| [HiDebug_ProcessSamplerConfig](capi-hidebug-hidebug-processsamplerconfig.md) | HiDebug_ProcessSamplerConfig | 采样配置的结构定义。 |
| [OH_HiDebug_ProfilingResult](capi-hidebug-oh-hidebug-profilingresult.md) | OH_HiDebug_ProfilingResult | 封装单次资源采集的结果。 |
| [OH_HiDebug_ResProfilerConfig](capi-hidebug-oh-hidebug-resprofilerconfig.md) | OH_HiDebug_ResProfilerConfig | 定义资源采集配置结构体类型。 |
| [HiDebug_Backtrace_Object__*](capi-hidebug-hidebug-backtrace-object--8h.md) | HiDebug_Backtrace_Object | 用于栈回溯及栈解析的对象。该对象封装了栈回溯所需的上下文信息，包括调用栈地址、线程状态等数据，通过相关接口可获取详细的栈帧信息和符号解析结果。该对象通过HiDebug相关接口创建，使用后需要调用对应的销毁接口释放资源。 |
| [HiDebug_ThreadCpuUsage*](capi-hidebug-hidebug-threadcpuusage8h.md) | HiDebug_ThreadCpuUsagePtr | Defines pointer of HiDebug_ThreadCpuUsage. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_HiDebug_ResourceType](#oh_hidebug_resourcetype) | OH_HiDebug_ResourceType | 定义资源采集类型的枚举。 |
| [OH_HiDebug_MemListenerType](#oh_hidebug_memlistenertype) | OH_HiDebug_MemListenerType | 内存监听回调的类型枚举。开发者根据回调类型处理相关逻辑。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| HIDEBUG_TRACE_TAG_FFRT (1ULL << 13) | FFRT tasks.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_COMMON_LIBRARY (1ULL << 16) | Common library subsystem tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_HDF (1ULL << 18) | HDF subsystem tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_NET (1ULL << 23) | Net tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_NWEB (1ULL << 24) | NWeb tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_AUDIO (1ULL << 27) | Distributed audio tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_FILE_MANAGEMENT (1ULL << 29) | File management tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_OHOS (1ULL << 30) | OHOS generic tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_ABILITY_MANAGER (1ULL << 31) | Ability Manager tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_CAMERA (1ULL << 32) | Camera module tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_MEDIA (1ULL << 33) | Media module tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_IMAGE (1ULL << 34) | Image module tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_AUDIO (1ULL << 35) | Audio module tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_DATA (1ULL << 36) | Distributed data manager module tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_GRAPHICS (1ULL << 38) | Graphics module tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_ARKUI (1ULL << 39) | ARKUI development framework tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_NOTIFICATION (1ULL << 40) | Notification module tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_MISC (1ULL << 41) | MISC module tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_MULTIMODAL_INPUT (1ULL << 42) | Multimodal input module tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_RPC (1ULL << 46) | RPC tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_ARK (1ULL << 47) | ARK tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_WINDOW_MANAGER (1ULL << 48) | Window manager tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_SCREEN (1ULL << 50) | Distributed screen tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_CAMERA (1ULL << 51) | Distributed camera tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_FRAMEWORK (1ULL << 52) | Distributed hardware framework tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_GLOBAL_RESOURCE_MANAGER (1ULL << 53) | Global resource manager tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_HARDWARE_DEVICE_MANAGER (1ULL << 54) | Distributed hardware device manager tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_SAMGR (1ULL << 55) | SA tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_POWER_MANAGER (1ULL << 56) | Power manager tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_SCHEDULER (1ULL << 57) | Distributed scheduler tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_DISTRIBUTED_INPUT (1ULL << 59) | Distributed input tag.<br>**起始版本：** 12 |
| HIDEBUG_TRACE_TAG_BLUETOOTH (1ULL << 60) | bluetooth tag.<br>**起始版本：** 12 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_HiDebug_RequestTraceCallback)(HiDebug_ErrorCode errorCode, const char* filePath)](#oh_hidebug_requesttracecallback) | OH_HiDebug_RequestTraceCallback | 请求trace采集的回调类型定义。 |
| [typedef void (\*OH_HiDebug_ProfilingCallback)(OH_HiDebug_ProfilingResult* result)](#oh_hidebug_profilingcallback) | OH_HiDebug_ProfilingCallback | 定义资源采集回调函数。 |

## 枚举类型说明

### OH_HiDebug_ResourceType

```c
enum OH_HiDebug_ResourceType
```

**描述**

定义资源采集类型的枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_RES_TYPE_FD |  |
| OH_RES_TYPE_THREAD |  |
| OH_RES_TYPE_NATIVE |  |
| OH_RES_TYPE_GPU |  |
| OH_RES_TYPE_GLOBAL_HANDLE |  |
| OH_RES_TYPE_DMA | DMA内存<br>**起始版本：** 26.1.0 |
| OH_RES_TYPE_ASHMEM | 匿名共享内存<br>**起始版本：** 26.1.0 |
| OH_RES_TYPE_COMPOSITE_HEAP | 组合堆<br>**起始版本：** 26.1.0 |

### OH_HiDebug_MemListenerType

```c
enum OH_HiDebug_MemListenerType
```

**描述**

内存监听回调的类型枚举。开发者根据回调类型处理相关逻辑。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_HIDEBUG_DO_NOTHING = 0 |  |
| OH_HIDEBUG_RUNNING_GC = 1 |  |
| OH_HIDEBUG_DUMP_SNAPSHOT = 2 |  |


## 函数说明

### OH_HiDebug_RequestTraceCallback()

```c
typedef void (*OH_HiDebug_RequestTraceCallback)(HiDebug_ErrorCode errorCode, const char* filePath)
```

**描述**

请求trace采集的回调类型定义。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| HiDebug_ErrorCode errorCode | 返回结果码，参考{@link HiDebug_ErrorCode}。 |
| const char\* filePath | 返回采集的trace文件，失败时可能是空指针。 |

### OH_HiDebug_ProfilingCallback()

```c
typedef void (*OH_HiDebug_ProfilingCallback)(OH_HiDebug_ProfilingResult* result)
```

**描述**

定义资源采集回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_HiDebug_ProfilingResult](capi-hidebug-oh-hidebug-profilingresult.md)\* result | 资源采集回调函数的参数。 |


