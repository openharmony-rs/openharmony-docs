# jsvm_types.h

## Overview

Provides the JSVM API type define.<br> Provides API to Provide independent, standard, and complete JavaScript engine capabilities for developers, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross language calls, and taking snapshots.

**Library**: libjsvm.so

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-arkts-jsvm.md)

## Summary

### Structs

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
| [JSVM_CompileProfile](capi-jsvm-jsvm-compileprofile.md) | JSVM_CompileProfile | compile profile passed with JSVM_COMPILE_COMPILE_PROFILE |
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
| [JSVM_BackingStore\_\_*](capi-jsvm-jsvm-backingstore--8h.md) | JSVM_BackingStore | To represent a SharedArrayBuffer BackingStore, which can be shared across multiple VM environments. |
| [JSVM_DeserializeResult\_\_*](capi-jsvm-jsvm-deserializeresult--8h.md) | JSVM_DeserializeResult | To represent a JavaScript background deserialize result. |
| [JSVM_CallbackStruct*](capi-jsvm-jsvm-callbackstruct8h.md) | JSVM_Callback | Function pointer type for user-provided native function which are to exposed to js via JSVM-API. |
| [JSVM_PropertyHandlerConfigurationStruct*](capi-jsvm-jsvm-propertyhandlerconfigurationstruct8h.md) | JSVM_PropertyHandlerCfg | The pointer type of the structure which contains the property handlers. |

### Enums

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

### Functions

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void(JSVM_CDECL* JSVM_Finalize)(JSVM_Env env, void* finalizeData, void* finalizeHint)](#jsvm_finalize) | JSVM_Finalize | Function pointer type for add-on provided function that allow the user to be notified. |
| [typedef void(JSVM_CDECL* JSVM_FinalizeArrayBuffer)(JSVM_Env env, void* finalizeData, void* finalizeHint, bool copied)](#jsvm_finalizearraybuffer) | JSVM_FinalizeArrayBuffer | Finalize callback for ArrayBuffers created from external memory.<br> Similar to JSVM_Finalize, but includes a copied parameter indicating whether the engine copied the external data into an internal buffer (true) or used zero-copy (false). When copied is true, the engine does not hold a reference to the original external data, so the caller may free it immediately after the API call returns. When copied is false, finalizeData points to the original external memory that the engine is releasing — the callback should free it. |
| [typedef bool(JSVM_CDECL* JSVM_OutputStream)(const char* data, int size, void* streamData)](#jsvm_outputstream) | JSVM_OutputStream | Function pointer type for callback of output stream. The first parameter data is the data pointer. And the second parameter size is the data size to output. A null data pointer indicates the end of the stream. The third parameter streamData is the pointer passed in together with the callback to the API functions that generate data to the output stream. The callback returns true to indicate the stream can continue to accept data. Otherwise, it will abort the stream. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location, const char* detail, bool isHeapOOM)](#jsvm_handlerforoomerror) | JSVM_HandlerForOOMError | Function pointer type of OOM-Error callback. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location, const char* message)](#jsvm_handlerforfatalerror) | JSVM_HandlerForFatalError | Function pointer type of Fatal-Error callback. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)](#jsvm_handlerforpromisereject) | JSVM_HandlerForPromiseReject | Function pointer type of Promise-Reject callback. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)](#jsvm_handlerforgc) | JSVM_HandlerForGC | Function pointer type of GC callback. |
| [typedef void(JSVM_CDECL* JSVM_HandlerForHeapThreshold)(JSVM_VM vm, uint64_t threshold, void* data)](#jsvm_handlerforheapthreshold) | JSVM_HandlerForHeapThreshold | Function pointer type for heap threshold callback. |

### Variables

| Name | Description |
| -- | -- |
| JSVM_CallbackStruct* JSVM_Callback | Function pointer type for user-provided native function which are to exposed to js via JSVM-API.<br>**Since**: 11<br>**System capability**: SystemCapability.ArkCompiler.JSVM<br><!--Device-JSVM_CallbackStruct* JSVM_Callback--><!--Device-JSVM_CallbackStruct* JSVM_Callback-End--> |
| JSVM_PropertyHandlerConfigurationStruct* JSVM_PropertyHandlerCfg | The pointer type of the structure which contains the property handlers.<br>**Since**: 12<br>**System capability**: SystemCapability.ArkCompiler.JSVM<br><!--Device-JSVM_PropertyHandlerConfigurationStruct* JSVM_PropertyHandlerCfg--><!--Device-JSVM_PropertyHandlerConfigurationStruct* JSVM_PropertyHandlerCfg-End--> |
| typedef uint16_t char16_t | Provides the JSVM API type define.<br> Provides API to Provide independent, standard, and complete JavaScript engine capabilities for developers, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross language calls, and taking snapshots.<br>**Since**: 11 /#define ARK_RUNTIME_JSVM_JSVM_TYPE_H#include <stddef.h>  // NOLINT(modernize-deprecated-headers)#include <stdint.h>  // NOLINT(modernize-deprecated-headers)#include <stdbool.h>  // NOLINT(modernize-deprecated-headers)<br>**System capability**: SystemCapability.ArkCompiler.JSVM<br><!--Device-typedef uint16_t char16_t--><!--Device-typedef uint16_t char16_t-End--> |

## Enum type description

### JSVM_PropertyAttributes

```c
enum JSVM_PropertyAttributes
```

**Description**

JSVM_PropertyAttributes are flag used to control the behavior of properties set on a js object.

<!--Device-enum JSVM_PropertyAttributes--><!--Device-enum JSVM_PropertyAttributes-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_DEFAULT = 0 | No explicit attributes are set on the property.<br><!--Device-JSVM_DEFAULT = 0--><!--Device-JSVM_DEFAULT = 0-End--> |
| JSVM_WRITABLE = 1 << 0 | The property is writable.<br><!--Device-JSVM_WRITABLE = 1 << 0--><!--Device-JSVM_WRITABLE = 1 << 0-End--> |
| JSVM_ENUMERABLE = 1 << 1 | The property is enumeable.<br><!--Device-JSVM_ENUMERABLE = 1 << 1--><!--Device-JSVM_ENUMERABLE = 1 << 1-End--> |
| JSVM_CONFIGURABLE = 1 << 2 | The property is configurable.<br><!--Device-JSVM_CONFIGURABLE = 1 << 2--><!--Device-JSVM_CONFIGURABLE = 1 << 2-End--> |
| JSVM_NO_RECEIVER_CHECK = 1 << 3 | Used to mark the receiver of a native method need not be checked. If JSVM_NO_RECEIVER_CHECK is not set, the method only accept instance of the defined class as receiver, Otherwise Exception "Type Error: Illegal Ivocation" will be throw into JSVM.<br><!--Device-JSVM_NO_RECEIVER_CHECK = 1 << 3--><!--Device-JSVM_NO_RECEIVER_CHECK = 1 << 3-End--> |
| JSVM_STATIC = 1 << 10 | Used with OH_JSVM_DefineClass to distinguish static properties from instance properties.<br><!--Device-JSVM_STATIC = 1 << 10--><!--Device-JSVM_STATIC = 1 << 10-End--> |
| JSVM_DEFAULT_METHOD = JSVM_WRITABLE \| JSVM_CONFIGURABLE | Default for class methods.<br><!--Device-JSVM_DEFAULT_METHOD = JSVM_WRITABLE \| JSVM_CONFIGURABLE--><!--Device-JSVM_DEFAULT_METHOD = JSVM_WRITABLE \| JSVM_CONFIGURABLE-End--> |
| JSVM_METHOD_NO_RECEIVER_CHECK = JSVM_DEFAULT_METHOD \| JSVM_NO_RECEIVER_CHECK | Class method with no receiver check<br><!--Device-JSVM_METHOD_NO_RECEIVER_CHECK = JSVM_DEFAULT_METHOD \| JSVM_NO_RECEIVER_CHECK--><!--Device-JSVM_METHOD_NO_RECEIVER_CHECK = JSVM_DEFAULT_METHOD \| JSVM_NO_RECEIVER_CHECK-End--> |
| JSVM_DEFAULT_JSPROPERTY = JSVM_WRITABLE \| JSVM_ENUMERABLE \| JSVM_CONFIGURABLE | Default for object properties, like in JS obj[prop].<br><!--Device-JSVM_DEFAULT_JSPROPERTY = JSVM_WRITABLE \| JSVM_ENUMERABLE \| JSVM_CONFIGURABLE--><!--Device-JSVM_DEFAULT_JSPROPERTY = JSVM_WRITABLE \| JSVM_ENUMERABLE \| JSVM_CONFIGURABLE-End--> |
| JSVM_JSPROPERTY_NO_RECEIVER_CHECK = JSVM_DEFAULT_JSPROPERTY \| JSVM_NO_RECEIVER_CHECK | Object properties with no receiver check<br><!--Device-JSVM_JSPROPERTY_NO_RECEIVER_CHECK = JSVM_DEFAULT_JSPROPERTY \| JSVM_NO_RECEIVER_CHECK--><!--Device-JSVM_JSPROPERTY_NO_RECEIVER_CHECK = JSVM_DEFAULT_JSPROPERTY \| JSVM_NO_RECEIVER_CHECK-End--> |

### JSVM_ValueType

```c
enum JSVM_ValueType
```

**Description**

Describes the type of a JSVM_Value.

<!--Device-enum JSVM_ValueType--><!--Device-enum JSVM_ValueType-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_UNDEFINED | undefined type.<br><!--Device-JSVM_UNDEFINED--><!--Device-JSVM_UNDEFINED-End--> |
| JSVM_NULL | null type.<br><!--Device-JSVM_NULL--><!--Device-JSVM_NULL-End--> |
| JSVM_BOOLEAN | boolean type.<br><!--Device-JSVM_BOOLEAN--><!--Device-JSVM_BOOLEAN-End--> |
| JSVM_NUMBER | number type.<br><!--Device-JSVM_NUMBER--><!--Device-JSVM_NUMBER-End--> |
| JSVM_STRING | string type.<br><!--Device-JSVM_STRING--><!--Device-JSVM_STRING-End--> |
| JSVM_SYMBOL | symbol type.<br><!--Device-JSVM_SYMBOL--><!--Device-JSVM_SYMBOL-End--> |
| JSVM_OBJECT | object type.<br><!--Device-JSVM_OBJECT--><!--Device-JSVM_OBJECT-End--> |
| JSVM_FUNCTION | function type.<br><!--Device-JSVM_FUNCTION--><!--Device-JSVM_FUNCTION-End--> |
| JSVM_EXTERNAL | external type.<br><!--Device-JSVM_EXTERNAL--><!--Device-JSVM_EXTERNAL-End--> |
| JSVM_BIGINT | bigint type.<br><!--Device-JSVM_BIGINT--><!--Device-JSVM_BIGINT-End--> |

### JSVM_TypedarrayType

```c
enum JSVM_TypedarrayType
```

**Description**

Describes the type of a typedarray.

<!--Device-enum JSVM_TypedarrayType--><!--Device-enum JSVM_TypedarrayType-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_INT8_ARRAY | int8 type.<br><!--Device-JSVM_INT8_ARRAY--><!--Device-JSVM_INT8_ARRAY-End--> |
| JSVM_UINT8_ARRAY | uint8 type.<br><!--Device-JSVM_UINT8_ARRAY--><!--Device-JSVM_UINT8_ARRAY-End--> |
| JSVM_UINT8_CLAMPED_ARRAY | uint8 clamped type.<br><!--Device-JSVM_UINT8_CLAMPED_ARRAY--><!--Device-JSVM_UINT8_CLAMPED_ARRAY-End--> |
| JSVM_INT16_ARRAY | int16 type.<br><!--Device-JSVM_INT16_ARRAY--><!--Device-JSVM_INT16_ARRAY-End--> |
| JSVM_UINT16_ARRAY | uint16 type.<br><!--Device-JSVM_UINT16_ARRAY--><!--Device-JSVM_UINT16_ARRAY-End--> |
| JSVM_INT32_ARRAY | int32 type.<br><!--Device-JSVM_INT32_ARRAY--><!--Device-JSVM_INT32_ARRAY-End--> |
| JSVM_UINT32_ARRAY | uint32 type.<br><!--Device-JSVM_UINT32_ARRAY--><!--Device-JSVM_UINT32_ARRAY-End--> |
| JSVM_FLOAT32_ARRAY | float32 type.<br><!--Device-JSVM_FLOAT32_ARRAY--><!--Device-JSVM_FLOAT32_ARRAY-End--> |
| JSVM_FLOAT64_ARRAY | float64 type.<br><!--Device-JSVM_FLOAT64_ARRAY--><!--Device-JSVM_FLOAT64_ARRAY-End--> |
| JSVM_BIGINT64_ARRAY | bigint64 type.<br><!--Device-JSVM_BIGINT64_ARRAY--><!--Device-JSVM_BIGINT64_ARRAY-End--> |
| JSVM_BIGUINT64_ARRAY | biguint64 type.<br><!--Device-JSVM_BIGUINT64_ARRAY--><!--Device-JSVM_BIGUINT64_ARRAY-End--> |

### JSVM_Status

```c
enum JSVM_Status
```

**Description**

Integral status code indicating the success or failure of a JSVM-API call.

<!--Device-enum JSVM_Status--><!--Device-enum JSVM_Status-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_OK | success status.<br><!--Device-JSVM_OK--><!--Device-JSVM_OK-End--> |
| JSVM_INVALID_ARG | invalidarg status.<br><!--Device-JSVM_INVALID_ARG--><!--Device-JSVM_INVALID_ARG-End--> |
| JSVM_OBJECT_EXPECTED | object expected status.<br><!--Device-JSVM_OBJECT_EXPECTED--><!--Device-JSVM_OBJECT_EXPECTED-End--> |
| JSVM_STRING_EXPECTED | string expected status.<br><!--Device-JSVM_STRING_EXPECTED--><!--Device-JSVM_STRING_EXPECTED-End--> |
| JSVM_NAME_EXPECTED | name expected status.<br><!--Device-JSVM_NAME_EXPECTED--><!--Device-JSVM_NAME_EXPECTED-End--> |
| JSVM_FUNCTION_EXPECTED | function expected status.<br><!--Device-JSVM_FUNCTION_EXPECTED--><!--Device-JSVM_FUNCTION_EXPECTED-End--> |
| JSVM_NUMBER_EXPECTED | number expected status.<br><!--Device-JSVM_NUMBER_EXPECTED--><!--Device-JSVM_NUMBER_EXPECTED-End--> |
| JSVM_BOOLEAN_EXPECTED | boolean expected status.<br><!--Device-JSVM_BOOLEAN_EXPECTED--><!--Device-JSVM_BOOLEAN_EXPECTED-End--> |
| JSVM_ARRAY_EXPECTED | array expected status.<br><!--Device-JSVM_ARRAY_EXPECTED--><!--Device-JSVM_ARRAY_EXPECTED-End--> |
| JSVM_GENERIC_FAILURE | generic failure status.<br><!--Device-JSVM_GENERIC_FAILURE--><!--Device-JSVM_GENERIC_FAILURE-End--> |
| JSVM_PENDING_EXCEPTION | pending exception status.<br><!--Device-JSVM_PENDING_EXCEPTION--><!--Device-JSVM_PENDING_EXCEPTION-End--> |
| JSVM_CANCELLED | cancelled status.<br><!--Device-JSVM_CANCELLED--><!--Device-JSVM_CANCELLED-End--> |
| JSVM_ESCAPE_CALLED_TWICE | escape called twice status.<br><!--Device-JSVM_ESCAPE_CALLED_TWICE--><!--Device-JSVM_ESCAPE_CALLED_TWICE-End--> |
| JSVM_HANDLE_SCOPE_MISMATCH | handle scope mismatch status.<br><!--Device-JSVM_HANDLE_SCOPE_MISMATCH--><!--Device-JSVM_HANDLE_SCOPE_MISMATCH-End--> |
| JSVM_CALLBACK_SCOPE_MISMATCH | callback scope mismatch status.<br><!--Device-JSVM_CALLBACK_SCOPE_MISMATCH--><!--Device-JSVM_CALLBACK_SCOPE_MISMATCH-End--> |
| JSVM_QUEUE_FULL | queue full status.<br><!--Device-JSVM_QUEUE_FULL--><!--Device-JSVM_QUEUE_FULL-End--> |
| JSVM_CLOSING | closing status.<br><!--Device-JSVM_CLOSING--><!--Device-JSVM_CLOSING-End--> |
| JSVM_BIGINT_EXPECTED | bigint expected status.<br><!--Device-JSVM_BIGINT_EXPECTED--><!--Device-JSVM_BIGINT_EXPECTED-End--> |
| JSVM_DATE_EXPECTED | date expected status.<br><!--Device-JSVM_DATE_EXPECTED--><!--Device-JSVM_DATE_EXPECTED-End--> |
| JSVM_ARRAYBUFFER_EXPECTED | arraybuffer expected status.<br><!--Device-JSVM_ARRAYBUFFER_EXPECTED--><!--Device-JSVM_ARRAYBUFFER_EXPECTED-End--> |
| JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED | detachable arraybuffer expected status.<br><!--Device-JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED--><!--Device-JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED-End--> |
| JSVM_WOULD_DEADLOCK | would deadlock status.<br><!--Device-JSVM_WOULD_DEADLOCK--><!--Device-JSVM_WOULD_DEADLOCK-End--> |
| JSVM_NO_EXTERNAL_BUFFERS_ALLOWED | no external buffers allowed status.<br><!--Device-JSVM_NO_EXTERNAL_BUFFERS_ALLOWED--><!--Device-JSVM_NO_EXTERNAL_BUFFERS_ALLOWED-End--> |
| JSVM_CANNOT_RUN_JS | cannot run +js status.<br><!--Device-JSVM_CANNOT_RUN_JS--><!--Device-JSVM_CANNOT_RUN_JS-End--> |
| JSVM_INVALID_TYPE | invalid input type status.<br>**Since**: 18<br><!--Device-JSVM_INVALID_TYPE--><!--Device-JSVM_INVALID_TYPE-End--> |
| JSVM_JIT_MODE_EXPECTED | jit mode expected status.<br>**Since**: 18<br><!--Device-JSVM_JIT_MODE_EXPECTED--><!--Device-JSVM_JIT_MODE_EXPECTED-End--> |

### JSVM_KeyCollectionMode

```c
enum JSVM_KeyCollectionMode
```

**Description**

limits the range of collected properties..

<!--Device-enum JSVM_KeyCollectionMode--><!--Device-enum JSVM_KeyCollectionMode-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_KEY_INCLUDE_PROTOTYPES | will include all keys of the objects's prototype chain as well.<br><!--Device-JSVM_KEY_INCLUDE_PROTOTYPES--><!--Device-JSVM_KEY_INCLUDE_PROTOTYPES-End--> |
| JSVM_KEY_OWN_ONLY | limits the collected properties to the given object only.<br><!--Device-JSVM_KEY_OWN_ONLY--><!--Device-JSVM_KEY_OWN_ONLY-End--> |

### JSVM_KeyFilter

```c
enum JSVM_KeyFilter
```

**Description**

Property filter bits. They can be or'ed to build a composite filter..

<!--Device-enum JSVM_KeyFilter--><!--Device-enum JSVM_KeyFilter-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_KEY_ALL_PROPERTIES = 0 | key all properties.<br><!--Device-JSVM_KEY_ALL_PROPERTIES = 0--><!--Device-JSVM_KEY_ALL_PROPERTIES = 0-End--> |
| JSVM_KEY_WRITABLE = 1 | key writable.<br><!--Device-JSVM_KEY_WRITABLE = 1--><!--Device-JSVM_KEY_WRITABLE = 1-End--> |
| JSVM_KEY_ENUMERABLE = 1 << 1 | key enumerable.<br><!--Device-JSVM_KEY_ENUMERABLE = 1 << 1--><!--Device-JSVM_KEY_ENUMERABLE = 1 << 1-End--> |
| JSVM_KEY_CONFIGURABLE = 1 << 2 | key configurable.<br><!--Device-JSVM_KEY_CONFIGURABLE = 1 << 2--><!--Device-JSVM_KEY_CONFIGURABLE = 1 << 2-End--> |
| JSVM_KEY_SKIP_STRINGS = 1 << 3 | key skip strings.<br><!--Device-JSVM_KEY_SKIP_STRINGS = 1 << 3--><!--Device-JSVM_KEY_SKIP_STRINGS = 1 << 3-End--> |
| JSVM_KEY_SKIP_SYMBOLS = 1 << 4 | key skip symbols.<br><!--Device-JSVM_KEY_SKIP_SYMBOLS = 1 << 4--><!--Device-JSVM_KEY_SKIP_SYMBOLS = 1 << 4-End--> |

### JSVM_KeyConversion

```c
enum JSVM_KeyConversion
```

**Description**

key conversion select.

<!--Device-enum JSVM_KeyConversion--><!--Device-enum JSVM_KeyConversion-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_KEY_KEEP_NUMBERS | will return numbers for integer indices.<br><!--Device-JSVM_KEY_KEEP_NUMBERS--><!--Device-JSVM_KEY_KEEP_NUMBERS-End--> |
| JSVM_KEY_NUMBERS_TO_STRINGS | will convert integer indices to strings.<br><!--Device-JSVM_KEY_NUMBERS_TO_STRINGS--><!--Device-JSVM_KEY_NUMBERS_TO_STRINGS-End--> |

### JSVM_MemoryPressureLevel

```c
enum JSVM_MemoryPressureLevel
```

**Description**

Memory pressure level.

<!--Device-enum JSVM_MemoryPressureLevel--><!--Device-enum JSVM_MemoryPressureLevel-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

| Enum item | Description |
| -- | -- |
| JSVM_MEMORY_PRESSURE_LEVEL_NONE | none pressure.<br><!--Device-JSVM_MEMORY_PRESSURE_LEVEL_NONE--><!--Device-JSVM_MEMORY_PRESSURE_LEVEL_NONE-End--> |
| JSVM_MEMORY_PRESSURE_LEVEL_MODERATE | moderate pressure.<br><!--Device-JSVM_MEMORY_PRESSURE_LEVEL_MODERATE--><!--Device-JSVM_MEMORY_PRESSURE_LEVEL_MODERATE-End--> |
| JSVM_MEMORY_PRESSURE_LEVEL_CRITICAL | critical pressure.<br><!--Device-JSVM_MEMORY_PRESSURE_LEVEL_CRITICAL--><!--Device-JSVM_MEMORY_PRESSURE_LEVEL_CRITICAL-End--> |
| JSVM_MEMORY_PRESSURE_LEVEL_LOW_MEMORY | Notifies that the system is running low on memory and triggers garbage collection immediately.<br>**Since**: 22<br><!--Device-JSVM_MEMORY_PRESSURE_LEVEL_LOW_MEMORY--><!--Device-JSVM_MEMORY_PRESSURE_LEVEL_LOW_MEMORY-End--> |

### JSVM_CompileMode

```c
enum JSVM_CompileMode
```

**Description**

Compile mode

<!--Device-enum JSVM_CompileMode--><!--Device-enum JSVM_CompileMode-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_COMPILE_MODE_DEFAULT | default mode.<br><!--Device-JSVM_COMPILE_MODE_DEFAULT--><!--Device-JSVM_COMPILE_MODE_DEFAULT-End--> |
| JSVM_COMPILE_MODE_CONSUME_CODE_CACHE | consume code cache.<br><!--Device-JSVM_COMPILE_MODE_CONSUME_CODE_CACHE--><!--Device-JSVM_COMPILE_MODE_CONSUME_CODE_CACHE-End--> |
| JSVM_COMPILE_MODE_EAGER_COMPILE | apply eager compile.<br><!--Device-JSVM_COMPILE_MODE_EAGER_COMPILE--><!--Device-JSVM_COMPILE_MODE_EAGER_COMPILE-End--> |
| JSVM_COMPILE_MODE_PRODUCE_COMPILE_PROFILE | preset for compile profile.<br><!--Device-JSVM_COMPILE_MODE_PRODUCE_COMPILE_PROFILE--><!--Device-JSVM_COMPILE_MODE_PRODUCE_COMPILE_PROFILE-End--> |
| JSVM_COMPILE_MODE_CONSUME_COMPILE_PROFILE | consume compile profile.<br><!--Device-JSVM_COMPILE_MODE_CONSUME_COMPILE_PROFILE--><!--Device-JSVM_COMPILE_MODE_CONSUME_COMPILE_PROFILE-End--> |

### JSVM_CompileOptionId

```c
enum JSVM_CompileOptionId
```

**Description**

Compile option id

<!--Device-enum JSVM_CompileOptionId--><!--Device-enum JSVM_CompileOptionId-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_COMPILE_MODE | compile mode.<br><!--Device-JSVM_COMPILE_MODE--><!--Device-JSVM_COMPILE_MODE-End--> |
| JSVM_COMPILE_CODE_CACHE | code cache content.<br><!--Device-JSVM_COMPILE_CODE_CACHE--><!--Device-JSVM_COMPILE_CODE_CACHE-End--> |
| JSVM_COMPILE_SCRIPT_ORIGIN | script origin.<br><!--Device-JSVM_COMPILE_SCRIPT_ORIGIN--><!--Device-JSVM_COMPILE_SCRIPT_ORIGIN-End--> |
| JSVM_COMPILE_COMPILE_PROFILE | compile profile content.<br><!--Device-JSVM_COMPILE_COMPILE_PROFILE--><!--Device-JSVM_COMPILE_COMPILE_PROFILE-End--> |
| JSVM_COMPILE_ENABLE_SOURCE_MAP | switch for source map support.<br><!--Device-JSVM_COMPILE_ENABLE_SOURCE_MAP--><!--Device-JSVM_COMPILE_ENABLE_SOURCE_MAP-End--> |
| JSVM_COMPILE_BACKGROUND_DESERIALIZE_RESULT | background deserialize code cache result.<br>**Since**: 24<br><!--Device-JSVM_COMPILE_BACKGROUND_DESERIALIZE_RESULT--><!--Device-JSVM_COMPILE_BACKGROUND_DESERIALIZE_RESULT-End--> |
| JSVM_COMPILE_CODE_CACHE_REJECTED | whether the code cache is rejected.<br>**Since**: 24<br><!--Device-JSVM_COMPILE_CODE_CACHE_REJECTED--><!--Device-JSVM_COMPILE_CODE_CACHE_REJECTED-End--> |

### JSVM_RegExpFlags

```c
enum JSVM_RegExpFlags
```

**Description**

Regular expression flag bits. They can be or'ed to enable a set of flags.

<!--Device-enum JSVM_RegExpFlags--><!--Device-enum JSVM_RegExpFlags-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_REGEXP_NONE = 0 | None mode.<br><!--Device-JSVM_REGEXP_NONE = 0--><!--Device-JSVM_REGEXP_NONE = 0-End--> |
| JSVM_REGEXP_GLOBAL = 1 << 0 | Global mode.<br><!--Device-JSVM_REGEXP_GLOBAL = 1 << 0--><!--Device-JSVM_REGEXP_GLOBAL = 1 << 0-End--> |
| JSVM_REGEXP_IGNORE_CASE = 1 << 1 | Ignore Case mode.<br><!--Device-JSVM_REGEXP_IGNORE_CASE = 1 << 1--><!--Device-JSVM_REGEXP_IGNORE_CASE = 1 << 1-End--> |
| JSVM_REGEXP_MULTILINE = 1 << 2 | Multiline mode.<br><!--Device-JSVM_REGEXP_MULTILINE = 1 << 2--><!--Device-JSVM_REGEXP_MULTILINE = 1 << 2-End--> |
| JSVM_REGEXP_STICKY = 1 << 3 | Sticky mode.<br><!--Device-JSVM_REGEXP_STICKY = 1 << 3--><!--Device-JSVM_REGEXP_STICKY = 1 << 3-End--> |
| JSVM_REGEXP_UNICODE = 1 << 4 | Unicode mode.<br><!--Device-JSVM_REGEXP_UNICODE = 1 << 4--><!--Device-JSVM_REGEXP_UNICODE = 1 << 4-End--> |
| JSVM_REGEXP_DOT_ALL = 1 << 5 | dotAll mode.<br><!--Device-JSVM_REGEXP_DOT_ALL = 1 << 5--><!--Device-JSVM_REGEXP_DOT_ALL = 1 << 5-End--> |
| JSVM_REGEXP_LINEAR = 1 << 6 | Linear mode.<br><!--Device-JSVM_REGEXP_LINEAR = 1 << 6--><!--Device-JSVM_REGEXP_LINEAR = 1 << 6-End--> |
| JSVM_REGEXP_HAS_INDICES = 1 << 7 | Has Indices mode.<br><!--Device-JSVM_REGEXP_HAS_INDICES = 1 << 7--><!--Device-JSVM_REGEXP_HAS_INDICES = 1 << 7-End--> |
| JSVM_REGEXP_UNICODE_SETS = 1 << 8 | Unicode Sets mode.<br><!--Device-JSVM_REGEXP_UNICODE_SETS = 1 << 8--><!--Device-JSVM_REGEXP_UNICODE_SETS = 1 << 8-End--> |

### JSVM_InitializedFlag

```c
enum JSVM_InitializedFlag
```

**Description**

initialization flag

<!--Device-enum JSVM_InitializedFlag--><!--Device-enum JSVM_InitializedFlag-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_ZERO_INITIALIZED | initialize with zero.<br><!--Device-JSVM_ZERO_INITIALIZED--><!--Device-JSVM_ZERO_INITIALIZED-End--> |
| JSVM_UNINITIALIZED | leave uninitialized.<br><!--Device-JSVM_UNINITIALIZED--><!--Device-JSVM_UNINITIALIZED-End--> |

### JSVM_WasmOptLevel

```c
enum JSVM_WasmOptLevel
```

**Description**

WebAssembly function optimization level

<!--Device-enum JSVM_WasmOptLevel--><!--Device-enum JSVM_WasmOptLevel-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_WASM_OPT_BASELINE = 10 | baseline optimization level.<br><!--Device-JSVM_WASM_OPT_BASELINE = 10--><!--Device-JSVM_WASM_OPT_BASELINE = 10-End--> |
| JSVM_WASM_OPT_HIGH = 20 | high optimization level.<br><!--Device-JSVM_WASM_OPT_HIGH = 20--><!--Device-JSVM_WASM_OPT_HIGH = 20-End--> |

### JSVM_CacheType

```c
enum JSVM_CacheType
```

**Description**

Cache data type

<!--Device-enum JSVM_CacheType--><!--Device-enum JSVM_CacheType-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

| Enum item | Description |
| -- | -- |
| JSVM_CACHE_TYPE_JS | js code cache, generated by OH_JSVM_CreateCodeCache<br><!--Device-JSVM_CACHE_TYPE_JS--><!--Device-JSVM_CACHE_TYPE_JS-End--> |
| JSVM_CACHE_TYPE_WASM | WebAssembly cache, generated by OH_JSVM_CreateWasmCache<br><!--Device-JSVM_CACHE_TYPE_WASM--><!--Device-JSVM_CACHE_TYPE_WASM-End--> |

### JSVM_MicrotaskPolicy

```c
enum JSVM_MicrotaskPolicy
```

**Description**

Microtask policies of JSVM.

<!--Device-enum JSVM_MicrotaskPolicy--><!--Device-enum JSVM_MicrotaskPolicy-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_MICROTASK_EXPLICIT = 0 | Microtasks are invoked with the OH_JSVM_PerformMicrotaskCheckpoint() method.<br><!--Device-JSVM_MICROTASK_EXPLICIT = 0--><!--Device-JSVM_MICROTASK_EXPLICIT = 0-End--> |
| JSVM_MICROTASK_AUTO | Microtasks are invoked when the script call depth decrements to zero. Default mode.<br><!--Device-JSVM_MICROTASK_AUTO--><!--Device-JSVM_MICROTASK_AUTO-End--> |

### JSVM_TraceCategory

```c
enum JSVM_TraceCategory
```

**Description**

Trace category for jsvm internal trace events.

<!--Device-enum JSVM_TraceCategory--><!--Device-enum JSVM_TraceCategory-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_TRACE_VM | Tracing main interface invoking of JSVM, such as run scripts.<br><!--Device-JSVM_TRACE_VM--><!--Device-JSVM_TRACE_VM-End--> |
| JSVM_TRACE_COMPILE | Tracing interface invoking about compilation, such as CompileCodeBackground.<br><!--Device-JSVM_TRACE_COMPILE--><!--Device-JSVM_TRACE_COMPILE-End--> |
| JSVM_TRACE_EXECUTE | Tracing interface invoking about execution status, such as Interrupts and Microtasks.<br><!--Device-JSVM_TRACE_EXECUTE--><!--Device-JSVM_TRACE_EXECUTE-End--> |
| JSVM_TRACE_RUNTIME | Tracing external callback<br><!--Device-JSVM_TRACE_RUNTIME--><!--Device-JSVM_TRACE_RUNTIME-End--> |
| JSVM_TRACE_STACK_TRACE | Tracing stack trace in JSVM.<br><!--Device-JSVM_TRACE_STACK_TRACE--><!--Device-JSVM_TRACE_STACK_TRACE-End--> |
| JSVM_TRACE_WASM | Tracing Main interface invoking of WASM, such as Compile Wasm Module and Instantiate.<br><!--Device-JSVM_TRACE_WASM--><!--Device-JSVM_TRACE_WASM-End--> |
| JSVM_TRACE_WASM_DETAILED | Tracing more detailed interface invoking of WASM, such as background compilation and wrappers.<br><!--Device-JSVM_TRACE_WASM_DETAILED--><!--Device-JSVM_TRACE_WASM_DETAILED-End--> |

### JSVM_PromiseRejectEvent

```c
enum JSVM_PromiseRejectEvent
```

**Description**

The promise-reject event.

<!--Device-enum JSVM_PromiseRejectEvent--><!--Device-enum JSVM_PromiseRejectEvent-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_PROMISE_REJECT_OTHER_REASONS = 0 | Promise is rejected for other reasons.<br><!--Device-JSVM_PROMISE_REJECT_OTHER_REASONS = 0--><!--Device-JSVM_PROMISE_REJECT_OTHER_REASONS = 0-End--> |
| JSVM_PROMISE_REJECT_WITH_NO_HANDLER = 1 | Promise rejected with no handler.<br><!--Device-JSVM_PROMISE_REJECT_WITH_NO_HANDLER = 1--><!--Device-JSVM_PROMISE_REJECT_WITH_NO_HANDLER = 1-End--> |
| JSVM_PROMISE_ADD_HANDLER_AFTER_REJECTED = 2 | Add the handler after Promise has been rejected.<br><!--Device-JSVM_PROMISE_ADD_HANDLER_AFTER_REJECTED = 2--><!--Device-JSVM_PROMISE_ADD_HANDLER_AFTER_REJECTED = 2-End--> |
| JSVM_PROMISE_REJECT_AFTER_RESOLVED = 3 | After the Promise has been resolved, try to reject the Promise again.<br><!--Device-JSVM_PROMISE_REJECT_AFTER_RESOLVED = 3--><!--Device-JSVM_PROMISE_REJECT_AFTER_RESOLVED = 3-End--> |
| JSVM_PROMISE_RESOLVE_AFTER_RESOLVED = 4 | After the Promise has been resolved, try resolving the Promise again.<br><!--Device-JSVM_PROMISE_RESOLVE_AFTER_RESOLVED = 4--><!--Device-JSVM_PROMISE_RESOLVE_AFTER_RESOLVED = 4-End--> |

### JSVM_MessageErrorLevel

```c
enum JSVM_MessageErrorLevel
```

**Description**

The level of message error.

<!--Device-enum JSVM_MessageErrorLevel--><!--Device-enum JSVM_MessageErrorLevel-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_MESSAGE_LOG = (1 << 0) | Log level message.<br><!--Device-JSVM_MESSAGE_LOG = (1 << 0)--><!--Device-JSVM_MESSAGE_LOG = (1 << 0)-End--> |
| JSVM_MESSAGE_DEBUG = (1 << 1) | Debug level message.<br><!--Device-JSVM_MESSAGE_DEBUG = (1 << 1)--><!--Device-JSVM_MESSAGE_DEBUG = (1 << 1)-End--> |
| JSVM_MESSAGE_INFO = (1 << 2) | Info level message.<br><!--Device-JSVM_MESSAGE_INFO = (1 << 2)--><!--Device-JSVM_MESSAGE_INFO = (1 << 2)-End--> |
| JSVM_MESSAGE_ERROR = (1 << 3) | Error level message.<br><!--Device-JSVM_MESSAGE_ERROR = (1 << 3)--><!--Device-JSVM_MESSAGE_ERROR = (1 << 3)-End--> |
| JSVM_MESSAGE_WARNING = (1 << 4) | Warning level message.<br><!--Device-JSVM_MESSAGE_WARNING = (1 << 4)--><!--Device-JSVM_MESSAGE_WARNING = (1 << 4)-End--> |
| JSVM_MESSAGE_ALL = JSVM_MESSAGE_LOG \| JSVM_MESSAGE_DEBUG \| JSVM_MESSAGE_INFO \| JSVM_MESSAGE_ERROR \| JSVM_MESSAGE_WARNING | All level message.<br><!--Device-JSVM_MESSAGE_ALL = JSVM_MESSAGE_LOG \| JSVM_MESSAGE_DEBUG \| JSVM_MESSAGE_INFO \| JSVM_MESSAGE_ERROR \| JSVM_MESSAGE_WARNING--><!--Device-JSVM_MESSAGE_ALL = JSVM_MESSAGE_LOG \| JSVM_MESSAGE_DEBUG \| JSVM_MESSAGE_INFO \| JSVM_MESSAGE_ERROR \| JSVM_MESSAGE_WARNING-End--> |

### JSVM_DefineClassOptionsId

```c
enum JSVM_DefineClassOptionsId
```

**Description**

DefineClass options id.

<!--Device-enum JSVM_DefineClassOptionsId--><!--Device-enum JSVM_DefineClassOptionsId-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_DEFINE_CLASS_NORMAL | Defining a class in normal mode.<br><!--Device-JSVM_DEFINE_CLASS_NORMAL--><!--Device-JSVM_DEFINE_CLASS_NORMAL-End--> |
| JSVM_DEFINE_CLASS_WITH_COUNT | Defining a class with count.<br><!--Device-JSVM_DEFINE_CLASS_WITH_COUNT--><!--Device-JSVM_DEFINE_CLASS_WITH_COUNT-End--> |
| JSVM_DEFINE_CLASS_WITH_PROPERTY_HANDLER | Defining a class with property handler.<br><!--Device-JSVM_DEFINE_CLASS_WITH_PROPERTY_HANDLER--><!--Device-JSVM_DEFINE_CLASS_WITH_PROPERTY_HANDLER-End--> |

### JSVM_CBTriggerTimeForGC

```c
enum JSVM_CBTriggerTimeForGC
```

**Description**

The timing of GC callback trigger.

<!--Device-enum JSVM_CBTriggerTimeForGC--><!--Device-enum JSVM_CBTriggerTimeForGC-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_CB_TRIGGER_BEFORE_GC | Trigger GC callback before GC.<br><!--Device-JSVM_CB_TRIGGER_BEFORE_GC--><!--Device-JSVM_CB_TRIGGER_BEFORE_GC-End--> |
| JSVM_CB_TRIGGER_AFTER_GC | Trigger GC callback after GC.<br><!--Device-JSVM_CB_TRIGGER_AFTER_GC--><!--Device-JSVM_CB_TRIGGER_AFTER_GC-End--> |

### JSVM_GCType

```c
enum JSVM_GCType
```

**Description**

The GC type.

<!--Device-enum JSVM_GCType--><!--Device-enum JSVM_GCType-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_GC_TYPE_SCAVENGE = 1 << 0 | The GC algorithm is Scavenge.<br><!--Device-JSVM_GC_TYPE_SCAVENGE = 1 << 0--><!--Device-JSVM_GC_TYPE_SCAVENGE = 1 << 0-End--> |
| JSVM_GC_TYPE_MINOR_MARK_COMPACT = 1 << 1 | The GC algorithm is Minor-Mark-Compact.<br><!--Device-JSVM_GC_TYPE_MINOR_MARK_COMPACT = 1 << 1--><!--Device-JSVM_GC_TYPE_MINOR_MARK_COMPACT = 1 << 1-End--> |
| JSVM_GC_TYPE_MARK_SWEEP_COMPACT = 1 << 2 | The GC algorithm is Mark-Sweep-Compact.<br><!--Device-JSVM_GC_TYPE_MARK_SWEEP_COMPACT = 1 << 2--><!--Device-JSVM_GC_TYPE_MARK_SWEEP_COMPACT = 1 << 2-End--> |
| JSVM_GC_TYPE_INCREMENTAL_MARKING = 1 << 3 | The GC algorithm is Incremental-Marking.<br><!--Device-JSVM_GC_TYPE_INCREMENTAL_MARKING = 1 << 3--><!--Device-JSVM_GC_TYPE_INCREMENTAL_MARKING = 1 << 3-End--> |
| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS = 1 << 4 | The GC algorithm is Weak-Callbacks.<br><!--Device-JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS = 1 << 4--><!--Device-JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS = 1 << 4-End--> |
| JSVM_GC_TYPE_ALL = JSVM_GC_TYPE_SCAVENGE \| JSVM_GC_TYPE_MINOR_MARK_COMPACT \| JSVM_GC_TYPE_MARK_SWEEP_COMPACT \| JSVM_GC_TYPE_INCREMENTAL_MARKING \| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS | All GC algorithm.<br><!--Device-JSVM_GC_TYPE_ALL = JSVM_GC_TYPE_SCAVENGE \| JSVM_GC_TYPE_MINOR_MARK_COMPACT \| JSVM_GC_TYPE_MARK_SWEEP_COMPACT \| JSVM_GC_TYPE_INCREMENTAL_MARKING \| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS--><!--Device-JSVM_GC_TYPE_ALL = JSVM_GC_TYPE_SCAVENGE \| JSVM_GC_TYPE_MINOR_MARK_COMPACT \| JSVM_GC_TYPE_MARK_SWEEP_COMPACT \| JSVM_GC_TYPE_INCREMENTAL_MARKING \| JSVM_GC_TYPE_PROCESS_WEAK_CALLBACKS-End--> |

### JSVM_GCCallbackFlags

```c
enum JSVM_GCCallbackFlags
```

**Description**

The GC callback flags.

<!--Device-enum JSVM_GCCallbackFlags--><!--Device-enum JSVM_GCCallbackFlags-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

| Enum item | Description |
| -- | -- |
| JSVM_NO_GC_CALLBACK_FLAGS | No GC callback falgs.<br><!--Device-JSVM_NO_GC_CALLBACK_FLAGS--><!--Device-JSVM_NO_GC_CALLBACK_FLAGS-End--> |
| JSVM_GC_CALLBACK_CONSTRUCT_RETAINED_OBJECT_INFOS | Reserved object information will be built in the garbage collection callback.<br><!--Device-JSVM_GC_CALLBACK_CONSTRUCT_RETAINED_OBJECT_INFOS--><!--Device-JSVM_GC_CALLBACK_CONSTRUCT_RETAINED_OBJECT_INFOS-End--> |
| JSVM_GC_CALLBACK_FORCED | Enforce Garbage Collection Callback.<br><!--Device-JSVM_GC_CALLBACK_FORCED--><!--Device-JSVM_GC_CALLBACK_FORCED-End--> |
| JSVM_GC_CALLBACK_SYNCHRONOUS_PHANTOM_CALLBACK_PROCESSING | Synchronous phantom callback processing.<br><!--Device-JSVM_GC_CALLBACK_SYNCHRONOUS_PHANTOM_CALLBACK_PROCESSING--><!--Device-JSVM_GC_CALLBACK_SYNCHRONOUS_PHANTOM_CALLBACK_PROCESSING-End--> |
| JSVM_GC_CALLBACK_COLLECT_ALL_AVAILABLE_GARBAGE | All available garbage objects are collected during garbage collection.<br><!--Device-JSVM_GC_CALLBACK_COLLECT_ALL_AVAILABLE_GARBAGE--><!--Device-JSVM_GC_CALLBACK_COLLECT_ALL_AVAILABLE_GARBAGE-End--> |
| JSVM_GC_CALLBACK_COLLECT_ALL_EXTERNAL_MEMORY | Garbage collection collects all external memory.<br><!--Device-JSVM_GC_CALLBACK_COLLECT_ALL_EXTERNAL_MEMORY--><!--Device-JSVM_GC_CALLBACK_COLLECT_ALL_EXTERNAL_MEMORY-End--> |
| JSVM_GC_CALLBACK_SCHEDULE_IDLE_GARBAGE_COLLECTION | Schedule Garbage Collection at Idle Time.<br><!--Device-JSVM_GC_CALLBACK_SCHEDULE_IDLE_GARBAGE_COLLECTION--><!--Device-JSVM_GC_CALLBACK_SCHEDULE_IDLE_GARBAGE_COLLECTION-End--> |

### JSVM_DebugOption

```c
enum JSVM_DebugOption
```

**Description**

Debug options.

<!--Device-enum JSVM_DebugOption--><!--Device-enum JSVM_DebugOption-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 20

| Enum item | Description |
| -- | -- |
| JSVM_SCOPE_CHECK | Scope check.<br><!--Device-JSVM_SCOPE_CHECK--><!--Device-JSVM_SCOPE_CHECK-End--> |


## Function description

### JSVM_Finalize()

```c
typedef void(JSVM_CDECL* JSVM_Finalize)(JSVM_Env env, void* finalizeData, void* finalizeHint)
```

**Description**

Function pointer type for add-on provided function that allow the user to be notified.

<!--Device-typedef void(JSVM_CDECL* JSVM_Finalize)(JSVM_Env env, void* finalizeData, void* finalizeHint)--><!--Device-typedef void(JSVM_CDECL* JSVM_Finalize)(JSVM_Env env, void* finalizeData, void* finalizeHint)-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

### JSVM_FinalizeArrayBuffer()

```c
#ifdef JSVM_EXPERIMENTAL
typedef void(JSVM_CDECL* JSVM_FinalizeArrayBuffer)(JSVM_Env env, void* finalizeData, void* finalizeHint, bool copied);
#endif // JSVM_EXPERIMENTAL
```

**Description**

Finalize callback for ArrayBuffers created from external memory.<br> Similar to JSVM_Finalize, but includes a copied parameter indicating whether the engine copied the external data into an internal buffer (true) or used zero-copy (false). When copied is true, the engine does not hold a reference to the original external data, so the caller may free it immediately after the API call returns. When copied is false, finalizeData points to the original external memory that the engine is releasing — the callback should free it.

<!--Device-typedef void(JSVM_CDECL* JSVM_FinalizeArrayBuffer)(JSVM_Env env, void* finalizeData, void* finalizeHint, bool copied)--><!--Device-typedef void(JSVM_CDECL* JSVM_FinalizeArrayBuffer)(JSVM_Env env, void* finalizeData, void* finalizeHint, bool copied)-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 26.0.0

### JSVM_OutputStream()

```c
typedef bool(JSVM_CDECL* JSVM_OutputStream)(const char* data, int size, void* streamData)
```

**Description**

Function pointer type for callback of output stream. The first parameter data is the data pointer. And the second parameter size is the data size to output. A null data pointer indicates the end of the stream. The third parameter streamData is the pointer passed in together with the callback to the API functions that generate data to the output stream. The callback returns true to indicate the stream can continue to accept data. Otherwise, it will abort the stream.

<!--Device-typedef bool(JSVM_CDECL* JSVM_OutputStream)(const char* data, int size, void* streamData)--><!--Device-typedef bool(JSVM_CDECL* JSVM_OutputStream)(const char* data, int size, void* streamData)-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

### JSVM_HandlerForOOMError()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location, const char* detail, bool isHeapOOM)
```

**Description**

Function pointer type of OOM-Error callback.

<!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location, const char* detail, bool isHeapOOM)--><!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForOOMError)(const char* location, const char* detail, bool isHeapOOM)-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* location | The location information of the OOM error. |
| const char* detail | The detail of the OOM error. |
| bool isHeapOOM | Determine whether the OOM type is Heap OOM. |

### JSVM_HandlerForFatalError()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location, const char* message)
```

**Description**

Function pointer type of Fatal-Error callback.

<!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location, const char* message)--><!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForFatalError)(const char* location, const char* message)-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* location | The location information of the Fatal error. |
| const char* message | The message of the Fatal error. |

### JSVM_HandlerForPromiseReject()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)
```

**Description**

Function pointer type of Promise-Reject callback.

<!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)--><!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForPromiseReject)(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | The environment that the function is invoked under. |
| [JSVM_PromiseRejectEvent](capi-jsvm-types-h.md#jsvm_promiserejectevent) rejectEvent | The promise-reject event. |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rejectInfo | An JS-object containing two properties: 'promise' and 'value'. The 'promise' represents a reference to the Promise object that was rejected. The 'value' represents the rejection reason associated with that promise. |

### JSVM_HandlerForGC()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)
```

**Description**

Function pointer type of GC callback.

<!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)--><!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForGC)(JSVM_VM vm, JSVM_GCType gcType, JSVM_GCCallbackFlags flags, void* data)-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | The VM instance that the JSVM-API call is invoked under. |
| [JSVM_GCType](capi-jsvm-types-h.md#jsvm_gctype) gcType | The gc type. |
| [JSVM_GCCallbackFlags](capi-jsvm-types-h.md#jsvm_gccallbackflags) flags | The GC callback flags. |
| void* data | The native pointer data. |

### JSVM_HandlerForHeapThreshold()

```c
typedef void(JSVM_CDECL* JSVM_HandlerForHeapThreshold)(JSVM_VM vm, uint64_t threshold, void* data)
```

**Description**

Function pointer type for heap threshold callback.

<!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForHeapThreshold)(JSVM_VM vm, uint64_t threshold, void* data)--><!--Device-typedef void(JSVM_CDECL* JSVM_HandlerForHeapThreshold)(JSVM_VM vm, uint64_t threshold, void* data)-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | The VM instance whose heap usage is observed at or above the threshold. |
| uint64_t threshold | The heap usage threshold in bytes. |
| void* data | The native pointer data. |


