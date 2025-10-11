# jsvm_types.h
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

JSVM-API type definitions. Provides independent, standard, and complete JavaScript engine capabilities for developers through APIs, including managing the engine lifecycle, compiling and running JavaScript code, implementing cross-language calling between JavaScript and C++, and taking snapshots.

**File to import**: <ark_runtime/jsvm_types.h>

**Library**: libjsvm.so

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

## Summary

### Structs

| Name                                                                                               | typedef Keyword                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                         |
|---------------------------------------------------------------------------------------------------|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [JSVM_CallbackStruct](capi-jsvm-jsvm-callbackstruct.md)                                           | JSVM_CallbackStruct                     | Pointer to and data of the native callbacks provided by the user. These functions are exposed to JavaScript via JSVM-API.                                                                                                                                                                                                                                                                                                                                                                       |
| [JSVM_HeapStatistics](capi-jsvm-jsvm-heapstatistics.md)                                           | JSVM_HeapStatistics                     | Used to save statistics about JavaScript heap memory usage.                                                                                                                                                                                                                                                                                                                                                                             |
| [JSVM_InitOptions](capi-jsvm-jsvm-initoptions.md)                                                 | JSVM_InitOptions                        | Options for initializing a JavaScript VM.                                                                                                                                                                                                                                                                                                                                                                                                  |
| [JSVM_CreateVMOptions](capi-jsvm-jsvm-createvmoptions.md)                                         | JSVM_CreateVMOptions                    | Options for creating a JavaScript VM.                                                                                                                                                                                                                                                                                                                                                                                                        |
| [JSVM_VMInfo](capi-jsvm-jsvm-vminfo.md)                                                           | JSVM_VMInfo                             | JavaScript VM information.                                                                                                                                                                                                                                                                                                                                                                                                           |
| [JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)                                   | JSVM_PropertyDescriptor                 | Property descriptor.                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [JSVM_ExtendedErrorInfo](capi-jsvm-jsvm-extendederrorinfo.md)                                     | JSVM_ExtendedErrorInfo                  | Extended error information.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [JSVM_TypeTag](capi-jsvm-jsvm-typetag.md)                                                         | JSVM_TypeTag                            | Type tag, stored as a 128-bit value of two unsigned 64-bit integers. As a UUID, JavaScript objects can be "tagged" to ensure that their types remain unchanged.                                                                                                                                                                                                                                                                                                                                                |
| [JSVM_PropertyHandlerConfigurationStruct](capi-jsvm-jsvm-propertyhandlerconfigurationstruct.md)   | JSVM_PropertyHandlerConfigurationStruct | Struct for triggering the corresponding callback when the getter, setter, deleter, or enumerator of an object is executed.                                                                                                                                                                                                                                                                                                                                                                |
| [JSVM_ScriptOrigin](capi-jsvm-jsvm-scriptorigin.md)                                               | JSVM_ScriptOrigin                       | Original information of a segment of JavaScript code, such as the source map path, source file name, and start line/column number in the source file.                                                                                                                                                                                                                                                                                                                                                                        |
| [JSVM_PropertyHandler](capi-jsvm-jsvm-propertyhandler.md)                                         | JSVM_PropertyHandler                    | Function pointer set of the callback function triggered when the class is called as a function and the callback function triggered when the instance object attribute is accessed.                                                                                                                                                                                                                                                                                                                                                                     |
| [JSVM_DefineClassOptions](capi-jsvm-jsvm-defineclassoptions.md)                                   | JSVM_DefineClassOptions                 | Defines class options.                                                                                                                                                                                                                                                                                                                                                                                                                |
| [JSVM_VM__*](capi-jsvm-jsvm-vm--8h.md)                                                            | JSVM_VM                                 | JavaScript VM instance.                                                                                                                                                                                                                                                                                                                                                                                                         |
| [JSVM_VMScope__*](capi-jsvm-jsvm-vmscope--8h.md)                                                  | JSVM_VMScope                            | JavaScript VM scope.                                                                                                                                                                                                                                                                                                                                                                                                        |
| [JSVM_EnvScope__*](capi-jsvm-jsvm-envscope--8h.md)                                                | JSVM_EnvScope                           | Environment scope of the current VM instance. The environment is available to the virtual machine instance of the thread only after the thread enters the JSVM_EnvScope through OH_JSVM_OpenEnvScope.                                                                                                                                                                                                                                                                                                                                       |
| [JSVM_Script__*](capi-jsvm-jsvm-script--8h.md)                                                    | JSVM_Script                             | JavaScript code.                                                                                                                                                                                                                                                                                                                                                                                                          |
| [JSVM_Env__*](capi-jsvm-jsvm-env--8h.md)                                                          | JSVM_Env                                | Indicates the context of the virtual machine specific status. It needs to be transferred as a parameter when the native function is called and transferred to any subsequent JSVM-API nested call.                                                                                                                                                                                                                                                                                                                                                               |
| [JSVM_CpuProfiler__*](capi-jsvm-jsvm-cpuprofiler--8h.md)                                          | JSVM_CpuProfiler                        | JavaScript CPU profiler.                                                                                                                                                                                                                                                                                                                                                                                                 |
| [JSVM_Value__*](capi-jsvm-jsvm-value--8h.md)                                                      | JSVM_Value                              | JavaScript value.                                                                                                                                                                                                                                                                                                                                                                                                             |
| [JSVM_Data__*](capi-jsvm-jsvm-data--8h.md)                                                        | JSVM_Data                               | Indicates a JavaScript data.                                                                                                                                                                                                                                                                                                                                                                                                      |
| [JSVM_Ref__*](capi-jsvm-jsvm-ref--8h.md)                                                          | JSVM_Ref                                | Reference to the JavaScript value.                                                                                                                                                                                                                                                                                                                                                                                                          |
| [JSVM_HandleScope__*](capi-jsvm-jsvm-handlescope--8h.md)                                          | JSVM_HandleScope                        | Scope of the JavaScript value. It is used to control and modify the lifecycle of an object created in a specific scope. Typically, the JSVM-API value is created in the context of JSVM_HandleScope. When a native method is called from JavaScript, the default JSVM_HandleScope exists. If the user does not explicitly create a new JSVM_HandleScope, the JSVM-API value is created in the default JSVM_HandleScope. For any code call (for example, during libuv callback call) other than the execution of the native method, the module needs to create a scope before calling any function that may create JavaScript values. JSVM_HandleScope is created using OH_JSVM_OpenHandleScope and destroyed using OH_JSVM_CloseHandleScope. Closing the scope represents indicating to the GC that all JSVM_Values created during the lifecycle of JSVM_HandleScope will no longer be referenced from the stack frame of the current heap.|
| [JSVM_EscapableHandleScope__*](capi-jsvm-jsvm-escapablehandlescope--8h.md)                        | JSVM_EscapableHandleScope               | A special type of handle scope, which is used to return the value created in a specific handle scope to the parent scope.                                                                                                                                                                                                                                                                                                                                                                      |
| [JSVM_CallbackInfo__*](capi-jsvm-jsvm-callbackinfo--8h.md)                                        | JSVM_CallbackInfo                       | An opaque data type passed to the callback. It can be used to obtain additional information about the context in which the function is called.                                                                                                                                                                                                                                                                                                                                                                                     |
| [JSVM_Deferred__*](capi-jsvm-jsvm-deferred--8h.md)                                                | JSVM_Deferred                           | Promise deferred object.                                                                                                                                                                                                                                                                                                                                                                                                             |
| [JSVM_PropertyHandlerConfigurationStruct*](capi-jsvm-jsvm-propertyhandlerconfigurationstruct8h.md) | JSVM_PropertyHandlerCfg                 | Pointer type of the struct that contains the property listening callback.                                                                                                                                                                                                                                                                                                                                                                                                          |
| [JSVM_CallbackStruct*](capi-jsvm-jsvm-callbackstruct8h.md)                                         | JSVM_Callback   | Pointer types of the native functions provided by user. These functions are exposed to JavaScript via JSVM-API.                                |

### Enumerated value

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [JSVM_PropertyAttributes](#jsvm_propertyattributes) | JSVM_PropertyAttributes | Control over the behavior of JavaScript object properties.|
| [JSVM_ValueType](#jsvm_valuetype) | JSVM_ValueType | JSVM_Value type.|
| [JSVM_TypedarrayType](#jsvm_typedarraytype) | JSVM_TypedarrayType | TypedArray type.|
| [JSVM_Status](#jsvm_status) | JSVM_Status | Complete status code indicating whether the JSVM-API call is successful or fails.|
| [JSVM_KeyCollectionMode](#jsvm_keycollectionmode) | JSVM_KeyCollectionMode | Limited range of properties to be searched for.|
| [JSVM_KeyFilter](#jsvm_keyfilter) | JSVM_KeyFilter | Property filter. You can use OR to construct a composite filter.|
| [JSVM_KeyConversion](#jsvm_keyconversion) | JSVM_KeyConversion | Key conversion options.|
| [JSVM_MemoryPressureLevel](#jsvm_memorypressurelevel) | JSVM_MemoryPressureLevel | Memory pressure level.|
| [JSVM_RegExpFlags](#jsvm_regexpflags) | JSVM_RegExpFlags | Regular expression flags. They can be used to enable a set of flags.|
| [JSVM_InitializedFlag](#jsvm_initializedflag) | JSVM_InitializedFlag | Flag of the initialization mode.|
| [JSVM_WasmOptLevel](#jsvm_wasmoptlevel) | JSVM_WasmOptLevel | WebAssembly function optimization level.|
| [JSVM_CacheType](#jsvm_cachetype) | JSVM_CacheType | Cache type.|
| [JSVM_MicrotaskPolicy](#jsvm_microtaskpolicy) | JSVM_MicrotaskPolicy | JSVM microtask execution policy.|
| [JSVM_TraceCategory](#jsvm_tracecategory) | JSVM_TraceCategory | Category of JSVM internal trace events.|
| [JSVM_CBTriggerTimeForGC](#jsvm_cbtriggertimeforgc) | JSVM_CBTriggerTimeForGC | Time when the callback function is triggered.|
| [JSVM_GCType](#jsvm_gctype) | JSVM_GCType | GC type.|
| [JSVM_GCCallbackFlags](#jsvm_gccallbackflags) | JSVM_GCCallbackFlags | GC callback function flag.|
| [JSVM_PromiseRejectEvent](#jsvm_promiserejectevent) | JSVM_PromiseRejectEvent | Promise-reject event.|
| [JSVM_MessageErrorLevel](#jsvm_messageerrorlevel) | JSVM_MessageErrorLevel | Error level of a message.|
| [JSVM_DefineClassOptionsId](#jsvm_defineclassoptionsid) | JSVM_DefineClassOptionsId | Option ID of a class.|
| [JSVM_DebugOption](#jsvm_debugoption) | JSVM_DebugOption | Debugging option.|

### Functions

| Name                                                                                                                                                                | typedef Keyword| Description|
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------| -- | -- |
| [typedef void (JSVM_CDECL* JSVM_Finalize)(JSVM_Env env,void* finalizeData,void* finalizeHint)](#jsvm_finalize)                                                     | JSVM_CDECL* JSVM_Finalize | Function pointer type. It is passed in when a native object or data is associated with a JavaScript object. This function is called when the associated JS object is reclaimed by GC to perform native cleanup.|
| [typedef bool (JSVM_CDECL* JSVM_OutputStream)(const char* data,int size,void* streamData)](#jsvm_outputstream)                                                     | JSVM_CDECL* JSVM_OutputStream | Pointer to the callback of the ASCII output stream. **data** indicates the pointer to the output data. **size** indicates the size of the output data. **void** points to the end of the stream. streamData indicates the pointer passed to the API function along with the callback. The API function generates data to the output stream.|
| [typedef void (JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)](#jsvm_handlerforgc)                         | JSVM_CDECL* JSVM_HandlerForGC | Function pointer type of the GC callback.|
| [typedef void (JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location,const char* detail,bool isHeapOOM)](#jsvm_handlerforoomerror)                             | JSVM_CDECL* JSVM_HandlerForOOMError | Function pointer type of the OOM-Error callback.|
| [typedef void (JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location,const char* message)](#jsvm_handlerforfatalerror)                                       | JSVM_CDECL* JSVM_HandlerForFatalError | Function pointer type of the Fatal-Error callback.|
| [typedef void (JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)](#jsvm_handlerforpromisereject) | JSVM_CDECL* JSVM_HandlerForPromiseReject | Function pointer type of the Promise-Reject callback.|

## Enum Description

### JSVM_PropertyAttributes

```
enum JSVM_PropertyAttributes
```

**Description**

Control over the behavior of JavaScript object properties.

**Since**: 11

| Value                                                                            | Description                                                 |
|---------------------------------------------------------------------------------|-----------------------------------------------------|
| JSVM_DEFAULT = 0                                                                | No explicit attribute set on the property.                                      |
| JSVM_WRITABLE = 1 << 0                                                          | Writable property.                                           |
| JSVM_ENUMERABLE = 1 << 1                                                        | Enumerable property.                                          |
| JSVM_CONFIGURABLE = 1 << 2                                                      | Configurable property.                                          |
| JSVM_STATIC = 1 << 10                                                           | Static property of the class, instead of the default instance property. Used only by **OH_JSVM_DefineClass**.|
| JSVM_DEFAULT_METHOD = JSVM_WRITABLE \| JSVM_CONFIGURABLE                        |Configurable, writable, but not enumerable property, like a method in a JavaScript class.                     |
| JSVM_DEFAULT_JSPROPERTY = JSVM_WRITABLE \| JSVM_ENUMERABLE \| JSVM_CONFIGURABLE | Writable, enumerable, and configurable property, like a property set by value assignment in JavaScript.|

### JSVM_ValueType

```
enum JSVM_ValueType
```

**Description**

JSVM_Value type.

**Since**: 11

| Value| Description|
| -- | -- |
| JSVM_UNDEFINED | Undefined.|
| JSVM_NULL | Null.|
| JSVM_BOOLEAN | Boolean.|
| JSVM_NUMBER | Number.|
| JSVM_STRING | String.|
| JSVM_SYMBOL | Symbol.|
| JSVM_OBJECT | Object.|
| JSVM_FUNCTION | Function.|
| JSVM_EXTERNAL | External.|
| JSVM_BIGINT | BigInt.|

### JSVM_TypedarrayType

```
enum JSVM_TypedarrayType
```

**Description**

TypedArray type.

**Since**: 11

| Value| Description|
| -- | -- |
| JSVM_INT8_ARRAY | int8 type.|
| JSVM_UINT8_ARRAY | uint8 type.|
| JSVM_UINT8_CLAMPED_ARRAY | Fixed uint8 type.|
| JSVM_INT16_ARRAY | int16 type.|
| JSVM_UINT16_ARRAY | uint16 type.|
| JSVM_INT32_ARRAY | int32 type.|
| JSVM_UINT32_ARRAY | uint32 type.|
| JSVM_FLOAT32_ARRAY | Float32 type.|
| JSVM_FLOAT64_ARRAY | float64 type.|
| JSVM_BIGINT64_ARRAY | bigint64 type.|
| JSVM_BIGUINT64_ARRAY | biguint64 type.|

### JSVM_Status

```
enum JSVM_Status
```

**Description**

Complete status code indicating whether the JSVM-API call is successful or fails.

**Since**: 11

| Value| Description|
| -- | -- |
| JSVM_OK | Successful.|
| JSVM_INVALID_ARG | Invalid.|
| JSVM_OBJECT_EXPECTED | Object expected.|
| JSVM_STRING_EXPECTED | String expected.|
| JSVM_NAME_EXPECTED | Name expected.|
| JSVM_FUNCTION_EXPECTED | Function expected.|
| JSVM_NUMBER_EXPECTED | Number expected.|
| JSVM_BOOLEAN_EXPECTED | Boolean expected.|
| JSVM_ARRAY_EXPECTED | Array expected.|
| JSVM_GENERIC_FAILURE | Generic failure.|
| JSVM_PENDING_EXCEPTION | Pending exception.|
| JSVM_CANCELLED | Canceled.|
| JSVM_ESCAPE_CALLED_TWICE | Escaped twice.|
| JSVM_HANDLE_SCOPE_MISMATCH | Mismatched handle scope.|
| JSVM_CALLBACK_SCOPE_MISMATCH | Mismatched callback scope.|
| JSVM_QUEUE_FULL | Full queue.|
| JSVM_CLOSING | Deactivating|
| JSVM_BIGINT_EXPECTED | Bigint expected.|
| JSVM_DATE_EXPECTED | Date expected.|
| JSVM_ARRAYBUFFER_EXPECTED | ArrayBuffer expected.|
| JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED | Detachable array buffer expected.|
| JSVM_WOULD_DEADLOCK | Would be in deadlock.|
| JSVM_NO_EXTERNAL_BUFFERS_ALLOWED | No external buffers allowed.|
| JSVM_CANNOT_RUN_JS | Cannot run JavaSript.|
| JSVM_INVALID_TYPE | The input parameter is of an invalid type.<br>**Since**: 18|
| JSVM_JIT_MODE_EXPECTED | No JIT permission.<br>**Since**: 18|

### JSVM_KeyCollectionMode

```
enum JSVM_KeyCollectionMode
```

**Description**

Limited range of properties to be searched for.

**Since**: 11

| Value| Description|
| -- | -- |
| JSVM_KEY_INCLUDE_PROTOTYPES | Includes properties on the prototype chain of the object.|
| JSVM_KEY_OWN_ONLY | Includes only the object's own properties.|

### JSVM_KeyFilter

```
enum JSVM_KeyFilter
```

**Description**

Property filter. You can use OR to construct a composite filter.

**Since**: 11

| Value| Description|
| -- | -- |
| JSVM_KEY_ALL_PROPERTIES = 0 | Key of all properties.|
| JSVM_KEY_WRITABLE = 1 | Writable key.|
| JSVM_KEY_ENUMERABLE = 1 << 1 | Enumerable key.|
| JSVM_KEY_CONFIGURABLE = 1 << 2 | Configurable key.|
| JSVM_KEY_SKIP_STRINGS = 1 << 3 | Key that skips strings.|
| JSVM_KEY_SKIP_SYMBOLS = 1 << 4 | Key that skips symbols.|

### JSVM_KeyConversion

```
enum JSVM_KeyConversion
```

**Description**

Key conversion options.

**Since**: 11

| Value| Description|
| -- | -- |
| JSVM_KEY_KEEP_NUMBERS | Gets the numbers of integer indexes.|
| JSVM_KEY_NUMBERS_TO_STRINGS | Converts integer indexes to strings.|

### JSVM_MemoryPressureLevel

```
enum JSVM_MemoryPressureLevel
```

**Description**

Memory pressure level.

**Since**: 11

| Value| Description|
| -- | -- |
| JSVM_MEMORY_PRESSURE_LEVEL_NONE | No pressure.|
| JSVM_MEMORY_PRESSURE_LEVEL_MODERATE | Moderate pressure.|
| JSVM_MEMORY_PRESSURE_LEVEL_CRITICAL | Critical pressure.|

### JSVM_RegExpFlags

```
enum JSVM_RegExpFlags
```

**Description**

Regular expression flags. They can be used to enable a set of flags.

**Since**: 12

| Value| Description|
| -- | -- |
| JSVM_REGEXP_NONE = 0 | None mode.|
| JSVM_REGEXP_GLOBAL = 1 << 0 | Global mode.|
| JSVM_REGEXP_IGNORE_CASE = 1 << 1 | Ignore Case mode.|
| JSVM_REGEXP_MULTILINE = 1 << 2 | Multiline mode.|
| JSVM_REGEXP_STICKY = 1 << 3 | Sticky mode.|
| JSVM_REGEXP_UNICODE = 1 << 4 | Unicode mode.|
| JSVM_REGEXP_DOT_ALL = 1 << 5 | dotAll mode.|
| JSVM_REGEXP_LINEAR = 1 << 6 | Linear mode.|
| JSVM_REGEXP_HAS_INDICES = 1 << 7 | Has Indices mode.|
| JSVM_REGEXP_UNICODE_SETS = 1 << 8 | Unicode Sets mode.|

### JSVM_InitializedFlag

```
enum JSVM_InitializedFlag
```

**Description**

Initialization flag.

**Since**: 12

| Value| Description|
| -- | -- |
| JSVM_ZERO_INITIALIZED | Initializes to 0.|
| JSVM_UNINITIALIZED | No initialization.|

### JSVM_WasmOptLevel

```
enum JSVM_WasmOptLevel
```

**Description**

WebAssembly function optimization level.

**Since**: 12

| Value| Description|
| -- | -- |
| JSVM_WASM_OPT_BASELINE = 10 | Baseline optimization level.|
| JSVM_WASM_OPT_HIGH = 20 | High optimization level.|

### JSVM_CacheType

```
enum JSVM_CacheType
```

**Description**

Cache type.

**Since**: 12

| Value| Description|
| -- | -- |
| JSVM_CACHE_TYPE_JS | JS cache, which is generated by calling OH_JSVM_CreateCodeCache.|
| JSVM_CACHE_TYPE_WASM | WebAssembly cache, which is generated by calling OH_JSVM_CreateWasmCache.|

### JSVM_MicrotaskPolicy

```
enum JSVM_MicrotaskPolicy
```

**Description**

JSVM microtask execution policy.

**Since**: 18

| Value| Description|
| -- | -- |
| JSVM_MICROTASK_EXPLICIT = 0 | Executes microtasks after the OH_JSVM_PerformMicrotaskCheckpoint method is called.|
| JSVM_MICROTASK_AUTO | Microtasks are automatically executed when the JS call stack is 0. Default mode.|

### JSVM_TraceCategory

```
enum JSVM_TraceCategory
```

**Description**

Category of a trace event in the JSVM.

**Since**: 18

| Value| Description|
| -- | -- |
| JSVM_TRACE_VM | Collects statistics on the calls of major JSVM APIs, such as the JS script execution.|
| JSVM_TRACE_COMPILE | Collects statistics on the calls of compilation-related APIs, such as background compilation.|
| JSVM_TRACE_EXECUTE | Collects statistics on the calls of APIs related to the running status, such as interruption and microtasks.|
| JSVM_TRACE_RUNTIME | Collects statistics on external function calls.|
| JSVM_TRACE_STACK_TRACE | Collects statistics on stacking information in the JSVM.|
| JSVM_TRACE_WASM | Collects statistics on the calls of major WASM APIs, such as WASM module compilation and instantiation.|
| JSVM_TRACE_WASM_DETAILED | Collects statistics on the calls of WASM APIs in more details, such as background compilation and jump compilation.|

### JSVM_CBTriggerTimeForGC

```
enum JSVM_CBTriggerTimeForGC
```

**Description**

Time when a callback function is triggered.

**Since**: 18

| Value| Description|
| -- | -- |
| JSVM_CB_TRIGGER_BEFORE_GC | A callback function is triggered before GC.|
| JSVM_CB_TRIGGER_AFTER_GC | A callback function is triggered after GC.|

### JSVM_GCType

```
enum JSVM_GCType
```

**Description**

GC type.

**Since**: 18

| Value                                                                                                                                                   | Description                              |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| JSVM_GC_TYPE_SCAVENGE = 1 << 0                                                                                                                         | The GC algorithm is Scavenge.                  |
| JSVM_GC_TYPE_MINOR_MARK_COMPACT = 1 << 1                                                                                                               | The GC algorithm is Minor-Mark-Compact.        |
| JSVM_GC_TYPE_MARK_SWEEP_COMPACT = 1 << 2                                                                                                               | The GC algorithm is Mark-Sweep-Compact.        |
| JSVM_GC_TYPE_INCREMENTAL_MARKING = 1 << 3                                                                                                              | The GC algorithm is Incremental-Marking.       |
| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS = 1 << 4                                                                                                           | The GC algorithm is Weak-Callbacks.            |
| JSVM_GC_TYPE_ALL = JSVM_GC_TYPE_SCAVENGE \| JSVM_GC_TYPE_MINOR_MARK_COMPACT \| JSVM_GC_TYPE_MARK_SWEEP_COMPACT \| JSVM_GC_TYPE_INCREMENTAL_MARKING \| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS | GC algorithms of all types.|

### JSVM_GCCallbackFlags

```
enum JSVM_GCCallbackFlags
```

**Description**

GC callback flag.

**Since**: 18

| Value| Description|
| -- | -- |
| JSVM_NO_GC_CALLBACK_FLAGS | No callback flag.|
| JSVM_GC_CALLBACK_CONSTRUCT_RETAINED_OBJECT_INFOS | Builds information about retained objects in the GC callback.|
| JSVM_GC_CALLBACK_FORCED | Forcibly executes the GC callback.|
| JSVM_GC_CALLBACK_SYNCHRONOUS_PHANTOM_CALLBACK_PROCESSING | Processes ghost objects synchronously in the GC callback.|
| JSVM_GC_CALLBACK_COLLECT_ALL_AVAILABLE_GARBAGE | Collects all available garbage objects during GC.|
| JSVM_GC_CALLBACK_COLLECT_ALL_EXTERNAL_MEMORY | Collects all external memory during GC.|
| JSVM_GC_CALLBACK_SCHEDULE_IDLE_GARBAGE_COLLECTION | Schedules GC when the device is idle.|

### JSVM_PromiseRejectEvent

```
enum JSVM_PromiseRejectEvent
```

**Description**

Promise-reject event.

**Since**: 18

| Value| Description|
| -- | -- |
| JSVM_PROMISE_REJECT_OTHER_REASONS = 0 | The promise is rejected, but the rejection reason is unknown or unclear.|
| JSVM_PROMISE_REJECT_WITH_NO_HANDLER = 1 | Promise rejected without a handler.|
| JSVM_PROMISE_HANDLER_ADDED_AFTER_REJECT = 2 | Promise rejected after a handler is added.|
| JSVM_PROMISE_REJECT_AFTER_RESOLVED = 3 | Promise rejected after it is resolved.|
| JSVM_PROMISE_RESOLVE_AFTER_RESOLVED = 4 | Promise resolved after it is rejected.|

### JSVM_MessageErrorLevel

```
enum JSVM_MessageErrorLevel
```

**Description**

Error level of a message.

**Since**: 18

| Value                                                                                                     | Description|
|----------------------------------------------------------------------------------------------------------| -- |
| JSVM_MESSAGE_LOG = (1 << 0)                                                                              | Log level.|
| JSVM_MESSAGE_DEBUG = (1 << 1)                                                                            | Debug level.|
| JSVM_MESSAGE_INFO = (1 << 2)                                                                             | Info level.|
| JSVM_MESSAGE_ERROR = (1 << 3)                                                                            | Error level.|
| JSVM_MESSAGE_WARNING = (1 << 4)                                                                          | Warning level.|
| JSVM_MESSAGE_ALL = JSVM_MESSAGE_LOG \| JSVM_MESSAGE_DEBUG \| JSVM_MESSAGE_INFO \| JSVM_MESSAGE_ERROR \| JSVM_MESSAGE_WARNING | All levels.|

### JSVM_DefineClassOptionsId

```
enum JSVM_DefineClassOptionsId
```

**Description**

Options ID of a class.

**Since**: 18

| Value| Description|
| -- | -- |
| JSVM_DEFINE_CLASS_NORMAL | Defines a class in normal mode.|
| JSVM_DEFINE_CLASS_WITH_COUNT | Reserves a specified number of interfield slots for the created class. Native data can be stored in these slots.|
| JSVM_DEFINE_CLASS_WITH_PROPERTY_HANDLER | Sets the interception attributes of the created class and sets the callback function when the class is called as a function.|

### JSVM_DebugOption

```
enum JSVM_DebugOption
```

**Description**

Debugging options.

**Since**: 20

| Value| Description|
| -- | -- |
| JSVM_SCOPE_CHECK | Scope verification.|


## Function Description

### JSVM_Finalize()

```
typedef void (JSVM_CDECL* JSVM_Finalize)(JSVM_Env env,void* finalizeData,void* finalizeHint)
```

**Description**

Function pointer type. It is passed in when a native object or data is associated with a JavaScript object. This function is called when the associated JS object is reclaimed by the GC to clear native data.

**Since**: 11

### JSVM_OutputStream()

```
typedef bool (JSVM_CDECL* JSVM_OutputStream)(const char* data,int size,void* streamData)
```

**Description**

Pointer to the callback of the ASCII output stream. **data** indicates the pointer to the output data. **size** indicates the size of the output data. **void** points to the end of the stream. **streamData** indicates the pointer passed to the API function together with the callback. The API function generates data to the output stream.

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| bool | If true is returned, the stream can continue to receive data. If false is returned, the stream is stopped.|

### JSVM_HandlerForGC()

```
typedef void (JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)
```

**Description**

Function pointer type of the GC callback.

**Since**: 18

### JSVM_HandlerForOOMError()

```
typedef void (JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location,const char* detail,bool isHeapOOM)
```

**Description**

Function pointer type of the OOM-Error callback.

**Since**: 18

### JSVM_HandlerForFatalError()

```
typedef void (JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location,const char* message)
```

**Description**

Defines the function pointer type of the Fatal-Error callback.

**Since**: 18

### JSVM_HandlerForPromiseReject()

```
typedef void (JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)
```

**Description**

Defines the function pointer type of the Promise-Reject callback.

**Since**: 18
