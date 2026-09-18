# jsvm_types.h

## Overview

Provides the JSVM API type define.<br> Provides API to Provide independent, standard, and complete JavaScript engine capabilities for developers, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross language calls, and taking snapshots.

**Library**: libjsvm.so

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [JSVM_CallbackStruct](capi-jsvm-jsvm-callbackstruct.md) | JSVM_CallbackStruct | Callback function pointer and data for user-provided native function which are to exposed to js via JSVM-API. |
| [JSVM_HeapStatistics](capi-jsvm-jsvm-heapstatistics.md) | JSVM_HeapStatistics | Heap statisics. |
| [JSVM_InitOptions](capi-jsvm-jsvm-initoptions.md) | JSVM_InitOptions | Init the JavaScript VM with init option. |
| [JSVM_CreateVMOptions](capi-jsvm-jsvm-createvmoptions.md) | JSVM_CreateVMOptions | Create the JavaScript VM with init option. |
| [JSVM_VMInfo](capi-jsvm-jsvm-vminfo.md) | JSVM_VMInfo | JavaScript VM info. |
| [JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md) | JSVM_PropertyDescriptor | Property descriptor. |
| [JSVM_ExtendedErrorInfo](capi-jsvm-jsvm-extendederrorinfo.md) | JSVM_ExtendedErrorInfo | JSVM-API uses both return values and JavaScript exceptions for error handling |
| [JSVM_TypeTag](capi-jsvm-jsvm-typetag.md) | JSVM_TypeTag | A 128-bit value stored as two unsigned 64-bit integers. It serves as a UUID with which JavaScript objects or externals can be "tagged" in order to ensure that they are of a certain type. |
| [JSVM_PropertyHandlerConfigurationStruct](capi-jsvm-jsvm-propertyhandlerconfigurationstruct.md) | JSVM_PropertyHandlerConfigurationStruct | When the object's getter, setter, deleter, and enumerator operations are performed, the corresponding callback will be triggered. |
| [JSVM_ScriptOrigin](capi-jsvm-jsvm-scriptorigin.md) | JSVM_ScriptOrigin | Source code information. |
| [JSVM_CompileOptions](capi-jsvm-jsvm-compileoptions.md) | JSVM_CompileOptions | Compile Options |
| [JSVM_CodeCache](capi-jsvm-jsvm-codecache.md) | JSVM_CodeCache | code cache passed with JSVM_COMPILE_CODE_CACHE |
| [JSVM_DefineClassOptions](capi-jsvm-jsvm-defineclassoptions.md) | JSVM_DefineClassOptions | DefineClass options. |
| [JSVM_PropertyHandler](capi-jsvm-jsvm-propertyhandler.md) | JSVM_PropertyHandler | The property-handler used to define class. |
| [JSVM_VM\_\_*](capi-jsvm-jsvm-vm--8h.md) | JSVM_VM | To represent a JavaScript VM instance. |
| [JSVM_VMScope\_\_*](capi-jsvm-jsvm-vmscope--8h.md) | JSVM_VMScope | To represent a JavaScript VM scope. |
| [JSVM_EnvScope\_\_*](capi-jsvm-jsvm-envscope--8h.md) | JSVM_EnvScope | To represent a JavaScript VM environment scope. |
| [JSVM_Script\_\_*](capi-jsvm-jsvm-script--8h.md) | JSVM_Script | To represent a JavaScript code. |
| [JSVM_Env\_\_*](capi-jsvm-jsvm-env--8h.md) | JSVM_Env | To represent a JavaScript VM instance. |
| [JSVM_CpuProfiler\_\_*](capi-jsvm-jsvm-cpuprofiler--8h.md) | JSVM_CpuProfiler | To represent a JavaScript profiler. |
| [JSVM_Value\_\_*](capi-jsvm-jsvm-value--8h.md) | JSVM_Value | To represent a JavaScript VM environment. |
| [JSVM_Ref\_\_*](capi-jsvm-jsvm-ref--8h.md) | JSVM_Ref | To represent a JavaScript value references. |
| [JSVM_HandleScope\_\_*](capi-jsvm-jsvm-handlescope--8h.md) | JSVM_HandleScope | To represent a JavaScript VM handle scope. |
| [JSVM_EscapableHandleScope\_\_*](capi-jsvm-jsvm-escapablehandlescope--8h.md) | JSVM_EscapableHandleScope | To represent a JavaScript VM escapable handle scope. |
| [JSVM_CallbackInfo\_\_*](capi-jsvm-jsvm-callbackinfo--8h.md) | JSVM_CallbackInfo | To represent a JavaScript VM callback additional information. |
| [JSVM_Deferred\_\_*](capi-jsvm-jsvm-deferred--8h.md) | JSVM_Deferred | To represent a JavaScript VM value deferred. |
| [JSVM_Data\_\_*](capi-jsvm-jsvm-data--8h.md) | JSVM_Data | To represent a JavaScript Data type. |
| [JSVM_DeserializeResult\_\_*](capi-jsvm-jsvm-deserializeresult--8h.md) | JSVM_DeserializeResult | To represent a JavaScript background deserialize result. |
| [JSVM_CallbackStruct*](capi-jsvm-jsvm-callbackstruct8h.md) | JSVM_Callback | Function pointer type for user-provided native function which are to exposed to js via JSVM-API. |
| [JSVM_PropertyHandlerConfigurationStruct*](capi-jsvm-jsvm-propertyhandlerconfigurationstruct8h.md) | JSVM_PropertyHandlerCfg | The pointer type of the structure which contains the property handlers. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [JSVM_PropertyAttributes](#jsvm_propertyattributes) | JSVM_PropertyAttributes | JSVM_PropertyAttributes are flag used to control the behavior of properties set on a js object. |
| [JSVM_ValueType](#jsvm_valuetype) | JSVM_ValueType | Describes the type of a JSVM_Value. |
| [JSVM_TypedarrayType](#jsvm_typedarraytype) | JSVM_TypedarrayType | Describes the type of a typedarray. |
| [JSVM_Status](#jsvm_status) | JSVM_Status | Integral status code indicating the success or failure of a JSVM-API call. |
| [JSVM_KeyCollectionMode](#jsvm_keycollectionmode) | JSVM_KeyCollectionMode | limits the range of collected properties.. |
| [JSVM_KeyFilter](#jsvm_keyfilter) | JSVM_KeyFilter | Property filter bits. They can be or'ed to build a composite filter.. |
| [JSVM_KeyConversion](#jsvm_keyconversion) | JSVM_KeyConversion | key conversion select. |
| [JSVM_MemoryPressureLevel](#jsvm_memorypressurelevel) | JSVM_MemoryPressureLevel | Memory pressure level. |
| [JSVM_CompileMode](#jsvm_compilemode) | JSVM_CompileMode | Compile mode |
| [JSVM_CompileOptionId](#jsvm_compileoptionid) | JSVM_CompileOptionId | Compile option id |
| [JSVM_RegExpFlags](#jsvm_regexpflags) | JSVM_RegExpFlags | Regular expression flag bits. They can be or'ed to enable a set of flags. |
| [JSVM_InitializedFlag](#jsvm_initializedflag) | JSVM_InitializedFlag | initialization flag |
| [JSVM_WasmOptLevel](#jsvm_wasmoptlevel) | JSVM_WasmOptLevel | WebAssembly function optimization level |
| [JSVM_CacheType](#jsvm_cachetype) | JSVM_CacheType | Cache data type |
| [JSVM_MicrotaskPolicy](#jsvm_microtaskpolicy) | JSVM_MicrotaskPolicy | Microtask policies of JSVM. |
| [JSVM_TraceCategory](#jsvm_tracecategory) | JSVM_TraceCategory | Trace category for jsvm internal trace events. |
| [JSVM_PromiseRejectEvent](#jsvm_promiserejectevent) | JSVM_PromiseRejectEvent | The promise-reject event. |
| [JSVM_MessageErrorLevel](#jsvm_messageerrorlevel) | JSVM_MessageErrorLevel | The level of message error. |
| [JSVM_DefineClassOptionsId](#jsvm_defineclassoptionsid) | JSVM_DefineClassOptionsId | DefineClass options id. |
| [JSVM_CBTriggerTimeForGC](#jsvm_cbtriggertimeforgc) | JSVM_CBTriggerTimeForGC | The timing of GC callback trigger. |
| [JSVM_GCType](#jsvm_gctype) | JSVM_GCType | The GC type. |
| [JSVM_GCCallbackFlags](#jsvm_gccallbackflags) | JSVM_GCCallbackFlags | The GC callback flags. |
| [JSVM_DebugOption](#jsvm_debugoption) | JSVM_DebugOption | Debug options. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void(JSVM_CDECL* JSVM_Finalize)(JSVM_Env env, void* finalizeData, void* finalizeHint)](#jsvm_cdecl-jsvm_finalize) | JSVM_CDECL* JSVM_Finalize | Function pointer type for add-on provided function that allow the user to be notified. |
| [typedef void(JSVM_CDECL* JSVM_FinalizeArrayBuffer)(JSVM_Env env, void* finalizeData, void* finalizeHint, bool copied)](#jsvm_cdecl-jsvm_finalizearraybuffer) | JSVM_CDECL* JSVM_FinalizeArrayBuffer | Finalize callback for ArrayBuffers created from external memory.<br> Similar to JSVM_Finalize, but includes a copied parameter indicating whether the engine copied the external data into an internal buffer (true) or used zero-copy (false). When copied is true, the engine does not hold a reference to the original external data, so the caller may free it immediately after the API call returns. When copied is false, finalizeData points to the original external memory that the engine is releasing — the callback should free it. |
| [typedef bool(JSVM_CDECL* JSVM_OutputStream)(const char* data, int size, void* streamData)](#jsvm_cdecl-jsvm_outputstream) | JSVM_CDECL* JSVM_OutputStream | Function pointer type for callback of output stream. The first parameter data is the data pointer. And the second parameter size is the data size to output. A null data pointer indicates the end of the stream. The third parameter streamData is the pointer passed in together with the callback to the API functions that generate data to the output stream. The callback returns true to indicate the stream can continue to accept data. Otherwise, it will abort the stream. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location, const char* detail, bool isHeapOOM)](#jsvm_cdecl-jsvm_handlerforoomerror) | JSVM_CDECL* JSVM_HandlerForOOMError | Function pointer type of OOM-Error callback. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location, const char* message)](#jsvm_cdecl-jsvm_handlerforfatalerror) | JSVM_CDECL* JSVM_HandlerForFatalError | Function pointer type of Fatal-Error callback. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)](#jsvm_cdecl-jsvm_handlerforpromisereject) | JSVM_CDECL* JSVM_HandlerForPromiseReject | Function pointer type of Promise-Reject callback. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)](#jsvm_cdecl-jsvm_handlerforgc) | JSVM_CDECL* JSVM_HandlerForGC | Function pointer type of GC callback. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForHeapThreshold)(JSVM_VM vm, uint64_t threshold, void* data)](#jsvm_cdecl-jsvm_handlerforheapthreshold) | JSVM_CDECL* JSVM_HandlerForHeapThreshold | Function pointer type for heap threshold callback. |

### Variable

| Name | Description |
| -- | -- |
| int *profile | profile pointer. |
| size_t length | length. |
| JSVM_CompileProfile  |  |
| JSVM_CallbackStruct* JSVM_Callback | Function pointer type for user-provided native function which are to exposed to js via JSVM-API.<br>**Since**: 11 |
| void(JSVM_CDECL* JSVM_Finalize)(JSVM_Env env, void* finalizeData, void* finalizeHint) | Function pointer type for add-on provided function that allow the user to be notified.<br>**Since**: 11 |
| void(JSVM_CDECL* JSVM_FinalizeArrayBuffer)(JSVM_Env env, void* finalizeData, void* finalizeHint, bool copied) | Finalize callback for ArrayBuffers created from external memory.<br> Similar to JSVM_Finalize, but includes a copied parameter indicating whether the engine copied the external data into an internal buffer (true) or used zero-copy (false). When copied is true, the engine does not hold a reference to the original external data, so the caller may free it immediately after the API call returns. When copied is false, finalizeData points to the original external memory that the engine is releasing — the callback should free it.<br>**Since**: 26.0.0 |
| bool(JSVM_CDECL* JSVM_OutputStream)(const char* data, int size, void* streamData) | Function pointer type for callback of output stream. The first parameter data is the data pointer. And the second parameter size is the data size to output. A null data pointer indicates the end of the stream. The third parameter streamData is the pointer passed in together with the callback to the API functions that generate data to the output stream. The callback returns true to indicate the stream can continue to accept data. Otherwise, it will abort the stream.<br>**Since**: 12 |
| JSVM_PropertyHandlerConfigurationStruct* JSVM_PropertyHandlerCfg | The pointer type of the structure which contains the property handlers.<br>**Since**: 12 |
| const struct { /** profile pointer. */ int *profile | compile profile passed with JSVM_COMPILE_COMPILE_PROFILE<br>**Since**: 12 |
| void(JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location, const char* detail, bool isHeapOOM) | Function pointer type of OOM-Error callback.<br>**Since**: 18 |
| void(JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location, const char* message) | Function pointer type of Fatal-Error callback.<br>**Since**: 18 |
| void(JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo) | Function pointer type of Promise-Reject callback.<br>**Since**: 18 |
| void(JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data) | Function pointer type of GC callback.<br>**Since**: 18 |
| void(JSVM_CDECL* JSVM_HandlerForHeapThreshold)(JSVM_VM vm, uint64_t threshold, void* data) | Function pointer type for heap threshold callback.<br>**Since**: 26.0.0 |

## Enum type description

### JSVM_PropertyAttributes

```c
enum JSVM_PropertyAttributes
```

**Description**

JSVM_PropertyAttributes are flag used to control the behavior of properties set on a js object.

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_DEFAULT = 0 | No explicit attributes are set on the property. |
| JSVM_WRITABLE = 1 << 0 | The property is writable. |
| JSVM_ENUMERABLE = 1 << 1 | The property is enumeable. |
| JSVM_CONFIGURABLE = 1 << 2 | The property is configurable. |
| JSVM_NO_RECEIVER_CHECK = 1 << 3 | Used to mark the receiver of a native method need not be checked. If JSVM_NO_RECEIVER_CHECK is not set, the method only accept instance of the defined class as receiver, Otherwise Exception "Type Error: Illegal Ivocation" will be throw into JSVM. |
| JSVM_STATIC = 1 << 10 | Used with OH_JSVM_DefineClass to distinguish static properties from instance properties. |
| JSVM_DEFAULT_METHOD = JSVM_WRITABLE \| JSVM_CONFIGURABLE | Default for class methods. |
| JSVM_METHOD_NO_RECEIVER_CHECK = JSVM_DEFAULT_METHOD \| JSVM_NO_RECEIVER_CHECK | Class method with no receiver check |
| JSVM_DEFAULT_JSPROPERTY = JSVM_WRITABLE \| JSVM_ENUMERABLE \| JSVM_CONFIGURABLE | Default for object properties, like in JS obj[prop]. |
| JSVM_JSPROPERTY_NO_RECEIVER_CHECK = JSVM_DEFAULT_JSPROPERTY \| JSVM_NO_RECEIVER_CHECK | Object properties with no receiver check |

### JSVM_ValueType

```c
enum JSVM_ValueType
```

**Description**

Describes the type of a JSVM_Value.

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_UNDEFINED | undefined type. |
| JSVM_NULL | null type. |
| JSVM_BOOLEAN | boolean type. |
| JSVM_NUMBER | number type. |
| JSVM_STRING | string type. |
| JSVM_SYMBOL | symbol type. |
| JSVM_OBJECT | object type. |
| JSVM_FUNCTION | function type. |
| JSVM_EXTERNAL | external type. |
| JSVM_BIGINT | bigint type. |

### JSVM_TypedarrayType

```c
enum JSVM_TypedarrayType
```

**Description**

Describes the type of a typedarray.

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_INT8_ARRAY | int8 type. |
| JSVM_UINT8_ARRAY | uint8 type. |
| JSVM_UINT8_CLAMPED_ARRAY | uint8 clamped type. |
| JSVM_INT16_ARRAY | int16 type. |
| JSVM_UINT16_ARRAY | uint16 type. |
| JSVM_INT32_ARRAY | int32 type. |
| JSVM_UINT32_ARRAY | uint32 type. |
| JSVM_FLOAT32_ARRAY | float32 type. |
| JSVM_FLOAT64_ARRAY | float64 type. |
| JSVM_BIGINT64_ARRAY | bigint64 type. |
| JSVM_BIGUINT64_ARRAY | biguint64 type. |

### JSVM_Status

```c
enum JSVM_Status
```

**Description**

Integral status code indicating the success or failure of a JSVM-API call.

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_OK | success status. |
| JSVM_INVALID_ARG | invalidarg status. |
| JSVM_OBJECT_EXPECTED | object expected status. |
| JSVM_STRING_EXPECTED | string expected status. |
| JSVM_NAME_EXPECTED | name expected status. |
| JSVM_FUNCTION_EXPECTED | function expected status. |
| JSVM_NUMBER_EXPECTED | number expected status. |
| JSVM_BOOLEAN_EXPECTED | boolean expected status. |
| JSVM_ARRAY_EXPECTED | array expected status. |
| JSVM_GENERIC_FAILURE | generic failure status. |
| JSVM_PENDING_EXCEPTION | pending exception status. |
| JSVM_CANCELLED | cancelled status. |
| JSVM_ESCAPE_CALLED_TWICE | escape called twice status. |
| JSVM_HANDLE_SCOPE_MISMATCH | handle scope mismatch status. |
| JSVM_CALLBACK_SCOPE_MISMATCH | callback scope mismatch status. |
| JSVM_QUEUE_FULL | queue full status. |
| JSVM_CLOSING | closing status. |
| JSVM_BIGINT_EXPECTED | bigint expected status. |
| JSVM_DATE_EXPECTED | date expected status. |
| JSVM_ARRAYBUFFER_EXPECTED | arraybuffer expected status. |
| JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED | detachable arraybuffer expected status. |
| JSVM_WOULD_DEADLOCK | would deadlock status. |
| JSVM_NO_EXTERNAL_BUFFERS_ALLOWED | no external buffers allowed status. |
| JSVM_CANNOT_RUN_JS | cannot run +js status. |
| JSVM_INVALID_TYPE |  |
| JSVM_JIT_MODE_EXPECTED |  |

### JSVM_KeyCollectionMode

```c
enum JSVM_KeyCollectionMode
```

**Description**

limits the range of collected properties..

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_KEY_INCLUDE_PROTOTYPES | will include all keys of the objects's prototype chain as well. |
| JSVM_KEY_OWN_ONLY | limits the collected properties to the given object only. |

### JSVM_KeyFilter

```c
enum JSVM_KeyFilter
```

**Description**

Property filter bits. They can be or'ed to build a composite filter..

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_KEY_ALL_PROPERTIES = 0 | key all properties. |
| JSVM_KEY_WRITABLE = 1 | key writable. |
| JSVM_KEY_ENUMERABLE = 1 << 1 | key enumerable. |
| JSVM_KEY_CONFIGURABLE = 1 << 2 | key configurable. |
| JSVM_KEY_SKIP_STRINGS = 1 << 3 | key skip strings. |
| JSVM_KEY_SKIP_SYMBOLS = 1 << 4 | key skip symbols. |

### JSVM_KeyConversion

```c
enum JSVM_KeyConversion
```

**Description**

key conversion select.

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_KEY_KEEP_NUMBERS | will return numbers for integer indices. |
| JSVM_KEY_NUMBERS_TO_STRINGS | will convert integer indices to strings. |

### JSVM_MemoryPressureLevel

```c
enum JSVM_MemoryPressureLevel
```

**Description**

Memory pressure level.

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_MEMORY_PRESSURE_LEVEL_NONE | none pressure. |
| JSVM_MEMORY_PRESSURE_LEVEL_MODERATE | moderate pressure. |
| JSVM_MEMORY_PRESSURE_LEVEL_CRITICAL | critical pressure. |
| JSVM_MEMORY_PRESSURE_LEVEL_LOW_MEMORY |  |

### JSVM_CompileMode

```c
enum JSVM_CompileMode
```

**Description**

Compile mode

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_COMPILE_MODE_DEFAULT | default mode. |
| JSVM_COMPILE_MODE_CONSUME_CODE_CACHE | consume code cache. |
| JSVM_COMPILE_MODE_EAGER_COMPILE | apply eager compile. |
| JSVM_COMPILE_MODE_PRODUCE_COMPILE_PROFILE | preset for compile profile. |
| JSVM_COMPILE_MODE_CONSUME_COMPILE_PROFILE | consume compile profile. |

### JSVM_CompileOptionId

```c
enum JSVM_CompileOptionId
```

**Description**

Compile option id

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_COMPILE_MODE | compile mode. |
| JSVM_COMPILE_CODE_CACHE | code cache content. |
| JSVM_COMPILE_SCRIPT_ORIGIN | script origin. |
| JSVM_COMPILE_COMPILE_PROFILE | compile profile content. |
| JSVM_COMPILE_ENABLE_SOURCE_MAP | switch for source map support. |
| JSVM_COMPILE_BACKGROUND_DESERIALIZE_RESULT |  |
| JSVM_COMPILE_CODE_CACHE_REJECTED |  |

### JSVM_RegExpFlags

```c
enum JSVM_RegExpFlags
```

**Description**

Regular expression flag bits. They can be or'ed to enable a set of flags.

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_REGEXP_NONE = 0 | None mode. |
| JSVM_REGEXP_GLOBAL = 1 << 0 | Global mode. |
| JSVM_REGEXP_IGNORE_CASE = 1 << 1 | Ignore Case mode. |
| JSVM_REGEXP_MULTILINE = 1 << 2 | Multiline mode. |
| JSVM_REGEXP_STICKY = 1 << 3 | Sticky mode. |
| JSVM_REGEXP_UNICODE = 1 << 4 | Unicode mode. |
| JSVM_REGEXP_DOT_ALL = 1 << 5 | dotAll mode. |
| JSVM_REGEXP_LINEAR = 1 << 6 | Linear mode. |
| JSVM_REGEXP_HAS_INDICES = 1 << 7 | Has Indices mode. |
| JSVM_REGEXP_UNICODE_SETS = 1 << 8 | Unicode Sets mode. |

### JSVM_InitializedFlag

```c
enum JSVM_InitializedFlag
```

**Description**

initialization flag

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_ZERO_INITIALIZED | initialize with zero. |
| JSVM_UNINITIALIZED | leave uninitialized. |

### JSVM_WasmOptLevel

```c
enum JSVM_WasmOptLevel
```

**Description**

WebAssembly function optimization level

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_WASM_OPT_BASELINE = 10 | baseline optimization level. |
| JSVM_WASM_OPT_HIGH = 20 | high optimization level. |

### JSVM_CacheType

```c
enum JSVM_CacheType
```

**Description**

Cache data type

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_CACHE_TYPE_JS | js code cache, generated by OH_JSVM_CreateCodeCache |
| JSVM_CACHE_TYPE_WASM | WebAssembly cache, generated by OH_JSVM_CreateWasmCache |

### JSVM_MicrotaskPolicy

```c
enum JSVM_MicrotaskPolicy
```

**Description**

Microtask policies of JSVM.

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_MICROTASK_EXPLICIT = 0 | Microtasks are invoked with the OH_JSVM_PerformMicrotaskCheckpoint() method. |
| JSVM_MICROTASK_AUTO | Microtasks are invoked when the script call depth decrements to zero. Default mode. |

### JSVM_TraceCategory

```c
enum JSVM_TraceCategory
```

**Description**

Trace category for jsvm internal trace events.

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_TRACE_VM | Tracing main interface invoking of JSVM, such as run scripts. |
| JSVM_TRACE_COMPILE | Tracing interface invoking about compilation, such as CompileCodeBackground. |
| JSVM_TRACE_EXECUTE | Tracing interface invoking about execution status, such as Interrupts and Microtasks. |
| JSVM_TRACE_RUNTIME | Tracing external callback |
| JSVM_TRACE_STACK_TRACE | Tracing stack trace in JSVM. |
| JSVM_TRACE_WASM | Tracing Main interface invoking of WASM, such as Compile Wasm Module and Instantiate. |
| JSVM_TRACE_WASM_DETAILED | Tracing more detailed interface invoking of WASM, such as background compilation and wrappers. |

### JSVM_PromiseRejectEvent

```c
enum JSVM_PromiseRejectEvent
```

**Description**

The promise-reject event.

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_PROMISE_REJECT_OTHER_REASONS = 0 | Promise is rejected for other reasons. |
| JSVM_PROMISE_REJECT_WITH_NO_HANDLER = 1 | Promise rejected with no handler. |
| JSVM_PROMISE_ADD_HANDLER_AFTER_REJECTED = 2 | Add the handler after Promise has been rejected. |
| JSVM_PROMISE_REJECT_AFTER_RESOLVED = 3 | After the Promise has been resolved, try to reject the Promise again. |
| JSVM_PROMISE_RESOLVE_AFTER_RESOLVED = 4 | After the Promise has been resolved, try resolving the Promise again. |

### JSVM_MessageErrorLevel

```c
enum JSVM_MessageErrorLevel
```

**Description**

The level of message error.

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_MESSAGE_LOG = (1 << 0) | Log level message. |
| JSVM_MESSAGE_DEBUG = (1 << 1) | Debug level message. |
| JSVM_MESSAGE_INFO = (1 << 2) | Info level message. |
| JSVM_MESSAGE_ERROR = (1 << 3) | Error level message. |
| JSVM_MESSAGE_WARNING = (1 << 4) | Warning level message. |
| JSVM_MESSAGE_ALL = JSVM_MESSAGE_LOG \| JSVM_MESSAGE_DEBUG \| JSVM_MESSAGE_INFO \| JSVM_MESSAGE_ERROR \| | All level message. |

### JSVM_DefineClassOptionsId

```c
enum JSVM_DefineClassOptionsId
```

**Description**

DefineClass options id.

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_DEFINE_CLASS_NORMAL | Defining a class in normal mode. |
| JSVM_DEFINE_CLASS_WITH_COUNT | Defining a class with count. |
| JSVM_DEFINE_CLASS_WITH_PROPERTY_HANDLER | Defining a class with property handler. |

### JSVM_CBTriggerTimeForGC

```c
enum JSVM_CBTriggerTimeForGC
```

**Description**

The timing of GC callback trigger.

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_CB_TRIGGER_BEFORE_GC | Trigger GC callback before GC. |
| JSVM_CB_TRIGGER_AFTER_GC | Trigger GC callback after GC. |

### JSVM_GCType

```c
enum JSVM_GCType
```

**Description**

The GC type.

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_GC_TYPE_SCAVENGE = 1 << 0 | The GC algorithm is Scavenge. |
| JSVM_GC_TYPE_MINOR_MARK_COMPACT = 1 << 1 | The GC algorithm is Minor-Mark-Compact. |
| JSVM_GC_TYPE_MARK_SWEEP_COMPACT = 1 << 2 | The GC algorithm is Mark-Sweep-Compact. |
| JSVM_GC_TYPE_INCREMENTAL_MARKING = 1 << 3 | The GC algorithm is Incremental-Marking. |
| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS = 1 << 4 | The GC algorithm is Weak-Callbacks. |
| JSVM_GC_TYPE_ALL = JSVM_GC_TYPE_SCAVENGE \| JSVM_GC_TYPE_MINOR_MARK_COMPACT \| | All GC algorithm. |

### JSVM_GCCallbackFlags

```c
enum JSVM_GCCallbackFlags
```

**Description**

The GC callback flags.

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_NO_GC_CALLBACK_FLAGS | No GC callback falgs. |
| JSVM_GC_CALLBACK_CONSTRUCT_RETAINED_OBJECT_INFOS | Reserved object information will be built in the garbage collection callback. |
| JSVM_GC_CALLBACK_FORCED | Enforce Garbage Collection Callback. |
| JSVM_GC_CALLBACK_SYNCHRONOUS_PHANTOM_CALLBACK_PROCESSING | Synchronous phantom callback processing. |
| JSVM_GC_CALLBACK_COLLECT_ALL_AVAILABLE_GARBAGE | All available garbage objects are collected during garbage collection. |
| JSVM_GC_CALLBACK_COLLECT_ALL_EXTERNAL_MEMORY | Garbage collection collects all external memory. |
| JSVM_GC_CALLBACK_SCHEDULE_IDLE_GARBAGE_COLLECTION | Schedule Garbage Collection at Idle Time. |

### JSVM_DebugOption

```c
enum JSVM_DebugOption
```

**Description**

Debug options.

**Since**: 20

| Enum item | Description |
| -- | -- |
| JSVM_SCOPE_CHECK | Scope check. |


## Function description

### JSVM_CDECL* JSVM_Finalize()

```c
typedef void(JSVM_CDECL* JSVM_Finalize)(JSVM_Env env, void* finalizeData, void* finalizeHint)
```

**Description**

Function pointer type for add-on provided function that allow the user to be notified.

**Since**: 11

### JSVM_CDECL* JSVM_FinalizeArrayBuffer()

```c
typedef void(JSVM_CDECL* JSVM_FinalizeArrayBuffer)(JSVM_Env env, void* finalizeData, void* finalizeHint, bool copied)
```

**Description**

Finalize callback for ArrayBuffers created from external memory.<br> Similar to JSVM_Finalize, but includes a copied parameter indicating whether the engine copied the external data into an internal buffer (true) or used zero-copy (false). When copied is true, the engine does not hold a reference to the original external data, so the caller may free it immediately after the API call returns. When copied is false, finalizeData points to the original external memory that the engine is releasing — the callback should free it.

**Since**: 26.0.0

### JSVM_CDECL* JSVM_OutputStream()

```c
typedef bool(JSVM_CDECL* JSVM_OutputStream)(const char* data, int size, void* streamData)
```

**Description**

Function pointer type for callback of output stream. The first parameter data is the data pointer. And the second parameter size is the data size to output. A null data pointer indicates the end of the stream. The third parameter streamData is the pointer passed in together with the callback to the API functions that generate data to the output stream. The callback returns true to indicate the stream can continue to accept data. Otherwise, it will abort the stream.

**Since**: 12

### JSVM_CDECL* JSVM_HandlerForOOMError()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location, const char* detail, bool isHeapOOM)
```

**Description**

Function pointer type of OOM-Error callback.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char\* location | The location information of the OOM error. |
| const char\* detail | The detail of the OOM error. |
| bool isHeapOOM | Determine whether the OOM type is Heap OOM. |

### JSVM_CDECL* JSVM_HandlerForFatalError()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location, const char* message)
```

**Description**

Function pointer type of Fatal-Error callback.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char\* location | The location information of the Fatal error. |
| const char\* message | The message of the Fatal error. |

### JSVM_CDECL* JSVM_HandlerForPromiseReject()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)
```

**Description**

Function pointer type of Promise-Reject callback.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | The environment that the function is invoked under. |
| [JSVM_PromiseRejectEvent](capi-jsvm-types-h.md#jsvm_promiserejectevent) rejectEvent | The promise-reject event. |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rejectInfo | An JS-object containing two properties: 'promise' and 'value'. The 'promise' represents a reference to the Promise object that was rejected. The 'value' represents the rejection reason associated with that promise. |

### JSVM_CDECL* JSVM_HandlerForGC()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)
```

**Description**

Function pointer type of GC callback.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | The VM instance that the JSVM-API call is invoked under. |
| [JSVM_GCType](capi-jsvm-types-h.md#jsvm_gctype) gcType | The gc type. |
| [JSVM_GCCallbackFlags](capi-jsvm-types-h.md#jsvm_gccallbackflags) flags | The GC callback flags. |
| void\* data | The native pointer data. |

### JSVM_CDECL* JSVM_HandlerForHeapThreshold()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForHeapThreshold)(JSVM_VM vm, uint64_t threshold, void* data)
```

**Description**

Function pointer type for heap threshold callback.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | The VM instance whose heap usage is observed at or above the threshold. |
| uint64_t threshold | The heap usage threshold in bytes. |
| void\* data | The native pointer data. |


