# jsvm_types.h
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## 概述

提供JSVM-API类型定义。通过API接口为开发者提供独立、标准、完整的JavaScript引擎能力，包括管理引擎生命周期、编译运行JS代码、实现JS/C++跨语言调用、拍摄快照等。

**引用文件：** <ark_runtime/jsvm_types.h>

**库：** libjsvm.so

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**相关模块：** [JSVM](capi-jsvm.md)

## 汇总

### 结构体

| 名称                                                                                                | typedef关键字                              | 描述                                                                                                                                                                                                                                                                                                                                                                                                                          |
|---------------------------------------------------------------------------------------------------|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [JSVM_CallbackStruct](capi-jsvm-jsvm-callbackstruct.md)                                           | JSVM_CallbackStruct                     | 用户提供的native回调函数的指针和数据，这些函数通过JSVM-API接口暴露给JavaScript。                                                                                                                                                                                                                                                                                                                                                                        |
| [JSVM_HeapStatistics](capi-jsvm-jsvm-heapstatistics.md)                                           | JSVM_HeapStatistics                     | 用于保存有关JavaScript堆内存使用情况的统计信息。                                                                                                                                                                                                                                                                                                                                                                              |
| [JSVM_InitOptions](capi-jsvm-jsvm-initoptions.md)                                                 | JSVM_InitOptions                        | 初始化选项，用于初始化JavaScript虚拟机。                                                                                                                                                                                                                                                                                                                                                                                                   |
| [JSVM_CreateVMOptions](capi-jsvm-jsvm-createvmoptions.md)                                         | JSVM_CreateVMOptions                    | 创建JavaScript虚拟机的选项。                                                                                                                                                                                                                                                                                                                                                                                                         |
| [JSVM_VMInfo](capi-jsvm-jsvm-vminfo.md)                                                           | JSVM_VMInfo                             | JavaScript虚拟机信息。                                                                                                                                                                                                                                                                                                                                                                                                            |
| [JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)                                   | JSVM_PropertyDescriptor                 | 属性描述符。                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [JSVM_ExtendedErrorInfo](capi-jsvm-jsvm-extendederrorinfo.md)                                     | JSVM_ExtendedErrorInfo                  | 扩展的异常信息。                                                                                                                                                                                                                                                                                                                                                                                                                    |
| [JSVM_TypeTag](capi-jsvm-jsvm-typetag.md)                                                         | JSVM_TypeTag                            | 类型标记，存储为两个无符号64位整数的128位值。作为一个UUID，通过它，JavaScript对象可以是"tagged"，以确保它们的类型保持不变。                                                                                                                                                                                                                                                                                                                                                 |
| [JSVM_PropertyHandlerConfigurationStruct](capi-jsvm-jsvm-propertyhandlerconfigurationstruct.md)   | JSVM_PropertyHandlerConfigurationStruct | 当执行对象的getter、setter、deleter和enumerator操作时，该结构体中对应的函数回调将会触发。                                                                                                                                                                                                                                                                                                                                                                 |
| [JSVM_ScriptOrigin](capi-jsvm-jsvm-scriptorigin.md)                                               | JSVM_ScriptOrigin                       | 某段JavaScript代码的原始信息，如sourceMap路径、源文件名、源文件中的起始行/列号等。                                                                                                                                                                                                                                                                                                                                                                         |
| [JSVM_PropertyHandler](capi-jsvm-jsvm-propertyhandler.md)                                         | JSVM_PropertyHandler                    | 包含将class作为函数进行调用时所触发的回调函数的函数指针和访问实例对象属性时触发的回调函数的函数指针集。                                                                                                                                                                                                                                                                                                                                                                      |
| [JSVM_DefineClassOptions](capi-jsvm-jsvm-defineclassoptions.md)                                   | JSVM_DefineClassOptions                 | 定义Class的选项。                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [JSVM_VM__*](capi-jsvm-jsvm-vm--8h.md)                                                            | JSVM_VM                                 | 表示JavaScript虚拟机实例。                                                                                                                                                                                                                                                                                                                                                                                                          |
| [JSVM_VMScope__*](capi-jsvm-jsvm-vmscope--8h.md)                                                  | JSVM_VMScope                            | 表示JavaScript虚拟机作用域。                                                                                                                                                                                                                                                                                                                                                                                                         |
| [JSVM_EnvScope__*](capi-jsvm-jsvm-envscope--8h.md)                                                | JSVM_EnvScope                           | 表示用于控制附加到当前虚拟机实例的环境。只有当线程通过OH_JSVM_OpenEnvScope进入该环境的JSVM_EnvScope后，该环境才对线程的虚拟机实例可用。                                                                                                                                                                                                                                                                                                                                        |
| [JSVM_Script__*](capi-jsvm-jsvm-script--8h.md)                                                    | JSVM_Script                             | 表示一段JavaScript代码。                                                                                                                                                                                                                                                                                                                                                                                                           |
| [JSVM_Env__*](capi-jsvm-jsvm-env--8h.md)                                                          | JSVM_Env                                | 表示虚拟机特定状态的上下文环境，需要在调用native函数时作为参数传递，并且传递给后续任何的JSVM-API嵌套调用。                                                                                                                                                                                                                                                                                                                                                                |
| [JSVM_CpuProfiler__*](capi-jsvm-jsvm-cpuprofiler--8h.md)                                          | JSVM_CpuProfiler                        | 表示一个JavaScript CPU时间性能分析器。                                                                                                                                                                                                                                                                                                                                                                                                  |
| [JSVM_Value__*](capi-jsvm-jsvm-value--8h.md)                                                      | JSVM_Value                              | 表示JavaScript值。                                                                                                                                                                                                                                                                                                                                                                                                              |
| [JSVM_Data__*](capi-jsvm-jsvm-data--8h.md)                                                        | JSVM_Data                               | 表示一个 JavaScript Data。                                                                                                                                                                                                                                                                                                                                                                                                       |
| [JSVM_Ref__*](capi-jsvm-jsvm-ref--8h.md)                                                          | JSVM_Ref                                | 表示JavaScript值的引用。                                                                                                                                                                                                                                                                                                                                                                                                           |
| [JSVM_HandleScope__*](capi-jsvm-jsvm-handlescope--8h.md)                                          | JSVM_HandleScope                        | 表示JavaScript值的作用域，用于控制和修改在特定范围内创建的对象的生命周期。通常，JSVM-API值是在JSVM_HandleScope的上下文中创建的。当从JavaScript调用native方法时，将存在默认JSVM_HandleScope。如果用户没有显式创建新的JSVM_HandleScope，将在默认JSVM_HandleScope中创建JSVM-API值。对于native方法执行之外的任何代码调用（例如，在libuv回调调用期间），模块需要在调用任何可能导致创建JavaScript值的函数之前创建一个作用域。JSVM_HandleScope是使用OH_JSVM_OpenHandleScope创建的，并使用OH_JSVM_CloseHandleScope销毁的。关闭作用域代表向GC指示在JSVM_HandleScope作用域的生命周期内创建的所有JSVM_Value将不再从当前堆的栈帧中引用。 |
| [JSVM_EscapableHandleScope__*](capi-jsvm-jsvm-escapablehandlescope--8h.md)                        | JSVM_EscapableHandleScope               | 表示一种特殊类型的handle scope，用于将在特定handle scope内创建的值返回到父作用域。                                                                                                                                                                                                                                                                                                                                                                       |
| [JSVM_CallbackInfo__*](capi-jsvm-jsvm-callbackinfo--8h.md)                                        | JSVM_CallbackInfo                       | 表示传递给回调函数的不透明数据类型。可用于获取调用该函数的上下文的附加信息。                                                                                                                                                                                                                                                                                                                                                                                      |
| [JSVM_Deferred__*](capi-jsvm-jsvm-deferred--8h.md)                                                | JSVM_Deferred                           | 表示Promise延迟对象。                                                                                                                                                                                                                                                                                                                                                                                                              |
| [JSVM_PropertyHandlerConfigurationStruct*](capi-jsvm-jsvm-propertyhandlerconfigurationstruct8h.md) | JSVM_PropertyHandlerCfg                 | 包含属性监听回调的结构的指针类型。                                                                                                                                                                                                                                                                                                                                                                                                           |
| [JSVM_CallbackStruct*](capi-jsvm-jsvm-callbackstruct8h.md)                                         | JSVM_Callback   | 用户提供的native函数的函数指针类型，这些函数通过JSVM-API接口暴露给JavaScript。                                 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [JSVM_PropertyAttributes](#jsvm_propertyattributes) | JSVM_PropertyAttributes | 用于控制JavaScript对象属性的行为。 |
| [JSVM_ValueType](#jsvm_valuetype) | JSVM_ValueType | 描述JSVM_Value的类型。 |
| [JSVM_TypedarrayType](#jsvm_typedarraytype) | JSVM_TypedarrayType | 描述TypedArray的类型。 |
| [JSVM_Status](#jsvm_status) | JSVM_Status | 表示JSVM-API调用成功或失败的完整状态码。 |
| [JSVM_KeyCollectionMode](#jsvm_keycollectionmode) | JSVM_KeyCollectionMode | 限制查找属性的范围。 |
| [JSVM_KeyFilter](#jsvm_keyfilter) | JSVM_KeyFilter | 属性过滤器，可以通过使用or来构造一个复合过滤器。 |
| [JSVM_KeyConversion](#jsvm_keyconversion) | JSVM_KeyConversion | 键转换选项。 |
| [JSVM_MemoryPressureLevel](#jsvm_memorypressurelevel) | JSVM_MemoryPressureLevel | 内存压力水平。 |
| [JSVM_RegExpFlags](#jsvm_regexpflags) | JSVM_RegExpFlags | 正则表达式标志位。它们可以用来启用一组标志。 |
| [JSVM_InitializedFlag](#jsvm_initializedflag) | JSVM_InitializedFlag | 初始化方式的标志位。 |
| [JSVM_WasmOptLevel](#jsvm_wasmoptlevel) | JSVM_WasmOptLevel | WebAssembly 函数优化等级。 |
| [JSVM_CacheType](#jsvm_cachetype) | JSVM_CacheType | 缓存类型。 |
| [JSVM_MicrotaskPolicy](#jsvm_microtaskpolicy) | JSVM_MicrotaskPolicy | JSVM 微任务执行策略。 |
| [JSVM_TraceCategory](#jsvm_tracecategory) | JSVM_TraceCategory | JSVM 内部 Trace 事件的类别。 |
| [JSVM_CBTriggerTimeForGC](#jsvm_cbtriggertimeforgc) | JSVM_CBTriggerTimeForGC | 触发回调函数的时机。 |
| [JSVM_GCType](#jsvm_gctype) | JSVM_GCType | GC类型。 |
| [JSVM_GCCallbackFlags](#jsvm_gccallbackflags) | JSVM_GCCallbackFlags | GC回调函数标记。 |
| [JSVM_PromiseRejectEvent](#jsvm_promiserejectevent) | JSVM_PromiseRejectEvent | promise-reject事件。 |
| [JSVM_MessageErrorLevel](#jsvm_messageerrorlevel) | JSVM_MessageErrorLevel | message的报错级别。 |
| [JSVM_DefineClassOptionsId](#jsvm_defineclassoptionsid) | JSVM_DefineClassOptionsId | 定义Class的选项ID。 |
| [JSVM_DebugOption](#jsvm_debugoption) | JSVM_DebugOption | 调试选项。 |

### 函数

| 名称                                                                                                                                                                 | typedef关键字 | 描述 |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------| -- | -- |
| [typedef void (JSVM_CDECL* JSVM_Finalize)(JSVM_Env env,void* finalizeData,void* finalizeHint)](#jsvm_finalize)                                                     | JSVM_CDECL* JSVM_Finalize | 函数指针类型，当native类型对象或数据与JS对象被关联时，传入该指针。该函数将会在关联的JS对象被GC回收时被调用，用以执行native的清理动作。 |
| [typedef bool (JSVM_CDECL* JSVM_OutputStream)(const char* data,int size,void* streamData)](#jsvm_outputstream)                                                     | JSVM_CDECL* JSVM_OutputStream | ASCII输出流回调的函数指针类型。参数data是指输出的数据指针。参数size是指输出的数据大小。空数据指针指示流的结尾。参数streamData是指与回调一起传递给API函数的指针，该API函数向输出流生成数据。 |
| [typedef void (JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)](#jsvm_handlerforgc)                         | JSVM_CDECL* JSVM_HandlerForGC | GC回调的函数指针类型。 |
| [typedef void (JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location,const char* detail,bool isHeapOOM)](#jsvm_handlerforoomerror)                             | JSVM_CDECL* JSVM_HandlerForOOMError | OOM-Error回调的函数指针类型。 |
| [typedef void (JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location,const char* message)](#jsvm_handlerforfatalerror)                                       | JSVM_CDECL* JSVM_HandlerForFatalError | Fatal-Error回调的函数指针类型。 |
| [typedef void (JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)](#jsvm_handlerforpromisereject) | JSVM_CDECL* JSVM_HandlerForPromiseReject | Promise-Reject回调的函数指针类型。 |

## 枚举类型说明

### JSVM_PropertyAttributes

```
enum JSVM_PropertyAttributes
```

**描述**

用于控制JavaScript对象属性的行为。

**起始版本：** 11

| 枚举项                                                                             | 描述                                                  |
|---------------------------------------------------------------------------------|-----------------------------------------------------|
| JSVM_DEFAULT = 0                                                                | 没有在属性上设置显式属性。                                       |
| JSVM_WRITABLE = 1 << 0                                                          | 该属性是可写的。                                            |
| JSVM_ENUMERABLE = 1 << 1                                                        | 该属性是可枚举的。                                           |
| JSVM_CONFIGURABLE = 1 << 2                                                      | 该属性是可配置的。                                           |
| JSVM_STATIC = 1 << 10                                                           | 该属性将被定义为类的静态属性，而不是默认的实例属性。这仅由OH_JSVM_DefineClass使用。 |
| JSVM_DEFAULT_METHOD = JSVM_WRITABLE \| JSVM_CONFIGURABLE                        |就像JS类中的方法一样，该属性是可配置和可写的，但不可枚举。                      |
| JSVM_DEFAULT_JSPROPERTY = JSVM_WRITABLE \| JSVM_ENUMERABLE \| JSVM_CONFIGURABLE | 就像JavaScript中通过赋值设置的属性一样，属性是可写、可枚举和可配置的。 |

### JSVM_ValueType

```
enum JSVM_ValueType
```

**描述**

描述JSVM_Value的类型。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| JSVM_UNDEFINED | 未定义类型。 |
| JSVM_NULL | Null类型。 |
| JSVM_BOOLEAN | 布尔类型。 |
| JSVM_NUMBER | 数字类型。 |
| JSVM_STRING | 字符串类型。 |
| JSVM_SYMBOL | 符号类型。 |
| JSVM_OBJECT | 对象类型。 |
| JSVM_FUNCTION | 函数类型。 |
| JSVM_EXTERNAL | 外部类型。 |
| JSVM_BIGINT | bigint类型。 |

### JSVM_TypedarrayType

```
enum JSVM_TypedarrayType
```

**描述**

描述TypedArray的类型。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| JSVM_INT8_ARRAY | int8类型。 |
| JSVM_UINT8_ARRAY | uint8类型。 |
| JSVM_UINT8_CLAMPED_ARRAY | uint8固定类型。 |
| JSVM_INT16_ARRAY | int16类型。 |
| JSVM_UINT16_ARRAY | uint16类型。 |
| JSVM_INT32_ARRAY | int32类型。 |
| JSVM_UINT32_ARRAY | uint32类型。 |
| JSVM_FLOAT32_ARRAY | float32类型。 |
| JSVM_FLOAT64_ARRAY | float64类型。 |
| JSVM_BIGINT64_ARRAY | bigint64类型。 |
| JSVM_BIGUINT64_ARRAY | biguint64类型。 |

### JSVM_Status

```
enum JSVM_Status
```

**描述**

表示JSVM-API调用成功或失败的完整状态码。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| JSVM_OK | 成功状态。 |
| JSVM_INVALID_ARG | 无效的状态。 |
| JSVM_OBJECT_EXPECTED | 期待传入对象类型。 |
| JSVM_STRING_EXPECTED | 期望传入字符串类型。 |
| JSVM_NAME_EXPECTED | 期望传入名字类型。 |
| JSVM_FUNCTION_EXPECTED | 期待传入函数类型。 |
| JSVM_NUMBER_EXPECTED | 期待传入数字类型。 |
| JSVM_BOOLEAN_EXPECTED | 期待传入布尔类型。 |
| JSVM_ARRAY_EXPECTED | 期待传入数组类型。 |
| JSVM_GENERIC_FAILURE | 泛型失败状态。 |
| JSVM_PENDING_EXCEPTION | 挂起异常状态。 |
| JSVM_CANCELLED | 取消状态。 |
| JSVM_ESCAPE_CALLED_TWICE | 转义调用了两次。 |
| JSVM_HANDLE_SCOPE_MISMATCH | 句柄作用域不匹配。 |
| JSVM_CALLBACK_SCOPE_MISMATCH | 回调作用域不匹配。 |
| JSVM_QUEUE_FULL | 队列满。 |
| JSVM_CLOSING | 关闭中。 |
| JSVM_BIGINT_EXPECTED | 期望传入Bigint类型。 |
| JSVM_DATE_EXPECTED | 期望传入日期类型。 |
| JSVM_ARRAYBUFFER_EXPECTED | 期望传入ArrayBuffer类型。 |
| JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED | 可分离的数组缓冲区预期状态。 |
| JSVM_WOULD_DEADLOCK | 将死锁状态。 |
| JSVM_NO_EXTERNAL_BUFFERS_ALLOWED | 不允许外部缓冲区。 |
| JSVM_CANNOT_RUN_JS | 不能执行JS。 |
| JSVM_INVALID_TYPE | 传入的参数为非法类型。<br>**起始版本：** 18 |
| JSVM_JIT_MODE_EXPECTED | 无 JIT 权限。<br>**起始版本：** 18 |

### JSVM_KeyCollectionMode

```
enum JSVM_KeyCollectionMode
```

**描述**

限制查找属性的范围。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| JSVM_KEY_INCLUDE_PROTOTYPES | 也包含对象原型链上的属性。 |
| JSVM_KEY_OWN_ONLY | 仅包含对象自身属性。 |

### JSVM_KeyFilter

```
enum JSVM_KeyFilter
```

**描述**

属性过滤器，可以通过使用or来构造一个复合过滤器。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| JSVM_KEY_ALL_PROPERTIES = 0 | 所有属性的键。 |
| JSVM_KEY_WRITABLE = 1 | 可写的键。 |
| JSVM_KEY_ENUMERABLE = 1 << 1 | 可枚举的键。 |
| JSVM_KEY_CONFIGURABLE = 1 << 2 | 可配置的键。 |
| JSVM_KEY_SKIP_STRINGS = 1 << 3 | 排除字符串类型的键。 |
| JSVM_KEY_SKIP_SYMBOLS = 1 << 4 | 排除符号类型的键。 |

### JSVM_KeyConversion

```
enum JSVM_KeyConversion
```

**描述**

键转换选项。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| JSVM_KEY_KEEP_NUMBERS | 将返回整数索引的数字。 |
| JSVM_KEY_NUMBERS_TO_STRINGS | 将整数索引转换为字符串。 |

### JSVM_MemoryPressureLevel

```
enum JSVM_MemoryPressureLevel
```

**描述**

内存压力水平。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| JSVM_MEMORY_PRESSURE_LEVEL_NONE | 无压力。 |
| JSVM_MEMORY_PRESSURE_LEVEL_MODERATE | 中等压力。 |
| JSVM_MEMORY_PRESSURE_LEVEL_CRITICAL | 临界压力。 |

### JSVM_RegExpFlags

```
enum JSVM_RegExpFlags
```

**描述**

正则表达式标志位。它们可以用来启用一组标志。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| JSVM_REGEXP_NONE = 0 | None模式。 |
| JSVM_REGEXP_GLOBAL = 1 << 0 | Global模式。 |
| JSVM_REGEXP_IGNORE_CASE = 1 << 1 | Ignore Case模式。 |
| JSVM_REGEXP_MULTILINE = 1 << 2 | Multiline模式。 |
| JSVM_REGEXP_STICKY = 1 << 3 | Sticky模式。 |
| JSVM_REGEXP_UNICODE = 1 << 4 | Unicode模式。 |
| JSVM_REGEXP_DOT_ALL = 1 << 5 | dotAll模式。 |
| JSVM_REGEXP_LINEAR = 1 << 6 | Linear模式。 |
| JSVM_REGEXP_HAS_INDICES = 1 << 7 | Has Indices模式。 |
| JSVM_REGEXP_UNICODE_SETS = 1 << 8 | Unicode Sets模式。 |

### JSVM_InitializedFlag

```
enum JSVM_InitializedFlag
```

**描述**

初始化方式的标志位。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| JSVM_ZERO_INITIALIZED | 初始化为0。 |
| JSVM_UNINITIALIZED | 不做初始化。 |

### JSVM_WasmOptLevel

```
enum JSVM_WasmOptLevel
```

**描述**

WebAssembly 函数优化等级。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| JSVM_WASM_OPT_BASELINE = 10 | baseline 优化等级。 |
| JSVM_WASM_OPT_HIGH = 20 | 高优化等级。 |

### JSVM_CacheType

```
enum JSVM_CacheType
```

**描述**

缓存类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| JSVM_CACHE_TYPE_JS | JS 缓存, 由接口 OH_JSVM_CreateCodeCache 生成。 |
| JSVM_CACHE_TYPE_WASM | WebAssembly 缓存, 由接口 OH_JSVM_CreateWasmCache 生成。 |

### JSVM_MicrotaskPolicy

```
enum JSVM_MicrotaskPolicy
```

**描述**

JSVM 微任务执行策略。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| JSVM_MICROTASK_EXPLICIT = 0 | 调用 OH_JSVM_PerformMicrotaskCheckpoint 方法后微任务执行。 |
| JSVM_MICROTASK_AUTO | JS 调用栈为 0 时自动执行微任务。默认模式。 |

### JSVM_TraceCategory

```
enum JSVM_TraceCategory
```

**描述**

JSVM 内部 Trace 事件的类别。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| JSVM_TRACE_VM | 采集 JSVM 主要接口调用, 例如执行 js 脚本。 |
| JSVM_TRACE_COMPILE | 采集编译相关的接口调用, 例如后台编译。 |
| JSVM_TRACE_EXECUTE | 采集与运行状态相关的接口调用, 例如中断与微任务。 |
| JSVM_TRACE_RUNTIME | 采集外部函数调用相关信息。 |
| JSVM_TRACE_STACK_TRACE | 采集 JSVM 中回栈相关信息。 |
| JSVM_TRACE_WASM | 采集主要的 WASM 相关接口调用, 例如编译与实例化 WASM 模块。 |
| JSVM_TRACE_WASM_DETAILED | 采集更多更细节的 WASM 相关接口调用，例如后台编译、跳板编译。 |

### JSVM_CBTriggerTimeForGC

```
enum JSVM_CBTriggerTimeForGC
```

**描述**

触发回调函数的时机。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| JSVM_CB_TRIGGER_BEFORE_GC | 在GC之前触发回调函数。 |
| JSVM_CB_TRIGGER_AFTER_GC | 在GC之后触发回调函数。 |

### JSVM_GCType

```
enum JSVM_GCType
```

**描述**

GC类型。

**起始版本：** 18

| 枚举项                                                                                                                                                    | 描述                               |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| JSVM_GC_TYPE_SCAVENGE = 1 << 0                                                                                                                         | GC算法为Scavenge。                   |
| JSVM_GC_TYPE_MINOR_MARK_COMPACT = 1 << 1                                                                                                               | GC算法为Minor-Mark-Compact。         |
| JSVM_GC_TYPE_MARK_SWEEP_COMPACT = 1 << 2                                                                                                               | GC算法为Mark-Sweep-Compact。         |
| JSVM_GC_TYPE_INCREMENTAL_MARKING = 1 << 3                                                                                                              | GC算法为Incremental-Marking。        |
| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS = 1 << 4                                                                                                           | GC算法为Weak-Callbacks。             |
| JSVM_GC_TYPE_ALL = JSVM_GC_TYPE_SCAVENGE \| JSVM_GC_TYPE_MINOR_MARK_COMPACT \| JSVM_GC_TYPE_MARK_SWEEP_COMPACT \| JSVM_GC_TYPE_INCREMENTAL_MARKING \| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS | 包含所有类型的GC算法。 |

### JSVM_GCCallbackFlags

```
enum JSVM_GCCallbackFlags
```

**描述**

GC回调函数标记。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| JSVM_NO_GC_CALLBACK_FLAGS | 无回调函数标记。 |
| JSVM_GC_CALLBACK_CONSTRUCT_RETAINED_OBJECT_INFOS | 垃圾回收回调中将构建保留对象信息。 |
| JSVM_GC_CALLBACK_FORCED | 强制执行垃圾回收回调。 |
| JSVM_GC_CALLBACK_SYNCHRONOUS_PHANTOM_CALLBACK_PROCESSING | 同步处理幽灵对象回调。 |
| JSVM_GC_CALLBACK_COLLECT_ALL_AVAILABLE_GARBAGE | 垃圾回收过程中会收集所有可用的垃圾对象。 |
| JSVM_GC_CALLBACK_COLLECT_ALL_EXTERNAL_MEMORY | 垃圾回收时会收集所有的外部内存。 |
| JSVM_GC_CALLBACK_SCHEDULE_IDLE_GARBAGE_COLLECTION | 在空闲时调度垃圾回收。 |

### JSVM_PromiseRejectEvent

```
enum JSVM_PromiseRejectEvent
```

**描述**

promise-reject事件。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| JSVM_PROMISE_REJECT_OTHER_REASONS = 0 | Promise被拒绝，但拒绝的原因未知或不明确。 |
| JSVM_PROMISE_REJECT_WITH_NO_HANDLER = 1 | Promise被拒绝但没有处理程序。 |
| JSVM_PROMISE_HANDLER_ADDED_AFTER_REJECT = 2 | Promise已被拒绝后，再添加处理程序。 |
| JSVM_PROMISE_REJECT_AFTER_RESOLVED = 3 | Promise已被解决后，再尝试拒绝该Promise。 |
| JSVM_PROMISE_RESOLVE_AFTER_RESOLVED = 4 | Promise已被解决后，再尝试解决该Promise。 |

### JSVM_MessageErrorLevel

```
enum JSVM_MessageErrorLevel
```

**描述**

message的报错级别。

**起始版本：** 18

| 枚举项                                                                                                      | 描述 |
|----------------------------------------------------------------------------------------------------------| -- |
| JSVM_MESSAGE_LOG = (1 << 0)                                                                              | Log级别的信息。 |
| JSVM_MESSAGE_DEBUG = (1 << 1)                                                                            | Debug级别的信息。 |
| JSVM_MESSAGE_INFO = (1 << 2)                                                                             | Info级别的信息。 |
| JSVM_MESSAGE_ERROR = (1 << 3)                                                                            | Error级别的信息。 |
| JSVM_MESSAGE_WARNING = (1 << 4)                                                                          | Warning级别的信息。 |
| JSVM_MESSAGE_ALL = JSVM_MESSAGE_LOG \| JSVM_MESSAGE_DEBUG \| JSVM_MESSAGE_INFO \| JSVM_MESSAGE_ERROR \| JSVM_MESSAGE_WARNING | 所有级别的信息。 |

### JSVM_DefineClassOptionsId

```
enum JSVM_DefineClassOptionsId
```

**描述**

定义Class的选项ID。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| JSVM_DEFINE_CLASS_NORMAL | 在常规模式下定义Class。 |
| JSVM_DEFINE_CLASS_WITH_COUNT | 为所创建的Class预留指定数量的interfield槽位，在这些槽位中可以存放native-data。 |
| JSVM_DEFINE_CLASS_WITH_PROPERTY_HANDLER | 为所创建的Class设置监听拦截属性以及设置作为函数调用时回调函数。 |

### JSVM_DebugOption

```
enum JSVM_DebugOption
```

**描述**

调试选项。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| JSVM_SCOPE_CHECK | scope校验功能。 |


## 函数说明

### JSVM_Finalize()

```
typedef void (JSVM_CDECL* JSVM_Finalize)(JSVM_Env env,void* finalizeData,void* finalizeHint)
```

**描述**

函数指针类型，当native类型对象或数据与JS对象被关联时，传入该指针。该函数将会在关联的JS对象被GC回收时被调用，用以执行native的清理动作。

**起始版本：** 11

### JSVM_OutputStream()

```
typedef bool (JSVM_CDECL* JSVM_OutputStream)(const char* data,int size,void* streamData)
```

**描述**

ASCII输出流回调的函数指针类型。参数data是指输出的数据指针。参数size是指输出的数据大小。空数据指针指示流的结尾。参数streamData是指与回调一起传递给API函数的指针，该API函数向输出流生成数据。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回true表示流可以继续接受数据，返回false将中止流。 |

### JSVM_HandlerForGC()

```
typedef void (JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)
```

**描述**

GC回调的函数指针类型。

**起始版本：** 18

### JSVM_HandlerForOOMError()

```
typedef void (JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location,const char* detail,bool isHeapOOM)
```

**描述**

OOM-Error回调的函数指针类型。

**起始版本：** 18

### JSVM_HandlerForFatalError()

```
typedef void (JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location,const char* message)
```

**描述**

Fatal-Error回调的函数指针类型。

**起始版本：** 18

### JSVM_HandlerForPromiseReject()

```
typedef void (JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)
```

**描述**

Promise-Reject回调的函数指针类型。

**起始版本：** 18


