# jsvm.h
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Defines JSVM-APIs. These APIs are used to provide independent, standard, and complete JS engine capabilities, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross-language calls, and taking snapshots.

**Reference file**: <ark_runtime/jsvm.h>

**Library**: libjsvm.so

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

## Summary

### Macros

| Name                                              | Description                                                                                                                                                |
|--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| **JSVM_VERSION_EXPERIMENTAL** 2147483647           | Defines the experimental JSVM version number.                                                                                                                                      |
| **JSVM_VERSION** 8                                 | Defines the JSVM version number.                                                                                                                                         |
| **JSVM_EXTERN  __attribute__**((visibility("default")))  | Defines the symbol that is externally visible.                                                                                                                                        |
| **JSVM_AUTO_LENGTH**   SIZE_MAX | Defines the automatic length.                                                                                                                                             |
| **EXTERN_C_START**                                 | Defines the segment start identifier for a compiler to compile the following code segment as C code.<br>When **__cplusplus** detects that a C++ compiler is being used, the value **"extern "C" {"** is assigned to **EXTERN_C_START**, indicating that the subsequent code is C code. If a C++ compiler is not being used, no tag is required.|
| **EXTERN_C_END**                                   | Defines the segment end identifier for a compiler to compile the following code segment as C code.<br>When **__cplusplus** detects that a C++ compiler is being used, the value **"}"** is assigned to **EXTERN_C_START**, indicating that the C code ends here. If a C++ compiler is not being used, no tag is required.                                                                                                                  |

### Functions

| Name| Description|
| -- | -- |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Init(const JSVM_InitOptions* options)](#oh_jsvm_init) | Initializes a JavaScript VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateVM(const JSVM_CreateVMOptions* options,JSVM_VM* result)](#oh_jsvm_createvm) | Creates a VM instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetMicrotaskPolicy(JSVM_VM vm,JSVM_MicrotaskPolicy policy)](#oh_jsvm_setmicrotaskpolicy) | Sets the microtask execution policy for a VM instance. If this method is not called, the default policy **JSVM_MicrotaskPolicy::JSVM_MICROTASK_AUTO** is used.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DestroyVM(JSVM_VM vm)](#oh_jsvm_destroyvm) | Destroys a VM instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateProxy(JSVM_Env env,JSVM_Value target,JSVM_Value handler,JSVM_Value* result)](#oh_jsvm_createproxy) | Creates a JavaScript proxy. This API is equivalent to calling **new Proxy(target, handler)** in JS.|
| [JSVM_Status JSVM_CDECL OH_JSVM_IsProxy(JSVM_Env env,JSVM_Value value,bool* isProxy)](#oh_jsvm_isproxy) | Checks whether the input value is a JavaScript proxy.|
| [JSVM_Status JSVM_CDECL OH_JSVM_ProxyGetTarget(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_proxygettarget) | Obtains the target object in the JavaScript Proxy.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenVMScope(JSVM_VM vm,JSVM_VMScope* result)](#oh_jsvm_openvmscope) | Opens a new VM scope for a VM instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseVMScope(JSVM_VM vm,JSVM_VMScope scope)](#oh_jsvm_closevmscope) | Closes the VM scope of a VM instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnv(JSVM_VM vm,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Env* result)](#oh_jsvm_createenv) | Creates a new environment based on the optional properties of the new context.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnvFromSnapshot(JSVM_VM vm,size_t index,JSVM_Env* result)](#oh_jsvm_createenvfromsnapshot) | Creates a new environment based on the startup snapshot of the VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DestroyEnv(JSVM_Env env)](#oh_jsvm_destroyenv) | Destroys the environment.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenEnvScope(JSVM_Env env,JSVM_EnvScope* result)](#oh_jsvm_openenvscope) | Opens a new environment scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseEnvScope(JSVM_Env env,JSVM_EnvScope scope)](#oh_jsvm_closeenvscope) | Closes the environment scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVM(JSVM_Env env,JSVM_VM* result)](#oh_jsvm_getvm) | Obtains a VM instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScript(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_Script* result)](#oh_jsvm_compilescript) | Compiles a JavaScript code snippet and returns the compiled script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOrigin(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_ScriptOrigin* origin,JSVM_Script* result)](#oh_jsvm_compilescriptwithorigin) | Compiles a JavaScript code snippet that contains source map information and returns the compiled script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOptions(JSVM_Env env,JSVM_Value script,size_t optionCount,JSVM_CompileOptions options[],JSVM_Value* result)](#oh_jsvm_compilescriptwithoptions) | Compiles a JavaScript code snippet and returns the compiled script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateCodeCache(JSVM_Env env,JSVM_Script script,const uint8_t** data,size_t* length)](#oh_jsvm_createcodecache) | Creates a code cache for the compiled script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RunScript(JSVM_Env env,JSVM_Script script,JSVM_Value* result)](#oh_jsvm_runscript) | Runs a JavaScript code snippet and returns its result, including the following precautions: Unlike eval, this function does not allow the script to access the current lexical scope, and therefore does not allow the script to access the module scope. This means that pseudo-global variables such as **require** will be unavailable. The script can access the global scope. The functions and variable declarations in the script will be added to the global object. Variable declarations using **let** and **const** are globally visible, but are not added to the global object. The value of **this** is **global** in the script. Without the JIT permission, the script containing WebAssembly fails to be executed. The performance varies in specific scenarios, and a log is printed to notify you.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetInstanceData(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint)](#oh_jsvm_setinstancedata) | Sets instance data so that it is associated with the currently running JSVM environment. You can use **OH_JSVM_GetInstanceData()** to obtain data later. Any existing data set by a previous call to **OH_JSVM_SetInstanceData()** will be overwritten. If **finalizeCb** was previously provided, it will not be called.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetInstanceData(JSVM_Env env,void** data)](#oh_jsvm_getinstancedata) | Obtains instance data that has been set by **OH_JSVM_SetInstanceData()**. If no associated data is set, this function is called successfully and **data** is set to **NULL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetLastErrorInfo(JSVM_Env env,const JSVM_ExtendedErrorInfo** result)](#oh_jsvm_getlasterrorinfo) | Obtains the **JSVM_ExtendedErrorInfo** struct that contains the last error. The content of **JSVM_ExtendedErrorInfo** returned is valid only before the JSVM-API function is called for the same environment. This includes a call to **OH_JSVM_IsExceptionPending**, so you may need to copy information for later use. The pointer returned in **error_message** points to a statically defined string, so if you copy it from the **error_message** field (which will be overwritten) before calling another JSVM-API function, you can safely use the pointer.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Throw(JSVM_Env env,JSVM_Value error)](#oh_jsvm_throw) | Throws the provided JavaScript value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwerror) | Throws a JavaScript Error with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowTypeError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwtypeerror) | Throws a JavaScript TypeError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowRangeError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwrangeerror) | Throws a JavaScript RangeError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowSyntaxError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwsyntaxerror) | Throws a JavaScript SyntaxError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsError(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_iserror) | Checks whether the given **JSVM_Value** indicates an error.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createerror) | Creates a JavaScript Error with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createtypeerror) | Creates a JavaScript TypeError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateRangeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createrangeerror) | Creates a JavaScript RangeError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSyntaxError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createsyntaxerror) | Creates a JavaScript SyntaxError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetAndClearLastException(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getandclearlastexception) | Obtains and clears the last exception. If pending occurs, a JavaScript exception is returned. Otherwise, **NULL** is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsExceptionPending(JSVM_Env env,bool* result)](#oh_jsvm_isexceptionpending) | Checks whether the last exception is caused by pending. If yes, **true** is returned. Otherwise, **false** is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenHandleScope(JSVM_Env env,JSVM_HandleScope* result)](#oh_jsvm_openhandlescope) | Opens a new handle scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseHandleScope(JSVM_Env env,JSVM_HandleScope scope)](#oh_jsvm_closehandlescope) | (Mandatory) Closes the handle scope in the reverse order of opening it.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope* result)](#oh_jsvm_openescapablehandlescope) | Opens an escapable handle scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope scope)](#oh_jsvm_closeescapablehandlescope) | (Mandatory) Closes the escapable handle scope in the reverse order of opening it. This JSVM_API can be called even if there is a pending JavaScript exception.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_EscapeHandle(JSVM_Env env,JSVM_EscapableHandleScope scope,JSVM_Value escapee,JSVM_Value* result)](#oh_jsvm_escapehandle) | Escapes a handle of a JavaScript object so that it is valid through the lifecycle of the outer scope. Each scope can be called only once. If it is called for multiple times, an error is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateReference(JSVM_Env env,JSVM_Value value,uint32_t initialRefcount,JSVM_Ref* result)](#oh_jsvm_createreference) | Creates a reference with the specified reference count for the input value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteReference(JSVM_Env env,JSVM_Ref ref)](#oh_jsvm_deletereference) | Deletes the input reference.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceRef(JSVM_Env env,JSVM_Ref ref,uint32_t* result)](#oh_jsvm_referenceref) | Increases the reference count and returns the new reference count.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceUnref(JSVM_Env env,JSVM_Ref ref,uint32_t* result)](#oh_jsvm_referenceunref) | Decreases the reference count and returns the new reference count.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceValue(JSVM_Env env,JSVM_Ref ref,JSVM_Value* result)](#oh_jsvm_getreferencevalue) | Obtains the **JSVM_Value** returned by the JSVM-API, which is the JavaScript value associated with **JSVM_Ref**. If the value is invalid, **NULL** is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArray(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_createarray) | Creates an array. This API returns the JSVM-API value of the JavaScript Array type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayWithLength(JSVM_Env env,size_t length,JSVM_Value* result)](#oh_jsvm_createarraywithlength) | Creates an array with a specified length. This API returns the JSVM-API value of the JavaScript Array type. The **length** property of the array is set to the input **length** parameter. However, there is no guarantee that the underlying buffer is pre-allocated by the VM when the array is created. This behavior is implemented by the underlying VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArraybuffer(JSVM_Env env,size_t byteLength,void** data,JSVM_Value* result)](#oh_jsvm_createarraybuffer) | Creates an array buffer. This API returns the JSVM-API value of the JavaScript ArrayBuffer type. ArrayBuffer is used to represent a fixed-length binary data buffer. It is usually used as the backup buffer of the **TypedArray** object. The allocated ArrayBuffer has an underlying byte buffer whose size is determined by the **length** parameter. The underlying buffer can be returned to and operated by the caller. This buffer can only be written directly from the native code. To write data from JavaScript to this buffer, you need to create a **TypedArray** or **DataView** object.|
| [JSVM_Status JSVM_CDECL OH_JSVM_AllocateArrayBufferBackingStoreData(size_t byteLength,JSVM_InitializedFlag initialized,void **data)](#oh_jsvm_allocatearraybufferbackingstoredata) | Allocates a segment of BackingStore memory to the array buffer.|
| [JSVM_Status JSVM_CDECL OH_JSVM_FreeArrayBufferBackingStoreData(void *data)](#oh_jsvm_freearraybufferbackingstoredata) | Frees the BackingStore memory allocated by **OH_JSVM_AllocateArrayBufferBackingStoreData**.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateArrayBufferFromBackingStoreData(JSVM_Env env,void *data,size_t backingStoreSize,size_t offset,size_t arrayBufferSize,JSVM_Value *result)](#oh_jsvm_createarraybufferfrombackingstoredata) | Creates an array buffer in the allocated BackingStore memory.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDate(JSVM_Env env,double time,JSVM_Value* result)](#oh_jsvm_createdate) | Creates a date. This API ignores leap seconds because ECMAScript complies with the POSIX time specifications.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternal(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Value* result)](#oh_jsvm_createexternal) | Creates a JavaScript value with external data. This is used to pass external data through JavaScript code. You can use **OH_JSVM_GetValueExternal** to retrieve the value from the native code. This API adds a **JSVM_Finalize** callback, which will be called when the newly created JavaScript object is garbage-collected. The created value is not an object, so it does not support additional properties. It is considered as a unique value type: Calling **OH_JSVM_Typeof()** with an external value generates **JSVM_EXTERNAL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateObject(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_createobject) | Creates a default JavaScript object. This function is equivalent to executing **new Object()** in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSymbol(JSVM_Env env,JSVM_Value description,JSVM_Value* result)](#oh_jsvm_createsymbol) | Creates a JavaScript symbol value with a UTF-8-encoded C string.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SymbolFor(JSVM_Env env,const char* utf8description,size_t length,JSVM_Value* result)](#oh_jsvm_symbolfor) | Searches the global registry for an existing symbol with the given description. This API returns the symbol if it already exists; otherwise, a symbol is created in the registry.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypedarray(JSVM_Env env,JSVM_TypedarrayType type,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)](#oh_jsvm_createtypedarray) | Creates a JavaScript **TypedArray** object based on an existing **ArrayBuffer** object. The **TypedArray** object provides an array-like view on the underlying data buffer, where each element has the same underlying binary scalar data type. The value of "**length** × element scalar bytes + **byteOffset**" must not be greater than the value of **ByteLength()** of the input array. Otherwise, a range error is thrown.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataview(JSVM_Env env,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)](#oh_jsvm_createdataview) | Creates a JavaScript **DataView** object based on an existing **ArrayBuffer** object. The **DataView** object provides an array-like view on the underlying data buffer, where elements can have different sizes and types. The sum of the binary length and byte offset cannot be greater than the size (in bytes) of the input array. Otherwise, a range error is thrown.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt32(JSVM_Env env,int32_t value,JSVM_Value* result)](#oh_jsvm_createint32) | Converts a value of the C int32_t type to a value of the JavaScript number type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateUint32(JSVM_Env env,uint32_t value,JSVM_Value* result)](#oh_jsvm_createuint32) | Converts a value of the C uint32_t type to a value of the JavaScript number type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt64(JSVM_Env env,int64_t value,JSVM_Value* result)](#oh_jsvm_createint64) | Converts a value of the C int64_t type to a value of the JavaScript number type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDouble(JSVM_Env env,double value,JSVM_Value* result)](#oh_jsvm_createdouble) | Converts a value of the C double type to a value of the JavaScript number type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintInt64(JSVM_Env env,int64_t value,JSVM_Value* result)](#oh_jsvm_createbigintint64) | Converts a value of the C int64_t type to a value of the JavaScript BigInt type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintUint64(JSVM_Env env,uint64_t value,JSVM_Value* result)](#oh_jsvm_createbigintuint64) | Converts a value of the C uint64_t type to a value of the JavaScript BigInt type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintWords(JSVM_Env env,int signBit,size_t wordCount,const uint64_t* words,JSVM_Value* result)](#oh_jsvm_createbigintwords) | Converts a group of 64-bit unsigned bits to a single BigInt value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringLatin1(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)](#oh_jsvm_createstringlatin1) | Converts an ISO-8859-1-encoded C string to a JavaScript string. A native string is copied.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf16(JSVM_Env env,const char16_t* str,size_t length,JSVM_Value* result)](#oh_jsvm_createstringutf16) | Converts a UTF-16LE-encoded C string to a JavaScript string. A native string is copied.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf8(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)](#oh_jsvm_createstringutf8) | Creates a JavaScript string using a UTF-8-encoded C string. A native string is copied.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetArrayLength(JSVM_Env env,JSVM_Value value,uint32_t* result)](#oh_jsvm_getarraylength) | Obtains the length of an array.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetArraybufferInfo(JSVM_Env env,JSVM_Value arraybuffer,void** data,size_t* byteLength)](#oh_jsvm_getarraybufferinfo) | Obtains the underlying data buffer of the **ArrayBuffer** and its length.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPrototype(JSVM_Env env,JSVM_Value object,JSVM_Value* result)](#oh_jsvm_getprototype) | Obtains the prototype of an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetTypedarrayInfo(JSVM_Env env,JSVM_Value typedarray,JSVM_TypedarrayType* type,size_t* length,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)](#oh_jsvm_gettypedarrayinfo) | Obtains the properties of a typed array. If any property is not required, its output parameter can be **NULL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetDataviewInfo(JSVM_Env env,JSVM_Value dataview,size_t* bytelength,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)](#oh_jsvm_getdataviewinfo) | Obtains the proprieties of a **DataView**. If any property is not required, its output parameter can be **NULL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetDateValue(JSVM_Env env,JSVM_Value value,double* result)](#oh_jsvm_getdatevalue) | Obtains the C double-precision primitive equivalent of a given JavaScript date. If this API call is successfully, **JSVM_OK** is returned. If a **JSVM_Value** of a non-JavaScript date type is passed in, **JSVM_DATA_EXPECTED** is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBool(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_getvaluebool) | Obtains the C Boolean primitive equivalent of a given JavaScript Boolean value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueDouble(JSVM_Env env,JSVM_Value value,double* result)](#oh_jsvm_getvaluedouble) | Obtains the C double-precision primitive equivalent of a given JavaScript number.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintInt64(JSVM_Env env,JSVM_Value value,int64_t* result,bool* lossless)](#oh_jsvm_getvaluebigintint64) | Obtains the C int64_t primitive equivalent of a given JavaScript BigInt value. If necessary, it truncates the value and sets **lossless** to **false**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintUint64(JSVM_Env env,JSVM_Value value,uint64_t* result,bool* lossless)](#oh_jsvm_getvaluebigintuint64) | Obtains the C uint64_t primitive equivalent of a given JavaScript BigInt value. If necessary, it truncates the value and sets **lossless** to **false**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintWords(JSVM_Env env,JSVM_Value value,int* signBit,size_t* wordCount,uint64_t* words)](#oh_jsvm_getvaluebigintwords) | Converts a BigInt value to the sign bit, 64-bit little-endian array, and number of elements in the array. Both **signBit** and **words** can be set to **NULL**. In this case, only **wordCount** is obtained.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueExternal(JSVM_Env env,JSVM_Value value,void** result)](#oh_jsvm_getvalueexternal) | Obtains the external data pointer previously passed to **OH_JSVM_CreateExternal()**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt32(JSVM_Env env,JSVM_Value value,int32_t* result)](#oh_jsvm_getvalueint32) | Obtains the C int32 primitive equivalent of a given JavaScript number.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt64(JSVM_Env env,JSVM_Value value,int64_t* result)](#oh_jsvm_getvalueint64) | Obtains the C int64 primitive equivalent of a given JavaScript number.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringLatin1(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)](#oh_jsvm_getvaluestringlatin1) | Obtains the ISO-8859-1-encoded string corresponding to the input value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf8(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)](#oh_jsvm_getvaluestringutf8) | Obtains the UTF-8-encoded string corresponding to the input value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf16(JSVM_Env env,JSVM_Value value,char16_t* buf,size_t bufsize,size_t* result)](#oh_jsvm_getvaluestringutf16) | Obtains the UTF-16-encoded string corresponding to the input value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueUint32(JSVM_Env env,JSVM_Value value,uint32_t* result)](#oh_jsvm_getvalueuint32) | Obtains the C uint_32 primitive equivalent of a given JavaScript number.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetBoolean(JSVM_Env env,bool value,JSVM_Value* result)](#oh_jsvm_getboolean) | Obtains a JavaScript singleton object that is used to represent the given Boolean value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetGlobal(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getglobal) | Obtains the global object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNull(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getnull) | Obtains the null object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetUndefined(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getundefined) | Obtains the undefined object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBool(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetobool) | Implements the abstract operation **ToBoolean()**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToNumber(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetonumber) | Implements the abstract operation **ToNumber()**. If the input value is an object, the function may run JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToObject(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetoobject) | Implements the abstract operation **ToObject()**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToString(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetostring) | Implements the abstract operation **ToString()**. If the input value is an object, the function may run JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Typeof(JSVM_Env env,JSVM_Value value,JSVM_ValueType* result)](#oh_jsvm_typeof) | Provides a behavior similar to calling the **typeof** operator on a defined object. The difference is that this function supports the detection of external values; it detects null as a separate type, while ECMAScript **typeof** is used to detect objects. If the value type is invalid, an error is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Instanceof(JSVM_Env env,JSVM_Value object,JSVM_Value constructor,bool* result)](#oh_jsvm_instanceof) | Provides a behavior similar to calling the **instanceof** operator on an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsArray(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isarray) | Provides a behavior similar to calling **IsArray** on an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isarraybuffer) | Checks whether the input object is an **ArrayBuffer**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDate(JSVM_Env env,JSVM_Value value,bool* isDate)](#oh_jsvm_isdate) | Checks whether the input object is a date.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsTypedarray(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_istypedarray) | Checks whether the input object is a typed array.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDataview(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isdataview) | Checks whether the input object is **DataView**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_StrictEquals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)](#oh_jsvm_strictequals) | Provides a behavior similar to calling the strict equality algorithm.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Equals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)](#oh_jsvm_equals) | Provides a behavior similar to calling the loose equality algorithm. Regardless of the JavaScript value type, **true** is returned as long as the values are equal.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DetachArraybuffer(JSVM_Env env,JSVM_Value arraybuffer)](#oh_jsvm_detacharraybuffer) | Provides a behavior similar to calling the **detach** operation of **ArrayBuffer**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDetachedArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isdetachedarraybuffer) | Provides a behavior similar to calling the **IsDetachedBuffer** operation of **ArrayBuffer**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_Value* result)](#oh_jsvm_getpropertynames) | Obtains the names of enumerable properties of an object as an array of characters. The properties of the object whose key is a symbol are not included.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetAllPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_KeyCollectionMode keyMode,JSVM_KeyFilter keyFilter,JSVM_KeyConversion keyConversion,JSVM_Value* result)](#oh_jsvm_getallpropertynames) | Obtains all available property names of the object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value value)](#oh_jsvm_setproperty) | Sets the **key** property for the input object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value* result)](#oh_jsvm_getproperty) | Obtains the **key** property from the input object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)](#oh_jsvm_hasproperty) | Checks whether the input object has the **key** property.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)](#oh_jsvm_deleteproperty) | Deletes the **key** property from the object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasOwnProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)](#oh_jsvm_hasownproperty) | Checks whether the input object has the **key** property. The key must be a string or symbol. Otherwise, an error is thrown. The JSVM-API does not perform any conversion between data types.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value value)](#oh_jsvm_setnamedproperty) | Sets a property with a specified name. This method is equivalent to calling **OH_JSVM_SetProperty** to set the **utf8Name** property.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value* result)](#oh_jsvm_getnamedproperty) | Obtains the named property. This method is equivalent to calling **OH_JSVM_GetProperty** to obtain the **utf8Name** property.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,bool* result)](#oh_jsvm_hasnamedproperty) | Checks whether an object has the named property. This method is equivalent to calling **OH_JSVM_HasProperty** to check whether the object has the **utf8Name** property.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value value)](#oh_jsvm_setelement) | Sets an element for the input object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value* result)](#oh_jsvm_getelement) | Obtains the element at the requested index.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)](#oh_jsvm_haselement) | Checks whether an input object has an element at the specified index. If yes, the JSVM-API returns **true**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)](#oh_jsvm_deleteelement) | Deletes the element at the specified index from an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineProperties(JSVM_Env env,JSVM_Value object,size_t propertyCount,const JSVM_PropertyDescriptor* properties)](#oh_jsvm_defineproperties) | Defines properties on a given object by using property descriptors. Through an array of property descriptors, this API sets the properties in the array in turn for the object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectFreeze(JSVM_Env env,JSVM_Value object)](#oh_jsvm_objectfreeze) | Freezes a JavaScript object. Once a JavaScript object is frozen, new properties cannot be added to it, existing properties cannot be removed, the enumerability, configurability, or writability of existing properties cannot be changed, and the values of existing properties and object prototypes cannot be changed.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSeal(JSVM_Env env,JSVM_Value object)](#oh_jsvm_objectseal) | Encapsulates a specified object, which prevents additions of properties and marks existing properties non-configurable.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CallFunction(JSVM_Env env,JSVM_Value recv,JSVM_Value func,size_t argc,const JSVM_Value* argv,JSVM_Value* result)](#oh_jsvm_callfunction) | Supports calling JavaScript function objects from native code, which is the main mechanism for JavaScript to call native code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunction(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback cb,JSVM_Value* result)](#oh_jsvm_createfunction) | Supports creating function objects in native code, which is the main mechanism for JavaScript to call native code. After this call, the newly created function is no longer automatically visible in the script. Instead, you should explicitly set properties on any visible object in JavaScript to access the function from the script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetCbInfo(JSVM_Env env,JSVM_CallbackInfo cbinfo,size_t* argc,JSVM_Value* argv,JSVM_Value* thisArg,void** data)](#oh_jsvm_getcbinfo) | Obtains detailed information about the callback, such as the parameter from the given callback information and the **this** pointer.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNewTarget(JSVM_Env env,JSVM_CallbackInfo cbinfo,JSVM_Value* result)](#oh_jsvm_getnewtarget) | Obtains the new target called by the constructor. If the current callback is not called by a constructor, the result is **NULL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_NewInstance(JSVM_Env env,JSVM_Value constructor,size_t argc,const JSVM_Value* argv,JSVM_Value* result)](#oh_jsvm_newinstance) | Instantiates a new JavaScript value by using the constructor represented by the given **JSVM_Value**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClass(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value* result)](#oh_jsvm_defineclass) | Defines a JavaScript class.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Wrap(JSVM_Env env,JSVM_Value jsObject,void* nativeObject,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)](#oh_jsvm_wrap) | Wraps a native instance in a JavaScript object, which can be retrieved using **OH_JSVM_Unwrap()** later.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Unwrap(JSVM_Env env,JSVM_Value jsObject,void** result)](#oh_jsvm_unwrap) | Unwraps a native instance in a JavaScript object. When the JavaScript code calls a method of a class or property accessor, the corresponding **JSVM_Callback** is called. If the callback is for an instance method or accessor, the **this** parameter of the callback is the wrapper object. Then you can obtain the C++ instance as the call target by calling **OH_JSVM_Unwrap()** of the wrapper object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RemoveWrap(JSVM_Env env,JSVM_Value jsObject,void** result)](#oh_jsvm_removewrap) | Removes the wrap of the native instance, which is previously wrapped in **js_object** by **OH_JSVM_Wrap()**. If the **finalize** callback is associated with wrap, it will not be called when the JavaScript object is garbage-collected.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_TypeTagObject(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag)](#oh_jsvm_typetagobject) | Associates the value of the **typeTag** pointer with a JavaScript object or an external value. You can call **OH_JSVM_CheckObjectTypeTag()** to check the type of the tag attached to the object to ensure that the object type is correct. If the object already has an associated type tag, **JSVM_INVALID_ARG** is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CheckObjectTypeTag(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag,bool* result)](#oh_jsvm_checkobjecttypetag) | Checks the **typeTag** with the tag on a JavaScript object or external value. If they are the same tag, **result** is set to **true**. Otherwise, **result** is set to **false**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_AddFinalizer(JSVM_Env env,JSVM_Value jsObject,void* finalizeData,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)](#oh_jsvm_addfinalizer) | Adds the **JSVM_Finalize** callback to a JavaScript object. This callback is called when the JavaScript object is garbage-collected. **OH_JSVM_AddFinalizer** can be called multiple times on a single JavaScript object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVersion(JSVM_Env env,uint32_t* result)](#oh_jsvm_getversion) | Obtains the latest JSVM-API version supported by the JSVM runtime. New JSVM-API APIs will be added to support more features. With this API, the new features of a certain JSVM version can be used, or callbacks are provided if a feature is not supported.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVMInfo(JSVM_VMInfo* result)](#oh_jsvm_getvminfo) | Obtains the VM information.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_AdjustExternalMemory(JSVM_Env env,int64_t changeInBytes,int64_t* result)](#oh_jsvm_adjustexternalmemory) | Notifies the underlying VM of the size of externally allocated memory that remains active due to the JavaScript object. Registering externally allocated memory triggers global garbage collection more frequently than in other ways.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_MemoryPressureNotification(JSVM_Env env,JSVM_MemoryPressureLevel level)](#oh_jsvm_memorypressurenotification) | Notifies the VM of insufficient system memory and selectively triggers garbage collection.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreatePromise(JSVM_Env env,JSVM_Deferred* deferred,JSVM_Value* promise)](#oh_jsvm_createpromise) | Creates a deferred object and a JavaScript promise.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ResolveDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value resolution)](#oh_jsvm_resolvedeferred) | Resolves a JavaScript promise by using the associated deferred object. It can only be used to resolve the JavaScript promise of the corresponding available deferred object. This means that promise must be created using **OH_JSVM_CreatePromise()**, and the object returned from this call must be retained so that it can be passed to this API.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RejectDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value rejection)](#oh_jsvm_rejectdeferred) | Rejects a JavaScript promise by using the associated deferred object. It can only be used to reject the JavaScript promise of the corresponding available deferred object. This means that promise must be created using **OH_JSVM_CreatePromise()**, and the object returned from this call must be retained so that it can be passed to this API.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsPromise(JSVM_Env env,JSVM_Value value,bool* isPromise)](#oh_jsvm_ispromise) | Checks whether a promise object is native.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_PromiseRegisterHandler(JSVM_Env env,JSVM_Value promise,JSVM_Value onFulfilled,JSVM_Value onRejected,JSVM_Value* result)](#oh_jsvm_promiseregisterhandler) | Registers a handler for processing promise fulfillment and rejection.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_JsonParse(JSVM_Env env,JSVM_Value jsonString,JSVM_Value* result)](#oh_jsvm_jsonparse) | Parses a JSON string and returns the parsed value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_JsonStringify(JSVM_Env env,JSVM_Value jsonObject,JSVM_Value* result)](#oh_jsvm_jsonstringify) | Converts an object into a JSON string and returns the converted string.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSnapshot(JSVM_VM vm,size_t contextCount,const JSVM_Env* contexts,const char** blobData,size_t* blobSize)](#oh_jsvm_createsnapshot) | Creates a VM startup snapshot.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetHeapStatistics(JSVM_VM vm,JSVM_HeapStatistics* result)](#oh_jsvm_getheapstatistics) | Obtains heap statistics of a VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_StartCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler* result)](#oh_jsvm_startcpuprofiler) | Creates and starts a CPU profiler instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_StopCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler profiler,JSVM_OutputStream stream,void* streamData)](#oh_jsvm_stopcpuprofiler) | Stops the CPU profiler and outputs the result to a stream.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_TakeHeapSnapshot(JSVM_VM vm,JSVM_OutputStream stream,void* streamData)](#oh_jsvm_takeheapsnapshot) | Obtains a snapshot of the current heap and outputs it to a stream.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspector(JSVM_Env env,const char* host,uint16_t port)](#oh_jsvm_openinspector) | Opens an inspector instance on the specified host and port for debugging JS code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseInspector(JSVM_Env env)](#oh_jsvm_closeinspector) | Closes all remaining inspector connections.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_WaitForDebugger(JSVM_Env env,bool breakNextLine)](#oh_jsvm_waitfordebugger) | Waits for the host to set up a socket connection with an inspector. After the connection is set up, the application continues to run. **Runtime.runIfWaitingForDebugger** is sent.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithPropertyHandler(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_PropertyHandlerCfg propertyHandlerCfg,JSVM_Callback callAsFunctionCallback,JSVM_Value* result)](#oh_jsvm_defineclasswithpropertyhandler) | Defines a set of JavaScript class property handlers including **getter**, **setter**, **deleter**, and **enumerator** with the given class name, constructor, properties, and callback, which are called as callbacks.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsLocked(JSVM_Env env, bool* isLocked)](#oh_jsvm_islocked) | Checks whether the current thread holds a lock of the specified environment. Only the thread that holds the lock can use the environment.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_AcquireLock(JSVM_Env env)](#oh_jsvm_acquirelock) | Obtains a lock. Only the thread that holds the lock can use the environment.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseLock(JSVM_Env env)](#oh_jsvm_releaselock) | Releases a lock. Only the thread that holds the lock can use the environment.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsUndefined(JSVM_Env env,JSVM_Value value,bool* isUndefined)](#oh_jsvm_isundefined) | Checks whether the input value is **Undefined**. This API is equivalent to **value === undefined** in JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNull(JSVM_Env env,JSVM_Value value,bool* isNull)](#oh_jsvm_isnull) | Checks whether the input value is a **Null** object. This API is equivalent to **value === null** in JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNullOrUndefined(JSVM_Env env,JSVM_Value value,bool* isNullOrUndefined)](#oh_jsvm_isnullorundefined) | Checks whether the input value is **Null** or **Undefined**. This API is equivalent to **value == null** in JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBoolean(JSVM_Env env,JSVM_Value value,bool* isBoolean)](#oh_jsvm_isboolean) | Checks whether the input value is a Boolean value. This API is equivalent to **typeof value ==='boolean'** in JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNumber(JSVM_Env env,JSVM_Value value,bool* isNumber)](#oh_jsvm_isnumber) | Checks whether the input value is a number. This API is equivalent to **typeof value === 'number'** in JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsString(JSVM_Env env,JSVM_Value value,bool* isString)](#oh_jsvm_isstring) | Checks whether the input value is a string. This API is equivalent to **typeof value === 'string'** in JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbol(JSVM_Env env,JSVM_Value value,bool* isSymbol)](#oh_jsvm_issymbol) | Checks whether the input value is a symbol. This API is equivalent to **typeof value === 'symbol'** in JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsFunction(JSVM_Env env,JSVM_Value value,bool* isFunction)](#oh_jsvm_isfunction) | Checks whether the input value is a function. This API is equivalent to **typeof value === 'function'** in JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsObject(JSVM_Env env,JSVM_Value value,bool* isObject)](#oh_jsvm_isobject) | Checks whether the input value is an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBigInt(JSVM_Env env,JSVM_Value value,bool* isBigInt)](#oh_jsvm_isbigint) | Checks whether the input value is a BigInt value. This API is equivalent to **typeof value === 'bigint'** in JavaScript code.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateMap(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_createmap) | Creates a JavaScript value of the Map type.|
| [JSVM_Status JSVM_CDECL OH_JSVM_IsMap(JSVM_Env env,JSVM_Value value,bool* isMap)](#oh_jsvm_ismap) | Checks whether the input value is of the Map type.|
| [JSVM_Status JSVM_CDECL OH_JSVM_IsConstructor(JSVM_Env env,JSVM_Value value,bool* isConstructor)](#oh_jsvm_isconstructor) | Checks whether the input value is a constructor.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateRegExp(JSVM_Env env,JSVM_Value value,JSVM_RegExpFlags flags,JSVM_Value* result)](#oh_jsvm_createregexp) | Creates a regular expression object corresponding to the input JavaScript string. This API may throw an exception.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectGetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value* result)](#oh_jsvm_objectgetprototypeof) | Obtains the prototype of a JavaScript object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value prototype)](#oh_jsvm_objectsetprototypeof) | Sets the prototype of a JavaScript object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSet(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_createset) | Creates a JavaScript value of the Set type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSet(JSVM_Env env,JSVM_Value value,bool* isSet)](#oh_jsvm_isset) | Checks whether the specified object is of the Set type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBigInt(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetobigint) | Implements the abstract operation **ToBigInt()**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsRegExp(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isregexp) | Checks whether the input value is a JavaScript RegExp object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunctionWithScript(JSVM_Env env,const char* funcName,size_t length,size_t argc,const JSVM_Value* argv,JSVM_Value script,JSVM_Value* result)](#oh_jsvm_createfunctionwithscript) | Creates a function with the given JavaScript as the function body.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_PumpMessageLoop(JSVM_VM vm,bool* result)](#oh_jsvm_pumpmessageloop) | Starts the message loop in the VM. This message loop can be executed through the external event loop.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_PerformMicrotaskCheckpoint(JSVM_VM vm)](#oh_jsvm_performmicrotaskcheckpoint) | Checks whether there are microtasks waiting in the queue. If yes, execute them.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsCallable(JSVM_Env env, JSVM_Value value, bool* isCallable)](#oh_jsvm_iscallable) | Checks whether the input value is callable.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RetainScript(JSVM_Env env, JSVM_Script script)](#oh_jsvm_retainscript) | Retains a **JSVM_Script** and extends its lifecycle beyond the current scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseScript(JSVM_Env env, JSVM_Script script)](#oh_jsvm_releasescript) | Releases the script retained by **OH_JSVM_RetainScript**. The released script cannot be used again.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspectorWithName(JSVM_Env env,int pid,const char* name)](#oh_jsvm_openinspectorwithname) | Opens the **name** inspector and its corresponding Unix Domain port with the specified PID.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmModule(JSVM_Env env,const uint8_t *wasmBytecode,size_t wasmBytecodeLength,const uint8_t *cacheData,size_t cacheDataLength,bool *cacheRejected,JSVM_Value *wasmModule)](#oh_jsvm_compilewasmmodule) | Compiles the WebAssembly bytecode to obtain a WebAssembly module. If the WebAssembly cache is provided, it will be deserialized first. If this API does not have the JIT permission, a log is printed to notify you.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmFunction(JSVM_Env env,JSVM_Value wasmModule,uint32_t functionIndex,JSVM_WasmOptLevel optLevel)](#oh_jsvm_compilewasmfunction) | Compiles a WebAssembly function with the specified index at a specified optimization level. If this API does not have the JIT permission, a log is printed to notify you.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsWasmModuleObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_iswasmmoduleobject) | Checks whether the given **JSVM_Value** is a WebAssembly module.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateWasmCache(JSVM_Env env,JSVM_Value wasmModule,const uint8_t** data,size_t* length)](#oh_jsvm_createwasmcache) | Creates a WebAssembly cache. If this API does not have the JIT permission, a log is printed to notify you.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseCache(JSVM_Env env,const uint8_t* cacheData,JSVM_CacheType cacheType)](#oh_jsvm_releasecache) | Releases the cache of a specified type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBigIntObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isbigintobject) | Checks whether the given **JSVM_Value** is a BigInt object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBooleanObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isbooleanobject) | Checks whether the given **JSVM_Value** is a Boolean object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsStringObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isstringobject) | Checks whether the given **JSVM_Value** is a string object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNumberObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isnumberobject) | Checks whether the given **JSVM_Value** is a number object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbolObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_issymbolobject) | Checks whether the given **JSVM_Value** is a symbol object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolAsyncIterator(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolasynciterator) | Obtains the **Symbol.AsyncIterator** capability from the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolHasInstance(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolhasinstance) | Obtains the **Symbol.HasInstance** capability from the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIsConcatSpreadable(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolisconcatspreadable) | Obtains the **Symbol.IsConcatSpreadable** capability from the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolMatch(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolmatch) | Obtains the **Symbol.Match** capability of the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolReplace(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolreplace) | Obtains the **Symbol.Replace** capability of the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSearch(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolsearch) | Obtains the **Symbol.Search** capability of the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSplit(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolsplit) | Obtains the **Symbol.Split** capability of the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToPrimitive(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboltoprimitive) | Obtains the **Symbol.ToPrimitive** capability of the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolUnscopables(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolunscopables) | Obtains the **Symbol.Unscopables** capability of the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToStringTag(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboltostringtag) | Obtains the **Symbol.ToStringTag** capability of the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIterator(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboliterator) | Obtains the **Symbol.Iterator** capability of the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_TraceStart(size_t count,const JSVM_TraceCategory* categories,const char* tag,size_t eventsCount)](#oh_jsvm_tracestart) | Starts collecting information of the specified trace categories for all JSVM runtime instances (thread-unsafe).|
| [JSVM_EXTERN JSVM_Status OH_JSVM_TraceStop(JSVM_OutputStream stream, void* streamData)](#oh_jsvm_tracestop) | Stops collecting information of a specified trace category for all JSVM runtime instances (thread-unsafe).|
| [JSVM_EXTERN JSVM_Status OH_JSVM_AddHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,JSVM_GCType gcType,void* userData)](#oh_jsvm_addhandlerforgc) | Adds a handler for GC to the VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RemoveHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,void* userData)](#oh_jsvm_removehandlerforgc) | Removes the handler for GC from the VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForOOMError(JSVM_VM vm,JSVM_HandlerForOOMError handler)](#oh_jsvm_sethandlerforoomerror) | Sets a handler for OOM errors. If the API is called repeatedly, only the last call takes effect. If the input handler is null, the previous setting is canceled.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetDebugOption(JSVM_Env env, JSVM_DebugOption debugOption, bool isEnabled)](#oh_jsvm_setdebugoption) | Enables or disables a specific debugging option for a JSVM environment.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForFatalError(JSVM_VM vm,JSVM_HandlerForFatalError handler)](#oh_jsvm_sethandlerforfatalerror) | Sets a handler for fatal errors. If the API is called repeatedly, only the last call takes effect. If the input handler is null, the previous setting is canceled.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForPromiseReject(JSVM_VM vm,JSVM_HandlerForPromiseReject handler)](#oh_jsvm_sethandlerforpromisereject) | Sets a handler for the PromiseReject error. If the API is called repeatedly, only the last call takes effect. If the input handler is null, the previous setting is canceled.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithOptions(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value parentClass,size_t optionCount,JSVM_DefineClassOptions options[],JSVM_Value* result)](#oh_jsvm_defineclasswithoptions) | Defines a class with options. When a C++ class is encapsulated, the C++ constructor callback passed through the constructor should be a static method in the class. This method calls the actual class constructor, encapsulates a new C++ instance into a JavaScript object based on the input options, and returns the encapsulated object.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringLatin1(JSVM_Env env,char* str,size_t length,JSVM_Finalize finalizeCallback,void* finalizeHint,JSVM_Value* result,bool* copied)](#oh_jsvm_createexternalstringlatin1) | Creates an external JavaScript string with an ISO-8859-1-encoded C string. If the creation fails, the original native string is copied.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringUtf16(JSVM_Env env,char16_t* str,size_t length,JSVM_Finalize finalizecallback,void* finalizeHint,JSVM_Value* result,bool* copied)](#oh_jsvm_createexternalstringutf16) | Creates an external JavaScript string with a UTF-16LE-encoded C string. If the creation fails, the original native string is copied.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreatePrivate(JSVM_Env env,JSVM_Value description,JSVM_Data* result)](#oh_jsvm_createprivate) | Creates a JavaScript private key object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value value)](#oh_jsvm_setprivate) | Sets the **private** property for an input object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value *result)](#oh_jsvm_getprivate) | Obtains the **private** property of an input object based on the private key.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeletePrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key)](#oh_jsvm_deleteprivate) | Deletes the **private** property corresponding to the private key from the input object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataReference(JSVM_Env env,JSVM_Data data,uint32_t initialRefcount,JSVM_Ref* result)](#oh_jsvm_createdatareference) | Creates a reference to a given **JSVM_Data** object. The initial reference count is the input value of **initialRefcount**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceData(JSVM_Env env,JSVM_Ref ref,JSVM_Data* result)](#oh_jsvm_getreferencedata) | Obtains the **JSVM_Data** (a JavaScript value associated with the JSVM reference) through the **result** parameter if the reference is still valid. Otherwise, the result is null.|

## Function Description

### OH_JSVM_Init()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Init(const JSVM_InitOptions* options)
```

**Description**

Initializes a JavaScript VM.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const JSVM_InitOptions](capi-jsvm-jsvm-initoptions.md)* options | Pointer to the options for initializing the JavaScript VM.|

**Returns**

| Type                                                         | Description|
|-------------------------------------------------------------| -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the operation fails, indicating that JSVM initialization is complete and that repeated execution is not required.|

### OH_JSVM_CreateVM()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateVM(const JSVM_CreateVMOptions* options,JSVM_VM* result)
```

**Description**

Creates a VM instance.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const JSVM_CreateVMOptions](capi-jsvm-jsvm-createvmoptions.md)* options | Pointer to the options for creating a VM instance.|
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md)* result | Pointer to the new VM instance.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_SetMicrotaskPolicy()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetMicrotaskPolicy(JSVM_VM vm,JSVM_MicrotaskPolicy policy)
```

**Description**

Sets the microtask execution policy for a VM instance. If this method is not called, the default policy **JSVM_MicrotaskPolicy::JSVM_MICROTASK_AUTO** is used.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | Target VM instance.|
| [JSVM_MicrotaskPolicy](capi-jsvm-types-h.md#jsvm_microtaskpolicy) policy | Policy for executing microtasks.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns **JSVM_OK** if this API call is successful.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_DestroyVM()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DestroyVM(JSVM_VM vm)
```

**Description**

Destroys a VM instance.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM instance to be destroyed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_CreateProxy()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateProxy(JSVM_Env env,JSVM_Value target,JSVM_Value handler,JSVM_Value* result)
```

**Description**

Creates a JavaScript proxy. This API is equivalent to calling **new Proxy(target, handler)** in JS.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) target | JavaScript object used to create a proxy.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) handler | Handler that defines the operations to be intercepted and how to handle intercepted operations.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JavaScript proxy created.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status): object expected. This code is returned if the target or handler is not a JavaScript object.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_IsProxy()

```c
JSVM_Status JSVM_CDECL OH_JSVM_IsProxy(JSVM_Env env,JSVM_Value value,bool* isProxy)
```

**Description**

Checks whether the input value is a JavaScript proxy.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Value to check.|
| bool* isProxy | Pointer to the check result, indicating whether the value is a JavaScript Proxy. The value **true** indicates the value is a JavaScript Proxy, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_ProxyGetTarget()

```c
JSVM_Status JSVM_CDECL OH_JSVM_ProxyGetTarget(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Obtains the target object in the JavaScript Proxy.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Proxy of the target object.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the target object.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_INVALID_TYPE](capi-jsvm-types-h.md#jsvm_status): invalid type. This code is returned if the value is not a JavaScript Proxy.|

### OH_JSVM_OpenVMScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenVMScope(JSVM_VM vm,JSVM_VMScope* result)
```

**Description**

Opens a new VM scope for a VM instance.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | Target VM instance.|
| [JSVM_VMScope](capi-jsvm-jsvm-vmscope--8h.md)* result | Pointer to the new VM scope.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CloseVMScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseVMScope(JSVM_VM vm,JSVM_VMScope scope)
```

**Description**

Closes the VM scope of a VM instance.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | Target VM instance.|
| [JSVM_VMScope](capi-jsvm-jsvm-vmscope--8h.md) scope | VM scope to be closed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateEnv()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnv(JSVM_VM vm,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Env* result)
```

**Description**

Creates a new environment based on the optional properties of the new context.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM instance, in which the new environment will be created.|
| size_t propertyCount | Number of elements in the property array.|
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Pointer to the array of property descriptors.|
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md)* result | Pointer to the new environment.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateEnvFromSnapshot()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnvFromSnapshot(JSVM_VM vm,size_t index,JSVM_Env* result)
```

**Description**

Creates a new environment based on the startup snapshot of the VM.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM instance, in which the new environment will be created.|
| size_t index | Index of the environment in the snapshot.|
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md)* result | Pointer to the new environment.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_DestroyEnv()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DestroyEnv(JSVM_Env env)
```

**Description**

Destroys the environment.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment to be destroyed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_OpenEnvScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenEnvScope(JSVM_Env env,JSVM_EnvScope* result)
```

**Description**

Opens a new environment scope.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_EnvScope](capi-jsvm-jsvm-envscope--8h.md)* result | Pointer to the new environment scope.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CloseEnvScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseEnvScope(JSVM_Env env,JSVM_EnvScope scope)
```

**Description**

Closes the environment scope.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_EnvScope](capi-jsvm-jsvm-envscope--8h.md) scope | Environment scope to be closed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetVM()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetVM(JSVM_Env env,JSVM_VM* result)
```

**Description**

Obtains a VM instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md)* result | Pointer to the VM instance of the specified environment.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CompileScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScript(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_Script* result)
```

**Description**

Compiles a JavaScript code snippet and returns the compiled script.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | JavaScript code that includes the script to be compiled.|
| const uint8_t* cachedData | (Optional) Pointer to the code cache data of the script.|
| size_t cacheDataLength | Length of the **cachedData** array.|
| bool eagerCompile | Whether to compile the script immediately. The value **true** indicates that the script should be compiled immediately, and **false** indicates the opposite.|
| bool* cacheRejected | Pointer to the Boolean value, indicating whether the code cache is rejected. The value **true** indicates the code cache is rejected, and **false** indicates the opposite.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md)* result | Pointer to the compiled script.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CompileScriptWithOrigin()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOrigin(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_ScriptOrigin* origin,JSVM_Script* result)
```

**Description**

Compiles a JavaScript code snippet that contains source map information and returns the compiled script.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | JavaScript code that includes the script to be compiled.|
| const uint8_t* cachedData | (Optional) Pointer to the code cache data of the script.|
| size_t cacheDataLength | Length of the **cachedData** array.|
| bool eagerCompile | Whether to compile the script immediately. The value **true** indicates that the script should be compiled immediately, and **false** indicates the opposite.|
| bool* cacheRejected | Pointer to the Boolean value, indicating whether the code cache is rejected. The value **true** indicates the code cache is rejected, and **false** indicates the opposite.|
| [JSVM_ScriptOrigin](capi-jsvm-jsvm-scriptorigin.md)* origin | Pointer to the source code information, including the source map location and source code file name.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md)* result | Pointer to the compiled script.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CompileScriptWithOptions()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOptions(JSVM_Env env,JSVM_Value script,size_t optionCount,JSVM_CompileOptions options[],JSVM_Value* result)
```

**Description**

Compiles a JavaScript code snippet and returns the compiled script.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | JavaScript code that includes the script to be compiled.|
| size_t optionCount | Length of the input options array.|
| JSVM_CompileOptions options[] | Array of options, which stores all compilation options.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the compiled script.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the input data is a null pointer.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CreateCodeCache()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateCodeCache(JSVM_Env env,JSVM_Script script,const uint8_t** data,size_t* length)
```

**Description**

Creates a code cache for the compiled script.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | Target script.|
| const uint8_t** data | Double pointer to the code cache data.|
| size_t* length | Pointer to the length of the code cache data.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure.|

### OH_JSVM_RunScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RunScript(JSVM_Env env,JSVM_Script script,JSVM_Value* result)
```

**Description**

Runs a JavaScript code snippet and returns its result, including the following precautions: Unlike eval, this function does not allow the script to access the current lexical scope, and therefore does not allow the script to access the module scope. This means that pseudo-global variables such as **require** will be unavailable. The script can access the global scope. The functions and variable declarations in the script will be added to the global object. Variable declarations using **let** and **const** are globally visible, but are not added to the global object. The value of **this** is **global** in the script. Without the JIT permission, the script containing WebAssembly fails to be executed. The performance varies in specific scenarios, and a log is printed to notify you.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | JavaScript string that includes the script to be executed.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the value generated after the script is executed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_SetInstanceData()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetInstanceData(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint)
```

**Description**

Sets instance data so that it is associated with the currently running JSVM environment. You can use **OH_JSVM_GetInstanceData()** to obtain data later. Any existing data set by a previous call to **OH_JSVM_SetInstanceData()** will be overwritten. If **finalizeCb** was previously provided, it will not be called.

**Since**: 11


**Parameters**

| Name                                                           | Description|
|----------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                      | Environment for calling the JSVM-API.|
| void* data                                                     | Pointer to the data bound for this instance.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | Function for destroying the environment.|
| void* finalizeHint                                             | Pointer to the optional hint passed to the **finalize** callback during garbage collection.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetInstanceData()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetInstanceData(JSVM_Env env,void** data)
```

**Description**

Obtains instance data that has been set by **OH_JSVM_SetInstanceData()**. If no associated data is set, this function is called successfully and **data** is set to **NULL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| void** data | Double pointer to the data that has been set by **OH_JSVM_SetInstanceData()**, associated with the current JSVM environment.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetLastErrorInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetLastErrorInfo(JSVM_Env env,const JSVM_ExtendedErrorInfo** result)
```

**Description**

Obtains the **JSVM_ExtendedErrorInfo** struct that contains the last error. The content of **JSVM_ExtendedErrorInfo** returned is valid only before the JSVM-API function is called for the same environment. This includes a call to **OH_JSVM_IsExceptionPending**, so you may need to copy information for later use. The pointer returned in **error_message** points to a statically defined string, so if you copy it from the **error_message** field (which will be overwritten) before calling another JSVM-API function, you can safely use the pointer.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [const JSVM_ExtendedErrorInfo](capi-jsvm-jsvm-extendederrorinfo.md)** result | Double pointer to the **JSVM_ExtendedErrorInfo** struct that contains more information about the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_Throw()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Throw(JSVM_Env env,JSVM_Value error)
```

**Description**

Throws the provided JavaScript value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) error | JavaScript error to be thrown.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_ThrowError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowError(JSVM_Env env,const char* code,const char* msg)
```

**Description**

Throws a JavaScript Error with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* code | Pointer to the optional error code to be set on the error.|
| const char* msg | Pointer to the C string representing the text associated with the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_ThrowTypeError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowTypeError(JSVM_Env env,const char* code,const char* msg)
```

**Description**

Throws a JavaScript TypeError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* code | Pointer to the optional error code to be set on the error.|
| const char* msg | Pointer to the C string representing the text associated with the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_ThrowRangeError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowRangeError(JSVM_Env env,const char* code,const char* msg)
```

**Description**

Throws a JavaScript RangeError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* code | Pointer to the optional error code to be set on the error.|
| const char* msg | Pointer to the C string representing the text associated with the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_ThrowSyntaxError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowSyntaxError(JSVM_Env env,const char* code,const char* msg)
```

**Description**

Throws a JavaScript SyntaxError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* code | Pointer to the optional error code to be set on the error.|
| const char* msg | Pointer to the C string representing the text associated with the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsError(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given **JSVM_Value** indicates an error.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* result | Pointer to the check result. The value **true** means the **JSVM_Value** indicates an error, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**Description**

Creates a JavaScript Error with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | Optional **JSVM_Value**, which is a string with the associated error code.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | Message that references the JavaScript string as an error.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the creation error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.|

### OH_JSVM_CreateTypeError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**Description**

Creates a JavaScript TypeError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | Optional **JSVM_Value**, which is a string with the associated error code.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | Message that references the JavaScript string as an error.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the creation error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.|

### OH_JSVM_CreateRangeError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateRangeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**Description**

Creates a JavaScript RangeError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | Optional **JSVM_Value**, which is a string with the associated error code.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | Message that references the JavaScript string as an error.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the creation error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.|

### OH_JSVM_CreateSyntaxError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSyntaxError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**Description**

Creates a JavaScript SyntaxError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | Optional **JSVM_Value**, which is a string with the associated error code.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | Message that references the JavaScript string as an error.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the creation error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.|

### OH_JSVM_GetAndClearLastException()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetAndClearLastException(JSVM_Env env,JSVM_Value* result)
```

**Description**

Obtains and clears the last exception. If pending occurs, a JavaScript exception is returned. Otherwise, **NULL** is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the exception. An exception is returned if pending occurs. Otherwise, **NULL** is returned.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsExceptionPending()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsExceptionPending(JSVM_Env env,bool* result)
```

**Description**

Checks whether the last exception is caused by pending. If yes, **true** is returned. Otherwise, **false** is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| bool* result | Pointer to the exception. The value **true** indicates the last exception is caused by pending, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_OpenHandleScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenHandleScope(JSVM_Env env,JSVM_HandleScope* result)
```

**Description**

Opens a new handle scope.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_HandleScope](capi-jsvm-jsvm-handlescope--8h.md)* result | Pointer to the new handle scope.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CloseHandleScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseHandleScope(JSVM_Env env,JSVM_HandleScope scope)
```

**Description**

(Mandatory) Closes the handle scope in the reverse order of opening it.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_HandleScope](capi-jsvm-jsvm-handlescope--8h.md) scope | Handle scope to be closed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_HANDLE_SCOPE_MISMATCH](capi-jsvm-types-h.md#jsvm_status): handle scope mismatch.|

### OH_JSVM_OpenEscapableHandleScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope* result)
```

**Description**

Opens an escapable handle scope.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_EscapableHandleScope](capi-jsvm-jsvm-escapablehandlescope--8h.md)* result | Pointer to the new escapable handle scope.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CloseEscapableHandleScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope scope)
```

**Description**

(Mandatory) Closes the escapable handle scope in the reverse order of opening it. This JSVM_API can be called even if there is a pending JavaScript exception.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_EscapableHandleScope](capi-jsvm-jsvm-escapablehandlescope--8h.md) scope | Escapable handle scope to be closed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_HANDLE_SCOPE_MISMATCH](capi-jsvm-types-h.md#jsvm_status): handle scope mismatch.|

### OH_JSVM_EscapeHandle()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_EscapeHandle(JSVM_Env env,JSVM_EscapableHandleScope scope,JSVM_Value escapee,JSVM_Value* result)
```

**Description**

Escapes a handle of a JavaScript object so that it is valid through the lifecycle of the outer scope. Each scope can be called only once. If it is called for multiple times, an error is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_EscapableHandleScope](capi-jsvm-jsvm-escapablehandlescope--8h.md) scope | Current scope.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) escapee | JavaScript object to be escaped.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the handle to be escaped.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_ESCAPE_CALLED_TWICE](capi-jsvm-types-h.md#jsvm_status): escape called twice. This code is returned if the scope object is closed.|

### OH_JSVM_CreateReference()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateReference(JSVM_Env env,JSVM_Value value,uint32_t initialRefcount,JSVM_Ref* result)
```

**Description**

Creates a reference with the specified reference count for the input value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM value for which a reference is being created.|
| uint32_t initialRefcount | Initial reference count of a new reference.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | Pointer to a new reference.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_DeleteReference()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteReference(JSVM_Env env,JSVM_Ref ref)
```

**Description**

Deletes the input reference.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | Reference to be deleted.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_ReferenceRef()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceRef(JSVM_Env env,JSVM_Ref ref,uint32_t* result)
```

**Description**

Increases the reference count and returns the new reference count.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | Input reference. Its reference count will increase.|
| uint32_t* result | Pointer to the new reference count.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_ReferenceUnref()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceUnref(JSVM_Env env,JSVM_Ref ref,uint32_t* result)
```

**Description**

Decreases the reference count and returns the new reference count.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | Input reference. Its reference count will decrease.|
| uint32_t* result | Pointer to the new reference count.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure.|

### OH_JSVM_GetReferenceValue()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceValue(JSVM_Env env,JSVM_Ref ref,JSVM_Value* result)
```

**Description**

Obtains the **JSVM_Value** returned by the JSVM-API, which is the JavaScript value associated with **JSVM_Ref**. If the value is invalid, **NULL** is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | JSVM reference for requesting the corresponding value.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** referenced by **JSVM_Ref**.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateArray()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArray(JSVM_Env env,JSVM_Value* result)
```

**Description**

Creates an array. This API returns the JSVM-API value of the JavaScript Array type.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JSVM value of the JavaScript Array type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateArrayWithLength()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayWithLength(JSVM_Env env,size_t length,JSVM_Value* result)
```

**Description**

Creates an array with a specified length. This API returns the JSVM-API value of the JavaScript Array type. The **length** property of the array is set to the input **length** parameter. However, there is no guarantee that the underlying buffer is pre-allocated by the VM when the array is created. This behavior is implemented by the underlying VM.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| size_t length | Initial length of the array.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JSVM value of the JavaScript Array type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateArraybuffer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArraybuffer(JSVM_Env env,size_t byteLength,void** data,JSVM_Value* result)
```

**Description**

Creates an array buffer. This API returns the JSVM-API value of the JavaScript ArrayBuffer type. ArrayBuffer is used to represent a fixed-length binary data buffer. It is usually used as the backup buffer of the **TypedArray** object. The allocated ArrayBuffer has an underlying byte buffer whose size is determined by the **length** parameter. The underlying buffer can be returned to and operated by the caller. This buffer can only be written directly from the native code. To write data from JavaScript to this buffer, you need to create a **TypedArray** or **DataView** object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| size_t byteLength | Length of the array buffer to be created, in bytes.|
| void** data | Double pointer to the underlying byte buffer of the ArrayBuffer. **data** can be ignored by passing **NULL** to it.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JSVM value of the JavaScript ArrayBuffer.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_AllocateArrayBufferBackingStoreData()

```c
JSVM_Status JSVM_CDECL OH_JSVM_AllocateArrayBufferBackingStoreData(size_t byteLength,JSVM_InitializedFlag initialized,void **data)
```

**Description**

Allocates a segment of BackingStore memory to the array buffer.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| size_t byteLength | Size of the BackingStore memory.|
| [JSVM_InitializedFlag](capi-jsvm-types-h.md#jsvm_initializedflag) initialized | Mode of initializing the BackingStore memory.|
| void **data | Double pointer to the address of allocated BackingStore memory.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the input data is a null pointer.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the memory application fails.|

### OH_JSVM_FreeArrayBufferBackingStoreData()

```c
JSVM_Status JSVM_CDECL OH_JSVM_FreeArrayBufferBackingStoreData(void *data)
```

**Description**

Frees the BackingStore memory allocated by **OH_JSVM_AllocateArrayBufferBackingStoreData**.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| void *data| Pointer to the allocated BackingStore memory.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the input data is a null pointer.|

### OH_JSVM_CreateArrayBufferFromBackingStoreData()

```c
JSVM_Status JSVM_CDECL OH_JSVM_CreateArrayBufferFromBackingStoreData(JSVM_Env env,void *data,size_t backingStoreSize,size_t offset,size_t arrayBufferSize,JSVM_Value *result)
```

**Description**

Creates an array buffer in the allocated BackingStore memory.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| void *data | Pointer to the allocated BackingStore memory.|
| size_t backingStoreSize | Size of the BackingStore memory.|
| size_t offset | Relative offset between the start position of the array buffer in the memory and the memory header, in bytes.|
| size_t arrayBufferSize | Size of the array buffer, in bytes.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) *result | Pointer to the array buffer address.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if one of the following exceptions occurs:<br>         1. The sum of **offset** and **arrayBufferSize** is larger than **backingStoreSize**.<br>         2. The value of **backingStoreSize** or **arrayBufferSize** is **0**.<br>         3. **data** or **result** is null.|

### OH_JSVM_CreateDate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDate(JSVM_Env env,double time,JSVM_Value* result)
```

**Description**

Creates a date. This API ignores leap seconds because ECMAScript complies with the POSIX time specifications.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| double time | ECMAScript time since 00:00:00 UTC on January 1, 1970, in milliseconds.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript **Date** object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CreateExternal()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternal(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Value* result)
```

**Description**

Creates a JavaScript value with external data. This is used to pass external data through JavaScript code. You can use **OH_JSVM_GetValueExternal** to retrieve the value from the native code. This API adds a **JSVM_Finalize** callback, which will be called when the newly created JavaScript object is garbage-collected. The created value is not an object, so it does not support additional properties. It is considered as a unique value type: Calling **OH_JSVM_Typeof()** with an external value generates **JSVM_EXTERNAL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| void* data | Raw pointer to external data.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | Optional callback used to collect external values. **JSVM_Finalize** provides more details.|
| void* finalizeHint | Pointer to the optional hint passed to the **finalize** callback during garbage collection.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of an external value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateObject(JSVM_Env env,JSVM_Value* result)
```

**Description**

Creates a default JavaScript object. This function is equivalent to executing **new Object()** in JavaScript.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateSymbol()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSymbol(JSVM_Env env,JSVM_Value description,JSVM_Value* result)
```

**Description**

Creates a JavaScript symbol value with a UTF-8-encoded C string.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) description | Optional **JSVM_Value**, which refers to the JavaScript string to be set to the symbol description.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.|

### OH_JSVM_SymbolFor()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SymbolFor(JSVM_Env env,const char* utf8description,size_t length,JSVM_Value* result)
```

**Description**

Searches the global registry for an existing symbol with the given description. This API returns the symbol if it already exists; otherwise, a symbol is created in the registry.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* utf8description | Pointer to the symbol description that is in a UTF-8-encoded C string.|
| size_t length | Length of the description string, in bytes. If it is null-terminated, the value is **JSVM_AUTO_LENGTH**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateTypedarray()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypedarray(JSVM_Env env,JSVM_TypedarrayType type,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)
```

**Description**

Creates a JavaScript **TypedArray** object based on an existing **ArrayBuffer** object. The **TypedArray** object provides an array-like view on the underlying data buffer, where each element has the same underlying binary scalar data type. The value of "**length** × element scalar bytes + **byteOffset**" must not be greater than the value of **ByteLength()** of the input array. Otherwise, a range error is thrown.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_TypedarrayType](capi-jsvm-types-h.md#jsvm_typedarraytype) type | Scalar data type of an element in **TypedArray**.|
| size_t length | Number of elements in **TypedArray**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | ArrayBuffer, which is the basis of **TypedArray**.|
| size_t byteOffset | Byte offset for the start position of mapping **TypedArray** in the ArrayBuffer.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript **TypedArray**.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CreateDataview()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataview(JSVM_Env env,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)
```

**Description**

Creates a JavaScript **DataView** object based on an existing **ArrayBuffer** object. The **DataView** object provides an array-like view on the underlying data buffer, where elements can have different sizes and types. The sum of the binary length and byte offset cannot be greater than the size (in bytes) of the input array. Otherwise, a range error is thrown.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| size_t length | Number of elements in **DataView**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | ArrayBuffer at the bottom layer of the **DataView**.|
| size_t byteOffset | Byte offset in the ArrayBuffer, indicating the start position of mapping a **DataView**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript **DataView** object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CreateInt32()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt32(JSVM_Env env,int32_t value,JSVM_Value* result)
```

**Description**

Converts a value of the C int32_t type to a value of the JavaScript number type.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| int32_t value | Integer value to be represented in JavaScript.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript number type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateUint32()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateUint32(JSVM_Env env,uint32_t value,JSVM_Value* result)
```

**Description**

Converts a value of the C uint32_t type to a value of the JavaScript number type.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| uint32_t value | Unsigned integer value to be represented in JavaScript.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript number type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateInt64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt64(JSVM_Env env,int64_t value,JSVM_Value* result)
```

**Description**

Converts a value of the C int64_t type to a value of the JavaScript number type.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| int64_t value | Integer value to be represented in JavaScript.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript number type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateDouble()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDouble(JSVM_Env env,double value,JSVM_Value* result)
```

**Description**

Converts a value of the C double type to a value of the JavaScript number type.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| double value | Double-precision value to be represented in JavaScript.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript number type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateBigintInt64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintInt64(JSVM_Env env,int64_t value,JSVM_Value* result)
```

**Description**

Converts a value of the C int64_t type to a value of the JavaScript BigInt type.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| int64_t value | Integer value to be represented in JavaScript.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript BigInt type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateBigintUint64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintUint64(JSVM_Env env,uint64_t value,JSVM_Value* result)
```

**Description**

Converts a value of the C uint64_t type to a value of the JavaScript BigInt type.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| uint64_t value | Unsigned integer value to be represented in JavaScript.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript BigInt type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateBigintWords()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintWords(JSVM_Env env,int signBit,size_t wordCount,const uint64_t* words,JSVM_Value* result)
```

**Description**

Converts a group of 64-bit unsigned bits to a single BigInt value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| int signBit | Whether the generated BigInt value is positive or negative.|
| size_t wordCount | Length of the words array.|
| const uint64_t* words | Pointer to the uint64_t little-endian words array.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript BigInt type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_CreateStringLatin1()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringLatin1(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)
```

**Description**

Converts an ISO-8859-1-encoded C string to a JavaScript string. A native string is copied.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* str | Pointer to the buffer of an ISO-8859-1-encoded string.|
| size_t length | Length of a string, in bytes. If it is null-terminated, the value is **JSVM_AUTO_LENGTH**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_CreateStringUtf16()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf16(JSVM_Env env,const char16_t* str,size_t length,JSVM_Value* result)
```

**Description**

Converts a UTF-16LE-encoded C string to a JavaScript string. A native string is copied.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char16_t* str | Pointer to the buffer of a UTF-16LE-encoded string.|
| size_t length | Length of a string in 2-byte code. If it is null-terminated, the value is **JSVM_AUTO_LENGTH**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_CreateStringUtf8()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf8(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)
```

**Description**

Creates a JavaScript string using a UTF-8-encoded C string. A native string is copied.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* str | Pointer to the buffer of a UTF-8-encoded string.|
| size_t length | Length of a string, in bytes. If it is null-terminated, the value is **JSVM_AUTO_LENGTH**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_GetArrayLength()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetArrayLength(JSVM_Env env,JSVM_Value value,uint32_t* result)
```

**Description**

Obtains the length of an array.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript array whose length is to be queried.|
| uint32_t* result | Pointer to the length of a uint32-encoded array.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_ARRAY_EXPECTED](capi-jsvm-types-h.md#jsvm_status): array expected. This code is returned if the input parameter is not of the array type.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_GetArraybufferInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetArraybufferInfo(JSVM_Env env,JSVM_Value arraybuffer,void** data,size_t* byteLength)
```

**Description**

Obtains the underlying data buffer of the **ArrayBuffer** and its length.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | ArrayBuffer to be queried.|
| void** data | Double pointer to the underlying data buffer of the ArrayBuffer. If **byte_length** is **0**, this value may be **NULL** or any other pointer value.|
| size_t* byteLength | Pointer to the length of the underlying data buffer, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_GetPrototype()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetPrototype(JSVM_Env env,JSVM_Value object,JSVM_Value* result)
```

**Description**

Obtains the prototype of an object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | JavaScript object whose prototype is to be returned. This will return the equivalent value of **Object.getPrototypeOf** (different from the **prototype** property of the function).|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the prototype of a given object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_GetTypedarrayInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetTypedarrayInfo(JSVM_Env env,JSVM_Value typedarray,JSVM_TypedarrayType* type,size_t* length,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)
```

**Description**

Obtains the properties of a typed array. If any property is not required, its output parameter can be **NULL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) typedarray | **TypedArray** whose properties are to be queried.|
| [JSVM_TypedarrayType](capi-jsvm-types-h.md#jsvm_typedarraytype)* type | Pointer to the scalar data type of an element in TypedArray.|
| size_t* length | Pointer to the number of elements in **TypedArray**.|
| void** data | Double pointer to the first element in **TypedArray**. The underlying data buffer of the **TypedArray** is adjusted by **byte_offset** so that it points to the first element. If the array length is **0**, **data** may be NULL or any other pointer value.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* arraybuffer | Pointer to the **ArrayBuffer** under **TypedArray**.|
| size_t* byteOffset | Pointer to the byte offset of the first **TypedArray** element in the native array. **data** points to the first element in the array after its value has been adjusted. Therefore, the first byte of the native array is located at (data - byte_offset).|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_GetDataviewInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetDataviewInfo(JSVM_Env env,JSVM_Value dataview,size_t* bytelength,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)
```

**Description**

Obtains the proprieties of a **DataView**. If any property is not required, its output parameter can be **NULL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) dataview |  **DataView** whose properties are to be queried.|
| size_t* bytelength | Pointer to the number of bytes in **DataView**.|
| void** data | Double pointer to the data buffer in **DataView**. If **bytelength** is **0**, this value may be **NULL** or any other pointer value.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* arraybuffer | Pointer to the **ArrayBuffer**, which is the basis of **DataView**.|
| size_t* byteOffset | Pointer to the byte offset for the start position of mapping **DataView** in the data buffer.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the input argument is not an external **JSVM_Value**.|

### OH_JSVM_GetDateValue()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetDateValue(JSVM_Env env,JSVM_Value value,double* result)
```

**Description**

Obtains the C double-precision primitive equivalent of a given JavaScript date. If this API call is successfully, **JSVM_OK** is returned. If a **JSVM_Value** of a non-JavaScript date type is passed in, **JSVM_DATA_EXPECTED** is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript date.|
| double* result | Pointer to the time value of the double type, expressed as the number of milliseconds since 00:00:00 UTC on January 1, 1970.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_DATE_EXPECTED](capi-jsvm-types-h.md#jsvm_status): date expected. This code is returned if the input argument is not of the date type.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_GetValueBool()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBool(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Obtains the C Boolean primitive equivalent of a given JavaScript Boolean value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Input JavaScript Boolean object.|
| bool* result | Pointer to the Boolean value equivalent to the given JavaScript Boolean object. If the value of the **value** object is **true**, **true** is returned; otherwise, **false** is returned.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_BOOLEAN_EXPECTED](capi-jsvm-types-h.md#jsvm_status): Boolean expected. This code is returned if the input parameter is not of the Boolean type.|

### OH_JSVM_GetValueDouble()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueDouble(JSVM_Env env,JSVM_Value value,double* result)
```

**Description**

Obtains the C double-precision primitive equivalent of a given JavaScript number.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| double* result | Pointer to the C double-precision primitive equivalent of a given JavaScript number.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status): number expected. This code is returned if the input parameter is not of the number type.|

### OH_JSVM_GetValueBigintInt64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintInt64(JSVM_Env env,JSVM_Value value,int64_t* result,bool* lossless)
```

**Description**

Obtains the C int64_t primitive equivalent of a given JavaScript BigInt value. If necessary, it truncates the value and sets **lossless** to **false**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript BigInt value.|
| int64_t* result | Pointer to the C int64_t primitive equivalent of the given JavaScript BigInt value.|
| bool* lossless | Pointer to the Boolean value. The value **true** indicates the BigInt value is losslessly converted, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status): BigInt expected. This code is returned if the input parameter is not of the BigInt type.|

### OH_JSVM_GetValueBigintUint64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintUint64(JSVM_Env env,JSVM_Value value,uint64_t* result,bool* lossless)
```

**Description**

Obtains the C uint64_t primitive equivalent of a given JavaScript BigInt value. If necessary, it truncates the value and sets **lossless** to **false**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript BigInt value.|
| uint64_t* result | Pointer to the C uint64_t primitive equivalent of the given JavaScript BigInt value.|
| bool* lossless | Pointer to the Boolean value. The value **true** indicates the BigInt value is losslessly converted, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status): BigInt expected. This code is returned if the input parameter is not of the BigInt type.|

### OH_JSVM_GetValueBigintWords()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintWords(JSVM_Env env,JSVM_Value value,int* signBit,size_t* wordCount,uint64_t* words)
```

**Description**

Converts a BigInt value to the sign bit, 64-bit little-endian array, and number of elements in the array. Both **signBit** and **words** can be set to **NULL**. In this case, only **wordCount** is obtained.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript BigInt value.|
| int* signBit | Pointer to the JavaScript BigInt value, indicating a positive or negative integer.|
| size_t* wordCount | Pointer to the length of the words array. It will be set to the actual number of words required to store this BigInt.|
| uint64_t* words | Pointer to the pre-allocated 64-bit words array.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status): BigInt expected. This code is returned if the input parameter is not of the BigInt type.|

### OH_JSVM_GetValueExternal()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueExternal(JSVM_Env env,JSVM_Value value,void** result)
```

**Description**

Obtains the external data pointer previously passed to **OH_JSVM_CreateExternal()**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript external value.|
| void** result | Double pointer to the data wrapped by the JavaScript external value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the input argument is not an external **JSVM_Value**.|

### OH_JSVM_GetValueInt32()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt32(JSVM_Env env,JSVM_Value value,int32_t* result)
```

**Description**

Obtains the C int32 primitive equivalent of a given JavaScript number.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| int32_t* result | Pointer to the C int32 primitive equivalent of the given JavaScript number.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status): number expected. This code is returned if the input parameter is not of the number type.|

### OH_JSVM_GetValueInt64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt64(JSVM_Env env,JSVM_Value value,int64_t* result)
```

**Description**

Obtains the C int64 primitive equivalent of a given JavaScript number.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| int64_t* result | Pointer to the C int64 primitive equivalent of the given JavaScript number.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status): number expected. This code is returned if the input parameter is not of the number type.|

### OH_JSVM_GetValueStringLatin1()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringLatin1(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)
```

**Description**

Obtains the ISO-8859-1-encoded string corresponding to the input value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| char* buf | Pointer to the buffer to which an ISO-8859-1 encoded string is written. If **NULL** is passed, the length of the string (in bytes, excluding the **null** terminator) is returned in **result**.|
| size_t bufsize | Size of the destination buffer. If the size is insufficient, the returned string is truncated and terminated with **null**.|
| size_t* result | Pointer to the number of bytes copied to the buffer, excluding the null terminator.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.|

### OH_JSVM_GetValueStringUtf8()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf8(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)
```

**Description**

Obtains the UTF-8-encoded string corresponding to the input value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript string.|
| char* buf | Pointer to the buffer to which a UTF-8-encoded string is written. If **NULL** is passed, the length of the string in bytes is returned in **result**, excluding the null terminator.|
| size_t bufsize | Size of the destination buffer. If the size is insufficient, the returned string is truncated and terminated with **null**.|
| size_t* result | Pointer to the number of bytes copied to the buffer, excluding the null terminator.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.|

### OH_JSVM_GetValueStringUtf16()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf16(JSVM_Env env,JSVM_Value value,char16_t* buf,size_t bufsize,size_t* result)
```

**Description**

Obtains the UTF-16-encoded string corresponding to the input value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript string.|
| char16_t* buf | Pointer to the buffer to which a UTF-16LE-encoded string is written. If **NULL** is passed, the length of the string in 2-byte code is returned, excluding the null terminator.|
| size_t bufsize | Size of the destination buffer. If the size is insufficient, the returned string is truncated and terminated with **null**.|
| size_t* result | Pointer to the number of the 2-byte code units copied to the buffer, excluding the null terminator.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.|

### OH_JSVM_GetValueUint32()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueUint32(JSVM_Env env,JSVM_Value value,uint32_t* result)
```

**Description**

Obtains the C uint_32 primitive equivalent of a given JavaScript number.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| uint32_t* result | Pointer to the C uint32_t primitive equivalent of a given **JSVM_Value**.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status): number expected. This code is returned if the input parameter is not of the number type.|

### OH_JSVM_GetBoolean()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetBoolean(JSVM_Env env,bool value,JSVM_Value* result)
```

**Description**

Obtains a JavaScript singleton object that is used to represent the given Boolean value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| bool value | Boolean value to be retrieved. The value can be **true** or **false**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript Boolean singleton to be retrieved.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetGlobal()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetGlobal(JSVM_Env env,JSVM_Value* result)
```

**Description**

Obtains the global object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript global object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetNull()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetNull(JSVM_Env env,JSVM_Value* result)
```

**Description**

Obtains the null object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript null object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetUndefined()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetUndefined(JSVM_Env env,JSVM_Value* result)
```

**Description**

Obtains the undefined object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript undefined value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CoerceToBool()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBool(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation **ToBoolean()**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript Boolean value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CoerceToNumber()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToNumber(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation **ToNumber()**. If the input value is an object, the function may run JavaScript code.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript number.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status): number expected. This code is returned if the input JavaScript value cannot be converted to a number.|

### OH_JSVM_CoerceToObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToObject(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation **ToObject()**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status): object expected. This code is returned if the input JavaScript value cannot be converted to an object.|

### OH_JSVM_CoerceToString()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToString(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation **ToString()**. If the input value is an object, the function may run JavaScript code.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input JavaScript value cannot be converted to a string.|

### OH_JSVM_Typeof()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Typeof(JSVM_Env env,JSVM_Value value,JSVM_ValueType* result)
```

**Description**

Provides a behavior similar to calling the **typeof** operator on a defined object. The difference is that this function supports the detection of external values; it detects null as a separate type, while ECMAScript **typeof** is used to detect objects. If the value type is invalid, an error is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value whose type is to be queried.|
| [JSVM_ValueType](capi-jsvm-types-h.md#jsvm_valuetype)* result | Pointer to the type of the JavaScript value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_Instanceof()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Instanceof(JSVM_Env env,JSVM_Value object,JSVM_Value constructor,bool* result)
```

**Description**

Provides a behavior similar to calling the **instanceof** operator on an object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | JavaScript value to be checked.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) constructor | Constructor to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that **object instanceof constructor** is **true**, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_FUNCTION_EXPECTED](capi-jsvm-types-h.md#jsvm_status): function expected. This code is returned if the input parameter is not of the function type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_IsArray()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsArray(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Provides a behavior similar to calling **IsArray** on an object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the given object is an array, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsArraybuffer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the input object is an **ArrayBuffer**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the specified object is an **ArrayBuffer**, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsDate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsDate(JSVM_Env env,JSVM_Value value,bool* isDate)
```

**Description**

Checks whether the input object is a date.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* isDate | Pointer to the check result. The value **true** indicates that the given **JSVM_Value** is a JavaScript **Date** object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsTypedarray()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsTypedarray(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the input object is a typed array.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the given **JSVM_Value** is a typed array, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsDataview()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsDataview(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the input object is **DataView**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the given **JSVM_Value** is a **DataView**, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_StrictEquals()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_StrictEquals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)
```

**Description**

Provides a behavior similar to calling the strict equality algorithm (===).

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) lhs | JavaScript value to be checked.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rhs | Another JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that two **JSVM_Value** objects are strictly equal, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_Equals()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Equals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)
```

**Description**

Provides a behavior similar to calling the loose equality algorithm (==). Regardless of the JavaScript value type, **true** is returned as long as the values are equal.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) lhs | JavaScript value to be checked.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rhs | Another JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that two **JSVM_Value** objects are loosely equal, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_DetachArraybuffer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DetachArraybuffer(JSVM_Env env,JSVM_Value arraybuffer)
```

**Description**

Provides a behavior similar to calling the **detach** operation of **ArrayBuffer**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | JavaScript **ArrayBuffer** to be detached.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED](capi-jsvm-types-h.md#jsvm_status): ArrayBuffer expected. This code is returned if the input parameter is not an analyzable **ArrayBuffer**.|

### OH_JSVM_IsDetachedArraybuffer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsDetachedArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Provides a behavior similar to calling the **IsDetachedBuffer** operation of **ArrayBuffer**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript **ArrayBuffer** to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the **ArrayBuffer** is detached, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetPropertyNames()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_Value* result)
```

**Description**

Obtains the names of enumerable properties of an object as an array of characters. The properties of the object whose key is a symbol are not included.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be retrieved.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to an array of property names of the object. You can use **OH_JSVM_GetArrayLength** and **OH_JSVM_GetElement** to iterate the result.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_GetAllPropertyNames()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetAllPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_KeyCollectionMode keyMode,JSVM_KeyFilter keyFilter,JSVM_KeyConversion keyConversion,JSVM_Value* result)
```

**Description**

Obtains all available property names of the object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object from which the properties are retrieved.|
| [JSVM_KeyCollectionMode](capi-jsvm-types-h.md#jsvm_keycollectionmode) keyMode | Key collection mode for retrieving the prototype properties.|
| [JSVM_KeyFilter](capi-jsvm-types-h.md#jsvm_keyfilter) keyFilter | Key filter for properties to be retrieved (enumerable/readable/writable).|
| [JSVM_KeyConversion](capi-jsvm-types-h.md#jsvm_keyconversion) keyConversion | Key conversion mode, which determines whether to convert a number to a string.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to an array of property names of the object. You can use **OH_JSVM_GetArrayLength** and **OH_JSVM_GetElement** to iterate the result.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_SetProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value value)
```

**Description**

Sets the **key** property for the input object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be set.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | Name of the property to be set.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_GetProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value* result)
```

**Description**

Obtains the **key** property from the input object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object from which the property is retrieved.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | Name of the property to be retrieved.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_HasProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_HasProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)
```

**Description**

Checks whether the input object has the **key** property.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be checked.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | Name of the property to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the input object has the **key** property, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_DeleteProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)
```

**Description**

Deletes the **key** property from the object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Target object.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | Name of the property to be deleted.|
| bool* result | Pointer to the operation result. The value **true** indicates that the property deletion is successful, and **false** indicates the opposite. **result** can be ignored by passing **NULL** to it.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_HasOwnProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_HasOwnProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)
```

**Description**

Checks whether the input object has the **key** property. The key must be a string or symbol. Otherwise, an error is thrown. The JSVM-API does not perform any conversion between data types.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be checked.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | Name of the property to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the input object has the **key** property, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_NAME_EXPECTED](capi-jsvm-types-h.md#jsvm_status): name expected. This code is returned if the input name is invalid.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_SetNamedProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value value)
```

**Description**

Sets a property with a specified name. This method is equivalent to calling **OH_JSVM_SetProperty** to set the **utf8Name** property.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be set.|
| const char* utf8name | Pointer to the name of the property to be set.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_GetNamedProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value* result)
```

**Description**

Obtains the named property. This method is equivalent to calling **OH_JSVM_GetProperty** to obtain the **utf8Name** property.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object from which the property is retrieved.|
| const char* utf8name | Pointer to the name of the property to be obtained.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_HasNamedProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_HasNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,bool* result)
```

**Description**

Checks whether an object has the named property. This method is equivalent to calling **OH_JSVM_HasProperty** to check whether the object has the **utf8Name** property.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be checked.|
| const char* utf8name | Pointer to the name of the property to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the input object has the named property, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_SetElement()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value value)
```

**Description**

Sets an element for the input object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be set.|
| uint32_t index | Index of the property to be set.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_GetElement()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value* result)
```

**Description**

Obtains the element at the requested index.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be retrieved.|
| uint32_t index | Index of the property to be obtained.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_HasElement()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_HasElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)
```

**Description**

Checks whether an input object has an element at the specified index. If yes, the JSVM-API returns **true**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be checked.|
| uint32_t index | Index to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the input object has the specified element, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_DeleteElement()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)
```

**Description**

Deletes the element at the specified index from an object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Target object.|
| uint32_t index | Index of the element to be deleted.|
| bool* result | Pointer to the operation result. The value **true** indicates that the element deletion is successful, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_DefineProperties()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DefineProperties(JSVM_Env env,JSVM_Value object,size_t propertyCount,const JSVM_PropertyDescriptor* properties)
```

**Description**

Defines properties on a given object by using property descriptors. Through an array of property descriptors, this API sets the properties in the array in turn for the object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be retrieved.|
| size_t propertyCount | Pointer to the number of elements in the properties array.|
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Pointer to the array of property descriptors.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_ObjectFreeze()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectFreeze(JSVM_Env env,JSVM_Value object)
```

**Description**

Freezes a JavaScript object. Once a JavaScript object is frozen, new properties cannot be added to it, existing properties cannot be removed, the enumerability, configurability, or writability of existing properties cannot be changed, and the values of existing properties and object prototypes cannot be changed.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be frozen.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_ObjectSeal()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSeal(JSVM_Env env,JSVM_Value object)
```

**Description**

Encapsulates a specified object, which prevents additions of properties and marks existing properties non-configurable.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be encapsulated.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_CallFunction()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CallFunction(JSVM_Env env,JSVM_Value recv,JSVM_Value func,size_t argc,const JSVM_Value* argv,JSVM_Value* result)
```

**Description**

Supports calling JavaScript function objects from native code, which is the main mechanism for JavaScript to call native code.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) recv | Value of **this** passed to the callee.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) func | JavaScript function to be called.|
| size_t argc | Number of elements in the argv array.|
| [const JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | Pointer to the **JSVM_values** array, representing the JavaScript values to be passed to the function as arguments.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the returned JavaScript object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_CreateFunction()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunction(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback cb,JSVM_Value* result)
```

**Description**

Supports creating function objects in native code, which is the main mechanism for JavaScript to call native code. After this call, the newly created function is no longer automatically visible in the script. Instead, you should explicitly set properties on any visible object in JavaScript to access the function from the script.

**Since**: 11


**Parameters**

| Name                                                              | Description|
|-------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                         | Environment for calling the JSVM-API.|
| const char* utf8name                                              | Pointer to the optional UTF-8-encoded name of the function. This is visible in JavaScript as the **name** property of the new function object.|
| size_t length                                                     | Length of **utf8name** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) cb          | Native function to be called when the function object is called. For details, see [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md).|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript function object of the newly created function.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_GetCbInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetCbInfo(JSVM_Env env,JSVM_CallbackInfo cbinfo,size_t* argc,JSVM_Value* argv,JSVM_Value* thisArg,void** data)
```

**Description**

Obtains detailed information about the callback, such as the parameter from the given callback information and the **this** pointer.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_CallbackInfo](capi-jsvm-jsvm-callbackinfo--8h.md) cbinfo | Callback information.|
| size_t* argc | Pointer to the length of the provided **argv** array and actual number of input arguments. **argc** can be ignored by passing **NULL** to it.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | Pointer to the C array of **JSVM_Value**, which is used to store copied arguments. If the number of arguments exceeds the provided number, only a requested number of arguments are copied. If fewer arguments are provided than declared, the rest of **argv** is filled with undefined **JSVM_Value**s. **argv** can be ignored by passing **NULL** to it.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* thisArg | Pointer to the JavaScript **this** argument. **thisArg** can be ignored by passing **NULL** to it.|
| void** data | Double pointer to the callback data. **data** can be ignored by passing **NULL** to it.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetNewTarget()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetNewTarget(JSVM_Env env,JSVM_CallbackInfo cbinfo,JSVM_Value* result)
```

**Description**

Obtains the new target called by the constructor. If the current callback is not called by a constructor, the result is **NULL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_CallbackInfo](capi-jsvm-jsvm-callbackinfo--8h.md) cbinfo | Callback information.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the new target called by the constructor.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_NewInstance()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_NewInstance(JSVM_Env env,JSVM_Value constructor,size_t argc,const JSVM_Value* argv,JSVM_Value* result)
```

**Description**

Instantiates a new JavaScript value by using the constructor represented by the given **JSVM_Value**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) constructor | JavaScript function that will be called as a constructor.|
| size_t argc | Number of elements in the argv array.|
| [const JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | Pointer to the JavaScript value array. **JSVM_Value** indicates the parameter of the constructor. If **argc** is 0, **argc** can be ignored by passing **NULL** to it.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the returned JavaScript object, which is the constructed object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_DefineClass()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClass(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value* result)
```

**Description**

Defines a JavaScript class.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* utf8name | Pointer to the name of the JavaScript constructor. You are advised to use the C++ class name when wrapping a C++ class.|
| size_t length | Length of **utf8name** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) constructor | Callback of the constructor used to create class. When a C++ class is wrapped, this method must comply with **JSVM_Callback**. It is a static member of the callback signature. C++ class constructors cannot be used. For details, see [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md).|
| size_t propertyCount | Number of properties in the array.|
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Pointer to the property descriptors, which are used to define the properties and methods of a class.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the constructor of a class.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_Wrap()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Wrap(JSVM_Env env,JSVM_Value jsObject,void* nativeObject,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)
```

**Description**

Wraps a native instance in a JavaScript object, which can be retrieved using **OH_JSVM_Unwrap()** later.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | JavaScript object that will wrap a native object.|
| void* nativeObject | Pointer to the native instance wrapped in a JavaScript object.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | Optional native callback, which can be used to release the native instance when the JavaScript object is garbage-collected.|
| void* finalizeHint | Pointer to the optional context hint passed to the **finalize** callback.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | Pointer to the optional reference to the wrapped object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_Unwrap()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Unwrap(JSVM_Env env,JSVM_Value jsObject,void** result)
```

**Description**

Unwraps a native instance in a JavaScript object. When the JavaScript code calls a method of a class or property accessor, the corresponding **JSVM_Callback** is called. If the callback is for an instance method or accessor, the **this** parameter of the callback is the wrapper object. Then you can obtain the C++ instance as the call target by calling **OH_JSVM_Unwrap()** of the wrapper object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | Object associated with the native instance.|
| void** result | Double pointer to the wrapped native instance.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_RemoveWrap()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RemoveWrap(JSVM_Env env,JSVM_Value jsObject,void** result)
```

**Description**

Removes the wrap of the native instance, which is previously wrapped in **js_object** by **OH_JSVM_Wrap()**. If the **finalize** callback is associated with wrap, it will not be called when the JavaScript object is garbage-collected.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | Object associated with the native instance.|
| void** result | Double pointer to the wrapped native instance.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_TypeTagObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_TypeTagObject(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag)
```

**Description**

Associates the value of the **typeTag** pointer with a JavaScript object or an external value. You can call **OH_JSVM_CheckObjectTypeTag()** to check the type of the tag attached to the object to ensure that the object type is correct. If the object already has an associated type tag, **JSVM_INVALID_ARG** is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript object or external value to be tagged.|
| [const JSVM_TypeTag](capi-jsvm-jsvm-typetag.md)* typeTag | Pointer to the type tag.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_CheckObjectTypeTag()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CheckObjectTypeTag(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag,bool* result)
```

**Description**

Checks the **typeTag** with the tag on a JavaScript object or external value. If they are the same tag, **result** is set to **true**. Otherwise, **result** is set to **false**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript object or external value to be checked.|
| [const JSVM_TypeTag](capi-jsvm-jsvm-typetag.md)* typeTag | Pointer to the type tag used to compare any tags found on an object.|
| bool* result | Pointer to the check result, indicating whether the specified type tag matches that on the object. If they are the same tag, **result** is set to **true**. Otherwise, **result** is set to **false**.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_AddFinalizer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_AddFinalizer(JSVM_Env env,JSVM_Value jsObject,void* finalizeData,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)
```

**Description**

Adds the **JSVM_Finalize** callback to a JavaScript object. This callback is called when the JavaScript object is garbage-collected. **OH_JSVM_AddFinalizer** can be called multiple times on a single JavaScript object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | JavaScript object associated with native data.|
| void* finalizeData | Pointer to the optional data to be passed to **finalizeCb**.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | Native callback used to release native data when a JavaScript object is garbage-collected. **JSVM_Finalize** provides more details.|
| void* finalizeHint | Pointer to the optional context hint passed to the **finalize** callback.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | Pointer to the optional reference to a JavaScript object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_GetVersion()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetVersion(JSVM_Env env,uint32_t* result)
```

**Description**

Obtains the latest JSVM-API version supported by the JSVM runtime. New JSVM-API APIs will be added to support more features. With this API, the new features of a certain JSVM version can be used, or callbacks are provided if a feature is not supported.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| uint32_t* result | Pointer to the JSVM-API of the latest version.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetVMInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetVMInfo(JSVM_VMInfo* result)
```

**Description**

Obtains the VM information.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VMInfo](capi-jsvm-jsvm-vminfo.md)* result | Pointer to the VM information.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_AdjustExternalMemory()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_AdjustExternalMemory(JSVM_Env env,int64_t changeInBytes,int64_t* result)
```

**Description**

Notifies the underlying VM of the size of externally allocated memory that remains active due to the JavaScript object. Registering externally allocated memory triggers global garbage collection more frequently than in other ways.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| int64_t changeInBytes | Change in the size of externally allocated memory that remains active due to the JavaScript object.|
| int64_t* result | Pointer to the adjusted value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_MemoryPressureNotification()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_MemoryPressureNotification(JSVM_Env env,JSVM_MemoryPressureLevel level)
```

**Description**

Notifies the VM of insufficient system memory and selectively triggers garbage collection.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_MemoryPressureLevel](capi-jsvm-types-h.md#jsvm_memorypressurelevel) level | Memory pressure level to be set for the current VM.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreatePromise()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreatePromise(JSVM_Env env,JSVM_Deferred* deferred,JSVM_Value* promise)
```

**Description**

Creates a deferred object and a JavaScript promise.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Deferred](capi-jsvm-jsvm-deferred--8h.md)* deferred | Pointer to the new deferred object, which can be passed to **OH_JSVM_ResolveDeferred()** or **OH_JSVM_RejectDeferred()** to resolve **resp** or reject the promise.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* promise | Pointer to the JavaScript promise associated with the deferred object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_ResolveDeferred()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ResolveDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value resolution)
```

**Description**

Resolves a JavaScript promise by using the associated deferred object. It can only be used to resolve the JavaScript promise of the corresponding available deferred object. This means that promise must be created using **OH_JSVM_CreatePromise()**, and the object returned from this call must be retained so that it can be passed to this API.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Deferred](capi-jsvm-jsvm-deferred--8h.md) deferred | Deferred object whose associated promise is to be parsed.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) resolution | Value used to resolve a promise.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_RejectDeferred()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RejectDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value rejection)
```

**Description**

Rejects a JavaScript promise by using the associated deferred object. It can only be used to reject the JavaScript promise of the corresponding available deferred object. This means that promise must be created using **OH_JSVM_CreatePromise()**, and the object returned from this call must be retained so that it can be passed to this API.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Deferred](capi-jsvm-jsvm-deferred--8h.md) deferred | Deferred object whose associated promise is to be parsed.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rejection | Value used to reject a promise.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_IsPromise()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsPromise(JSVM_Env env,JSVM_Value value,bool* isPromise)
```

**Description**

Checks whether a promise object is native.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Value to be checked.|
| bool* isPromise | Pointer to the check result. The value **true** indicates that the promise is a native promise object (which is created by the underlying engine), and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_PromiseRegisterHandler()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_PromiseRegisterHandler(JSVM_Env env,JSVM_Value promise,JSVM_Value onFulfilled,JSVM_Value onRejected,JSVM_Value* result)
```

**Description**

Registers a handler for processing promise fulfillment and rejection.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) promise | Promise for which a handler needs to be registered.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) onFulfilled | Handler to be invoked after the promise is fulfilled.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) onRejected | Handler to be invoked after the promise is rejected.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the new promise generated after a promise calls the **then** or **catch** API.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if **env** or **promise** is empty, or **onFulfilled** and **onRejected** are both empty.<br>         [JSVM_INVALID_TYPE](capi-jsvm-types-h.md#jsvm_status): invalid type. This code is returned if the promise, **onFulfilled**, or **onRejected** is not of the JavaScript type.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if API execution error occurs.|

### OH_JSVM_JsonParse()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_JsonParse(JSVM_Env env,JSVM_Value jsonString,JSVM_Value* result)
```

**Description**

Parses a JSON string and returns the parsed value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsonString | String to be parsed.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the value obtained by parsing.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input parameter is not of the string type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_JsonStringify()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_JsonStringify(JSVM_Env env,JSVM_Value jsonObject,JSVM_Value* result)
```

**Description**

Converts an object into a JSON string and returns the converted string.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsonObject | Object to be stringified.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the converted string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CreateSnapshot()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSnapshot(JSVM_VM vm,size_t contextCount,const JSVM_Env* contexts,const char** blobData,size_t* blobSize)
```

**Description**

Creates a VM startup snapshot.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | Target environment in which the API will be called.|
| size_t contextCount | Number of contexts.|
| [const JSVM_Env](capi-jsvm-jsvm-env--8h.md)* contexts | Pointer to the array of contexts to be added to the snapshot.|
| const char** blobData | Double pointer to the snapshot data.|
| size_t* blobSize | Pointer to the size of snapshot data.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_GetHeapStatistics()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetHeapStatistics(JSVM_VM vm,JSVM_HeapStatistics* result)
```

**Description**

Obtains heap statistics of a VM.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM that returns heap statistics.|
| [JSVM_HeapStatistics](capi-jsvm-jsvm-heapstatistics.md)* result | Pointer to the heap statistics.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_StartCpuProfiler()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_StartCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler* result)
```

**Description**

Creates and starts a CPU profiler instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM for starting the CPU profiler.|
| [JSVM_CpuProfiler](capi-jsvm-jsvm-cpuprofiler--8h.md)* result | Pointer to the CPU profiler.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_StopCpuProfiler()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_StopCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler profiler,JSVM_OutputStream stream,void* streamData)
```

**Description**

Stops the CPU profiler and outputs the result to a stream.

**Since**: 12


**Parameters**

| Name                                                               | Description|
|--------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                             | VM for starting the CPU profiler.|
| [JSVM_CpuProfiler](capi-jsvm-jsvm-cpuprofiler--8h.md) profiler     | CPU profiler to be stopped.|
| [JSVM_OutputStream](capi-jsvm-types-h.md#jsvm_outputstream) stream | Callback for the output stream.|
| void* streamData                                                   | Pointer to the optional data passed to the output stream. For example, it can be a file stream that writes the sample data passed in the output stream to a file.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_TakeHeapSnapshot()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_TakeHeapSnapshot(JSVM_VM vm,JSVM_OutputStream stream,void* streamData)
```

**Description**

Obtains a snapshot of the current heap and outputs it to a stream.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM whose heap snapshot is to be obtained.|
| [JSVM_OutputStream](capi-jsvm-types-h.md#jsvm_outputstream) stream | Callback for the output stream.|
| void* streamData | Pointer to the optional data passed to the output stream. For example, it can be a file stream that writes the sample data passed in the output stream to a file.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_OpenInspector()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspector(JSVM_Env env,const char* host,uint16_t port)
```

**Description**

Opens an inspector instance on the specified host and port for debugging JS code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* host | Pointer to the IP address of the host for listening for the inspector connection.|
| uint16_t port | Port for listening for the inspector connection.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_CloseInspector()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseInspector(JSVM_Env env)
```

**Description**

Closes all remaining inspector connections.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_WaitForDebugger()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_WaitForDebugger(JSVM_Env env,bool breakNextLine)
```

**Description**

Waits for the host to set up a socket connection with an inspector. After the connection is set up, the application continues to run. **Runtime.runIfWaitingForDebugger** is sent.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| bool breakNextLine | Whether to break in the next line of JavaScript code. If this parameter is set to **true**, the next line of JavaScript code is suspended. You need to use the debugger to control the execution of the JavaScript code. If this parameter is set to **false**, the next line of JavaScript code is not interrupted.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_DefineClassWithPropertyHandler()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithPropertyHandler(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_PropertyHandlerCfg propertyHandlerCfg,JSVM_Callback callAsFunctionCallback,JSVM_Value* result)
```

**Description**

Defines a set of JavaScript class property handlers including **getter**, **setter**, **deleter**, and **enumerator** with the given class name, constructor, properties, and callback, which are called as callbacks.

**Since**: 12


**Parameters**

| Name                                                                              | Description|
|-----------------------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                                         | Environment for calling the JSVM-API.|
| const char* utf8name                                                              | Pointer to the name of the JavaScript class constructor.|
| size_t length                                                                     | Length of **utf8name** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) constructor                     | Callback of the constructor used to create class. This method must be of the **JSVM_Callback** type. The callback of the constructor must be a static member. C++ class constructors cannot be used. For details, see [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md).|
| size_t propertyCount                                                              | Number of properties in the array.|
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Pointer to the property descriptors of static data and instance data. For details about the properties, accessors, and methods of a class, see **JSVM_PropertyDescriptor**.|
| [JSVM_PropertyHandlerCfg](capi-jsvm-jsvm-propertyhandlerconfigurationstruct.md) propertyHandlerCfg                                    | Callback to be invoked when an instance object property is accessed.|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) callAsFunctionCallback          | Callback to be invoked when an instance object is called as a function.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result                 | Pointer to the **JSVM_Value** of the constructor of a JavaScript class.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure due to unknown reasons.|

### OH_JSVM_IsLocked()

```c++
JSVM_EXTERN JSVM_Status OH_JSVM_IsLocked(JSVM_Env env, bool* isLocked)
```

**Description**

Checks whether the current thread holds a lock of the specified environment. Only the thread that holds the lock can use the environment.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the API.|
| bool* isLocked | Pointer to the result indicating whether the current thread holds the environment lock. The value **true** indicates that the environment lock is held, and the value **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_AcquireLock()

```c++
JSVM_EXTERN JSVM_Status OH_JSVM_AcquireLock(JSVM_Env env)
```

**Description**

Obtains a lock. Only the thread that holds the lock can use the environment.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the API.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_ReleaseLock()

```c++
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseLock(JSVM_Env env)
```

**Description**

Releases a lock. Only the thread that holds the lock can use the environment.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the API.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsUndefined()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsUndefined(JSVM_Env env,JSVM_Value value,bool* isUndefined)
```

**Description**

Checks whether the input value is **Undefined**. This API is equivalent to **value === undefined** in JavaScript code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isUndefined | Pointer to the check result. The value **true** indicates that the **JSVM_Value** is **Undefined**, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsNull()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsNull(JSVM_Env env,JSVM_Value value,bool* isNull)
```

**Description**

Checks whether the input value is a **Null** object. This API is equivalent to **value === null** in JavaScript code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isNull | Pointer to the check result. The value **true** indicates that the **JSVM_Value** is **Null**, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsNullOrUndefined()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsNullOrUndefined(JSVM_Env env,JSVM_Value value,bool* isNullOrUndefined)
```

**Description**

Checks whether the input value is **Null** or **Undefined**. This API is equivalent to **value == null** in JavaScript code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isNullOrUndefined | Pointer to the check result. The value **true** indicates that the **JSVM_Value** is **Null** or **Undefined**, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsBoolean()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsBoolean(JSVM_Env env,JSVM_Value value,bool* isBoolean)
```

**Description**

Checks whether the input value is a Boolean value. This API is equivalent to **typeof value ==='boolean'** in JavaScript code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isBoolean | Pointer to the check result. The value **true** indicates that the **JSVM_Value** is of the Boolean type, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsNumber()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsNumber(JSVM_Env env,JSVM_Value value,bool* isNumber)
```

**Description**

Checks whether the input value is a number. This API is equivalent to **typeof value === 'number'** in JavaScript code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isNumber | Pointer to the check result. The value **true** indicates that the **JSVM_Value** is a number, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsString()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsString(JSVM_Env env,JSVM_Value value,bool* isString)
```

**Description**

Checks whether the input value is a string. This API is equivalent to **typeof value === 'string'** in JavaScript code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isString | Pointer to the check result. The value **true** indicates that the **JSVM_Value** is a string, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsSymbol()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbol(JSVM_Env env,JSVM_Value value,bool* isSymbol)
```

**Description**

Checks whether the input value is a symbol. This API is equivalent to **typeof value === 'symbol'** in JavaScript code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isSymbol | Pointer to the check result. The value **true** indicates that the **JSVM_Value** is a symbol, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsFunction()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsFunction(JSVM_Env env,JSVM_Value value,bool* isFunction)
```

**Description**

Checks whether the input value is a function. This API is equivalent to **typeof value === 'function'** in JavaScript code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isFunction | Pointer to the check result. The value **true** indicates that the **JSVM_Value** is a function, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsObject(JSVM_Env env,JSVM_Value value,bool* isObject)
```

**Description**

Checks whether the input value is an object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isObject | Pointer to the check result. The value **true** indicates that the given value is an object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsBigInt()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsBigInt(JSVM_Env env,JSVM_Value value,bool* isBigInt)
```

**Description**

Checks whether the input value is a BigInt value. This API is equivalent to **typeof value === 'bigint'** in JavaScript code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isBigInt | Pointer to the check result. The value **true** indicates that the **JSVM_Value** is of the BigInt type, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateMap()

```c
JSVM_Status JSVM_CDECL OH_JSVM_CreateMap(JSVM_Env env, JSVM_Value* result)
```

**Description**

Creates a JavaScript value of the Map type.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of the JavaScript Map type.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_IsMap()

```c
JSVM_Status JSVM_CDECL OH_JSVM_IsMap(JSVM_Env env,JSVM_Value value,bool* isMap)
```

**Description**

Checks whether the input value is of the Map type.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isMap | Pointer to the check result. The value **true** indicates that the input value is of the Map type, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_IsConstructor()

```c
JSVM_Status JSVM_CDECL OH_JSVM_IsConstructor(JSVM_Env env,JSVM_Value value,bool* isConstructor)
```

**Description**

Checks whether the input value is a constructor.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* isConstructor | Pointer to the check result. The value **true** indicates that the input value is a constructor, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_CreateRegExp()

```c
JSVM_Status JSVM_CDECL OH_JSVM_CreateRegExp(JSVM_Env env,JSVM_Value value,JSVM_RegExpFlags flags,JSVM_Value* result)
```

**Description**

Creates a regular expression object corresponding to the input JavaScript string. This API may throw an exception.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript string to be converted to a regular expression.|
| [JSVM_RegExpFlags](capi-jsvm-types-h.md#jsvm_regexpflags) flags | Regular expression flags.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the **JSVM_Value** of JavaScript RegExp.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception. This code is returned if an exception is thrown during API running.|

### OH_JSVM_ObjectGetPrototypeOf()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectGetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value* result)
```

**Description**

Obtains the prototype of a JavaScript object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object |  JavaScript object whose prototype is to be returned.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the prototype of a given object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception. This code is returned if an exception is thrown during API running.|

### OH_JSVM_ObjectSetPrototypeOf()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value prototype)
```

**Description**

Sets the prototype of a JavaScript object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | JavaScript object whose prototype needs to be set.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) prototype | Object prototype.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the prototype fails to be set. For example, cyclically setting the prototype will trigger the failure.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception. This code is returned if an exception is thrown during API running.|

### OH_JSVM_CreateSet()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSet(JSVM_Env env,JSVM_Value* result)
```

**Description**

Creates a JavaScript value of the Set type.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the created JavaScript value of the Set type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_IsSet()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsSet(JSVM_Env env,JSVM_Value value,bool* isSet)
```

**Description**

Checks whether the specified object is of the Set type.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Object to be checked.|
| bool* isSet | Pointer to the check result. The value **true** indicates that the given object is of the Set type, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|

### OH_JSVM_CoerceToBigInt()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBigInt(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation **ToBigInt()**.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the converted JavaScript value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status): BigInt expected. This code is returned if the input JavaScript value cannot be converted to a BigInt value.|

### OH_JSVM_IsRegExp()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsRegExp(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the input value is a JavaScript RegExp object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | **JSVM_Value** to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the input value is a JavaScript RegExp object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_CreateFunctionWithScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunctionWithScript(JSVM_Env env,const char* funcName,size_t length,size_t argc,const JSVM_Value* argv,JSVM_Value script,JSVM_Value* result)
```

**Description**

Creates a function with the given JavaScript as the function body.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* funcName | Pointer to the string containing the function name. If **NULL** is passed to it, an anonymous function is created.|
| size_t length | Length of **funcName** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| size_t argc | Number of elements in the argv array.|
| [const JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | Pointer to the **JSVM_values** array, representing the JavaScript values to be passed to the function as arguments.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | JavaScript string that is used as the function body.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the JavaScript function object of the newly created function.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the input JavaScript cannot be compiled.|

### OH_JSVM_PumpMessageLoop()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_PumpMessageLoop(JSVM_VM vm,bool* result)
```

**Description**

Starts the message loop in the VM. This message loop can be executed through the external event loop.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM instance for starting a message loop.|
| bool* result | Pointer to the operation result. The value **true** indicates that the message loop is started successfully, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_PerformMicrotaskCheckpoint()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_PerformMicrotaskCheckpoint(JSVM_VM vm)
```

**Description**

Checks whether there are microtasks waiting in the queue. If yes, execute them.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM instance in which microtasks are to be checked.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_IsCallable()

```c++
JSVM_EXTERN JSVM_Status OH_JSVM_IsCallable(JSVM_Env env, JSVM_Value value, bool* isCallable)
```

**Description**

Checks whether the input value is callable.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* isCallable | Pointer to the result indicating whether the given value is callable. The value **true** indicates that the given value is callable, and the value **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_RetainScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RetainScript(JSVM_Env env, JSVM_Script script)
```

**Description**

Retains a **JSVM_Script** and extends its lifecycle beyond the current scope.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the API.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | JavaScript script to be retained.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the script is empty or has been retained.|

### OH_JSVM_ReleaseScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseScript(JSVM_Env env, JSVM_Script script)
```

**Description**

Releases the script retained by **OH_JSVM_RetainScript**. The released script cannot be used again.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the API.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | JavaScript string that includes the script to be released.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the script is empty or has not been retained.|

### OH_JSVM_OpenInspectorWithName()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspectorWithName(JSVM_Env env,int pid,const char* name)
```

**Description**

Opens the **name** inspector and its corresponding Unix Domain port with the specified PID.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the API.|
| int pid | PID for identifying the inspector connection.|
| const char* name | Pointer to the name of an inspector. If **nullptr** is passed in, the default name **jsvm** is used.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CompileWasmModule()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmModule(JSVM_Env env,const uint8_t *wasmBytecode,size_t wasmBytecodeLength,const uint8_t *cacheData,size_t cacheDataLength,bool *cacheRejected,JSVM_Value *wasmModule)
```

**Description**

Compiles the WebAssembly bytecode to obtain a WebAssembly module. If the WebAssembly cache is provided, it will be deserialized first. If this API does not have the JIT permission, a log is printed to notify you.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const uint8_t *wasmBytecode | Pointer to the WebAssembly bytecode.|
| size_t wasmBytecodeLength | Length of the WebAssembly bytecode, in bytes.|
| const uint8_t *cacheData | Pointer to the optional WebAssembly cache.|
| size_t cacheDataLength | Optional WebAssembly cache length, in bytes.|
| bool *cacheRejected | Pointer to the operation result. The value **true** indicates that the provided WebAssembly cache is rejected by the engine, and **false** indicates the opposite.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) *wasmModule | Pointer to the generated WebAssembly module.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the **env** or **wasmBytecode** parameter is empty, or the input data length parameter is invalid.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the compilation fails.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.<br>         [JSVM_JIT_MODE_EXPECTED](capi-jsvm-types-h.md#jsvm_status): JIT mode expected.|

### OH_JSVM_CompileWasmFunction()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmFunction(JSVM_Env env,JSVM_Value wasmModule,uint32_t functionIndex,JSVM_WasmOptLevel optLevel)
```

**Description**

Compiles a WebAssembly function with the specified index at a specified optimization level. If this API does not have the JIT permission, a log is printed to notify you.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) wasmModule | WebAssembly module where the function to be compiled is located.|
| uint32_t functionIndex | Index of the function to be compiled. The index must be within the valid range.|
| [JSVM_WasmOptLevel](capi-jsvm-types-h.md#jsvm_wasmoptlevel) optLevel | Optimization level. Currently, only the high optimization level is supported.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the **env** or **wasmModule** parameter is empty, or **wasmModule** is not a real WebAssembly module.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the function index is out of range or the compilation fails.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.<br>         [JSVM_JIT_MODE_EXPECTED](capi-jsvm-types-h.md#jsvm_status): JIT mode expected.|

### OH_JSVM_IsWasmModuleObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsWasmModuleObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given **JSVM_Value** is a WebAssembly module.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the given value is a WebAssembly module, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_CreateWasmCache()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateWasmCache(JSVM_Env env,JSVM_Value wasmModule,const uint8_t** data,size_t* length)
```

**Description**

Creates a WebAssembly cache. If this API does not have the JIT permission, a log is printed to notify you.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) wasmModule | Compiled WebAssembly module.|
| const uint8_t** data | Double pointer to the generated WebAssembly cache.|
| size_t* length | Pointer to the length of the generated WebAssembly cache, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the cache fails to be generated.<br>         [JSVM_JIT_MODE_EXPECTED](capi-jsvm-types-h.md#jsvm_status): JIT mode expected.|

### OH_JSVM_ReleaseCache()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseCache(JSVM_Env env,const uint8_t* cacheData,JSVM_CacheType cacheType)
```

**Description**

Releases the cache of a specified type.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const uint8_t* cacheData | Pointer to the cache data to be released. Repeated release is an undefined behavior.|
| [JSVM_CacheType](capi-jsvm-types-h.md#jsvm_cachetype) cacheType | Cache type. A generated cache can be released accordingly.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in or the **cacheType** argument is invalid.|

### OH_JSVM_IsBigIntObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsBigIntObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given **JSVM_Value** is a BigInt object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the given value is a BigInt object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_IsBooleanObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsBooleanObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given **JSVM_Value** is a Boolean object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the given value is a Boolean object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_IsStringObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsStringObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given **JSVM_Value** is a string object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the given value is a string object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_IsNumberObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsNumberObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given **JSVM_Value** is a number object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the given value is a number object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_IsSymbolObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbolObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given **JSVM_Value** is a symbol object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Pointer to the check result. The value **true** indicates that the given value is a symbol object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolAsyncIterator()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolAsyncIterator(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.AsyncIterator** capability from the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.AsyncIterator** of the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolHasInstance()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolHasInstance(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.HasInstance** capability from the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.HasInstance** of the well-Known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolIsConcatSpreadable()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIsConcatSpreadable(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.IsConcatSpreadable** capability from the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.IsConcatSpreadable** of the well-Known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolMatch()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolMatch(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.Match** capability of the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.Match** of the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolReplace()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolReplace(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.Replace** capability of the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.Replace** of the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolSearch()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSearch(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.Search** capability of the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.Search** of the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolSplit()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSplit(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.Split** capability of the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.Split** of the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolToPrimitive()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToPrimitive(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.ToPrimitive** capability of the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.ToPrimitive** of the well-Known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolUnscopables()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolUnscopables(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.Unscopables** capability of the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.Unscopables** of the well-Known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolToStringTag()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToStringTag(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.ToStringTag** capability of the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.ToStringTag** of the well-Known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_GetSymbolIterator()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIterator(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the **Symbol.Iterator** capability of the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to **Symbol.Iterator** of the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if a null pointer argument is passed in.|

### OH_JSVM_TraceStart()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_TraceStart(size_t count,const JSVM_TraceCategory* categories,const char* tag,size_t eventsCount)
```

**Description**

Starts collecting information of the specified trace categories for all JSVM runtime instances (thread-unsafe).

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| size_t count | Number of trace categories.|
| [const JSVM_TraceCategory](capi-jsvm-types-h.md#jsvm_tracecategory)* categories | Pointer to the array of trace categories.|
| const char* tag | Pointer to the tag defined and assigned to trace data.|
| size_t eventsCount | Maximum number of trace events that can be stored.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.  <br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if **categories** or **count** is invalid.|

### OH_JSVM_TraceStop()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_TraceStop(JSVM_OutputStream stream, void* streamData)
```

**Description**

Stops collecting information of a specified trace category for all JSVM runtime instances (thread-unsafe).

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_OutputStream](capi-jsvm-types-h.md#jsvm_outputstream) stream | Callback for the output stream, which is used to receive trace data.|
| void* streamData | Pointer to the output stream, which is used by the output stream callback to output data.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.  <br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if **stream** or **streamData** is empty.|

### OH_JSVM_AddHandlerForGC()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_AddHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,JSVM_GCType gcType,void* userData)
```

**Description**

Adds a handler for GC to the VM.

**Since**: 18


**Parameters**

| Name                                                                                | Description|
|-------------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                              | Environment for calling the JSVM-API.|
| [JSVM_CBTriggerTimeForGC](capi-jsvm-types-h.md#jsvm_cbtriggertimeforgc) triggerTime | Time when the GC callback is triggered.|
| [JSVM_HandlerForGC](capi-jsvm-types-h.md#jsvm_handlerforgc) handler                 | Handler to be invoked when GC is triggered.|
| [JSVM_GCType](capi-jsvm-types-h.md#jsvm_gctype) gcType                              | GC type.|
| void* userData                                                                      | Pointer to the native user data.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if **vm** or **handler** is empty or the handler has been added.|

### OH_JSVM_RemoveHandlerForGC()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RemoveHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,void* userData)
```

**Description**

Removes the handler for GC from the VM.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | Environment for calling the JSVM-API.|
| [JSVM_CBTriggerTimeForGC](capi-jsvm-types-h.md#jsvm_cbtriggertimeforgc) triggerTime | Time when the GC callback is triggered.|
| [JSVM_HandlerForGC](capi-jsvm-types-h.md#jsvm_handlerforgc) handler | Handler to be invoked when GC is triggered.|
| void* userData | Pointer to the native user data.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if **vm** or **handler** is empty, the handler has been removed, or the handler has never been added.|

### OH_JSVM_SetHandlerForOOMError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForOOMError(JSVM_VM vm,JSVM_HandlerForOOMError handler)
```

**Description**

Sets a handler for OOM errors. If the API is called repeatedly, only the last call takes effect. If the input handler is null, the previous setting is canceled.

**Since**: 18


**Parameters**

| Name                                                                            | Description|
|---------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                          | Environment for calling the JSVM-API.|
| [JSVM_HandlerForOOMError](capi-jsvm-types-h.md#jsvm_handlerforoomerror) handler | Handler for OOM errors.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if **vm** is empty.|

### OH_JSVM_SetDebugOption()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetDebugOption(JSVM_Env env, JSVM_DebugOption debugOption, bool isEnabled)
```

**Description**

Enables or disables a specific debugging option for a JSVM environment.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_DebugOption](capi-jsvm-types-h.md#jsvm_debugoption) debugOption | Debugging option.|
| bool isEnabled | Whether to enable or disable the debugging option. The value **true** indicates yes, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the input **env** is a null pointer.|

### OH_JSVM_SetHandlerForFatalError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForFatalError(JSVM_VM vm,JSVM_HandlerForFatalError handler)
```

**Description**

Sets a handler for fatal errors. If the API is called repeatedly, only the last call takes effect. If the input handler is null, the previous setting is canceled.

**Since**: 18


**Parameters**

| Name                                                                                | Description|
|-------------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                              | Environment for calling the JSVM-API.|
| [JSVM_HandlerForFatalError](capi-jsvm-types-h.md#jsvm_handlerforfatalerror) handler | Handler for fatal errors.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if **vm** is empty.|

### OH_JSVM_SetHandlerForPromiseReject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForPromiseReject(JSVM_VM vm,JSVM_HandlerForPromiseReject handler)
```

**Description**

Sets a handler for the PromiseReject error. If the API is called repeatedly, only the last call takes effect. If the input handler is null, the previous setting is canceled.

**Since**: 18


**Parameters**

| Name                                                                                      | Description|
|-------------------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                                    | Environment for calling the JSVM-API.|
| [JSVM_HandlerForPromiseReject](capi-jsvm-types-h.md#jsvm_handlerforpromisereject) handler | Handler for PromiseReject errors.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if **vm** is empty.|

### OH_JSVM_DefineClassWithOptions()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithOptions(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value parentClass,size_t optionCount,JSVM_DefineClassOptions options[],JSVM_Value* result)
```

**Description**

Defines a class with options. When a C++ class is encapsulated, the C++ constructor callback passed through the constructor should be a static method in the class. This method calls the actual class constructor, encapsulates a new C++ instance into a JavaScript object based on the input options, and returns the encapsulated object.

**Since**: 18


**Parameters**

| Name                                                                              | Description|
|-----------------------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                                         | Environment for calling the JSVM-API.|
| const char* utf8name                                                              | Pointer to the name of the JavaScript constructor. You are advised to use the C++ class name when wrapping a C++ class.|
| size_t length                                                                     | Length of **utf8name** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) constructor                     | Callback of the constructor used to create class. When a C++ class is wrapped, this method must comply with **JSVM_Callback**. It is a static member of the callback signature. C++ class constructors cannot be used. For details, see [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md).|
| size_t propertyCount                                                              | Number of properties in the array.|
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Pointer to the property descriptors, which are used to define the properties and methods of a class.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) parentClass             | Parent class of the defined class.|
| size_t optionCount                                                                | Number of options in the array.|
| [JSVM_DefineClassOptions](capi-jsvm-jsvm-defineclassoptions.md) options[]                                             | Array of options used to define the class.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result                 | Pointer to the **JSVM_Value** of the constructor of a class.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if the input pointers contains a null pointer.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the execution fails due to invalid **utf8name**, **constructor**, or **properties**.|

### OH_JSVM_CreateExternalStringLatin1()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternalStringLatin1(JSVM_Env env, char* str, size_t length, JSVM_Finalize finalizeCallback, void* finalizeHint, JSVM_Value* result, bool* copied)
```

**Description**

Creates an external JavaScript string with an ISO-8859-1-encoded C string. If the creation fails, the original native string is copied.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| char* str | Pointer to the ISO-8859-1-encoded string.|
| size_t length | Length of the string. If the string is a null-terminated string, you can directly pass it in **JSVM_AUTO_LENGTH**.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCallback | (Optional) Callback to be invoked when the created string is reclaimed by the GC. For details, see the description of **JSVM_Finalize**.|
| void* finalizeHint | (Optional) Pointer to the finalize hint. This will be passed to the triggered **finalize** callback when a string is reclaimed.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Pointer to the created JavaScript external string, which is of the **JSVM_Value** type.|
| bool* copied | Pointer to the operation result. The value **true** indicates that the external string creation fails and a native JavaScript string is returned, and **false** indicates that the external string creation succeeds.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if any value of **env**, **str**, or **copied** is empty.|

### OH_JSVM_CreateExternalStringUtf16()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternalStringUtf16(JSVM_Env env, char16_t* str, size_t length, JSVM_Finalize finalizecallback, void* finalizeHint, JSVM_Value* result, bool* copied)
```

**Description**

Creates an external JavaScript string with a UTF-16LE-encoded C string. If the creation fails, the original native string is copied.

**Since**: 18


**Parameters**

| Name                                                                 | Description|
|----------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                            | Environment for calling the JSVM-API.|
| char16_t* str                                                        | Pointer to the UTF-16LE-encoded string.|
| size_t length                                                        | Length of the string. If the string is a null-terminated string, you can directly pass it in **JSVM_AUTO_LENGTH**.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCallback | (Optional) Callback to be invoked when the created string is reclaimed by the GC. For details, see the description of **JSVM_Finalize**.|
| void* finalizeHint                                                   | (Optional) Pointer to the finalize hint. This will be passed to the triggered **finalize** callback when a string is reclaimed.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result    | Pointer to the created JavaScript external string, which is of the **JSVM_Value** type.|
| bool* copied                                                         | Pointer to the operation result. The value **true** indicates that the external string creation fails and a native JavaScript string is returned, and **false** indicates that the external string creation succeeds.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) | Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if any value of **env**, **str**, or **copied** is empty.|

### OH_JSVM_CreatePrivate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreatePrivate(JSVM_Env env,JSVM_Value description,JSVM_Data* result)
```

**Description**

Creates a JavaScript private key object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) description | (Optional) JavaScript description of the private key.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md)* result | Pointer to the created JavaScript private key object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if either **env** or **result** is empty.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): string expected. This code is returned if the input description is not a string.|

### OH_JSVM_SetPrivate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value value)
```

**Description**

Sets the **private** property for an input object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Target object.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) key | Private key object of the **private** property.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Value of the **private** property.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if any input parameter is empty or the key is not a private key object.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status): object expected. This code is returned if the input object is not a real JavaScript object.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the **private** property fails to be set and no exception occurs.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_GetPrivate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value *result)
```

**Description**

Obtains the **private** property of an input object based on the private key.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Target object.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) key | Private key object of the **private** property.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) *result | Value of the **private** property.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if any input parameter is empty or the key is not a private key object.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status): object expected. This code is returned if the input object is not a real JavaScript object.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the **private** property fails to be obtained and no exception occurs.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_DeletePrivate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DeletePrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key)
```

**Description**

Deletes the **private** property corresponding to the private key from the input object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Target object.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) key | Private key object of the **private** property.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument. This code is returned if any input parameter is empty or the key is not a private key object.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status): object expected. This code is returned if the input object is not a real JavaScript object.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): generic failure. This code is returned if the **private** property fails to be deleted and no exception occurs.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): pending exception.|

### OH_JSVM_CreateDataReference()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataReference(JSVM_Env env,JSVM_Data data,uint32_t initialRefcount,JSVM_Ref* result)
```

**Description**

Creates a reference to a given **JSVM_Data** object. The initial reference count is the input value of **initialRefcount**.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) data | Target **JSVM_Data** object.|
| uint32_t initialRefcount | Initial reference count.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | Pointer to the created object reference.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.|

### OH_JSVM_GetReferenceData()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceData(JSVM_Env env,JSVM_Ref ref,JSVM_Data* result)
EXTERN_C_END
```

**Description**

Obtains the **JSVM_Data** (a JavaScript value associated with the JSVM reference) through the **result** parameter if the reference is still valid. Otherwise, the result is null.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | JSVM reference for requesting the corresponding value.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md)* result | Pointer to the **JSVM_Data** referenced by **JSVM_Ref**.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Returns a JSVM status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): operation successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): invalid argument.|
