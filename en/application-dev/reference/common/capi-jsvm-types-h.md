# jsvm_types.h
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Defines JSVM-API types. JSVM-API is used to provide independent, standard, and complete JS engine capabilities, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross-language calls, and taking snapshots.

**File to import**: <ark_runtime/jsvm_types.h>

**Library**: libjsvm.so

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

## Summary

### Structs

| Name                                                                                               | typedef Keyword                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                         |
|---------------------------------------------------------------------------------------------------|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [JSVM_CallbackStruct](capi-jsvm-jsvm-callbackstruct.md)                                           | JSVM_CallbackStruct                     | Defines the pointer to the data of the native callbacks provided by the user. These functions are exposed to JavaScript via JSVM-API.                                                                                                                                                                                                                                                                                                                                                                       |
| [JSVM_HeapStatistics](capi-jsvm-jsvm-heapstatistics.md)                                           | JSVM_HeapStatistics                     | Stores statistics about JavaScript heap memory usage.                                                                                                                                                                                                                                                                                                                                                                             |
| [JSVM_InitOptions](capi-jsvm-jsvm-initoptions.md)                                                 | JSVM_InitOptions                        | Defines options for initializing a JavaScript VM.                                                                                                                                                                                                                                                                                                                                                                                                  |
| [JSVM_CreateVMOptions](capi-jsvm-jsvm-createvmoptions.md)                                         | JSVM_CreateVMOptions                    | Defines options for creating a JavaScript VM.                                                                                                                                                                                                                                                                                                                                                                                                        |
| [JSVM_VMInfo](capi-jsvm-jsvm-vminfo.md)                                                           | JSVM_VMInfo                             | Defines JavaScript VM information.                                                                                                                                                                                                                                                                                                                                                                                                           |
| [JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)                                   | JSVM_PropertyDescriptor                 | Defines property descriptor.                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [JSVM_ExtendedErrorInfo](capi-jsvm-jsvm-extendederrorinfo.md)                                     | JSVM_ExtendedErrorInfo                  | Defines extended error information.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [JSVM_TypeTag](capi-jsvm-jsvm-typetag.md)                                                         | JSVM_TypeTag                            | Defines the type tag, which is stored as a 128-bit value of two unsigned 64-bit integers. As a UUID, it can tag JavaScript objects to ensure that their types remain unchanged.                                                                                                                                                                                                                                                                                                                                                |
| [JSVM_PropertyHandlerConfigurationStruct](capi-jsvm-jsvm-propertyhandlerconfigurationstruct.md)   | JSVM_PropertyHandlerConfigurationStruct | Defines a struct for triggering the corresponding callback when the getter, setter, deleter, or enumerator of an object is executed.                                                                                                                                                                                                                                                                                                                                                                |
| [JSVM_ScriptOrigin](capi-jsvm-jsvm-scriptorigin.md)                                               | JSVM_ScriptOrigin                       | Defines the original information about a JavaScript code segment, such as the source map path, source file name, and start line/column number in the source file.                                                                                                                                                                                                                                                                                                                                                                        |
| [JSVM_PropertyHandler](capi-jsvm-jsvm-propertyhandler.md)                                         | JSVM_PropertyHandler                    | Defines the pointer to the callback function triggered when a class is called as a function, and the pointer collection of the callback function triggered when an instance object property is accessed.                                                                                                                                                                                                                                                                                                                                                                     |
| [JSVM_DefineClassOptions](capi-jsvm-jsvm-defineclassoptions.md)                                   | JSVM_DefineClassOptions                 | Defines class options.                                                                                                                                                                                                                                                                                                                                                                                                                |
| [JSVM_VM__*](capi-jsvm-jsvm-vm--8h.md)                                                            | JSVM_VM                                 | Defines a JavaScript VM instance.                                                                                                                                                                                                                                                                                                                                                                                                         |
| [JSVM_VMScope__*](capi-jsvm-jsvm-vmscope--8h.md)                                                  | JSVM_VMScope                            | Defines the JavaScript VM scope.                                                                                                                                                                                                                                                                                                                                                                                                        |
| [JSVM_EnvScope__*](capi-jsvm-jsvm-envscope--8h.md)                                                | JSVM_EnvScope                           | Defines the environment scope of the current VM instance. The environment is available to the VM instance of the thread only after the thread enters **JSVM_EnvScope** of the environment through **OH_JSVM_OpenEnvScope**.                                                                                                                                                                                                                                                                                                                                       |
| [JSVM_Script__*](capi-jsvm-jsvm-script--8h.md)                                                    | JSVM_Script                             | Defines the JavaScript code.                                                                                                                                                                                                                                                                                                                                                                                                          |
| [JSVM_Env__*](capi-jsvm-jsvm-env--8h.md)                                                          | JSVM_Env                                | Defines the context of a specific VM state. It needs to be passed as a parameter when the native function is called and passed to any subsequent JSVM-API nested call.                                                                                                                                                                                                                                                                                                                                                               |
| [JSVM_CpuProfiler__*](capi-jsvm-jsvm-cpuprofiler--8h.md)                                          | JSVM_CpuProfiler                        | Defines a JavaScript CPU profiler.                                                                                                                                                                                                                                                                                                                                                                                                 |
| [JSVM_Value__*](capi-jsvm-jsvm-value--8h.md)                                                      | JSVM_Value                              | Defines the JavaScript value.                                                                                                                                                                                                                                                                                                                                                                                                             |
| [JSVM_Data__*](capi-jsvm-jsvm-data--8h.md)                                                        | JSVM_Data                               | Defines the JavaScript data.                                                                                                                                                                                                                                                                                                                                                                                                      |
| [JSVM_Ref__*](capi-jsvm-jsvm-ref--8h.md)                                                          | JSVM_Ref                                | Defines the reference to the JavaScript value.                                                                                                                                                                                                                                                                                                                                                                                                          |
| [JSVM_HandleScope__*](capi-jsvm-jsvm-handlescope--8h.md)                                          | JSVM_HandleScope                        | Defines the scope of the JavaScript value. It is used to control and modify the lifecycle of an object created in a specific scope. Typically, the JSVM-API value is created in the context of **JSVM_HandleScope**. When the native method is called from JavaScript, the default **JSVM_HandleScope** exists. If the user does not explicitly create a new **JSVM_HandleScope**, the JSVM-API value is created in the default **JSVM_HandleScope**. For any code call other than native method execution (for example, libuv callback), the module needs to create a scope before calling any function that may create a JavaScript value. **JSVM_HandleScope** is created using **OH_JSVM_OpenHandleScope** and destroyed using **OH_JSVM_CloseHandleScope**. Closing the scope indicates to the GC that all **JSVM_Values** created during the lifecycle of **JSVM_HandleScope** will no longer be referenced from the stack frame of the current heap.|
| [JSVM_EscapableHandleScope__*](capi-jsvm-jsvm-escapablehandlescope--8h.md)                        | JSVM_EscapableHandleScope               | Defines a special type of handle scope, which is used to return the value created in a specific handle scope to the parent scope.                                                                                                                                                                                                                                                                                                                                                                      |
| [JSVM_CallbackInfo__*](capi-jsvm-jsvm-callbackinfo--8h.md)                                        | JSVM_CallbackInfo                       | Defines an opaque data type passed to the callback. It can be used to obtain additional information about the context in which the function is called.                                                                                                                                                                                                                                                                                                                                                                                     |
| [JSVM_Deferred__*](capi-jsvm-jsvm-deferred--8h.md)                                                | JSVM_Deferred                           | Defines the deferred object.                                                                                                                                                                                                                                                                                                                                                                                                             |
| [JSVM_PropertyHandlerConfigurationStruct*](capi-jsvm-jsvm-propertyhandlerconfigurationstruct8h.md) | JSVM_PropertyHandlerCfg                 | Defines the pointer type of the struct that contains the property handler.                                                                                                                                                                                                                                                                                                                                                                                                          |
| [JSVM_CallbackStruct*](capi-jsvm-jsvm-callbackstruct8h.md)                                         | JSVM_Callback   | Defines the pointer types of the native functions provided by user. These functions are exposed to JavaScript via JSVM-API.                                |
| [JSVM_CompileProfile](capi-jsvm-jsvm-compileprofile.md) | JSVM_CompileProfile | Defines the compilation sampling file transferred together with **JSVM_COMPILE_COMPILE_PROFILE**.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [JSVM_PropertyAttributes](#jsvm_propertyattributes) | JSVM_PropertyAttributes | Enumerates the behaviors of controlling JavaScript object properties.|
| [JSVM_ValueType](#jsvm_valuetype) | JSVM_ValueType | Enumerates **JSVM_Value** types.|
| [JSVM_TypedarrayType](#jsvm_typedarraytype) | JSVM_TypedarrayType | Enumerates **TypedArray** types.|
| [JSVM_Status](#jsvm_status) | JSVM_Status | Enumerates complete status codes indicating whether the JSVM-API call is successful or failed.|
| [JSVM_KeyCollectionMode](#jsvm_keycollectionmode) | JSVM_KeyCollectionMode | Enumerates ranges of properties to be searched for.|
| [JSVM_KeyFilter](#jsvm_keyfilter) | JSVM_KeyFilter | Enumerates key filters. You can use OR to construct a composite filter.|
| [JSVM_KeyConversion](#jsvm_keyconversion) | JSVM_KeyConversion | Enumerates key conversion options.|
| [JSVM_MemoryPressureLevel](#jsvm_memorypressurelevel) | JSVM_MemoryPressureLevel | Enumerates memory pressure levels.|
| [JSVM_RegExpFlags](#jsvm_regexpflags) | JSVM_RegExpFlags | Enumerates regular expression flags. They can be used to enable a set of flags.|
| [JSVM_InitializedFlag](#jsvm_initializedflag) | JSVM_InitializedFlag | Enumerates the initialization modes of flags.|
| [JSVM_WasmOptLevel](#jsvm_wasmoptlevel) | JSVM_WasmOptLevel | Enumerates WebAssembly optimization levels.|
| [JSVM_CacheType](#jsvm_cachetype) | JSVM_CacheType | Enumerates cache types.|
| [JSVM_MicrotaskPolicy](#jsvm_microtaskpolicy) | JSVM_MicrotaskPolicy | Enumerates JSVM microtask execution policies.|
| [JSVM_TraceCategory](#jsvm_tracecategory) | JSVM_TraceCategory | Enumerates categories of the JSVM internal trace events.|
| [JSVM_CBTriggerTimeForGC](#jsvm_cbtriggertimeforgc) | JSVM_CBTriggerTimeForGC | Enumerates the timings when the callback is triggered.|
| [JSVM_GCType](#jsvm_gctype) | JSVM_GCType | Enumerates GC types.|
| [JSVM_GCCallbackFlags](#jsvm_gccallbackflags) | JSVM_GCCallbackFlags | Enumerates GC callback flags.|
| [JSVM_PromiseRejectEvent](#jsvm_promiserejectevent) | JSVM_PromiseRejectEvent | Enumerates reject events for a promise.|
| [JSVM_MessageErrorLevel](#jsvm_messageerrorlevel) | JSVM_MessageErrorLevel | Enumerates error message levels.|
| [JSVM_DefineClassOptionsId](#jsvm_defineclassoptionsid) | JSVM_DefineClassOptionsId | Enumerates definition modes for a class.|
| [JSVM_DebugOption](#jsvm_debugoption) | JSVM_DebugOption | Enumerates debugging options.|

### Functions

| Name                                                                                                                                                                | typedef Keyword| Description|
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------| -- | -- |
| [typedef void (JSVM_CDECL* JSVM_Finalize)(JSVM_Env env,void* finalizeData,void* finalizeHint)](#jsvm_finalize)                                                     | JSVM_CDECL* JSVM_Finalize | Defines a pointer to the **JSVM_Finalize** function. It is passed in when a native object or data is associated with a JavaScript object, and is called when the associated JavaScript object is reclaimed by the GC to execute the native cleanup action.|
| [typedef bool (JSVM_CDECL* JSVM_OutputStream)(const char* data,int size,void* streamData)](#jsvm_outputstream)                                                     | JSVM_CDECL* JSVM_OutputStream | Defines a pointer to the callback of the ASCII output stream. **data** indicates the pointer to the output data. **size** indicates the size of the output data. **void** is a null pointer that points to the end of the stream. **streamData** indicates the pointer passed to the API function together with the callback. The API function generates data to the output stream.|
| [typedef void (JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)](#jsvm_handlerforgc)                         | JSVM_CDECL* JSVM_HandlerForGC | Defines a pointer to the handler for GC callback.|
| [typedef void (JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location,const char* detail,bool isHeapOOM)](#jsvm_handlerforoomerror)                             | JSVM_CDECL* JSVM_HandlerForOOMError | Defines a pointer to the handler for OOM-Error callback.|
| [typedef void (JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location,const char* message)](#jsvm_handlerforfatalerror)                                       | JSVM_CDECL* JSVM_HandlerForFatalError | Defines a pointer to the handler for Fatal-Error callback.|
| [typedef void (JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)](#jsvm_handlerforpromisereject) | JSVM_CDECL* JSVM_HandlerForPromiseReject | Defines a pointer to the handler for Promise-Reject callback.|

### Variables

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| uint16_t    | char16_t   | Create an alias, **char16_t**, for **uint16_t**.<br>This code ensures that the **char16_t** type is available in all target compilation environments, even in some old environments that do not support it. **char16_t** is a new basic data type introduced in C++11. It is used to store 16-bit characters and represent UTF-16-encoded characters.<br>If the compiler does not recognize **char16_t**, manually define a custom type whose underlying implementation is a 16-bit unsigned integer. The prerequisite is as follows: the current compiler is not a C++ compiler, or it is a Microsoft Visual C++ compiler with a version earlier than Visual Studio 2015 (exclusive).|

## Enum Description

### JSVM_PropertyAttributes

```c
enum JSVM_PropertyAttributes
```

**Description**

Enumerates the behaviors of controlling JavaScript object properties.

**Since**: 11

| Enum Item                                                                               | Description                                                 |
|---------------------------------------------------------------------------------------|-----------------------------------------------------|
| JSVM_DEFAULT = 0                                                                      | No explicit attribute set on the property.                                      |
| JSVM_WRITABLE = 1 << 0                                                                | Writable property.                                           |
| JSVM_ENUMERABLE = 1 << 1                                                              | Enumerable property.                                          |
| JSVM_CONFIGURABLE = 1 << 2                                                            | Configurable property.                                          |
| JSVM_NO_RECEIVER_CHECK = 1 << 3                                                       | Receiver used to mark the local methods does not need to be checked. If **JSVM_NO_RECEIVER_CHECK** is not set, the method accepts only the instance of the defined class as the receiver. Otherwise, an exception "TypeError: illegal call" is thrown to the JSVM.                                          |
| JSVM_STATIC = 1 << 10                                                                 | Static property of the class, instead of the default instance property. Used only by **OH_JSVM_DefineClass**.|
| JSVM_DEFAULT_METHOD = JSVM_WRITABLE \| JSVM_CONFIGURABLE                              | Configurable, writable, but not enumerable property, like a method of a JavaScript class.                     |
| JSVM_METHOD_NO_RECEIVER_CHECK = JSVM_DEFAULT_METHOD \| JSVM_NO_RECEIVER_CHECK         | Class method whose receiver does not need to be checked.                     |
| JSVM_DEFAULT_JSPROPERTY = JSVM_WRITABLE \| JSVM_ENUMERABLE \| JSVM_CONFIGURABLE       | Writable, enumerable, and configurable property, like a property set by value assignment in JavaScript.|
| JSVM_JSPROPERTY_NO_RECEIVER_CHECK = JSVM_DEFAULT_JSPROPERTY \| JSVM_NO_RECEIVER_CHECK | Object property whose receiver does not need to be checked.|

### JSVM_ValueType

```c
enum JSVM_ValueType
```

**Description**

Enumerates **JSVM_Value** types.

**Since**: 11

| Enum Item| Description|
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

```c
enum JSVM_TypedarrayType
```

**Description**

Enumerates **TypedArray** types.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| JSVM_INT8_ARRAY | int8 type.|
| JSVM_UINT8_ARRAY | uint8 type.|
| JSVM_UINT8_CLAMPED_ARRAY | Fixed uint8 type.|
| JSVM_INT16_ARRAY | int16 type.|
| JSVM_UINT16_ARRAY | uint16 type.|
| JSVM_INT32_ARRAY | int32 type.|
| JSVM_UINT32_ARRAY | uint32 type.|
| JSVM_FLOAT32_ARRAY | float32 type.|
| JSVM_FLOAT64_ARRAY | float64 type.|
| JSVM_BIGINT64_ARRAY | bigint64 type.|
| JSVM_BIGUINT64_ARRAY | biguint64 type.|

### JSVM_Status

```c
enum JSVM_Status
```

**Description**

Enumerates complete status codes indicating whether the JSVM-API call is successful or failed.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| JSVM_OK | Successful.|
| JSVM_INVALID_ARG | Invalid argument.|
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
| JSVM_ESCAPE_CALLED_TWICE | Escape called twice.|
| JSVM_HANDLE_SCOPE_MISMATCH | Handle scope mismatch.|
| JSVM_CALLBACK_SCOPE_MISMATCH | Callback scope mismatch.|
| JSVM_QUEUE_FULL | Full queue.|
| JSVM_CLOSING | Closing.|
| JSVM_BIGINT_EXPECTED | BigInt expected.|
| JSVM_DATE_EXPECTED | Date expected.|
| JSVM_ARRAYBUFFER_EXPECTED | ArrayBuffer expected.|
| JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED | Detachable array buffer expected.|
| JSVM_WOULD_DEADLOCK | Would be in deadlock.|
| JSVM_NO_EXTERNAL_BUFFERS_ALLOWED | No external buffers allowed.|
| JSVM_CANNOT_RUN_JS | Cannot run JavaSript.|
| JSVM_INVALID_TYPE | Invalid type.<br>**Since**: 18|
| JSVM_JIT_MODE_EXPECTED | JIT mode expected.<br>**Since**: 18|

### JSVM_KeyCollectionMode

```c
enum JSVM_KeyCollectionMode
```

**Description**

Enumerates ranges of properties to be searched for.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| JSVM_KEY_INCLUDE_PROTOTYPES | Properties on the prototype chain of the object are included.|
| JSVM_KEY_OWN_ONLY | Only the object's own properties are included.|

### JSVM_KeyFilter

```c
enum JSVM_KeyFilter
```

**Description**

Enumerates key filters. You can use OR to construct a composite filter.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| JSVM_KEY_ALL_PROPERTIES = 0 | Key of all properties.|
| JSVM_KEY_WRITABLE = 1 | Writable key.|
| JSVM_KEY_ENUMERABLE = 1 << 1 | Enumerable key.|
| JSVM_KEY_CONFIGURABLE = 1 << 2 | Configurable key.|
| JSVM_KEY_SKIP_STRINGS = 1 << 3 | Key that skips strings.|
| JSVM_KEY_SKIP_SYMBOLS = 1 << 4 | Key that skips symbols.|

### JSVM_KeyConversion

```c
enum JSVM_KeyConversion
```

**Description**

Enumerates key conversion options.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| JSVM_KEY_KEEP_NUMBERS | Returns the numbers of integer indexes.|
| JSVM_KEY_NUMBERS_TO_STRINGS | Converts integer indexes to strings.|

### JSVM_MemoryPressureLevel

```c
enum JSVM_MemoryPressureLevel
```

**Description**

Enumerates memory pressure levels.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| JSVM_MEMORY_PRESSURE_LEVEL_NONE | No pressure.|
| JSVM_MEMORY_PRESSURE_LEVEL_MODERATE | Moderate pressure.|
| JSVM_MEMORY_PRESSURE_LEVEL_CRITICAL | Critical pressure.|

### JSVM_RegExpFlags

```c
enum JSVM_RegExpFlags
```

**Description**

Enumerates regular expression flags. They can be used to enable a set of flags.

**Since**: 12

| Enum Item| Description|
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

```c
enum JSVM_InitializedFlag
```

**Description**

Enumerates the initialization modes of flags.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| JSVM_ZERO_INITIALIZED | Flags are initialized to 0.|
| JSVM_UNINITIALIZED | No initialization.|

### JSVM_WasmOptLevel

```c
enum JSVM_WasmOptLevel
```

**Description**

Enumerates WebAssembly optimization levels.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| JSVM_WASM_OPT_BASELINE = 10 | Baseline optimization level.|
| JSVM_WASM_OPT_HIGH = 20 | High optimization level.|

### JSVM_CacheType

```c
enum JSVM_CacheType
```

**Description**

Enumerates cache types.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| JSVM_CACHE_TYPE_JS | JavaScript cache, which is generated by **OH_JSVM_CreateCodeCache**.|
| JSVM_CACHE_TYPE_WASM | WebAssembly cache, which is generated by **OH_JSVM_CreateWasmCache**.|

### JSVM_MicrotaskPolicy

```c
enum JSVM_MicrotaskPolicy
```

**Description**

Enumerates JSVM microtask execution policies.

**Since**: 18

| Enum Item| Description|
| -- | -- |
| JSVM_MICROTASK_EXPLICIT = 0 | Microtasks are executed after the **OH_JSVM_PerformMicrotaskCheckpoint** method is called.|
| JSVM_MICROTASK_AUTO | Microtasks are automatically executed when the JS call stack is 0. This policy is used by default.|

### JSVM_TraceCategory

```c
enum JSVM_TraceCategory
```

**Description**

Enumerates categories of the JSVM internal trace events.

**Since**: 18

| Enum Item| Description|
| -- | -- |
| JSVM_TRACE_VM | Collects the calls of main JSVM APIs, for example, executing JS scripts.|
| JSVM_TRACE_COMPILE | Collects the calls of compilation APIs, for example, background compilation.|
| JSVM_TRACE_EXECUTE | Collects the calls of APIs related to the running status, for example, task interruption and microtasks.|
| JSVM_TRACE_RUNTIME | Collects information about the external function calls.|
| JSVM_TRACE_STACK_TRACE | Collects stack trace information from the JSVM.|
| JSVM_TRACE_WASM | Collects the calls of main WASM APIs, for example, compiling and instantiating WASM modules.|
| JSVM_TRACE_WASM_DETAILED | Collects detailed WASM API calls, for example, background compilation and jumpboard compilation.|

### JSVM_CBTriggerTimeForGC

```c
enum JSVM_CBTriggerTimeForGC
```

**Description**

Enumerates the timings when the callback is triggered.

**Since**: 18

| Enum Item| Description|
| -- | -- |
| JSVM_CB_TRIGGER_BEFORE_GC | A callback function is triggered before GC.|
| JSVM_CB_TRIGGER_AFTER_GC | A callback function is triggered after GC.|

### JSVM_GCType

```c
enum JSVM_GCType
```

**Description**

Enumerates GC types.

**Since**: 18

| Enum Item                                                                                                                                                   | Description                              |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| JSVM_GC_TYPE_SCAVENGE = 1 << 0                                                                                                                         | The GC algorithm is Scavenge.                  |
| JSVM_GC_TYPE_MINOR_MARK_COMPACT = 1 << 1                                                                                                               | The GC algorithm is Minor-Mark-Compact.        |
| JSVM_GC_TYPE_MARK_SWEEP_COMPACT = 1 << 2                                                                                                               | The GC algorithm is Mark-Sweep-Compact.        |
| JSVM_GC_TYPE_INCREMENTAL_MARKING = 1 << 3                                                                                                              | The GC algorithm is Incremental-Marking.       |
| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS = 1 << 4                                                                                                           | The GC algorithm is Weak-Callbacks.            |
| JSVM_GC_TYPE_ALL = JSVM_GC_TYPE_SCAVENGE \| JSVM_GC_TYPE_MINOR_MARK_COMPACT \| JSVM_GC_TYPE_MARK_SWEEP_COMPACT \| JSVM_GC_TYPE_INCREMENTAL_MARKING \| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS | All types of GC algorithms are included.|

### JSVM_GCCallbackFlags

```c
enum JSVM_GCCallbackFlags
```

**Description**

Enumerates GC callback flags.

**Since**: 18

| Enum Item| Description|
| -- | -- |
| JSVM_NO_GC_CALLBACK_FLAGS | No callback flag.|
| JSVM_GC_CALLBACK_CONSTRUCT_RETAINED_OBJECT_INFOS | Builds reserved object information in the GC callback.|
| JSVM_GC_CALLBACK_FORCED | Forcibly executes the GC callback.|
| JSVM_GC_CALLBACK_SYNCHRONOUS_PHANTOM_CALLBACK_PROCESSING | Synchronously processes ghost object callbacks.|
| JSVM_GC_CALLBACK_COLLECT_ALL_AVAILABLE_GARBAGE | Collects all available garbage objects during GC.|
| JSVM_GC_CALLBACK_COLLECT_ALL_EXTERNAL_MEMORY | Collects all external memory during GC.|
| JSVM_GC_CALLBACK_SCHEDULE_IDLE_GARBAGE_COLLECTION | Schedules GC when idle.|

### JSVM_PromiseRejectEvent

```c
enum JSVM_PromiseRejectEvent
```

**Description**

Enumerates reject events for a promise.

**Since**: 18

| Enum Item| Description|
| -- | -- |
| JSVM_PROMISE_REJECT_OTHER_REASONS = 0 | A promise is rejected, but the rejection reason is unknown or unclear.|
| JSVM_PROMISE_REJECT_WITH_NO_HANDLER = 1 | A promise is rejected but no handler is available.|
| JSVM_PROMISE_ADD_HANDLER_AFTER_REJECTED = 2 | A handler is added after a promise is rejected.|
| JSVM_PROMISE_REJECT_AFTER_RESOLVED = 3 | Attempts to reject a promise after this promise is resolved.|
| JSVM_PROMISE_RESOLVE_AFTER_RESOLVED = 4 | Attempts to resolve a promise after this promise is resolved.|

### JSVM_MessageErrorLevel

```c
enum JSVM_MessageErrorLevel
```

**Description**

Enumerates error message levels.

**Since**: 18

| Enum Item                                                                                                     | Description|
|----------------------------------------------------------------------------------------------------------| -- |
| JSVM_MESSAGE_LOG = (1 << 0)                                                                              | Logs.|
| JSVM_MESSAGE_DEBUG = (1 << 1)                                                                            | Debugging messages.|
| JSVM_MESSAGE_INFO = (1 << 2)                                                                             | Information.|
| JSVM_MESSAGE_ERROR = (1 << 3)                                                                            | Errors.|
| JSVM_MESSAGE_WARNING = (1 << 4)                                                                          | Warnings.|
| JSVM_MESSAGE_ALL = JSVM_MESSAGE_LOG \| JSVM_MESSAGE_DEBUG \| JSVM_MESSAGE_INFO \| JSVM_MESSAGE_ERROR \| JSVM_MESSAGE_WARNING | Information of all levels.|

### JSVM_DefineClassOptionsId

```c
enum JSVM_DefineClassOptionsId
```

**Description**

Enumerates definition modes for a class.

**Since**: 18

| Enum Item| Description|
| -- | -- |
| JSVM_DEFINE_CLASS_NORMAL | Defines a class in normal mode.|
| JSVM_DEFINE_CLASS_WITH_COUNT | Reserves a specified number of interfield slots for the created class. Native data can be stored in these slots.|
| JSVM_DEFINE_CLASS_WITH_PROPERTY_HANDLER | Sets a listener property for the created class and sets a callback to be invoked when it is called as a function.|

### JSVM_DebugOption

```c
enum JSVM_DebugOption
```

**Description**

Enumerates debugging options.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| JSVM_SCOPE_CHECK | Scope check.|


## Function Description

### JSVM_Finalize()

```c
typedef void (JSVM_CDECL* JSVM_Finalize)(JSVM_Env env,void* finalizeData,void* finalizeHint)
```

**Description**

Defines a pointer to the **JSVM_Finalize** function. It is passed in when a native object or data is associated with a JavaScript object, and is called when the associated JavaScript object is reclaimed by the GC to execute the native cleanup action.

**Since**: 11

### JSVM_OutputStream()

```c
typedef bool (JSVM_CDECL* JSVM_OutputStream)(const char* data,int size,void* streamData)
```

**Description**

Defines a pointer to the callback of the ASCII output stream. **data** indicates the pointer to the output data. **size** indicates the size of the output data. **void** is a null pointer that points to the end of the stream. **streamData** indicates the pointer passed to the API function together with the callback. The API function generates data to the output stream.

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the stream can continue to receive data; returns **false** if the stream is closed.|

### JSVM_HandlerForGC()

```c
typedef void (JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)
```

**Description**

Defines a pointer to the handler for GC callback.

**Since**: 18

### JSVM_HandlerForOOMError()

```c
typedef void (JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location,const char* detail,bool isHeapOOM)
```

**Description**

Defines a pointer to the handler for OOM-Error callback.

**Since**: 18

### JSVM_HandlerForFatalError()

```c
typedef void (JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location,const char* message)
```

**Description**

Defines a pointer to the handler for Fatal-Error callback.

**Since**: 18

### JSVM_HandlerForPromiseReject()

```c
typedef void (JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)
```

**Description**

Defines a pointer to the handler for Promise-Reject callback.

**Since**: 18
