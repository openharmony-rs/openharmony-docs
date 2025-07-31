# hidebug.h

## 概述

定义HiDebug模块的调试功能。

**库：** libohhidebug.so

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**起始版本：** 12

**相关模块：** [HiDebug](capi-hidebug.md)

## 汇总

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [double OH_HiDebug_GetSystemCpuUsage()](#oh_hidebug_getsystemcpuusage) | - | 获取系统的CPU资源占用情况百分比。 |
| [double OH_HiDebug_GetAppCpuUsage()](#oh_hidebug_getappcpuusage) | - | 获取进程的CPU使用率百分比。 |
| [HiDebug_ThreadCpuUsagePtr OH_HiDebug_GetAppThreadCpuUsage()](#oh_hidebug_getappthreadcpuusage) | - | 获取应用所有线程CPU使用情况。 |
| [void OH_HiDebug_FreeThreadCpuUsage(HiDebug_ThreadCpuUsagePtr *threadCpuUsage)](#oh_hidebug_freethreadcpuusage) | - | 释放线程数据结构。 |
| [void OH_HiDebug_GetSystemMemInfo(HiDebug_SystemMemInfo *systemMemInfo)](#oh_hidebug_getsystemmeminfo) | - | 获取系统内存信息。 |
| [void OH_HiDebug_GetAppNativeMemInfo(HiDebug_NativeMemInfo *nativeMemInfo)](#oh_hidebug_getappnativememinfo) | - | 获取应用程序进程的内存信息。 |
| [void OH_HiDebug_GetAppMemoryLimit(HiDebug_MemoryLimit *memoryLimit)](#oh_hidebug_getappmemorylimit) | - | 获取应用程序进程的内存限制。 |
| [HiDebug_ErrorCode OH_HiDebug_StartAppTraceCapture(HiDebug_TraceFlag flag, uint64_t tags, uint32_t limitSize,char* fileName, uint32_t length)](#oh_hidebug_startapptracecapture) | - | 启动应用trace采集。 |
| [HiDebug_ErrorCode OH_HiDebug_StopAppTraceCapture()](#oh_hidebug_stopapptracecapture) | - | 停止采集应用程序trace。 |
| [HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemory(uint32_t *value)](#oh_hidebug_getgraphicsmemory) | - | 获取应用gpu显存大小。 |
| [int OH_HiDebug_BacktraceFromFp(HiDebug_Backtrace_Object object, void* startFp, void** pcArray, int size)](#oh_hidebug_backtracefromfp) | - | 根据给定的fp地址进行栈回溯，该函数异步信号安全。 |
| [typedef void (\*OH_HiDebug_SymbolicAddressCallback)(void* pc, void* arg, const HiDebug_StackFrame* frame)](#oh_hidebug_symbolicaddresscallback) | OH_HiDebug_SymbolicAddressCallback | 若[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口调用成功，将通过该函数将解析后的栈信息返回给调用者。 |
| [HiDebug_ErrorCode OH_HiDebug_SymbolicAddress(HiDebug_Backtrace_Object object, void* pc, void* arg,OH_HiDebug_SymbolicAddressCallback callback)](#oh_hidebug_symbolicaddress) | - | 通过给定的pc地址获取详细的符号信息，该函数非异步信号安全。 |
| [HiDebug_Backtrace_Object OH_HiDebug_CreateBacktraceObject(void)](#oh_hidebug_createbacktraceobject) | - | 创建一个用于栈回溯及栈解析的对象，该函数非异步信号安全。 |
| [void OH_HiDebug_DestroyBacktraceObject(HiDebug_Backtrace_Object object)](#oh_hidebug_destroybacktraceobject) | - | 销毁由[OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject)创建的对象，以释放栈回溯及栈解析过程中申请的资源，该函数非异步信号安全。 |
| [HiDebug_ErrorCode OH_HiDebug_SetMallocDispatchTable(struct HiDebug_MallocDispatch *dispatchTable)](#oh_hidebug_setmallocdispatchtable) | - | 设置基础库C库MallocDisaptch表，用于替换开发者自定义的内存操作函数（例如：malloc/free/calloc/realloc/mmap/munmap)。MallocDisaptch表是基础库C库中封装malloc/calloc/realloc/free等内存操作函数的结构体。HiDebug_MallocDispatch只是MallocDisaptch结构体的一部分。 |
| [HiDebug_MallocDispatch* OH_HiDebug_GetDefaultMallocDispatchTable(void)](#oh_hidebug_getdefaultmallocdispatchtable) | - | 获取基础库C库当前默认MallocDispatch表，调用[OH_HiDebug_RestoreMallocDispatchTable](capi-hidebug-h.md#oh_hidebug_restoremallocdispatchtable)可恢复。 |
| [void OH_HiDebug_RestoreMallocDispatchTable(void)](#oh_hidebug_restoremallocdispatchtable) | - | 恢复基础库C库MallocDispatch表。 |

## 函数说明

### OH_HiDebug_GetSystemCpuUsage()

```
double OH_HiDebug_GetSystemCpuUsage()
```

**描述**

获取系统的CPU资源占用情况百分比。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| double | 返回系统CPU资源占用情况百分比。如果返回结果为0，可能的原因是获取失败。 |

### OH_HiDebug_GetAppCpuUsage()

```
double OH_HiDebug_GetAppCpuUsage()
```

**描述**

获取进程的CPU使用率百分比。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| double | 返回进程的CPU使用率百分比。如果返回结果为0，可能因当前应用的CPU使用率过低导致。 |

### OH_HiDebug_GetAppThreadCpuUsage()

```
HiDebug_ThreadCpuUsagePtr OH_HiDebug_GetAppThreadCpuUsage()
```

**描述**

获取应用所有线程CPU使用情况。

**起始版本：** 12

**返回：**

| 类型 | 说明                                                                                           |
| -- |----------------------------------------------------------------------------------------------|
| [HiDebug_ThreadCpuUsagePtr](capi-hidebug-hidebug-threadcpuusage.md) | 返回所有线程CPU使用情况，见[HiDebug_ThreadCpuUsagePtr](capi-hidebug-hidebug-threadcpuusage.md)。<br>         若返回结果为null，可能因未获取到线程相关数据所致。 |

### OH_HiDebug_FreeThreadCpuUsage()

```
void OH_HiDebug_FreeThreadCpuUsage(HiDebug_ThreadCpuUsagePtr *threadCpuUsage)
```

**描述**

释放线程数据结构。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_ThreadCpuUsagePtr](capi-hidebug-hidebug-threadcpuusage.md) *threadCpuUsage | 应用的所有线程可用CPU使用缓冲区指针，见[HiDebug_ThreadCpuUsagePtr](capi-hidebug-hidebug-threadcpuusage.md)。传入的参数是要由OH_HiDebug_GetAppThreadCpuUsage()得到的。 |

### OH_HiDebug_GetSystemMemInfo()

```
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

```
void OH_HiDebug_GetAppNativeMemInfo(HiDebug_NativeMemInfo *nativeMemInfo)
```

**描述**

获取应用程序进程的内存信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md) *nativeMemInfo | 表示指向[HiDebug_NativeMemInfo](capi-hidebug-hidebug-nativememinfo.md)。函数调用后，若结构体数据为空，则表明调用失败。 |

### OH_HiDebug_GetAppMemoryLimit()

```
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

```
HiDebug_ErrorCode OH_HiDebug_StartAppTraceCapture(HiDebug_TraceFlag flag, uint64_t tags, uint32_t limitSize,char* fileName, uint32_t length)
```

**描述**

启动应用trace采集。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_TraceFlag](capi-hidebug-type-h.md#hidebug_traceflag) flag | 采集线程trace方式。 |
| uint64_t tags | 采集trace场景标签。 |
| uint32_t limitSize | trace文件的最大大小（以字节为单位），最大为 500MB。 |
| char* fileName | 输出trace文件名缓冲区。 |
| uint32_t length | 输出trace文件名缓冲区长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode) | 0 - 成功。<br>         [HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode) 401 - fileName参数为空指针或者传入的length参数过小或者limitSize参数小于等于0。<br>         11400102 - 已经开启了一个trace。<br>         11400103 - 没有权限去开启trace。<br>         11400104 - 系统内部错误。 |

### OH_HiDebug_StopAppTraceCapture()

```
HiDebug_ErrorCode OH_HiDebug_StopAppTraceCapture()
```

**描述**

停止采集应用程序trace。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode) | 0 - 成功。<br>         11400104 - 系统内部错误。<br>         11400105 - 当前没有trace正在运行 |

### OH_HiDebug_GetGraphicsMemory()

```
HiDebug_ErrorCode OH_HiDebug_GetGraphicsMemory(uint32_t *value)
```

**描述**

获取应用gpu显存大小。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t *value | 指向用来保存接口获取到的应用显存大小（单位KB）的变量的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode) | 0 - 接口获取成功。<br>          401 - 无效参数，所传递参数为空指针。<br>          11400104 - 系统内部错误。 |

### OH_HiDebug_BacktraceFromFp()

```
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

```
typedef void (*OH_HiDebug_SymbolicAddressCallback)(void* pc, void* arg, const HiDebug_StackFrame* frame)
```

**描述**

若[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口调用成功，将通过该函数将解析后的栈信息返回给调用者。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| void* pc | 传入[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口的需要解析的pc地址。 |
|  void* arg | 传入[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口的arg值。 |
| [ const HiDebug_StackFrame](capi-hidebug-hidebug-stackframe.md)* frame | 由传入[OH_HiDebug_SymbolicAddress](capi-hidebug-h.md#oh_hidebug_symbolicaddress)接口的pc地址解析后的得到栈信息[HiDebug_StackFrame](capi-hidebug-hidebug-stackframe.md)指针，该指针指向内容仅在该函数作用域内有效。 |

### OH_HiDebug_SymbolicAddress()

```
HiDebug_ErrorCode OH_HiDebug_SymbolicAddress(HiDebug_Backtrace_Object object, void* pc, void* arg,OH_HiDebug_SymbolicAddressCallback callback)
```

**描述**

通过给定的pc地址获取详细的符号信息，该函数非异步信号安全。

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
| [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode) | 返回结果具体可参考[HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode)：<br>         [HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) 成功获取到详细的栈信息，且该函数传入的callback被调用。<br>         [HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode) 无效参数。<br>         [HIDEBUG_INVALID_SYMBOLIC_PC_ADDRESS](capi-hidebug-type-h.md#hidebug_errorcode) 无法根据传入的pc地址找到对应的符号。 |

### OH_HiDebug_CreateBacktraceObject()

```
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

```
void OH_HiDebug_DestroyBacktraceObject(HiDebug_Backtrace_Object object)
```

**描述**

销毁由[OH_HiDebug_CreateBacktraceObject](capi-hidebug-h.md#oh_hidebug_createbacktraceobject)创建的对象，以释放栈回溯及栈解析过程中申请的资源，该函数非异步信号安全。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiDebug_Backtrace_Object](capi-hidebug-hidebug-backtrace-object--8h.md) object | 需要被销毁的对象。 |

### OH_HiDebug_SetMallocDispatchTable()

```
HiDebug_ErrorCode OH_HiDebug_SetMallocDispatchTable(struct HiDebug_MallocDispatch *dispatchTable)
```

**描述**

设置基础库C库MallocDisaptch表，用于替换开发者自定义的内存操作函数（例如：malloc/free/calloc/realloc/mmap/munmap)。MallocDisaptch表是基础库C库中封装malloc/calloc/realloc/free等内存操作函数的结构体。HiDebug_MallocDispatch只是MallocDisaptch结构体的一部分。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md) *dispatchTable | 指向开发者自定义内存操作函数[HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md)结构体指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode) | 返回结果具体可参考[HiDebug_ErrorCode](capi-hidebug-type-h.md#hidebug_errorcode)：<br>         [HIDEBUG_SUCCESS](capi-hidebug-type-h.md#hidebug_errorcode) 成功设置自定义内存操作函数。<br>         [HIDEBUG_INVALID_ARGUMENT](capi-hidebug-type-h.md#hidebug_errorcode) 无效参数。 |

### OH_HiDebug_GetDefaultMallocDispatchTable()

```
HiDebug_MallocDispatch* OH_HiDebug_GetDefaultMallocDispatchTable(void)
```

**描述**

获取基础库C库当前默认MallocDispatch表，调用[OH_HiDebug_RestoreMallocDispatchTable](capi-hidebug-h.md#oh_hidebug_restoremallocdispatchtable)可恢复。

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md)* | 当前C库默认的[HiDebug_MallocDispatch](capi-hidebug-hidebug-mallocdispatch.md)结构体指针。 |

### OH_HiDebug_RestoreMallocDispatchTable()

```
void OH_HiDebug_RestoreMallocDispatchTable(void)
```

**描述**

恢复基础库C库MallocDispatch表。

**起始版本：** 20


