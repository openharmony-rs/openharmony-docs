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
| [HiDebug_ThreadCpuUsage](capi-hidebug-hidebug-threadcpuusage.md) | HiDebug_ThreadCpuUsage | Defines the struct for the CPU usage of all threads of an application. |
| [HiDebug_SystemMemInfo](capi-hidebug-hidebug-systemmeminfo.md) | HiDebug_SystemMemInfo | Defines a struct for the system memory information. |
| [HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md) | HiDebug_NativeMemInfo | Defines the struct for the local memory information of the application process. |
| [HiDebug_MemoryLimit](capi-hidebug-hidebug-memorylimit.md) | HiDebug_MemoryLimit | Defines the struct for the memory limit of the application process. |
| [OH_HiDebug_RequestTraceConfig](capi-hidebug-oh-hidebug-requesttraceconfig.md) | OH_HiDebug_RequestTraceConfig | 定义trace请求配置。 |
| [HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md) | HiDebug_MallocDispatch | 应用程序进程可替换/恢复的HiDebug_MallocDispatch表结构类型定义。 |
| [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) | HiDebug_JsStackFrame | Defines a struct for the JS stack frame content. |
| [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) | HiDebug_NativeStackFrame | Defines the native stack frame content. |
| [HiDebug_StackFrame](capi-hidebug-hidebug-stackframe.md) | HiDebug_StackFrame | Defines the stack frame content. |
| [HiDebug_GraphicsMemorySummary](capi-hidebug-hidebug-graphicsmemorysummary.md) | HiDebug_GraphicsMemorySummary | Defines a struct for the application graphics memory usage details. |
| [HiDebug_ProcessSamplerConfig](capi-hidebug-hidebug-processsamplerconfig.md) | HiDebug_ProcessSamplerConfig | Defines a struct for sampling configuration. |
| [OH_HiDebug_ResProfilerConfig](capi-hidebug-oh-hidebug-resprofilerconfig.md) | OH_HiDebug_ResProfilerConfig | 定义资源采集配置结构体类型。 |
| [OH_HiDebug_ProfilingResult](capi-hidebug-oh-hidebug-profilingresult.md) | OH_HiDebug_ProfilingResult | 封装单次资源采集的结果。 |
| [HiDebug_Backtrace_Object__*](capi-hidebug-hidebug-backtrace-object--8h.md) | HiDebug_Backtrace_Object | 用于栈回溯及栈解析的对象。 |
| [HiDebug_ThreadCpuUsage*](capi-hidebug-hidebug-threadcpuusage8h.md) | HiDebug_ThreadCpuUsagePtr | Defines pointer of HiDebug_ThreadCpuUsage. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [HiDebug_TraceFlag](#hidebug_traceflag) | HiDebug_TraceFlag | 采集trace线程的类型。 |
| [HiDebug_StackFrameType](#hidebug_stackframetype) | HiDebug_StackFrameType | 栈帧类型的枚举值定义。 |
| [HiDebug_CrashObjType](#hidebug_crashobjtype) | HiDebug_CrashObjType | 维测信息数据类型的枚举。 |
| [OH_HiDebug_ResourceType](#oh_hidebug_resourcetype) | OH_HiDebug_ResourceType | 定义资源采集类型的枚举。 |
| [OH_HiDebug_MemListenerType](#oh_hidebug_memlistenertype) | OH_HiDebug_MemListenerType | 内存监听回调的类型。开发者根据回调类型处理相关逻辑。 |

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

### HiDebug_TraceFlag

```c
enum HiDebug_TraceFlag
```

**描述**

采集trace线程的类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| HIDEBUG_TRACE_FLAG_MAIN_THREAD = 1 | 只采集当前应用主线程。 |
| HIDEBUG_TRACE_FLAG_ALL_THREADS = 2 | 采集当前应用下所有线程。 |

### HiDebug_StackFrameType

```c
enum HiDebug_StackFrameType
```

**描述**

栈帧类型的枚举值定义。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| HIDEBUG_STACK_FRAME_TYPE_JS = 1 | js类型栈帧。 |
| HIDEBUG_STACK_FRAME_TYPE_NATIVE = 2 | native类型栈帧。 |

### HiDebug_CrashObjType

```c
enum HiDebug_CrashObjType
```

**描述**

维测信息数据类型的枚举。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| HIDEBUG_CRASHOBJ_STRING = 0 | 字符串 |
| HIDEBUG_CRASHOBJ_MEMORY_64B = 1 | 64字节内存块 |
| HIDEBUG_CRASHOBJ_MEMORY_256B = 2 | 256字节内存块 |
| HIDEBUG_CRASHOBJ_MEMORY_1024B = 3 | 1024字节内存块 |
| HIDEBUG_CRASHOBJ_MEMORY_2048B = 4 | 2048字节内存块 |
| HIDEBUG_CRASHOBJ_MEMORY_4096B = 5 | 4096字节内存块 |

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

### OH_HiDebug_MemListenerType

```c
enum OH_HiDebug_MemListenerType
```

**描述**

内存监听回调的类型。开发者根据回调类型处理相关逻辑。

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
| (HiDebug_ErrorCode errorCode | 返回结果码，参考{@link HiDebug_ErrorCode}。 |
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
| (OH_HiDebug_ProfilingResult\* result | 资源采集回调函数的参数。 |


