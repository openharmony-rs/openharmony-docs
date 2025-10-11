# jsvm.h
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Provides JSVM-API API definitions. The JSVM APIs provide independent, standard, and complete JavaScript engine capabilities for developers, including managing the engine lifecycle, compiling and running JavaScript code, implementing cross-language calling between JavaScript and C++, and taking snapshots.

**File to import**: <ark_runtime/jsvm.h>

**Library**: libjsvm.so

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

## Summary

### Macros

| Name                                              | Description                                                                                                                                                |
|--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| **JSVM_VERSION_EXPERIMENTAL** 2147483647           | Experimental JSVM version number.                                                                                                                                      |
| **JSVM_VERSION** 8                                 | JSVM version number.                                                                                                                                         |
| **JSVM_EXTERN  attribute**(visibility("default")))  | Specifies that the symbol is visible to external entities.                                                                                                                                        |
| **JSVM_AUTO_LENGTH**   SIZE_MAX | Automatic length.                                                                                                                                             |
| **EXTERN_C_START**                                 | Identifies the start of the following code segment to be compiled by the compiler as C code:<br>When the preprocessing directive __cplusplus detects that the C++ compiler is compiling, EXTERN_C_START is assigned the value "extern "C" {" to indicate that the subsequent code is C code. When the preprocessing directive __cplusplus detects that the C++ compiler is not compiling, no mark is required.|
| **EXTERN_C_END**                                   | Identifies the end of the following code segment to be compiled by the compiler as C code:<br>When the preprocessing directive __cplusplus detects that the C++ compiler is compiling, EXTERN_C_START is assigned the value "}" to indicate that the C code ends here. When the preprocessing directive __cplusplus detects that the C++ compiler is not compiling, no mark is required.                                                                                                                  |

### Functions

| Name| Description|
| -- | -- |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Init(const JSVM_InitOptions* options)](#oh_jsvm_init) | Initializes a JavaScript VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateVM(const JSVM_CreateVMOptions* options,JSVM_VM* result)](#oh_jsvm_createvm) | Creates a VM instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetMicrotaskPolicy(JSVM_VM vm,JSVM_MicrotaskPolicy policy)](#oh_jsvm_setmicrotaskpolicy) | Sets the microtask execution policy of a virtual machine instance. If this method is not called, the default policy of the virtual machine instance is JSVM_MicrotaskPolicy::JSVM_MICROTASK_AUTO.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DestroyVM(JSVM_VM vm)](#oh_jsvm_destroyvm) | Destroys a VM instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateProxy(JSVM_Env env,JSVM_Value target,JSVM_Value handler,JSVM_Value* result)](#oh_jsvm_createproxy) | Creates a JavaScript proxy, which is equivalent to executing new Proxy(target, handler) in JavaScript.|
| [JSVM_Status JSVM_CDECL OH_JSVM_IsProxy(JSVM_Env env,JSVM_Value value,bool* isProxy)](#oh_jsvm_isproxy) | Checks whether the input value is a JavaScript proxy.|
| [JSVM_Status JSVM_CDECL OH_JSVM_ProxyGetTarget(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_proxygettarget) | Obtains the target object in the JavaScript proxy.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenVMScope(JSVM_VM vm,JSVM_VMScope* result)](#oh_jsvm_openvmscope) | Opens a new VM scope for a VM instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseVMScope(JSVM_VM vm,JSVM_VMScope scope)](#oh_jsvm_closevmscope) | Closes the VM scope of a VM instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnv(JSVM_VM vm,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Env* result)](#oh_jsvm_createenv) | Creates a new environment based on the optional properties of the new context.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnvFromSnapshot(JSVM_VM vm,size_t index,JSVM_Env* result)](#oh_jsvm_createenvfromsnapshot) | Creates a new environment based on the startup snapshot of the VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DestroyEnv(JSVM_Env env)](#oh_jsvm_destroyenv) | Destroys the environment.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenEnvScope(JSVM_Env env,JSVM_EnvScope* result)](#oh_jsvm_openenvscope) | Opens a new environment scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseEnvScope(JSVM_Env env,JSVM_EnvScope scope)](#oh_jsvm_closeenvscope) | Closes an environment scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVM(JSVM_Env env,JSVM_VM* result)](#oh_jsvm_getvm) | Retrieves VM instances in a given environment.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScript(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_Script* result)](#oh_jsvm_compilescript) | Compiles a string of JavaScript code and returns the compiled script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOrigin(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_ScriptOrigin* origin,JSVM_Script* result)](#oh_jsvm_compilescriptwithorigin) | Compiles a string of JavaScript code that contains source map information and returns the compiled script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOptions(JSVM_Env env,JSVM_Value script,size_t optionCount,JSVM_CompileOptions options[],JSVM_Value* result)](#oh_jsvm_compilescriptwithoptions) | Compiles a string of JavaScript code and returns the compiled script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateCodeCache(JSVM_Env env,JSVM_Script script,const uint8_t** data,size_t* length)](#oh_jsvm_createcodecache) | Creates a code cache for the compiled script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RunScript(JSVM_Env env,JSVM_Script script,JSVM_Value* result)](#oh_jsvm_runscript) | Executes a string of JavaScript code and returns the result. Note that this function does not allow the script to access the current lexical scope, and therefore does not allow the script to access the module scope. This means that pseudo-global variables such as require are unavailable. The script can access the global scope. The functions and variable declarations in the script will be added to the global object. Variable declarations using **let** and **const** are globally visible, but are not added to the global object. The value of **this** is **global** in the script. If the JIT permission is not supported, the script containing WebAssembly will fail to be executed. There are performance differences in specific scenarios, and a log is printed to prompt the developer.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetInstanceData(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint)](#oh_jsvm_setinstancedata) | Sets instance data so that it is associated with the currently running JSVM environment. You can use **OH_JSVM_GetInstanceData()** to get data later. Any existing data associated with the currently running JSVM environment that was set by a previous call to OH_JSVM_SetInstanceData() will be overwritten. If **finalizeCb** was previously provided, it will not be called.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetInstanceData(JSVM_Env env,void** data)](#oh_jsvm_getinstancedata) | Retrieves data associated with the currently running JSVM environment by calling OH_JSVM_SetInstanceData(). If no associated data is set, this function is called successfully and **data** is set to **NULL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetLastErrorInfo(JSVM_Env env,const JSVM_ExtendedErrorInfo** result)](#oh_jsvm_getlasterrorinfo) | Retrieves the JSVM_ExtendedErrorInfo structure, which contains information about the last error that occurred. The content of **JSVM_ExtendedErrorInfo** returned is valid only before the JSVM-API function is called for the same environment. This includes a call to **OH_JSVM_IsExceptionPending**, so you may often need to copy information for later use. The pointer returned in error_message points to a statically defined string, so you can safely use the pointer if you copy it out of the error_message field (which will be overwritten) before calling another JSVM-API function.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Throw(JSVM_Env env,JSVM_Value error)](#oh_jsvm_throw) | Throws the provided JavaScript value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwerror) | Throws a JavaScript Error with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowTypeError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwtypeerror) | Throws a JavaScript TypeError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowRangeError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwrangeerror) | Throws a JavaScript RangeError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowSyntaxError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwsyntaxerror) | Throws a JavaScript SyntaxError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsError(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_iserror) | Checks whether the given JSVM_Value indicates an error.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createerror) | Creates a JavaScript Error with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createtypeerror) | Creates a JavaScript TypeError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateRangeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createrangeerror) | Creates a JavaScript RangeError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSyntaxError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createsyntaxerror) | Creates a JavaScript SyntaxError with the provided text.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetAndClearLastException(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getandclearlastexception) | Gets and clears the last exception. If pending occurs, a JavaScript exception is returned. Otherwise, **NULL** is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsExceptionPending(JSVM_Env env,bool* result)](#oh_jsvm_isexceptionpending) | Checks whether the last exception is caused by pending. If yes, **true** is returned. Otherwise, **false** is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenHandleScope(JSVM_Env env,JSVM_HandleScope* result)](#oh_jsvm_openhandlescope) | Opens a new scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseHandleScope(JSVM_Env env,JSVM_HandleScope scope)](#oh_jsvm_closehandlescope) | (Required) Closes the passed scope in the reverse order of creating the scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope* result)](#oh_jsvm_openescapablehandlescope) | Creates a new scope where an object can be promoted to the outer scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope scope)](#oh_jsvm_closeescapablehandlescope) | (Required) Closes the passed scope in the reverse order of creating the scope. This JSVM_API can be called even if there is a suspended JavaScript exception.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_EscapeHandle(JSVM_Env env,JSVM_EscapableHandleScope scope,JSVM_Value escapee,JSVM_Value* result)](#oh_jsvm_escapehandle) | Escalates the handle to a JavaScript object so that it is valid through the lifecycle of the external scope. Each scope can be called only once. If it is called for multiple times, an error is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateReference(JSVM_Env env,JSVM_Value value,uint32_t initialRefcount,JSVM_Ref* result)](#oh_jsvm_createreference) | Creates a new reference with the specified reference count for the passed-in value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteReference(JSVM_Env env,JSVM_Ref ref)](#oh_jsvm_deletereference) | Deletes the passed-in reference.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceRef(JSVM_Env env,JSVM_Ref ref,uint32_t* result)](#oh_jsvm_referenceref) | Increases the reference count and returns the new reference count.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceUnref(JSVM_Env env,JSVM_Ref ref,uint32_t* result)](#oh_jsvm_referenceunref) | Decreases the reference count and returns the new reference count.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceValue(JSVM_Env env,JSVM_Ref ref,JSVM_Value* result)](#oh_jsvm_getreferencevalue) | If the JSVM-API is still valid, the JSVM_Value is returned, indicating the JavaScript value associated with JSVM_Ref. Otherwise, the result is **NULL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArray(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_createarray) | Returns the JSVM-API value corresponding to the JavaScript Array type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayWithLength(JSVM_Env env,size_t length,JSVM_Value* result)](#oh_jsvm_createarraywithlength) | Returns the JSVM-API value corresponding to the JavaScript Array type. Sets the length attribute of the array to the passed length parameter. However, the underlying buffer is not guaranteed to be pre-allocated by the VM when the array is created. This behavior is left to the underlying VM implementation.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArraybuffer(JSVM_Env env,size_t byteLength,void** data,JSVM_Value* result)](#oh_jsvm_createarraybuffer) | Returns the JSVM-API value corresponding to the JavaScript ArrayBuffer type. ArrayBuffer is used to represent a binary data buffer of fixed length. It is usually used as the backup buffer of the TypedArray object. The allocated ArrayBuffer has an underlying byte buffer whose size is determined by the **length** argument. The underlying buffer can be returned to and operated by the caller. This buffer can only be written directly from the native code. If you want to write the buffer from JavaScript, you need to create a TypedArray or DataView object.|
| [JSVM_Status JSVM_CDECL OH_JSVM_AllocateArrayBufferBackingStoreData(size_t byteLength,JSVM_InitializedFlag initialized,void **data)](#oh_jsvm_allocatearraybufferbackingstoredata) | Allocates a segment of BackingStore memory for the array buffer to use.|
| [JSVM_Status JSVM_CDECL OH_JSVM_FreeArrayBufferBackingStoreData(void *data)](#oh_jsvm_freearraybufferbackingstoredata) | Frees the BackingStore memory allocated by **OH_JSVM_AllocateArrayBufferBackingStoreData**.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateArrayBufferFromBackingStoreData(JSVM_Env env,void *data,size_t backingStoreSize,size_t offset,size_t arrayBufferSize,JSVM_Value *result)](#oh_jsvm_createarraybufferfrombackingstoredata) | Creates an array buffer on the allocated BackingStore memory.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDate(JSVM_Env env,double time,JSVM_Value* result)](#oh_jsvm_createdate) | Allocates a JavaScript Date object. This API does not process leap seconds. This is because ECMAScript complies with the POSIX time specifications and ignores leap seconds.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternal(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Value* result)](#oh_jsvm_createexternal) | Allocates a JavaScript value with external data. This is used to pass external data through JavaScript code. You can use **OH_JSVM_GetValueExternal** to retrieve the value from the native code. This API adds a **JSVM_Finalize** callback, which is called when the newly created JavaScript object is garbage collected. The created value is not an object, so it does not support additional attributes. It is considered a unique value type: OH_JSVM_Typeof() called with an external value generates JSVM_EXTERNAL.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateObject(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_createobject) | Allocates a default JavaScript object. This function is equivalent to executing **new Object()** in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSymbol(JSVM_Env env,JSVM_Value description,JSVM_Value* result)](#oh_jsvm_createsymbol) | Creates a JavaScript symbol value using a C string encoded in UTF8.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SymbolFor(JSVM_Env env,const char* utf8description,size_t length,JSVM_Value* result)](#oh_jsvm_symbolfor) | Searches the global registry for an existing symbol with the given description. If the symbol already exists, it is returned; otherwise, a new symbol is created in the registry.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypedarray(JSVM_Env env,JSVM_TypedarrayType type,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)](#oh_jsvm_createtypedarray) | Creates a JavaScript TypedArray object based on an existing ArrayBuffer object. The TypedArray object provides an array-like view on the underlying data buffer, where each element has the same underlying binary scalar data type. Requirement: length * element scalar byte value + byteOffset is not greater than the ByteLength() of the input array. Otherwise, a range error (RangeError) is thrown.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataview(JSVM_Env env,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)](#oh_jsvm_createdataview) | Creates a JavaScript DataView object based on an existing ArrayBuffer object. The DataView object provides an array-like view on the underlying data buffer, where elements can have different sizes and types. Requirements: The binary length plus byteOffset must not be greater than the size (in bytes) of the input array. Otherwise, a range error (RangeError) is thrown.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt32(JSVM_Env env,int32_t value,JSVM_Value* result)](#oh_jsvm_createint32) | Converts a C int32_t value to a JavaScript number value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateUint32(JSVM_Env env,uint32_t value,JSVM_Value* result)](#oh_jsvm_createuint32) | Converts a C uint32_t value to a JavaScript number value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt64(JSVM_Env env,int64_t value,JSVM_Value* result)](#oh_jsvm_createint64) | Converts a C int64_t value to a JavaScript number value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDouble(JSVM_Env env,double value,JSVM_Value* result)](#oh_jsvm_createdouble) | Converts a C double value to a JavaScript number value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintInt64(JSVM_Env env,int64_t value,JSVM_Value* result)](#oh_jsvm_createbigintint64) | Converts a C int64_t value to a JavaScript BigInt value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintUint64(JSVM_Env env,uint64_t value,JSVM_Value* result)](#oh_jsvm_createbigintuint64) | Converts a C uint64_t value to a JavaScript BigInt value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintWords(JSVM_Env env,int signBit,size_t wordCount,const uint64_t* words,JSVM_Value* result)](#oh_jsvm_createbigintwords) | Converts a group of 64-bit unsigned bits to a single BigInt value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringLatin1(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)](#oh_jsvm_createstringlatin1) | Converts an ISO-8859-1-encoded C string to a JavaScript string value. Copies a native string.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf16(JSVM_Env env,const char16_t* str,size_t length,JSVM_Value* result)](#oh_jsvm_createstringutf16) | Converts a UTF16-LE-encoded C string to a JavaScript string value. Copies a native string.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf8(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)](#oh_jsvm_createstringutf8) | Creates a JavaScript string value from a C string encoded in UTF8. Copies a native string.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetArrayLength(JSVM_Env env,JSVM_Value value,uint32_t* result)](#oh_jsvm_getarraylength) | Gets the length of an array.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetArraybufferInfo(JSVM_Env env,JSVM_Value arraybuffer,void** data,size_t* byteLength)](#oh_jsvm_getarraybufferinfo) | Gets the underlying data buffer of the ArrayBuffer and its length.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPrototype(JSVM_Env env,JSVM_Value object,JSVM_Value* result)](#oh_jsvm_getprototype) | Gets the prototype of an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetTypedarrayInfo(JSVM_Env env,JSVM_Value typedarray,JSVM_TypedarrayType* type,size_t* length,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)](#oh_jsvm_gettypedarrayinfo) | Gets the properties of a typed array. If any property is not required, its output parameter can be **NULL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetDataviewInfo(JSVM_Env env,JSVM_Value dataview,size_t* bytelength,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)](#oh_jsvm_getdataviewinfo) | Gets the proprieties of a DataView. If any property is not required, its output parameter can be set to **NULL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetDateValue(JSVM_Env env,JSVM_Value value,double* result)](#oh_jsvm_getdatevalue) | Returns the C double-precision basic type value equivalent to the given JavaScript Date time value. If this API is successfully called, **JSVM_OK** is returned. If a JSVM_Value of a non-JavaScript date type is passed in, **JSVM_DATA_EXPECTED** is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBool(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_getvaluebool) | Returns the C Boolean basic type value equivalent to the given JavaScript Boolean.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueDouble(JSVM_Env env,JSVM_Value value,double* result)](#oh_jsvm_getvaluedouble) | Returns the C double-precision basic type value equivalent to the given JavaScript number.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintInt64(JSVM_Env env,JSVM_Value value,int64_t* result,bool* lossless)](#oh_jsvm_getvaluebigintint64) | Returns the C int64_t basic type value equivalent to the given JavaScript BigInt. If necessary, it truncates the value and sets **lossless** to **false**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintUint64(JSVM_Env env,JSVM_Value value,uint64_t* result,bool* lossless)](#oh_jsvm_getvaluebigintuint64) | Returns the C uint64_t base type value equivalent to the given JavaScript BigInt. If necessary, it truncates the value and sets **lossless** to **false**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintWords(JSVM_Env env,JSVM_Value value,int* signBit,size_t* wordCount,uint64_t* words)](#oh_jsvm_getvaluebigintwords) | Gets the sign bit, 64-bit little-endian array, and number of elements in the array from a BigInt value. Both **signBit** and **words** can be set to **NULL**. In this case, only **wordCount** is obtained.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueExternal(JSVM_Env env,JSVM_Value value,void** result)](#oh_jsvm_getvalueexternal) | Gets the external data pointer previously passed to **OH_JSVM_CreateExternal()**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt32(JSVM_Env env,JSVM_Value value,int32_t* result)](#oh_jsvm_getvalueint32) | Returns the C int32 base type value equivalent to the given JavaScript number.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt64(JSVM_Env env,JSVM_Value value,int64_t* result)](#oh_jsvm_getvalueint64) | Returns the C int64 base type value equivalent to the given JavaScript number.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringLatin1(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)](#oh_jsvm_getvaluestringlatin1) | Returns the ISO-8859-1 encoded string corresponding to the input value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf8(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)](#oh_jsvm_getvaluestringutf8) | Returns the UTF8 encoded string corresponding to the input value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf16(JSVM_Env env,JSVM_Value value,char16_t* buf,size_t bufsize,size_t* result)](#oh_jsvm_getvaluestringutf16) | Queries the UTF16 encoded string corresponding to the input value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueUint32(JSVM_Env env,JSVM_Value value,uint32_t* result)](#oh_jsvm_getvalueuint32) | Returns the C uint_32 basic type value equivalent to the given JavaScript number.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetBoolean(JSVM_Env env,bool value,JSVM_Value* result)](#oh_jsvm_getboolean) | Returns the JavaScript singleton object that represents the given Boolean value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetGlobal(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getglobal) | Gets the global object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNull(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getnull) | Gets the null object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetUndefined(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getundefined) | Gets the undefined object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBool(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetobool) | Implements the abstract operation ToBoolean().|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToNumber(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetonumber) | Implements the abstract operation ToNumber(). If the passed-in value is an object, the function may run JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToObject(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetoobject) | Implements the abstract operation ToObject().|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToString(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetostring) | Implements the abstract operation ToString(). If the passed-in value is an object, the function may run JavaScript code.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Typeof(JSVM_Env env,JSVM_Value value,JSVM_ValueType* result)](#oh_jsvm_typeof) | Provides behavior similar to calling the typeof operator on a defined object. The difference is that this function supports detecting external values. It detects null as a separate type, while ECMAScript typeof detects object. If the value type is invalid, an error is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Instanceof(JSVM_Env env,JSVM_Value object,JSVM_Value constructor,bool* result)](#oh_jsvm_instanceof) | Provides behavior similar to calling the instanceof operator on an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsArray(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isarray) | Provides behavior similar to calling IsArray on an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isarraybuffer) | Checks whether the passed-in object is ArrayBuffer.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDate(JSVM_Env env,JSVM_Value value,bool* isDate)](#oh_jsvm_isdate) | Checks whether the passed-in object is a date.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsTypedarray(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_istypedarray) | Checks whether the passed-in object is a typed array.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDataview(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isdataview) | Checks whether the passed-in object is a DataView.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_StrictEquals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)](#oh_jsvm_strictequals) | Provides behavior similar to calling the strict equality algorithm.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Equals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)](#oh_jsvm_equals) | Provides behavior similar to calling the loose equality algorithm. Regardless of the JavaScript value type, **true** is returned as long as the values are equal.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DetachArraybuffer(JSVM_Env env,JSVM_Value arraybuffer)](#oh_jsvm_detacharraybuffer) | Provides behavior similar to calling the ArrayBuffer detach operation.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDetachedArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isdetachedarraybuffer) | Provides behavior similar to calling the ArrayBuffer IsDetachedBuffer operation.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_Value* result)](#oh_jsvm_getpropertynames) | Returns the names of the object's enumerable properties as a character array. The properties of the object whose key is a symbol are not included.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetAllPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_KeyCollectionMode keyMode,JSVM_KeyFilter keyFilter,JSVM_KeyConversion keyConversion,JSVM_Value* result)](#oh_jsvm_getallpropertynames) | Returns an array of all available property names of the object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value value)](#oh_jsvm_setproperty) | Sets the property named key for the passed object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value* result)](#oh_jsvm_getproperty) | Obtains the property named key from the passed object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)](#oh_jsvm_hasproperty) | Checks whether the passed object has a property named key.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)](#oh_jsvm_deleteproperty) | Attempts to delete the property named key from the object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasOwnProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)](#oh_jsvm_hasownproperty) | Checks whether the input object has a property named key. key must be a string or symbol. Otherwise, an error is thrown. The JSVM-API does not perform any conversion between data types.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value value)](#oh_jsvm_setnamedproperty) | This method is equivalent to the OH_JSVM_SetProperty method called by object to set the property named `utf8Name`.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value* result)](#oh_jsvm_getnamedproperty) | This method is equivalent to the OH_JSVM_GetProperty method called by object to obtain the property object named `utf8Name`.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,bool* result)](#oh_jsvm_hasnamedproperty) | This method is equivalent to the OH_JSVM_HasProperty method called by object to query whether the object has a property named `utf8Name`.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value value)](#oh_jsvm_setelement) | Sets an element on the passed-in object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value* result)](#oh_jsvm_getelement) | Gets the element at the requested index.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)](#oh_jsvm_haselement) | Checks whether an object has an element at the specified index. If yes, the JSVM-API returns **true**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)](#oh_jsvm_deleteelement) | Deletes the element at the specified index from an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineProperties(JSVM_Env env,JSVM_Value object,size_t propertyCount,const JSVM_PropertyDescriptor* properties)](#oh_jsvm_defineproperties) | Defines multiple properties on a given object efficiently using property descriptors. Sets the properties in the passed array of property descriptors on the object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectFreeze(JSVM_Env env,JSVM_Value object)](#oh_jsvm_objectfreeze) | Freezes a specified object to prevent new properties from being added, existing properties from being deleted, the enumerability, configurability, and writability of existing properties from being changed, the values of existing properties from being changed, and the object prototype from being changed.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSeal(JSVM_Env env,JSVM_Value object)](#oh_jsvm_objectseal) | Encapsulates a specified object to prevent new properties from being added and marks all existing properties as unconfigurable.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CallFunction(JSVM_Env env,JSVM_Value recv,JSVM_Value func,size_t argc,const JSVM_Value* argv,JSVM_Value* result)](#oh_jsvm_callfunction) | Allows JavaScript function objects to be called from native code. This is the main mechanism for callback from native code to JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunction(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback cb,JSVM_Value* result)](#oh_jsvm_createfunction) | Supports creating function objects in native code, which is the main mechanism for JavaScript to call native code. After this call, the newly created function is no longer automatically visible in the script. Instead, you must explicitly set the property on any object visible in JavaScript to access the function from the script.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetCbInfo(JSVM_Env env,JSVM_CallbackInfo cbinfo,size_t* argc,JSVM_Value* argv,JSVM_Value* thisArg,void** data)](#oh_jsvm_getcbinfo) | This method is used in the callback function to retrieve details about the call, such as the parameters and this pointer from the given callback information.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNewTarget(JSVM_Env env,JSVM_CallbackInfo cbinfo,JSVM_Value* result)](#oh_jsvm_getnewtarget) | Gets the new target called by the constructor. If the current callback is not a constructor call, the result is **NULL**.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_NewInstance(JSVM_Env env,JSVM_Value constructor,size_t argc,const JSVM_Value* argv,JSVM_Value* result)](#oh_jsvm_newinstance) | Instantiates a new JavaScript value by using the constructor represented by the given JSVM_Value.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClass(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value* result)](#oh_jsvm_defineclass) | Defines a JavaScript class.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Wrap(JSVM_Env env,JSVM_Value jsObject,void* nativeObject,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)](#oh_jsvm_wrap) | Encapsulates a native instance in a JavaScript object. The instance can be retrieved later using OH_JSVM_Unwrap().|
| [JSVM_EXTERN JSVM_Status OH_JSVM_Unwrap(JSVM_Env env,JSVM_Value jsObject,void** result)](#oh_jsvm_unwrap) | When the JavaScript code calls a method of a class or property accessor, the corresponding JSVM_Callback is called. If the callback is for an instance method or accessor, the this parameter of the callback is the wrapper object. You can call OH_JSVM_Unwrap() of the wrapper object to obtain the C++ instance as the call target.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RemoveWrap(JSVM_Env env,JSVM_Value jsObject,void** result)](#oh_jsvm_removewrap) | Use OH_JSVM_Wrap() to retrieve the native instance previously wrapped in the JavaScript object js_object and remove the wrapping. If the **finalize** callback is associated with wrap, it will not be called when the JavaScript object is garbage collected.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_TypeTagObject(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag)](#oh_jsvm_typetagobject) | Associates the value of the typeTag pointer with a JavaScript object or an external value. You can call OH_JSVM_CheckObjectTypeTag() to check the tag type attached to the object to ensure that the object type is correct. If the object already has an associated type tag, **JSVM_INVALID_ARG** is returned.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CheckObjectTypeTag(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag,bool* result)](#oh_jsvm_checkobjecttypetag) | Compares the typeTag with the tag on a JavaScript object or external value. If the same tag is found, set result to true. Otherwise, set result to false.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_AddFinalizer(JSVM_Env env,JSVM_Value jsObject,void* finalizeData,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)](#oh_jsvm_addfinalizer) | Adds the **JSVM_Finalize** callback to a JavaScript object. This callback is called when the JavaScript object is garbage collected. **OH_JSVM_AddFinalizer** can be called multiple times on a single JavaScript object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVersion(JSVM_Env env,uint32_t* result)](#oh_jsvm_getversion) | Gets the latest JSVM-API version supported by the JSVM runtime. New JSVM-API APIs will be added to support more functions. Purpose of this API: Functions can be used in JSVM versions that support them, and callback behaviors can be provided in JSVM versions that do not support them.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVMInfo(JSVM_VMInfo* result)](#oh_jsvm_getvminfo) | Gets the VM information.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_AdjustExternalMemory(JSVM_Env env,int64_t changeInBytes,int64_t* result)](#oh_jsvm_adjustexternalmemory) | Notifies the underlying VM of the size of externally allocated memory that remains active due to the JavaScript object. Registering externally allocated memory triggers global garbage collection more frequently than in other ways.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_MemoryPressureNotification(JSVM_Env env,JSVM_MemoryPressureLevel level)](#oh_jsvm_memorypressurenotification) | Notifies the VM of insufficient system memory and selectively triggers garbage collection.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreatePromise(JSVM_Env env,JSVM_Deferred* deferred,JSVM_Value* promise)](#oh_jsvm_createpromise) | Creates a deferred object and a JavaScript promise.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ResolveDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value resolution)](#oh_jsvm_resolvedeferred) | Resolves a JavaScript promise by using the associated deferred object. It can only be used to resolve the JavaScript promise of the corresponding available deferred object. This means that the promise must be created using OH_JSVM_CreatePromise() and the object returned from the call must be retained before being passed to this API.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RejectDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value rejection)](#oh_jsvm_rejectdeferred) | Rejects a JavaScript promise by using the associated deferred object. It can only be used to reject the JavaScript promise of the corresponding available deferred object. This means that the promise must be created using OH_JSVM_CreatePromise() and the object returned from the call must be retained before being passed to this API.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsPromise(JSVM_Env env,JSVM_Value value,bool* isPromise)](#oh_jsvm_ispromise) | Checks whether a promise object is a native promise object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_PromiseRegisterHandler(JSVM_Env env,JSVM_Value promise,JSVM_Value onFulfilled,JSVM_Value onRejected,JSVM_Value* result)](#oh_jsvm_promiseregisterhandler) | Registers a callback function for processing promise fulfillment or rejection.|
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
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithPropertyHandler(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_PropertyHandlerCfg propertyHandlerCfg,JSVM_Callback callAsFunctionCallback,JSVM_Value* result)](#oh_jsvm_defineclasswithpropertyhandler) | Defines a JavaScript class with a given class name, constructor, properties, and callback handler. The properties include getter, setter, deleter, and enumerator. The callback handler is called as a function.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsUndefined(JSVM_Env env,JSVM_Value value,bool* isUndefined)](#oh_jsvm_isundefined) | Checks whether the value passed in is **Undefined**. This is equivalent to `value === undefined` in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNull(JSVM_Env env,JSVM_Value value,bool* isNull)](#oh_jsvm_isnull) | Checks whether the value passed in is a **Null** object. This is equivalent to `value === null` in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNullOrUndefined(JSVM_Env env,JSVM_Value value,bool* isNullOrUndefined)](#oh_jsvm_isnullorundefined) | Checks whether the value passed in is **Null** or **Undefined**. This is equivalent to `value == null` in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBoolean(JSVM_Env env,JSVM_Value value,bool* isBoolean)](#oh_jsvm_isboolean) | Checks whether the value passed in is a Boolean value. This is equivalent to `typeof value === 'boolean'` in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNumber(JSVM_Env env,JSVM_Value value,bool* isNumber)](#oh_jsvm_isnumber) | Checks whether the value passed in is a number. This is equivalent to `typeof value === 'number'` in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsString(JSVM_Env env,JSVM_Value value,bool* isString)](#oh_jsvm_isstring) | Checks whether the value passed in is a string. This is equivalent to `typeof value === 'tring'` in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbol(JSVM_Env env,JSVM_Value value,bool* isSymbol)](#oh_jsvm_issymbol) | Checks whether the value passed in is a symbol. This is equivalent to `typeof value === 'ymbol'` in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsFunction(JSVM_Env env,JSVM_Value value,bool* isFunction)](#oh_jsvm_isfunction) | Checks whether the value passed in is a function. This is equivalent to `typeof value === 'function'` in JavaScript.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsObject(JSVM_Env env,JSVM_Value value,bool* isObject)](#oh_jsvm_isobject) | Checks whether the value passed in is an object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBigInt(JSVM_Env env,JSVM_Value value,bool* isBigInt)](#oh_jsvm_isbigint) | Checks whether the value passed in is a BigInt. This is equivalent to `typeof value === 'bigint'` in JavaScript.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateMap(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_createmap) | Returns the JavaScript value corresponding to the JavaScript Map type.|
| [JSVM_Status JSVM_CDECL OH_JSVM_IsMap(JSVM_Env env,JSVM_Value value,bool* isMap)](#oh_jsvm_ismap) | Checks whether the value passed in is a map.|
| [JSVM_Status JSVM_CDECL OH_JSVM_IsConstructor(JSVM_Env env,JSVM_Value value,bool* isConstructor)](#oh_jsvm_isconstructor) | Checks whether the value passed in is a constructor.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateRegExp(JSVM_Env env,JSVM_Value value,JSVM_RegExpFlags flags,JSVM_Value* result)](#oh_jsvm_createregexp) | This API returns the regular expression object corresponding to the input JavaScript string. An exception may be thrown.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectGetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value* result)](#oh_jsvm_objectgetprototypeof) | Gets the prototype of a JavaScript object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value prototype)](#oh_jsvm_objectsetprototypeof) | Sets the prototype of a JavaScript object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSet(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_createset) | Creates a JavaScript Set object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSet(JSVM_Env env,JSVM_Value value,bool* isSet)](#oh_jsvm_isset) | Checks whether the specified object is of the Set type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBigInt(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetobigint) | Implements the abstract operation `ToBigInt()`.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsRegExp(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isregexp) | Checks whether the value passed in is a JavaScript RegExp object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunctionWithScript(JSVM_Env env,const char* funcName,size_t length,size_t argc,const JSVM_Value* argv,JSVM_Value script,JSVM_Value* result)](#oh_jsvm_createfunctionwithscript) | Creates a function with the given JavaScript as the function body.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_PumpMessageLoop(JSVM_VM vm,bool* result)](#oh_jsvm_pumpmessageloop) | Starts the task queue in the virtual machine, which can be executed through the external event loop.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_PerformMicrotaskCheckpoint(JSVM_VM vm)](#oh_jsvm_performmicrotaskcheckpoint) | Checks whether there are micro tasks waiting in the queue. If yes, execute them.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RetainScript(JSVM_Env env, JSVM_Script script)](#oh_jsvm_retainscript) | Permanently saves a JSVM_Script and extends its lifecycle beyond the current scope.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseScript(JSVM_Env env, JSVM_Script script)](#oh_jsvm_releasescript) | Releases the script reserved by OH_JSVM_RetainScript. After the script is released, do not use the input script again.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspectorWithName(JSVM_Env env,int pid,const char* name)](#oh_jsvm_openinspectorwithname) | Opens an inspector named name and opens the Unix domain port of the corresponding pid.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmModule(JSVM_Env env,const uint8_t *wasmBytecode,size_t wasmBytecodeLength,const uint8_t *cacheData,size_t cacheDataLength,bool *cacheRejected,JSVM_Value *wasmModule)](#oh_jsvm_compilewasmmodule) | Compiles the WebAssembly bytecode to obtain a WebAssembly module. If the WebAssembly cache is provided, it will be deserialized first. If the JIT permission is not supported, a log is printed for notification.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmFunction(JSVM_Env env,JSVM_Value wasmModule,uint32_t functionIndex,JSVM_WasmOptLevel optLevel)](#oh_jsvm_compilewasmfunction) | Compiles the function with the specified index in the WebAssembly module at a specified optimization level. If the JIT permission is not supported, a log is printed for notification.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsWasmModuleObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_iswasmmoduleobject) | Checks whether the given JSVM_Value is a WebAssembly module.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateWasmCache(JSVM_Env env,JSVM_Value wasmModule,const uint8_t** data,size_t* length)](#oh_jsvm_createwasmcache) | Creates a WebAssembly cache. If the JIT permission is not supported, a log is printed for notification.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseCache(JSVM_Env env,const uint8_t* cacheData,JSVM_CacheType cacheType)](#oh_jsvm_releasecache) | Releases the cache of a specified type.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBigIntObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isbigintobject) | Checks whether the given JSVM_Value is a BigInt object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBooleanObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isbooleanobject) | Checks whether the given JSVM_Value is a Boolean object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsStringObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isstringobject) | Checks whether the given JSVM_Value is a string object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNumberObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isnumberobject) | Checks whether the given JSVM_Value is a number object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbolObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_issymbolobject) | Checks whether the given JSVM_Value is a symbol object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolAsyncIterator(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolasynciterator) | Obtains the Symbol.AsyncIterator capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolHasInstance(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolhasinstance) | Obtains the Symbol.HasInstance capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIsConcatSpreadable(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolisconcatspreadable) | Obtains the Symbol.IsConcatSpreadable capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolMatch(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolmatch) | Obtains the Symbol.Match capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolReplace(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolreplace) | Obtains the Symbol.Replace capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSearch(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolsearch) | Obtains the Symbol.Search capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSplit(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolsplit) | Obtains the Symbol.Split capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToPrimitive(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboltoprimitive) | Obtains the Symbol.ToPrimitive capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolUnscopables(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolunscopables) | Obtains the Symbol.Unscopables capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToStringTag(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboltostringtag) | Obtains the Symbol.ToStringTag capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIterator(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboliterator) | Obtains the Symbol.Iterator capability in the well-known symbol.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_TraceStart(size_t count,const JSVM_TraceCategory* categories,const char* tag,size_t eventsCount)](#oh_jsvm_tracestart) | Starts to collect information of a specified trace type for all JSVM runtime instances (thread-unsafe).|
| [JSVM_EXTERN JSVM_Status OH_JSVM_TraceStop(JSVM_OutputStream stream, void* streamData)](#oh_jsvm_tracestop) | Stops collecting information of a specified trace type for all JSVM runtime instances (thread-unsafe).|
| [JSVM_EXTERN JSVM_Status OH_JSVM_AddHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,JSVM_GCType gcType,void* userData)](#oh_jsvm_addhandlerforgc) | Adds a GC callback function to a VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_RemoveHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,void* userData)](#oh_jsvm_removehandlerforgc) | Removes a GC callback function from a VM.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForOOMError(JSVM_VM vm,JSVM_HandlerForOOMError handler)](#oh_jsvm_sethandlerforoomerror) | Sets a callback for handling OOM errors. If this method is called repeatedly, only the last call takes effect. If handler is null, the previous setting is canceled.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetDebugOption(JSVM_Env env, JSVM_DebugOption debugOption, bool isEnabled)](#oh_jsvm_setdebugoption) | Enables or disables a specified debugging option of a JSVM_Env instance.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForFatalError(JSVM_VM vm,JSVM_HandlerForFatalError handler)](#oh_jsvm_sethandlerforfatalerror) | Sets a callback for handling fatal errors. If this method is called repeatedly, only the last call takes effect. If handler is null, the previous setting is canceled.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForPromiseReject(JSVM_VM vm,JSVM_HandlerForPromiseReject handler)](#oh_jsvm_sethandlerforpromisereject) | Sets a callback for PromiseReject errors. If an API is called repeatedly, only the last call takes effect. If handler is set to null, the previous setting is canceled.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithOptions(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value parentClass,size_t optionCount,JSVM_DefineClassOptions options[],JSVM_Value* result)](#oh_jsvm_defineclasswithoptions) | When encapsulating a C++ class, the C++ constructor callback passed through the constructor function should be a static method in the class. This method calls the actual class constructor, encapsulates the new C++ instance in a JavaScript object based on the passed options, and returns the encapsulated object.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringLatin1(JSVM_Env env,char* str,size_t length,JSVM_Finalize finalizeCallback,void* finalizeHint,JSVM_Value* result,bool* copied)](#oh_jsvm_createexternalstringlatin1) | This API uses ISO-8859-1-encoded C strings to create external JavaScript strings. If an external string fails to be created, the native string is copied.|
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringUtf16(JSVM_Env env,char16_t* str,size_t length,JSVM_Finalize finalizecallback,void* finalizeHint,JSVM_Value* result,bool* copied)](#oh_jsvm_createexternalstringutf16) | This API uses UTF16-LE encoded C strings to create an external JavaScript string. If the external string fails to be created, the native string is copied.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreatePrivate(JSVM_Env env,JSVM_Value description,JSVM_Data* result)](#oh_jsvm_createprivate) | Creates a JavaScript private key object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value value)](#oh_jsvm_setprivate) | Sets the private attribute for the passed object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value *result)](#oh_jsvm_getprivate) | Obtains the private attribute of the private key from the passed object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeletePrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key)](#oh_jsvm_deleteprivate) | Deletes the private attribute of the private key from the passed object.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataReference(JSVM_Env env,JSVM_Data data,uint32_t initialRefcount,JSVM_Ref* result)](#oh_jsvm_createdatareference) | Creates a reference to a given JSVM_Data object. The initial reference count is the passed initialRefcount.|
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceData(JSVM_Env env,JSVM_Ref ref,JSVM_Data* result)](#oh_jsvm_getreferencedata) | If the reference is still valid, the corresponding JSVM_Data is returned through the result parameter, indicating the JavaScript value associated with JSVM_Ref. Otherwise, the result is empty.|

## Function Description

### OH_JSVM_Init()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Init(const JSVM_InitOptions* options)
```

**Description**

Initializes a JavaScript VM.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const JSVM_InitOptions](capi-jsvm-jsvm-initoptions.md)* options | Options for initializing the JavaScript VM.|

**Returns**

| Type                                                         | Description|
|-------------------------------------------------------------| -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails. The JSVM initialization is complete in the current process and does not need to be performed again.|

### OH_JSVM_CreateVM()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateVM(const JSVM_CreateVMOptions* options,JSVM_VM* result)
```

**Description**

Creates a VM instance.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const JSVM_CreateVMOptions](capi-jsvm-jsvm-createvmoptions.md)* options | Options for creating a VM instance.|
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md)* result | New VM instance.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_SetMicrotaskPolicy()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetMicrotaskPolicy(JSVM_VM vm,JSVM_MicrotaskPolicy policy)
```

**Description**

Sets the microtask execution policy of a VM instance. If this method is not called, the default policy of the VM instance is JSVM_MicrotaskPolicy::JSVM_MICROTASK_AUTO.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM instance for setting the microtask execution policy.|
| [JSVM_MicrotaskPolicy](capi-jsvm-types-h.md#jsvm_microtaskpolicy) policy | Policy for executing microtasks.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  JSVM_OK if the API is successfully called.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_DestroyVM()

```
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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): The execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): The input parameter is invalid.|

### OH_JSVM_CreateProxy()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateProxy(JSVM_Env env,JSVM_Value target,JSVM_Value handler,JSVM_Value* result)
```

**Description**

Creates a JavaScript proxy, which is equivalent to executing new Proxy(target, handler) in JavaScript.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) target | JavaScript object used to create a proxy.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) handler | JavaScript object that defines the operations to be intercepted and how to handle the intercepted operations.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Created JavaScript proxy.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Execution status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) The API is successfully called.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) The target or handler is not a JavaScript object.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) The execution fails due to an unknown reason.|

### OH_JSVM_IsProxy()

```
JSVM_Status JSVM_CDECL OH_JSVM_IsProxy(JSVM_Env env,JSVM_Value value,bool* isProxy)
```

**Description**

Checks whether the input value is a JavaScript proxy.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Value to be checked.|
| bool* isProxy | Whether the value is a JavaScript proxy. The options are true and false.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Execution status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) The API is successfully called.|

### OH_JSVM_ProxyGetTarget()

```
JSVM_Status JSVM_CDECL OH_JSVM_ProxyGetTarget(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Obtains the target object in a JavaScript proxy.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Proxy of the target object to be obtained.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Target object of the proxy.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Execution status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the API is successfully called.<br>         [JSVM_INVALID_TYPE](capi-jsvm-types-h.md#jsvm_status) indicates that the value is not a JavaScript proxy.|

### OH_JSVM_OpenVMScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenVMScope(JSVM_VM vm,JSVM_VMScope* result)
```

**Description**

Opens a new VM scope for a VM instance.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | Target VM instance.|
| [JSVM_VMScope](capi-jsvm-jsvm-vmscope--8h.md)* result | New VM scope.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CloseVMScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseVMScope(JSVM_VM vm,JSVM_VMScope scope)
```

**Description**

Closes the VM scope of a VM instance.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | Target VM instance.|
| [JSVM_VMScope](capi-jsvm-jsvm-vmscope--8h.md) scope | VM scope to be stopped.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateEnv()

```
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
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Array of property descriptors.|
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md)* result | New environment.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateEnvFromSnapshot()

```
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
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md)* result | New environment.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_DestroyEnv()

```
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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_OpenEnvScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenEnvScope(JSVM_Env env,JSVM_EnvScope* result)
```

**Description**

Opens a new environment scope.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_EnvScope](capi-jsvm-jsvm-envscope--8h.md)* result | New environment scope.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CloseEnvScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseEnvScope(JSVM_Env env,JSVM_EnvScope scope)
```

**Description**

Closes an environment scope.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_EnvScope](capi-jsvm-jsvm-envscope--8h.md) scope | Environment scope to be closed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetVM()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetVM(JSVM_Env env,JSVM_VM* result)
```

**Description**

Retrieves the virtual machine instance of a given environment.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md)* result | VM instance of the specified environment.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CompileScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScript(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_Script* result)
```

**Description**

Compiles a string of JavaScript code and returns the compiled script.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | JavaScript code that includes the script to be compiled.|
| const uint8_t* cachedData | Optional. Code cache data of the script.|
| size_t cacheDataLength | Length of the cachedData array.|
| bool eagerCompile | Whether to compile the script immediately. The value true indicates yes, and the value false indicates no.|
| bool* cacheRejected | Whether the code cache is compiled. The value true indicates yes, and the value false indicates no.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md)* result | Compiled script.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): The execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status): The input parameter is not of the string type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): The execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): A JavaScript exception occurs during the execution.|

### OH_JSVM_CompileScriptWithOrigin()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOrigin(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_ScriptOrigin* origin,JSVM_Script* result)
```

**Description**

Compiles a string of JavaScript code that contains source map information and returns the compiled script.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | JavaScript code that includes the script to be compiled.|
| const uint8_t* cachedData | Optional. Code cache data of the script.|
| size_t cacheDataLength | Length of the cachedData array.|
| bool eagerCompile | Whether to compile the script immediately. The options are true (yes) and false (no).|
| bool* cacheRejected | Whether the code cache is compiled. The options are true (yes) and false (no).|
| [JSVM_ScriptOrigin](capi-jsvm-jsvm-scriptorigin.md)* origin | Source code information, including the source map location and source code file name.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md)* result | Compiled script.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_CompileScriptWithOptions()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOptions(JSVM_Env env,JSVM_Value script,size_t optionCount,JSVM_CompileOptions options[],JSVM_Value* result)
```

**Description**

Compiles a string of JavaScript code and returns the compiled script.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | JavaScript code that includes the script to be compiled.|
| size_t optionCount | Length of the input option array.|
| JSVM_CompileOptions options[] | Option array, which stores all compilation options.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Compiled script.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input data is a null pointer.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_CreateCodeCache()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateCodeCache(JSVM_Env env,JSVM_Script script,const uint8_t** data,size_t* length)
```

**Description**

Creates a code cache for the compiled script.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Target environment in which the JSVM-API will be called.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | Target compilation script.|
| const uint8_t** data | Code cache data|
| size_t* length | Length of the code cache data.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails.|

### OH_JSVM_RunScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RunScript(JSVM_Env env,JSVM_Script script,JSVM_Value* result)
```

**Description**

Executes a string of JavaScript code and returns the result. Note that the function does not allow the script to access the current lexical scope or module scope, unlike eval. This means that pseudo-global variables such as require are unavailable. The script can access the global scope. The functions and variable declarations in the script will be added to the global object. Variable declarations using **let** and **const** are globally visible, but are not added to the global object. The value of **this** is **global** in the script. If JIT permission is not supported, the script containing WebAssembly will fail to be executed. There are performance differences in specific scenarios, and a log is printed to notify the developer.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | JavaScript string that includes the script to be executed.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Value generated after the script is executed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during execution.|

### OH_JSVM_SetInstanceData()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetInstanceData(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint)
```

**Description**

Sets instance data so that it is associated with the currently running JSVM environment. You can use **OH_JSVM_GetInstanceData()** to get data later. Any existing data that is associated with the currently running JSVM environment and is set by calling OH_JSVM_SetInstanceData() will be overwritten. If **finalizeCb** was previously provided, it will not be called.

**Since**: 11


**Parameters**

| Name                                                           | Description|
|----------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                      | Environment for calling the JSVM-API.|
| void* data                                                     | Data bound for this instance.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | Function for destroying the environment.|
| void* finalizeHint                                             | Optional hint passed to the **finalize** callback during collection.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetInstanceData()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetInstanceData(JSVM_Env env,void** data)
```

**Description**

Obtains the data associated with the currently running JSVM environment by calling OH_JSVM_SetInstanceData(). If no associated data is set, this function is called successfully and **data** is set to **NULL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| void** data | Data that has been by **OH_JSVM_SetInstanceData()**, associated with the current JSVM environment.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetLastErrorInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetLastErrorInfo(JSVM_Env env,const JSVM_ExtendedErrorInfo** result)
```

**Description**

Retrieves the JSVM_ExtendedErrorInfo structure, which contains information about the last error that occurred. The content of **JSVM_ExtendedErrorInfo** returned is valid only before the JSVM-API function is called for the same environment. This includes a call to **OH_JSVM_IsExceptionPending**, so you may often need to copy information for later use. The pointer returned in error_message points to a statically defined string. Therefore, you can safely use the pointer if you copy it out of the error_message field (which will be overwritten) before calling another JSVM-API function.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [const JSVM_ExtendedErrorInfo](capi-jsvm-jsvm-extendederrorinfo.md)** result | JSVM_ExtendedErrorInfo struct that contains more information about the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_Throw()

```
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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_ThrowError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowError(JSVM_Env env,const char* code,const char* msg)
```

**Description**

Throws a JavaScript error with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* code | Optional error code to be set on the error.|
| const char* msg | C string representing the text associated with the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_ThrowTypeError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowTypeError(JSVM_Env env,const char* code,const char* msg)
```

**Description**

Throws a JavaScript TypeError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* code | Optional error code to be set on the error.|
| const char* msg | C string representing the text associated with the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_ThrowRangeError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowRangeError(JSVM_Env env,const char* code,const char* msg)
```

**Description**

Throws a JavaScript RangeError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* code | Optional error code to be set on the error.|
| const char* msg | C string representing the text associated with the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_ThrowSyntaxError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowSyntaxError(JSVM_Env env,const char* code,const char* msg)
```

**Description**

Throws a JavaScript SyntaxError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* code | Optional error code to be set on the error.|
| const char* msg | C string representing the text associated with the error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_IsError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsError(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given JSVM_Value indicates an error.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* result | If JSVM_Value indicates an error, **true** is returned. Otherwise, **false** is returned.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**Description**

Creates a JavaScript Error with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | (Optional) JSVM_Value, which is a string with the associated error code.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | Message that references the JavaScript string as an error.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Created error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.|

### OH_JSVM_CreateTypeError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**Description**

Creates a JavaScript TypeError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | (Optional) JSVM_Value, which is a string with the associated error code.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | Message that references the JavaScript string as an error.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Created error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.|

### OH_JSVM_CreateRangeError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateRangeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**Description**

Creates a JavaScript RangeError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | (Optional) JSVM_Value, which is a string with the associated error code.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | Message that references the JavaScript string as an error.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Created error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.|

### OH_JSVM_CreateSyntaxError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSyntaxError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**Description**

Creates a JavaScript SyntaxError with the provided text.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | (Optional) JSVM_Value, which is a string with the associated error code.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | Message that references the JavaScript string as an error.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Created error.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.|

### OH_JSVM_GetAndClearLastException()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetAndClearLastException(JSVM_Env env,JSVM_Value* result)
```

**Description**

Gets and clears the last exception. If pending occurs, a JavaScript exception is returned. Otherwise, **NULL** is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | An exception is returned if pending occurs. Otherwise, **NULL** is returned.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_IsExceptionPending()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsExceptionPending(JSVM_Env env,bool* result)
```

**Description**

Checks whether the last exception is caused by pending. If yes, **true** is returned. Otherwise, **false** is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| bool* result | If the exception is suspended, the value is true. Otherwise, the value is false.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_OpenHandleScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenHandleScope(JSVM_Env env,JSVM_HandleScope* result)
```

**Description**

Opens a new scope.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_HandleScope](capi-jsvm-jsvm-handlescope--8h.md)* result | New scope.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CloseHandleScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseHandleScope(JSVM_Env env,JSVM_HandleScope scope)
```

**Description**

(Mandatory) Closes the passed scope in the reverse order of creating scopes.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_HandleScope](capi-jsvm-jsvm-handlescope--8h.md) scope | Scope to be closed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_HANDLE_SCOPE_MISMATCH](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails.|

### OH_JSVM_OpenEscapableHandleScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope* result)
```

**Description**

Opens a new scope that can move an object from it to an external scope.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_EscapableHandleScope](capi-jsvm-jsvm-escapablehandlescope--8h.md)* result | New scope.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CloseEscapableHandleScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope scope)
```

**Description**

(Required) Closes the passed scope in the reverse order of creating the scope. This JSVM_API can be called even if there is a suspended JavaScript exception.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_EscapableHandleScope](capi-jsvm-jsvm-escapablehandlescope--8h.md) scope | Scope to be closed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_HANDLE_SCOPE_MISMATCH](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails.|

### OH_JSVM_EscapeHandle()

```
JSVM_EXTERN JSVM_Status OH_JSVM_EscapeHandle(JSVM_Env env,JSVM_EscapableHandleScope scope,JSVM_Value escapee,JSVM_Value* result)
```

**Description**

Escalates the handle to a JavaScript object so that it is valid through the lifecycle of the external scope. Each scope can be called only once. If it is called for multiple times, an error is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_EscapableHandleScope](capi-jsvm-jsvm-escapablehandlescope--8h.md) scope | Current scope.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) escapee | JavaScript object to be escalated.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Handle to the escalated object in the external scope.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_ESCAPE_CALLED_TWICE](capi-jsvm-types-h.md#jsvm_status) indicates that the scope object has been closed.|

### OH_JSVM_CreateReference()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateReference(JSVM_Env env,JSVM_Value value,uint32_t initialRefcount,JSVM_Ref* result)
```

**Description**

Creates a new reference with the specified reference count for the passed-in value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value for which a reference is being created.|
| uint32_t initialRefcount | Initial reference count of a new reference.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | Points to a new reference.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_DeleteReference()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteReference(JSVM_Env env,JSVM_Ref ref)
```

**Description**

Deletes the passed-in reference.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | JSVM_Ref to be deleted.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_ReferenceRef()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceRef(JSVM_Env env,JSVM_Ref ref,uint32_t* result)
```

**Description**

Increases the reference count and returns the new reference count.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | Reference that is passed in. Its reference count will increase.|
| uint32_t* result | New reference count.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_ReferenceUnref()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceUnref(JSVM_Env env,JSVM_Ref ref,uint32_t* result)
```

**Description**

Decreases the reference count and returns the new reference count.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | JSVM_Ref that is passed in. Its reference count will decrease.|
| uint32_t* result | New reference count.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails.|

### OH_JSVM_GetReferenceValue()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceValue(JSVM_Env env,JSVM_Ref ref,JSVM_Value* result)
```

**Description**

If it is still valid, this JSVM-API returns JSVM_Value, indicating the JavaScript value associated with JSVM_Ref. Otherwise, the result is **NULL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | JSVM_Ref for requesting the corresponding value.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value referenced by JSVM_Ref.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateArray()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArray(JSVM_Env env,JSVM_Value* result)
```

**Description**

Returns the JSVM-API value corresponding to the JavaScript Array type.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript array.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateArrayWithLength()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayWithLength(JSVM_Env env,size_t length,JSVM_Value* result)
```

**Description**

Returns the JSVM-API value corresponding to the JavaScript Array type. The length attribute of the array is set to the input length parameter. However, the underlying buffer is not pre-allocated by the VM when the array is created. This behavior is left to the underlying VM implementation.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| size_t length | Initial length of the array.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript array.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateArraybuffer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArraybuffer(JSVM_Env env,size_t byteLength,void** data,JSVM_Value* result)
```

**Description**

Returns the JSVM-API value corresponding to the JavaScript ArrayBuffer type. ArrayBuffer is used to represent a binary data buffer of a fixed length. It is usually used as the backup buffer of the TypedArray object. The allocated ArrayBuffer has an underlying byte buffer whose size is determined by the **length** argument. The underlying buffer can be returned to and operated by the caller. This buffer can only be written directly from the native code. If you want to write the buffer from JavaScript, you need to create a TypedArray or DataView object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| size_t byteLength | Length of the array buffer to be created, in bytes.|
| void** data | Pointer to the underlying byte buffer of the ArrayBuffer. **data** can be ignored by passing **NULL** to it.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript ArrayBuffer.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_AllocateArrayBufferBackingStoreData()

```
JSVM_Status JSVM_CDECL OH_JSVM_AllocateArrayBufferBackingStoreData(size_t byteLength,JSVM_InitializedFlag initialized,void **data)
```

**Description**

Applies for a segment of BackingStore memory for the array buffer.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| size_t byteLength | Size of the BackingStore memory.|
| [JSVM_InitializedFlag](capi-jsvm-types-h.md#jsvm_initializedflag) initialized | Mode of initializing the BackingStore memory.|
| void **data | Pointer to the address of allocated BackingStore memory.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input data is a null pointer.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the memory application fails.|

### OH_JSVM_FreeArrayBufferBackingStoreData()

```
JSVM_Status JSVM_CDECL OH_JSVM_FreeArrayBufferBackingStoreData(void *data)
```

**Description**

Frees the BackingStore memory allocated by **OH_JSVM_AllocateArrayBufferBackingStoreData**.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| void *data| Allocated BackingStore memory.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input data is a null pointer.|

### OH_JSVM_CreateArrayBufferFromBackingStoreData()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateArrayBufferFromBackingStoreData(JSVM_Env env,void *data,size_t backingStoreSize,size_t offset,size_t arrayBufferSize,JSVM_Value *result)
```

**Description**

Creates an array buffer on the allocated BackingStore memory.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| void *data | Allocated BackingStore memory.|
| size_t backingStoreSize | Size of the BackingStore memory.|
| size_t offset | Relative offset between the start position of the array buffer in the memory and the memory header, in bytes.|
| size_t arrayBufferSize | Size of the array buffer, in bytes.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) *result | Pointer to the array buffer address|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that one of the following exceptions is triggered:<br>         1. offset + arrayBufferSize > backingStoreSize.<br>         2. The value of backingStoreSize or arrayBufferSize is 0.<br>         3. The data or result is empty.|

### OH_JSVM_CreateDate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDate(JSVM_Env env,double time,JSVM_Value* result)
```

**Description**

Allocates a JavaScript Date object. This API does not process leap seconds. This is because ECMAScript complies with the POSIX time specifications and ignores leap seconds.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| double time | ECMAScript time since 00:00:00 UTC on January 1, 1970, in milliseconds.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript Date object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_CreateExternal()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternal(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Value* result)
```

**Description**

Allocates a JavaScript value with external data. This is used to pass external data through JavaScript code. You can use **OH_JSVM_GetValueExternal** to retrieve the value from the native code. This API adds a **JSVM_Finalize** callback, which is called when the newly created JavaScript object is garbage collected. The created value is not an object, so it does not support additional attributes. It is considered as a unique value type. JSVM_EXTERNAL is generated when OH_JSVM_Typeof() is called using an external value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| void* data | Raw pointer to external data.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | Optional callback called to collect external values. **JSVM_Finalize** provides more details.|
| void* finalizeHint | Optional hint passed to the **finalize** callback during collection.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of an external value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateObject(JSVM_Env env,JSVM_Value* result)
```

**Description**

Allocates a default JavaScript object. This function is equivalent to executing **new Object()** in JavaScript.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateSymbol()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSymbol(JSVM_Env env,JSVM_Value description,JSVM_Value* result)
```

**Description**

Creates a JavaScript symbol value using a UTF8 encoded C string.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) description | Optional JSVM_Value, which refers to the JavaScript string to be set to the symbol description.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.|

### OH_JSVM_SymbolFor()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SymbolFor(JSVM_Env env,const char* utf8description,size_t length,JSVM_Value* result)
```

**Description**

Searches the global registry for an existing symbol with the given description. If the symbol already exists, it is returned. Otherwise, a new symbol is created in the registry.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* utf8description | UTF-8 C string, indicating the text used as the symbol description.|
| size_t length | Length of the description string, in bytes. If it is null-terminated, the value is **JSVM_AUTO_LENGTH**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateTypedarray()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypedarray(JSVM_Env env,JSVM_TypedarrayType type,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)
```

**Description**

Creates a JavaScript TypedArray object based on an existing ArrayBuffer object. A TypedArray object provides an array-like view on the underlying data buffer, where each element has the same underlying binary scalar data type. Requirement: length x Scalar byte value of the element + byteOffset is less than or equal to the value of ByteLength() of the input array. Otherwise, a range error (RangeError) is thrown.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_TypedarrayType](capi-jsvm-types-h.md#jsvm_typedarraytype) type | Scalar data type of an element in TypedArray.|
| size_t length | Number of elements in TypedArray.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | ArrayBuffer, which is the basis of TypedArray.|
| size_t byteOffset | Byte offset for the start position of mapping TypedArray in the ArrayBuffer.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript TypedArray.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during execution.|

### OH_JSVM_CreateDataview()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataview(JSVM_Env env,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)
```

**Description**

Creates a JavaScript DataView object based on an existing ArrayBuffer object. A DataView object provides an array-like view on the underlying data buffer, where elements can have different sizes and types. Requirements: The length of the binary plus byteOffset must not be greater than the size (in bytes) of the input array. Otherwise, a range error (RangeError) is thrown.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| size_t length | Number of elements in a DataView.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | ArrayBuffer at the bottom layer of the DataView.|
| size_t byteOffset | Byte offset in the ArrayBuffer, indicating the start position of mapping a DataView.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript DataView object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during execution.|

### OH_JSVM_CreateInt32()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt32(JSVM_Env env,int32_t value,JSVM_Value* result)
```

**Description**

Converts a C int32_t value to a JavaScript number value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| int32_t value | Integer to be represented in JavaScript.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript number type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateUint32()

```
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
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript number type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateInt64()

```
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
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript number type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateDouble()

```
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
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript number type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateBigintInt64()

```
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
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript BigInt type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateBigintUint64()

```
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
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript BigInt type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateBigintWords()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintWords(JSVM_Env env,int signBit,size_t wordCount,const uint64_t* words,JSVM_Value* result)
```

**Description**

Converts a group of 64-bit unsigned bits to a single BigInt value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| int signBit | Whether the generated BigInt is positive or negative.|
| size_t wordCount | Length of the words array.|
| const uint64_t* words | uint64_t little-endian words array.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript BigInt type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_CreateStringLatin1()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringLatin1(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)
```

**Description**

Converts a C string encoded in ISO-8859-1 to a JavaScript string value. Copies a native string.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* str | Buffer of an ISO-8859-1-encoded string.|
| size_t length | Length of a string, in bytes. If it is null-terminated, the value is **JSVM_AUTO_LENGTH**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_CreateStringUtf16()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf16(JSVM_Env env,const char16_t* str,size_t length,JSVM_Value* result)
```

**Description**

Converts a UTF16-LE encoded C string to a JavaScript string value. Copies a native string.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char16_t* str | Buffer of a UTF16-LE-encoded string.|
| size_t length | Length of a string in 2-byte code. If it is null-terminated, the value is **JSVM_AUTO_LENGTH**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_CreateStringUtf8()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf8(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)
```

**Description**

Creates a JavaScript string value using a UTF8 encoded C string. Copies a native string.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* str | Buffer of a UTF8-encoded string.|
| size_t length | Length of a string, in bytes. If it is null-terminated, the value is **JSVM_AUTO_LENGTH**.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_GetArrayLength()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetArrayLength(JSVM_Env env,JSVM_Value value,uint32_t* result)
```

**Description**

Gets the length of an array.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript array whose length is to be queried.|
| uint32_t* result | uint32 indicates the array length.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_ARRAY_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the array type.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_GetArraybufferInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetArraybufferInfo(JSVM_Env env,JSVM_Value arraybuffer,void** data,size_t* byteLength)
```

**Description**

Gets the underlying data buffer of the ArrayBuffer and its length.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | ArrayBuffer to be queried.|
| void** data | Underlying data buffer of the ArrayBuffer. If byte_length is 0, the value may be NULL or any other pointer value.|
| size_t* byteLength | Length of the underlying data buffer, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_GetPrototype()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetPrototype(JSVM_Env env,JSVM_Value object,JSVM_Value* result)
```

**Description**

Gets the prototype of an object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | JavaScript object whose prototype is to be returned. This will return the equivalent of **Object.getPrototypeOf** (different from the prototype property of the function).|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Prototype of a given object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_GetTypedarrayInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetTypedarrayInfo(JSVM_Env env,JSVM_Value typedarray,JSVM_TypedarrayType* type,size_t* length,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)
```

**Description**

Gets the properties of a typed array. If any property is not required, its output parameter can be **NULL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) typedarray | TypedArray whose properties are to be queried.|
| [JSVM_TypedarrayType](capi-jsvm-types-h.md#jsvm_typedarraytype)* type | Scalar data type of an element in TypedArray.|
| size_t* length | Number of elements in the TypedArray.|
| void** data | The data buffer of the TypedArray is adjusted based on the value of byte_offset so that the data buffer points to the first element in the TypedArray. If the array length is **0**, **data** may be NULL or any other pointer value.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* arraybuffer | ArrayBuffer under TypedArray.|
| size_t* byteOffset | Byte offset of the first TypedArray element in the native array. **data** points to the first element in the array after its value has been adjusted. Therefore, the first byte of the native array is located at data - byte_offset.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_GetDataviewInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetDataviewInfo(JSVM_Env env,JSVM_Value dataview,size_t* bytelength,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)
```

**Description**

Gets the proprieties of a DataView. If any property is not required, its output parameter can be set to **NULL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) dataview |  DataView whose properties are to be queried.|
| size_t* bytelength | Number of bytes in a DataView.|
| void** data | Data buffer in a DataView. If the value of byteLength is 0, the value may be NULL or any other pointer value.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* arraybuffer | ArrayBuffer, which is the basis of DataView.|
| size_t* byteOffset | Byte offset for the start position of mapping DataView in the data buffer.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not an external JSVM_Value.|

### OH_JSVM_GetDateValue()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetDateValue(JSVM_Env env,JSVM_Value value,double* result)
```

**Description**

Returns the C double-precision base type value equivalent to the given JavaScript Date time value. If this API is successfully called, **JSVM_OK** is returned. If a JSVM_Value of a non-JavaScript date type is passed in, **JSVM_DATA_EXPECTED** is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript date.|
| double* result | Time value of the double type, expressed as the number of milliseconds since 00:00:00 UTC on January 1, 1970.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_DATE_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the Date type.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_GetValueBool()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBool(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Returns the C basic Boolean type value that is equivalent to the given JavaScript Boolean.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript Boolean object.|
| bool* result | Returns the bool value that is equivalent to the given JavaScript Boolean object. If the value of the value object is true, the result is true. Otherwise, the result is false.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_BOOLEAN_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the Boolean type.|

### OH_JSVM_GetValueDouble()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueDouble(JSVM_Env env,JSVM_Value value,double* result)
```

**Description**

Returns the C double-precision basic type value that is equivalent to the given JavaScript number.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| double* result | C double-precision primitive equivalent of a given JavaScript number.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the number type.|

### OH_JSVM_GetValueBigintInt64()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintInt64(JSVM_Env env,JSVM_Value value,int64_t* result,bool* lossless)
```

**Description**

Returns the C int64_t basic type equivalent to the given JavaScript BigInt. If necessary, it truncates the value and sets **lossless** to **false**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript BigInt.|
| int64_t* result | C int64_t primitive equivalent of the given JavaScript BigInt.|
| bool* lossless | Indicates whether the BigInt value has been losslessly converted. The value true indicates that the BigInt value has been losslessly converted, and the value false indicates that the BigInt value has not been losslessly converted.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the BitInt type.|

### OH_JSVM_GetValueBigintUint64()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintUint64(JSVM_Env env,JSVM_Value value,uint64_t* result,bool* lossless)
```

**Description**

Returns the C uint64_t basic type value that is equivalent to the given JavaScript BigInt. If necessary, it truncates the value and sets **lossless** to **false**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript BigInt.|
| uint64_t* result | C uint64_t primitive equivalent of the given JavaScript BigInt.|
| bool* lossless | Indicates whether the BigInt value has been converted without loss. The value true indicates yes, and the value false indicates no.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the BitInt type.|

### OH_JSVM_GetValueBigintWords()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintWords(JSVM_Env env,JSVM_Value value,int* signBit,size_t* wordCount,uint64_t* words)
```

**Description**

Gets the sign bit, 64-bit little-endian array, and number of elements in the array from a BigInt value. Both **signBit** and **words** can be set to **NULL**. In this case, only **wordCount** is obtained.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript BigInt.|
| int* signBit | Whether JavaScript BigInt is a positive or negative integer.|
| size_t* wordCount | Length of the words array. It will be set to the actual number of words required to store this BigInt.|
| uint64_t* words | Pointer to the pre-allocated 64-bit words array.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the BitInt type.|

### OH_JSVM_GetValueExternal()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueExternal(JSVM_Env env,JSVM_Value value,void** result)
```

**Description**

Gets the external data pointer previously passed to **OH_JSVM_CreateExternal()**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript external value.|
| void** result | Pointer to the data wrapped by the JavaScript external value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not an external JSVM_Value.|

### OH_JSVM_GetValueInt32()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt32(JSVM_Env env,JSVM_Value value,int32_t* result)
```

**Description**

Returns the C int32 basic type value that is equivalent to the given JavaScript number.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| int32_t* result | C int32 primitive equivalent of a given JavaScript number.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the number type.|

### OH_JSVM_GetValueInt64()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt64(JSVM_Env env,JSVM_Value value,int64_t* result)
```

**Description**

Returns the C int64 basic type value that is equivalent to the given JavaScript number.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| int64_t* result | C int64 primitive equivalent of a given JavaScript number.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the number type.|

### OH_JSVM_GetValueStringLatin1()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringLatin1(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)
```

**Description**

Returns the ISO-8859-1 encoded string corresponding to the input value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| char* buf | Buffer to which an ISO-8859-1 encoded string is written. If NULL is passed, the length of the string (in bytes, excluding the null terminator) is returned in result.|
| size_t bufsize | Size of the destination buffer. If the size is insufficient, the returned string is truncated and terminated with null.|
| size_t* result | Number of bytes copied to the buffer, excluding the null terminator.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.|

### OH_JSVM_GetValueStringUtf8()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf8(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)
```

**Description**

Returns the UTF8 encoded string corresponding to the input value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript string.|
| char* buf | Buffer to which a UTF8-encoded string is written. If NULL is passed, the string length (excluding the null terminator) is returned in bytes in result.|
| size_t bufsize | Size of the destination buffer. If the size is insufficient, the returned string is truncated and terminated with null.|
| size_t* result | Number of bytes copied to the buffer, excluding the null terminator.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.|

### OH_JSVM_GetValueStringUtf16()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf16(JSVM_Env env,JSVM_Value value,char16_t* buf,size_t bufsize,size_t* result)
```

**Description**

Queries the UTF16-encoded string corresponding to the input value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript string.|
| char16_t* buf | Buffer to which a UTF16-LE-encoded string is written. If NULL is passed, the 2-byte code unit length of the string is returned, excluding the null terminator.|
| size_t bufsize | Size of the destination buffer. If the size is insufficient, the returned string is truncated and terminated with null.|
| size_t* result | Number of the 2-byte code units copied to the buffer, excluding the null terminator.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.|

### OH_JSVM_GetValueUint32()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueUint32(JSVM_Env env,JSVM_Value value,uint32_t* result)
```

**Description**

Returns the C uint_32 basic type value equivalent to the given JavaScript number.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript number.|
| uint32_t* result | C uint32_t primitive equivalent of a given JSVM_Value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the number type.|

### OH_JSVM_GetBoolean()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetBoolean(JSVM_Env env,bool value,JSVM_Value* result)
```

**Description**

Returns the JavaScript singleton object that represents the given Boolean value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| bool value | Boolean value to be retrieved. The value can be true or false.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JavaScript Boolean singleton to be retrieved.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetGlobal()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetGlobal(JSVM_Env env,JSVM_Value* result)
```

**Description**

Gets the global object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JavaScript global object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetNull()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetNull(JSVM_Env env,JSVM_Value* result)
```

**Description**

Gets the null object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JavaScript null object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetUndefined()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetUndefined(JSVM_Env env,JSVM_Value* result)
```

**Description**

Gets the undefined object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JavaScript undefined value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CoerceToBool()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBool(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation ToBoolean().

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Forced JavaScript Boolean.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_CoerceToNumber()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToNumber(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation ToNumber(). If the passed-in value is an object, the function may run JavaScript code.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Forced JavaScript number.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input JavaScript value cannot be converted to a number.|

### OH_JSVM_CoerceToObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToObject(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation ToObject().

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Forced JavaScript object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input JavaScript value cannot be converted to an object.|

### OH_JSVM_CoerceToString()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToString(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation ToString(). If the passed-in value is an object, the function may run JavaScript code.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Forced JavaScript string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input JavaScript value cannot be converted to a string.|

### OH_JSVM_Typeof()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Typeof(JSVM_Env env,JSVM_Value value,JSVM_ValueType* result)
```

**Description**

Provides behavior similar to calling the typeof operator on a defined object. The difference is that this function can detect external values. It detects null as a separate type, while ECMAScript typeof detects object. If the value type is invalid, an error is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value whose type is to be queried.|
| [JSVM_ValueType](capi-jsvm-types-h.md#jsvm_valuetype)* result | Type of the JavaScript value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): The input parameter is invalid.|

### OH_JSVM_Instanceof()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Instanceof(JSVM_Env env,JSVM_Value object,JSVM_Value constructor,bool* result)
```

**Description**

Provides behavior similar to calling the instanceof operator on an object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | JavaScript value to be checked.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) constructor | JavaScript function object of the constructor to be checked.|
| bool* result | If object instanceof constructor is true, set it to a Boolean value of true, and vice versa.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_FUNCTION_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the function type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_IsArray()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsArray(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Provides behavior similar to calling IsArray on an object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Whether the given object is an array. The value true indicates that the object is an array, and the value false indicates that the object is not an array.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_IsArraybuffer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the passed-in object is ArrayBuffer.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Whether the specified object is an ArrayBuffer. The value true indicates that the object is an ArrayBuffer, and the value false indicates that the object is not an ArrayBuffer.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_IsDate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsDate(JSVM_Env env,JSVM_Value value,bool* isDate)
```

**Description**

Checks whether the passed-in object is a date.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* isDate | Whether the given JSVM_Value indicates a JavaScript Date object. The value true indicates yes, and the value false indicates no.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_IsTypedarray()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsTypedarray(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the passed-in object is a typed array.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Whether the given JSVM_Value indicates a TypedArray. The value true indicates yes, and the value false indicates no.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_IsDataview()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsDataview(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the passed-in object is a DataView.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Whether the given JSVM_Value represents DataView. The value true indicates that the given JSVM_Value represents DataView, and the value false indicates that the given JSVM_Value does not represent DataView.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_StrictEquals()

```
JSVM_EXTERN JSVM_Status OH_JSVM_StrictEquals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)
```

**Description**

Provides behavior similar to calling the strict equality algorithm.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) lhs | JavaScript value to be checked.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rhs | JavaScript value to be checked.|
| bool* result | Checks whether two JSVM_Value objects are strictly equal (===). The value true indicates that they are strictly equal, and the value false indicates that they are not strictly equal.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_Equals()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Equals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)
```

**Description**

Provides behavior similar to calling the loose equality algorithm. Regardless of the JavaScript value type, **true** is returned as long as the values are equal.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) lhs | JavaScript value to be checked.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rhs | JavaScript value to be checked.|
| bool* result | Checks whether two JSVM_Value objects are loosely equal (==). The value true indicates that they are loosely equal, and the value false indicates that they are not loosely equal.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_DetachArraybuffer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DetachArraybuffer(JSVM_Env env,JSVM_Value arraybuffer)
```

**Description**

Provides behavior similar to calling the ArrayBuffer detach operation.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | JavaScript ArrayBuffer to be detached.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not an analyzable ArrayBuffer.|

### OH_JSVM_IsDetachedArraybuffer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsDetachedArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Provides behavior similar to calling the ArrayBuffer IsDetachedBuffer operation.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript ArrayBuffer to be checked.|
| bool* result | Whether the ArrayBuffer is detached. The value true indicates that the ArrayBuffer is detached, and the value false indicates that the ArrayBuffer is not detached.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetPropertyNames()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_Value* result)
```

**Description**

Returns the names of the enumerable properties of an object in the form of a character array. The properties of the object whose key is a symbol are not included.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be searched for.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | An array of JavaScript values, which are the property names of an object. You can use **OH_JSVM_GetArrayLength** and **OH_JSVM_GetElement** to iterate the result.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_GetAllPropertyNames()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetAllPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_KeyCollectionMode keyMode,JSVM_KeyFilter keyFilter,JSVM_KeyConversion keyConversion,JSVM_Value* result)
```

**Description**

Returns an array that contains all available attribute names of an object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object from which the property is retrieved.|
| [JSVM_KeyCollectionMode](capi-jsvm-types-h.md#jsvm_keycollectionmode) keyMode | Whether to retrieve the prototype properties.|
| [JSVM_KeyFilter](capi-jsvm-types-h.md#jsvm_keyfilter) keyFilter | Properties to be retrieved (enumerated/readable/writable).|
| [JSVM_KeyConversion](capi-jsvm-types-h.md#jsvm_keyconversion) keyConversion | Whether to convert a number property key to a string.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | An array of JavaScript values, which are the property names of an object. You can use **OH_JSVM_GetArrayLength** and **OH_JSVM_GetElement** to iterate the result.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to an unknown reason.|

### OH_JSVM_SetProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value value)
```

**Description**

Sets the key attribute for the passed object.

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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to an unknown reason.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_GetProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value* result)
```

**Description**

Obtains the key attribute from the passed object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object from which the property is retrieved.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | Name of the property to be retrieved.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_HasProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_HasProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)
```

**Description**

Checks whether the passed object has an attribute named key.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be queried.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | Name of the property to be checked.|
| bool* result | Whether the attribute exists on the object. The value true indicates that the attribute exists, and the value false indicates that the attribute does not exist.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_DeleteProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)
```

**Description**

Attempts to delete the attribute named key from the object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be queried.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | Name of the property to be deleted.|
| bool* result | Whether the attribute is successfully deleted. The value true indicates that the attribute is successfully deleted, and the value false indicates that the attribute fails to be deleted. **result** can be ignored by passing **NULL** to it.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_HasOwnProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_HasOwnProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)
```

**Description**

Checks whether the input object has an attribute named key. key must be a string or symbol. Otherwise, an error is reported. The JSVM-API does not perform any conversion between data types.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be queried.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | Name of the attribute to be checked.|
| bool* result | Whether the object has the attribute. The value true indicates that the object has the attribute, and the value false indicates that the object does not have the attribute.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): The execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): The execution fails due to unknown reasons.<br>         [JSVM_NAME_EXPECTED](capi-jsvm-types-h.md#jsvm_status): The input name is invalid.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): A JS exception occurs during the execution.|

### OH_JSVM_SetNamedProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value value)
```

**Description**

This method is equivalent to calling OH_JSVM_SetProperty to set the property named `utf8Name`.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be set.|
| const char* utf8name | Name of the property to be set.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_GetNamedProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value* result)
```

**Description**

This method is equivalent to calling OH_JSVM_GetProperty to obtain the property object named `utf8Name`.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object from which the property is retrieved.|
| const char* utf8name | Name of the property to be obtained.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_HasNamedProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_HasNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,bool* result)
```

**Description**

This method is equivalent to the OH_JSVM_HasProperty method called by the object to query whether the object has an attribute named `utf8Name`.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be queried.|
| const char* utf8name | Name of the property to be checked.|
| bool* result | Whether the attribute exists on the object. The value true indicates that the attribute exists, and the value false indicates that the attribute does not exist.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to an unknown reason.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_SetElement()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value value)
```

**Description**

Sets an element on the passed-in object.

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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to an unknown reason.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_GetElement()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value* result)
```

**Description**

Gets the element at the requested index.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be searched for.|
| uint32_t index | Index of the property to be obtained.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Property value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): The execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): The execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): A JS exception occurs during the execution.|

### OH_JSVM_HasElement()

```
JSVM_EXTERN JSVM_Status OH_JSVM_HasElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)
```

**Description**

Checks whether an object has an element at the specified index. If yes, the JSVM-API returns **true**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be queried.|
| uint32_t index | Index where there is an element.|
| bool* result | Whether the attribute exists on the object. The value true indicates that the attribute exists, and the value false indicates that the attribute does not exist.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_DeleteElement()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)
```

**Description**

Deletes the element at the specified index from an object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be queried.|
| uint32_t index | Index of the property to be deleted.|
| bool* result | Whether the element is successfully deleted. The value true indicates that the element is successfully deleted, and the value false indicates that the element is not successfully deleted.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_DefineProperties()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DefineProperties(JSVM_Env env,JSVM_Value object,size_t propertyCount,const JSVM_PropertyDescriptor* properties)
```

**Description**

Defines multiple attributes for a given object efficiently using attribute descriptors. This API sets attributes in the array to the object in sequence using an array of attribute descriptors.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object whose property is to be searched for.|
| size_t propertyCount | Number of elements in the properties array.|
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Array of property descriptors.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): The execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): The input parameter is invalid.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): The execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): A JavaScript exception occurs during the execution.|

### OH_JSVM_ObjectFreeze()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectFreeze(JSVM_Env env,JSVM_Value object)
```

**Description**

Freezes a specified object to prevent new attributes from being added, existing attributes from being deleted, the enumerability, configurability, and writability of existing attributes from being changed, values of existing attributes from being changed, and the object prototype from being changed.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be frozen.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_ObjectSeal()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSeal(JSVM_Env env,JSVM_Value object)
```

**Description**

Encapsulates a specified object to prevent new attributes from being added and marks all existing attributes as unconfigurable.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object to be sealed.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_CallFunction()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CallFunction(JSVM_Env env,JSVM_Value recv,JSVM_Value func,size_t argc,const JSVM_Value* argv,JSVM_Value* result)
```

**Description**

Calls a JavaScript function object from native code. This is the main mechanism for callback from native code to JavaScript.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) recv | Value of **this** passed to the callee.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) func | JavaScript function to be called.|
| size_t argc | Number of elements in the argv array.|
| [const JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | JSVM_values array, representing the JavaScript values to be passed to the function as arguments.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Returned JavaScript object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_CreateFunction()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunction(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback cb,JSVM_Value* result)
```

**Description**

Supports creating function objects in native code, which is the main mechanism for JavaScript to call native code. After this call, the newly created function is no longer automatically visible in the script. Instead, you must explicitly set the attribute on any object visible in JavaScript to access the function from the script.

**Since**: 11


**Parameters**

| Name                                                              | Description|
|-------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                         | Environment for calling the JSVM-API.|
| const char* utf8name                                              | Optional name of the function encoded as UTF8. This name is visible in JavaScript as the name attribute of the new function object.|
| size_t length                                                     | Length of **utf8name** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) cb          | Native function that needs to be called when the function object is called. For details, see [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md).|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JavaScript function object of the new function.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_GetCbInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetCbInfo(JSVM_Env env,JSVM_CallbackInfo cbinfo,size_t* argc,JSVM_Value* argv,JSVM_Value* thisArg,void** data)
```

**Description**

Retrieves details about the call, such as the parameters and this pointer from the given callback information.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_CallbackInfo](capi-jsvm-jsvm-callbackinfo--8h.md) cbinfo | Callback information.|
| size_t* argc | Length of the provided argv array and the actual number of received parameters. You can pass NULL to selectively ignore the length.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | C array of JSVM_Value, which is used to store copied arguments. If the number of parameters exceeds the provided number, only the requested number of parameters is copied. If the provided parameters are fewer than the declared ones, the remaining part of argv is filled with JSVM_Value values representing undefined. **argv** can be ignored by passing **NULL** to it.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* thisArg | JavaScript **this** argument. **thisArg** can be ignored by passing **NULL** to it.|
| void** data | Pointer to the callback data. **data** can be ignored by passing **NULL** to it.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetNewTarget()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetNewTarget(JSVM_Env env,JSVM_CallbackInfo cbinfo,JSVM_Value* result)
```

**Description**

Gets the new target called by the constructor. If the current callback is not a constructor call, the result is **NULL**.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_CallbackInfo](capi-jsvm-jsvm-callbackinfo--8h.md) cbinfo | Callback information.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | New target called by the constructor.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_NewInstance()

```
JSVM_EXTERN JSVM_Status OH_JSVM_NewInstance(JSVM_Env env,JSVM_Value constructor,size_t argc,const JSVM_Value* argv,JSVM_Value* result)
```

**Description**

Instantiates a new JavaScript value by using the constructor represented by the given JSVM_Value.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) constructor | JavaScript function that will be called as a constructor.|
| size_t argc | Number of elements in the argv array.|
| [const JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | JavaScript value array. **JSVM_Value** indicates the parameter of the constructor. If **argc** is 0, **argc** can be ignored by passing **NULL** to it.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Indicates the returned JavaScript object, which is the constructed object in this example.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_DefineClass()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClass(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value* result)
```

**Description**

Defines a JavaScript class.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* utf8name | Name of the JavaScript constructor. You are advised to use the C++ class name when wrapping a C++ class.|
| size_t length | Length of **utf8name** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) constructor | Callback used to create the constructor of a class. When a C++ class is wrapped, this method must comply with **JSVM_Callback**. It is a static member of the callback signature. C++ class constructors cannot be used. For details, see [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md).|
| size_t propertyCount | Number of items in the properties array.|
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Attribute descriptor of a class, which is used to define the properties and methods of the class.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the constructor of a class.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during the execution.|

### OH_JSVM_Wrap()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Wrap(JSVM_Env env,JSVM_Value jsObject,void* nativeObject,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)
```

**Description**

Encapsulates a native instance in a JavaScript object. The native instance can be retrieved using OH_JSVM_Unwrap().

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | JavaScript object that will wrap a native object.|
| void* nativeObject | Native instance wrapped in a JavaScript object.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | Optional native callback, which can be used to release the native instance when the JavaScript object is garbage collected.|
| void* finalizeHint | Optional context hint passed to the **finalize** callback.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | Optional reference to the wrap object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during execution.|

### OH_JSVM_Unwrap()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Unwrap(JSVM_Env env,JSVM_Value jsObject,void** result)
```

**Description**

When the JavaScript code calls a method of a class or property accessor, the corresponding JSVM_Callback is called. If the callback is for an instance method or accessor, the this parameter of the callback is the wrapper object. You can call OH_JSVM_Unwrap() of the wrapper object to obtain the C++ instance as the call target.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | Object associated with the native instance.|
| void** result | Pointer to the wrapped native instance.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_RemoveWrap()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RemoveWrap(JSVM_Env env,JSVM_Value jsObject,void** result)
```

**Description**

This function is used to retrieve the native instance previously wrapped in the JavaScript object js_object and remove the wrapping. If the **finalize** callback is associated with wrap, it will not be called when the JavaScript object is garbage collected.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | Object associated with the native instance.|
| void** result | Pointer to the wrapped native instance.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_TypeTagObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_TypeTagObject(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag)
```

**Description**

Associates the value of the typeTag pointer with a JavaScript object or an external value. You can call OH_JSVM_CheckObjectTypeTag() to determine the tag type attached to an object to ensure that the object type is correct. If the object already has an associated type tag, **JSVM_INVALID_ARG** is returned.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript object or external value to be tagged.|
| [const JSVM_TypeTag](capi-jsvm-jsvm-typetag.md)* typeTag | Tag object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_CheckObjectTypeTag()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CheckObjectTypeTag(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag,bool* result)
```

**Description**

Compares the typeTag with the tag on a JavaScript object or external value. If the same tag is found, result is set to true. Otherwise, result is set to false.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript object or external value of the type tag to be checked.|
| [const JSVM_TypeTag](capi-jsvm-jsvm-typetag.md)* typeTag | Tag used to compare any tags found on an object.|
| bool* result | Indicating whether the specified type tag matches the type tag on the object. If the same label is found, set result to true. Otherwise, set result to false.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_AddFinalizer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_AddFinalizer(JSVM_Env env,JSVM_Value jsObject,void* finalizeData,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)
```

**Description**

Adds the **JSVM_Finalize** callback to a JavaScript object. This callback is called when the JavaScript object is garbage collected. **OH_JSVM_AddFinalizer** can be called multiple times on a single JavaScript object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | JavaScript object associated with native data.|
| void* finalizeData | Optional data to be passed to **finalizeCb**.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | Native callback used to release native data when the JavaScript object is garbage collected. **JSVM_Finalize** provides more details.|
| void* finalizeHint | Optional context hint passed to the **finalize** callback.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | Optional reference to a JavaScript object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_GetVersion()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetVersion(JSVM_Env env,uint32_t* result)
```

**Description**

Gets the latest JSVM-API version supported by the JSVM runtime. New JSVM-API APIs will be added to support more functions. This API is introduced to allow the use of new functions in JSVM versions that support them, and to provide callback behavior in JSVM versions that do not support them.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| uint32_t* result | JSVM-API of the latest version.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetVMInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetVMInfo(JSVM_VMInfo* result)
```

**Description**

Gets the VM information.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VMInfo](capi-jsvm-jsvm-vminfo.md)* result | VM information.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_AdjustExternalMemory()

```
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
| int64_t* result | Adjustment value.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_MemoryPressureNotification()

```
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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreatePromise()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreatePromise(JSVM_Env env,JSVM_Deferred* deferred,JSVM_Value* promise)
```

**Description**

Creates a deferred object and a JavaScript promise.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Deferred](capi-jsvm-jsvm-deferred--8h.md)* deferred | A newly created deferred object, which can be passed to OH_JSVM_ResolveDeferred() or OH_JSVM_RejectDeferred() to resolve resp. or reject the promise.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* promise | JavaScript promise associated with the deferred object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_ResolveDeferred()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ResolveDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value resolution)
```

**Description**

Resolves a JavaScript promise by using the associated deferred object. It can only be used to resolve the JavaScript promise of the corresponding available deferred object. This means that the promise must be created using OH_JSVM_CreatePromise() and the object returned from the call must be retained before being passed to this API.

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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_RejectDeferred()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RejectDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value rejection)
```

**Description**

Rejects a JavaScript promise by using the associated deferred object. It can only be used to reject the JavaScript promise of the corresponding available deferred object. This means that the promise must be created using OH_JSVM_CreatePromise(), and the object returned from the call must be retained before being passed to this API.

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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_IsPromise()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsPromise(JSVM_Env env,JSVM_Value value,bool* isPromise)
```

**Description**

Checks whether a promise object is a native promise object.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Value to be checked.|
| bool* isPromise | Whether the object is a native promise object (promise object created by the underlying engine). The value true indicates that the object is a native promise object, and the value false indicates that the object is not a native promise.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_PromiseRegisterHandler()

```
JSVM_EXTERN JSVM_Status OH_JSVM_PromiseRegisterHandler(JSVM_Env env,JSVM_Value promise,JSVM_Value onFulfilled,JSVM_Value onRejected,JSVM_Value* result)
```

**Description**

Registers the callback function for processing promise fulfillment or rejection.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) promise | Promise for which a callback needs to be registered.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) onFulfilled | This function is called after the promise is fulfilled.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) onRejected | This function is called after the promise is rejected.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter. A new promise generated after the promise invokes the then or catch API.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Execution status code.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) The env or promise parameter is empty, or both the onFulfilled and onRejected parameters are empty.<br>         [JSVM_INVALID_TYPE](capi-jsvm-types-h.md#jsvm_status) The promise parameter is not of the JS Promise type, or the onFulfilled or onRejected parameter is not of the JS Function type.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) A JS exception exists.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) The API execution is incorrect.|

### OH_JSVM_JsonParse()

```
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
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Value obtained by parsing.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is not of the string type.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_JsonStringify()

```
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
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | String returned after successful conversion.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.|

### OH_JSVM_CreateSnapshot()

```
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
| [const JSVM_Env](capi-jsvm-jsvm-env--8h.md)* contexts | Array of contexts to be added to the snapshot.|
| const char** blobData | Snapshot data.|
| size_t* blobSize | Size of snapshot data.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_GetHeapStatistics()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetHeapStatistics(JSVM_VM vm,JSVM_HeapStatistics* result)
```

**Description**

Obtains heap statistics of a VM.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM that returns heap statistics.|
| [JSVM_HeapStatistics](capi-jsvm-jsvm-heapstatistics.md)* result | Heap statistics.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_StartCpuProfiler()

```
JSVM_EXTERN JSVM_Status OH_JSVM_StartCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler* result)
```

**Description**

Use **OH_JSVM_StartCpuProfiler** to create and start a CPU profiler instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM for starting the CPU profiler.|
| [JSVM_CpuProfiler](capi-jsvm-jsvm-cpuprofiler--8h.md)* result | Pointer to the CPU profiler.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_StopCpuProfiler()

```
JSVM_EXTERN JSVM_Status OH_JSVM_StopCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler profiler,JSVM_OutputStream stream,void* streamData)
```

**Description**

Use **OH_JSVM_StopCpuProfiler** to stop the CPU profiler and output the result to a stream.

**Since**: 12


**Parameters**

| Name                                                               | Description|
|--------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                             | VM for starting the CPU profiler.|
| [JSVM_CpuProfiler](capi-jsvm-jsvm-cpuprofiler--8h.md) profiler     | CPU profiler to be stopped.|
| [JSVM_OutputStream](capi-jsvm-types-h.md#jsvm_outputstream) stream | Output stream callback.|
| void* streamData                                                   | Optional data passed to the output stream callback. For example, it can be a file stream, which is used to write the sampled data passed in the output stream callback to a file.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_TakeHeapSnapshot()

```
JSVM_EXTERN JSVM_Status OH_JSVM_TakeHeapSnapshot(JSVM_VM vm,JSVM_OutputStream stream,void* streamData)
```

**Description**

Use **OH_JSVM_TakeHeapSnapshot** to obtain a snapshot of the current heap and output it to a stream.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM whose heap snapshot is to be obtained.|
| [JSVM_OutputStream](capi-jsvm-types-h.md#jsvm_outputstream) stream | Output stream callback.|
| void* streamData | Optional data passed to the output stream callback. For example, it can be a file stream, which is used to write the sampled data passed in the output stream callback to a file.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_OpenInspector()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspector(JSVM_Env env,const char* host,uint16_t port)
```

**Description**

Use **OH_JSVM_OpenInspector** to open an inspector instance on the specified host and port for debugging JS code.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* host | IP address of the host for listening on the inspector connection.|
| uint16_t port | Port for listening on the inspector connection.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during execution.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_CloseInspector()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseInspector(JSVM_Env env)
```

**Description**

Use **OH_JSVM_CloseInspector** to close all remaining inspector connections.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JS exception occurs during execution.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_WaitForDebugger()

```
JSVM_EXTERN JSVM_Status OH_JSVM_WaitForDebugger(JSVM_Env env,bool breakNextLine)
```

**Description**

Waits for the host to set up a socket connection with an inspector. After the connection is set up, the application continues to run. **Runtime.runIfWaitingForDebugger** is sent.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| bool breakNextLine | Whether to interrupt the next line of JavaScript code. If breakNextLine is set to true, the execution of the next line of JavaScript code is paused. Developers need to use the debugging button of the debugger to control the execution of JavaScript. If breakNextLine is set to false, the execution is not interrupted.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during the execution.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_DefineClassWithPropertyHandler()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithPropertyHandler(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_PropertyHandlerCfg propertyHandlerCfg,JSVM_Callback callAsFunctionCallback,JSVM_Value* result)
```

**Description**

Defines a JavaScript class with a given class name, constructor, properties, and callback handler. Property operations include getter, setter, deleter, and enumerator, and are called as function callbacks.

**Since**: 12


**Parameters**

| Name                                                                              | Description|
|-----------------------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                                         | Environment for calling the JSVM-API.|
| const char* utf8name                                                              | Name of the JavaScript class constructor.|
| size_t length                                                                     | Length of **utf8name** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) constructor                     | Callback used to create the constructor of a class. This method must be of the **JSVM_Callback** type. The callback in the constructor must be a static member. C++ class constructors cannot be used. For details, see [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md).|
| size_t propertyCount                                                              | Number of items in the properties array.|
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Properties, accessors, and methods of the property descriptor array class of static data and instance data. For details, see **JSVM_PropertyDescriptor**.|
| [JSVM_PropertyHandlerCfg](capi-jsvm-jsvm-propertyhandlerconfigurationstruct.md) propertyHandlerCfg                                    | Callback triggered when an instance object property is accessed.|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) callAsFunctionCallback          | Callback triggered when an instance object is called as a function.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result                 | JSVM_Value of the constructor of a JavaScript class.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that a JavaScript exception occurs during execution.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the execution fails due to unknown reasons.|

### OH_JSVM_IsUndefined()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsUndefined(JSVM_Env env,JSVM_Value value,bool* isUndefined)
```

**Description**

Checks whether the value passed in is **Undefined**. This is equivalent to `value === undefined` in JavaScript.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isUndefined | Whether the given JSVM_Value is undefined. The value true indicates that the given JSVM_Value is undefined, and the value false indicates that the given JSVM_Value is not undefined.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful. This API does not trigger any exception.|

### OH_JSVM_IsNull()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsNull(JSVM_Env env,JSVM_Value value,bool* isNull)
```

**Description**

Checks whether the value passed in is a **Null** object. This is equivalent to `value === null` in JavaScript.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isNull | Indicates whether the given JSVM_Value is null. The value true indicates yes, and the value false indicates no.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful. This API does not trigger any exceptions.|

### OH_JSVM_IsNullOrUndefined()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsNullOrUndefined(JSVM_Env env,JSVM_Value value,bool* isNullOrUndefined)
```

**Description**

Checks whether the value passed in is **Null** or **Undefined**. This is equivalent to `value == null` in JavaScript.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isNullOrUndefined | Indicates whether the given JSVM_Value is null or undefined. The value true indicates yes, and the value false indicates no.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful. This API does not trigger any exceptions.|

### OH_JSVM_IsBoolean()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsBoolean(JSVM_Env env,JSVM_Value value,bool* isBoolean)
```

**Description**

Checks whether the value passed in is a Boolean value. It is equivalent to `typeof value === 'boolean'` in JavaScript.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isBoolean | Indicates whether the given JSVM_Value is a Boolean. The value true indicates that it is a Boolean, and the value false indicates that it is not a Boolean.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful. This API does not trigger any exceptions.|

### OH_JSVM_IsNumber()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsNumber(JSVM_Env env,JSVM_Value value,bool* isNumber)
```

**Description**

Checks whether the value passed in is a number. It is equivalent to `typeof value === 'number'` in JavaScript.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isNumber | Indicates whether the given JSVM_Value is a number. The value true indicates that it is a number, and the value false indicates that it is not a number.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful and this API does not trigger any exception.|

### OH_JSVM_IsString()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsString(JSVM_Env env,JSVM_Value value,bool* isString)
```

**Description**

Checks whether the value passed in is a string. This is equivalent to `typeof value === 'tring'` in JavaScript.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isString | Whether the given JSVM_Value is a string. The value true indicates that the given JSVM_Value is a string, and the value false indicates that the given JSVM_Value is not a string.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful and this API does not trigger any exception.|

### OH_JSVM_IsSymbol()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbol(JSVM_Env env,JSVM_Value value,bool* isSymbol)
```

**Description**

Checks whether the value passed in is a symbol. This is equivalent to `typeof value === 'ymbol'` in JavaScript.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isSymbol | Checks whether the given JSVM_Value is a symbol. The value true indicates that the JSVM_Value is a symbol, and the value false indicates that the JSVM_Value is not a symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful. This API does not trigger any exceptions.|

### OH_JSVM_IsFunction()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsFunction(JSVM_Env env,JSVM_Value value,bool* isFunction)
```

**Description**

Checks whether the value passed in is a function. This is equivalent to `typeof value === 'function'` in JavaScript.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isFunction | Checks whether the given JSVM_Value is a function. The value true indicates that the JSVM_Value is a function, and the value false indicates that the JSVM_Value is not a function.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful. This API does not trigger any exceptions.|

### OH_JSVM_IsObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsObject(JSVM_Env env,JSVM_Value value,bool* isObject)
```

**Description**

Checks whether the value passed in is an object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isObject | Indicates whether the given JSVM_Value is an object. The value true indicates that the JSVM_Value is an object, and the value false indicates that the JSVM_Value is not an object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful. This API does not trigger any exceptions.|

### OH_JSVM_IsBigInt()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsBigInt(JSVM_Env env,JSVM_Value value,bool* isBigInt)
```

**Description**

Checks whether the value passed in is a BigInt. This is equivalent to `typeof value === 'bigint'` in JavaScript.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isBigInt | Indicates whether the given JSVM_Value is a BigInt. The value true indicates that the JSVM_Value is a BigInt, and the value false indicates that the JSVM_Value is not a BigInt.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful. This API does not trigger any exceptions.|

### OH_JSVM_CreateMap()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateMap(JSVM_Env env, JSVM_Value* result)
```

**Description**

Returns the JavaScript value corresponding to the JavaScript Map type.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript map.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_IsMap()

```
JSVM_Status JSVM_CDECL OH_JSVM_IsMap(JSVM_Env env,JSVM_Value value,bool* isMap)
```

**Description**

Checks whether the value passed in is a map.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isMap | Whether the given value is a map. The value true indicates that the given value is a map, and the value false indicates that the given value is not a map.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_IsConstructor()

```
JSVM_Status JSVM_CDECL OH_JSVM_IsConstructor(JSVM_Env env,JSVM_Value value,bool* isConstructor)
```

**Description**

Checks whether the value passed in is a constructor.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* isConstructor | Whether the given value is a constructor. The value true indicates that the given value is a constructor, and the value false indicates that the given value is not a constructor.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_CreateRegExp()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateRegExp(JSVM_Env env,JSVM_Value value,JSVM_RegExpFlags flags,JSVM_Value* result)
```

**Description**

Returns the regular expression object corresponding to the input JavaScript string. An exception may be thrown.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript string to be converted to a regular expression.|
| [JSVM_RegExpFlags](capi-jsvm-types-h.md#jsvm_regexpflags) flags | Regular expression flags.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of JavaScript RegExp.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that an exception is thrown when the API is running.|

### OH_JSVM_ObjectGetPrototypeOf()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectGetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value* result)
```

**Description**

Gets the prototype of a JavaScript object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object |  JavaScript object whose prototype is to be returned.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Prototype of a given object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that an exception is thrown during API running.|

### OH_JSVM_ObjectSetPrototypeOf()

```
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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the prototype fails to be set. This failure is triggered when the prototype is set cyclically.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that an exception is thrown during API running.|

### OH_JSVM_CreateSet()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSet(JSVM_Env env,JSVM_Value* result)
```

**Description**

Creates a JavaScript Set object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Created JavaScript Set object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_IsSet()

```
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
| bool* isSet | Whether the given object is of the Set type. The value true indicates that the object is of the Set type, and the value false indicates that the object is not of the Set type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input parameter is invalid.|

### OH_JSVM_CoerceToBigInt()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBigInt(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**Description**

Implements the abstract operation `ToBigInt()`.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be forcibly converted.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JavaScript value that is successfully converted to a BigInt type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input JavaScript value cannot be converted to BitInt.|

### OH_JSVM_IsRegExp()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsRegExp(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the value passed in is a JavaScript RegExp object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JSVM_Value to be checked.|
| bool* result | Whether the given JSVM_Value is a JavaScript RegExp object. The value true indicates that it is, and the value false indicates that it is not.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_CreateFunctionWithScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunctionWithScript(JSVM_Env env,const char* funcName,size_t length,size_t argc,const JSVM_Value* argv,JSVM_Value script,JSVM_Value* result)
```

**Description**

Creates a function with the given JavaScript as the function body.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const char* funcName | A string containing the function name. If **NULL** is passed to it, an anonymous function is created.|
| size_t length | Length of **funcName** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| size_t argc | Number of elements in the argv array.|
| [const JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | JSVM_values array, representing the JavaScript values to be passed to the function as arguments.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | JavaScript string that is used as the function body.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Value of the JavaScript function object of the newly created function.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the input JavaScript cannot be compiled.|

### OH_JSVM_PumpMessageLoop()

```
JSVM_EXTERN JSVM_Status OH_JSVM_PumpMessageLoop(JSVM_VM vm,bool* result)
```

**Description**

Starts the task queue in a VM. The task queue can be executed through the external event loop.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM instance for starting a task queue.|
| bool* result | Whether the task queue is successfully started. The value true indicates that the task queue is successfully started, and the value false indicates that the task queue fails to be started.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Result code of the JSVM function.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_PerformMicrotaskCheckpoint()

```
JSVM_EXTERN JSVM_Status OH_JSVM_PerformMicrotaskCheckpoint(JSVM_VM vm)
```

**Description**

Checks whether there are micro tasks waiting in the queue. If yes, execute them.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | VM instance for which micro tasks are to be checked.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Result code of the JSVM function.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_RetainScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RetainScript(JSVM_Env env, JSVM_Script script)
```

**Description**

Permanently saves a JSVM_Script and extends its lifecycle beyond the current scope.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment where this API is called.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | JavaScript string that contains the script to be saved permanently.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the script is empty or has been saved.|

### OH_JSVM_ReleaseScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseScript(JSVM_Env env, JSVM_Script script)
```

**Description**

Releases the script reserved by OH_JSVM_RetainScript. After the script is released, do not use the input script again.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment where this API is called.|
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | JavaScript string that contains the script to be released.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the script is empty or has not been saved.|

### OH_JSVM_OpenInspectorWithName()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspectorWithName(JSVM_Env env,int pid,const char* name)
```

**Description**

Opens an inspector named name and opens the Unix domain port of the corresponding PID.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment where the API is called.|
| int pid | Process ID of the inspector connection.|
| const char* name | Inspector name. If nullptr is passed, the default name is jsvm.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that an exception occurs.|

### OH_JSVM_CompileWasmModule()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmModule(JSVM_Env env,const uint8_t *wasmBytecode,size_t wasmBytecodeLength,const uint8_t *cacheData,size_t cacheDataLength,bool *cacheRejected,JSVM_Value *wasmModule)
```

**Description**

Compiles WebAssembly bytecode to obtain a WebAssembly module. If the WebAssembly cache is provided, it will be deserialized first. If the JIT permission is not supported, a log is printed to notify the developer.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const uint8_t *wasmBytecode | WebAssembly bytecode.|
| size_t wasmBytecodeLength | Length of the WebAssembly bytecode, in bytes.|
| const uint8_t *cacheData | Optional WebAssembly cache.|
| size_t cacheDataLength | Optional WebAssembly cache length, in bytes.|
| bool *cacheRejected | Output parameter, indicating whether the provided WebAssembly cache is rejected by the engine. The value true indicates that the provided WebAssembly cache is rejected by the engine, and the value false indicates that the provided WebAssembly cache is not rejected by the engine.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) *wasmModule | Output parameter, which indicates the generated WebAssembly module.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the env or wasmBytecode parameter is empty, or the length of the input data is invalid.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the compilation fails.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that an exception occurs.<br>         [JSVM_JIT_MODE_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the current environment does not support the JIT permission.|

### OH_JSVM_CompileWasmFunction()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmFunction(JSVM_Env env,JSVM_Value wasmModule,uint32_t functionIndex,JSVM_WasmOptLevel optLevel)
```

**Description**

Compiles the function with the specified index in the WebAssembly module at a specified optimization level. If the JIT permission is not supported, a log is printed to notify the developer.

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
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): The execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): The env or wasmModule parameter is empty, or wasmModule is not a real WebAssembly module.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status): The function index is out of range or the compilation fails.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status): An exception occurs.<br>         [JSVM_JIT_MODE_EXPECTED](capi-jsvm-types-h.md#jsvm_status): The current environment does not support the JIT permission.|

### OH_JSVM_IsWasmModuleObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsWasmModuleObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given JSVM_Value is a WebAssembly module.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Output parameter, indicating whether the given value is a WebAssembly module. The value true indicates yes, and false indicates no.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_CreateWasmCache()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateWasmCache(JSVM_Env env,JSVM_Value wasmModule,const uint8_t** data,size_t* length)
```

**Description**

Creates a WebAssembly cache. If the JIT permission is not supported, a log line is printed to prompt the developer.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) wasmModule | Compiled WebAssembly module.|
| const uint8_t** data | Output parameter, indicating the generated WebAssembly cache.|
| size_t* length | Output parameter, indicating the length of the generated WebAssembly cache, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer parameter is passed.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the cache fails to be generated.<br>         [JSVM_JIT_MODE_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the current environment does not have the JIT permission.|

### OH_JSVM_ReleaseCache()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseCache(JSVM_Env env,const uint8_t* cacheData,JSVM_CacheType cacheType)
```

**Description**

Releases the cache of a specified type.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| const uint8_t* cacheData | Cache data to be released. Repeated release is an undefined behavior.|
| [JSVM_CacheType](capi-jsvm-types-h.md#jsvm_cachetype) cacheType | Cache type. A generated cache can be released accordingly.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer parameter is passed or the value of cacheType is invalid.|

### OH_JSVM_IsBigIntObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsBigIntObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether a given JSVM_Value is a BigInt object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Output parameter, which indicates whether the given value is a BigInt object. The value true indicates that the given value is a BigInt object, and the value false indicates that the given value is not a BigInt object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_IsBooleanObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsBooleanObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether a given JSVM_Value is a Boolean object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Output parameter, which indicates whether the given value is a Boolean object. The value true indicates that the given value is a Boolean object, and the value false indicates that the given value is not a Boolean object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_IsStringObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsStringObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given JSVM_Value is a string object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Output parameter, indicating whether the given value is a string object. The value true indicates that the given value is a string object, and the value false indicates that the given value is not a string object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_IsNumberObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsNumberObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given JSVM_Value is a number object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Output parameter, which indicates whether the given value is a Number object. The value true indicates that the given value is a Number object, and the value false indicates that the given value is not a Number object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_IsSymbolObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbolObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**Description**

Checks whether the given JSVM_Value is a Symbol object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | JavaScript value to be checked.|
| bool* result | Output parameter, which indicates whether the given value is a Symbol object. The value true indicates that the given value is a Symbol object, and the value false indicates that the given value is not a Symbol object.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_GetSymbolAsyncIterator()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolAsyncIterator(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.AsyncIterator capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter, which is the Symbol.AsyncIterator in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_GetSymbolHasInstance()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolHasInstance(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.HasInstance capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter, which is the Symbol.HasInstance in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer parameter is passed.|

### OH_JSVM_GetSymbolIsConcatSpreadable()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIsConcatSpreadable(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.IsConcatSpreadable capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter, which is the Symbol.IsConcatSpreadable in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer parameter is passed.|

### OH_JSVM_GetSymbolMatch()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolMatch(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.Match capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter, which is the Symbol.Match in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_GetSymbolReplace()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolReplace(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.Replace capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter, which is the Symbol.Replace in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_GetSymbolSearch()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSearch(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.Search capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter. Symbol.Search in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_GetSymbolSplit()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSplit(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.Split capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter. Symbol.Split in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_GetSymbolToPrimitive()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToPrimitive(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.ToPrimitive capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter, which is the Symbol.ToPrimitive in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_GetSymbolUnscopables()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolUnscopables(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.Unscopables capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter, which is the Symbol.Unscopables in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_GetSymbolToStringTag()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToStringTag(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.ToStringTag capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter. Symbol.ToStringTag in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer is passed.|

### OH_JSVM_GetSymbolIterator()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIterator(JSVM_Env env, JSVM_Value* result)
```

**Description**

Obtains the Symbol.Iterator capability in the well-known symbol.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Output parameter, which is the Symbol.Iterator in the well-known symbol.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that a null pointer parameter is passed.|

### OH_JSVM_TraceStart()

```
JSVM_EXTERN JSVM_Status OH_JSVM_TraceStart(size_t count,const JSVM_TraceCategory* categories,const char* tag,size_t eventsCount)
```

**Description**

Starts to collect information of a specified trace type for all JSVM runtime instances (thread-unsafe).

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| size_t count | Number of trace collection categories.|
| [const JSVM_TraceCategory](capi-jsvm-types-h.md#jsvm_tracecategory)* categories | Array of specific trace collection categories.|
| const char* tag | Label defined by the user and assigned to trace data.|
| size_t eventsCount | Maximum number of stored trace events.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status. .<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) categories or count is invalid.|

### OH_JSVM_TraceStop()

```
JSVM_EXTERN JSVM_Status OH_JSVM_TraceStop(JSVM_OutputStream stream, void* streamData)
```

**Description**

Stops collecting information of a specified trace type (thread-unsafe) for all JSVM running times.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_OutputStream](capi-jsvm-types-h.md#jsvm_outputstream) stream | Output stream callback function, which is used to receive trace data.|
| void* streamData | Output stream pointer of, which is used to assist the output stream callback function in data output.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status. .<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) stream or streamData is empty.|

### OH_JSVM_AddHandlerForGC()

```
JSVM_EXTERN JSVM_Status OH_JSVM_AddHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,JSVM_GCType gcType,void* userData)
```

**Description**

Adds a GC callback function to the VM.

**Since**: 18


**Parameters**

| Name                                                                                | Description|
|-------------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                              | Environment for calling the JSVM-API.|
| [JSVM_CBTriggerTimeForGC](capi-jsvm-types-h.md#jsvm_cbtriggertimeforgc) triggerTime | Time when the GC callback function is triggered.|
| [JSVM_HandlerForGC](capi-jsvm-types-h.md#jsvm_handlerforgc) handler                 | When GC is triggered, the passed callback function is called.|
| [JSVM_GCType](capi-jsvm-types-h.md#jsvm_gctype) gcType                              | GC type.|
| void* userData                                                                      | Native pointer data.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the function is executed successfully.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input vm or handler is empty or the handler has been added.|

### OH_JSVM_RemoveHandlerForGC()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RemoveHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,void* userData)
```

**Description**

Removes the GC callback function from the VM.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | Environment for calling the JSVM-API.|
| [JSVM_CBTriggerTimeForGC](capi-jsvm-types-h.md#jsvm_cbtriggertimeforgc) triggerTime | Time when the GC callback function is triggered.|
| [JSVM_HandlerForGC](capi-jsvm-types-h.md#jsvm_handlerforgc) handler | When GC is triggered, the input callback function is called.|
| void* userData | Native pointer data.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the function is executed successfully.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input vm or handler is empty, the handler has been deleted, or<br> the handler has never been added.|

### OH_JSVM_SetHandlerForOOMError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForOOMError(JSVM_VM vm,JSVM_HandlerForOOMError handler)
```

**Description**

Sets a callback for handling OOM errors. If the API is called repeatedly, only the last call takes effect. If the input handler is null, the previous setting is canceled.

**Since**: 18


**Parameters**

| Name                                                                            | Description|
|---------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                          | Environment for calling the JSVM-API.|
| [JSVM_HandlerForOOMError](capi-jsvm-types-h.md#jsvm_handlerforoomerror) handler | OOM error handler.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the function is executed successfully.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the vm is empty.|

### OH_JSVM_SetDebugOption()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetDebugOption(JSVM_Env env, JSVM_DebugOption debugOption, bool isEnabled)
```

**Description**

Enables or disables a specified debugging option of a specific JSVM_Env.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_DebugOption](capi-jsvm-types-h.md#jsvm_debugoption) debugOption | Debugging option to be modified.|
| bool isEnabled | Whether to enable or disable the debugging option. true indicates that the debugging option is enabled, and false indicates that the debugging option is disabled.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the function is successfully executed.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) If the input env is a null pointer, this error code is returned.|

### OH_JSVM_SetHandlerForFatalError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForFatalError(JSVM_VM vm,JSVM_HandlerForFatalError handler)
```

**Description**

Sets a callback for fatal errors. If an API is called repeatedly, only the last call takes effect. If the input handler is null, the previous setting is canceled.

**Since**: 18


**Parameters**

| Name                                                                                | Description|
|-------------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                              | Environment for calling the JSVM-API.|
| [JSVM_HandlerForFatalError](capi-jsvm-types-h.md#jsvm_handlerforfatalerror) handler | Handler of fatal errors.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the function is successfully executed.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the VM is empty.|

### OH_JSVM_SetHandlerForPromiseReject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForPromiseReject(JSVM_VM vm,JSVM_HandlerForPromiseReject handler)
```

**Description**

Sets a callback for PromiseReject errors. If an API is called repeatedly, only the last call takes effect. If the input handler is null, the previous setting is canceled.

**Since**: 18


**Parameters**

| Name                                                                                      | Description|
|-------------------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                                    | Environment for calling the JSVM-API.|
| [JSVM_HandlerForPromiseReject](capi-jsvm-types-h.md#jsvm_handlerforpromisereject) handler | PromiseReject error handler.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status): The function is executed successfully.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status): The VM is empty.|

### OH_JSVM_DefineClassWithOptions()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithOptions(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value parentClass,size_t optionCount,JSVM_DefineClassOptions options[],JSVM_Value* result)
```

**Description**

When encapsulating a C++ class, the C++ constructor callback passed through the constructor must be a static method in the class. This method calls the actual class constructor, encapsulates the new C++ instance in a JavaScript object based on the input options, and returns the encapsulated object.

**Since**: 18


**Parameters**

| Name                                                                              | Description|
|-----------------------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                                         | Environment for calling the JSVM-API.|
| const char* utf8name                                                              | Name of the JavaScript constructor. You are advised to use the C++ class name when wrapping a C++ class.|
| size_t length                                                                     | Length of **utf8name** (in bytes) or **JSVM_AUTO_LENGTH** (if null-terminated).|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) constructor                     | Callback used to create the constructor of a class. When a C++ class is wrapped, this method must comply with **JSVM_Callback**. It is a static member of the callback signature. C++ class constructors cannot be used. For details, see [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md).|
| size_t propertyCount                                                              | Number of items in the properties array.|
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | Attribute descriptor of a class, which is used to define the properties and methods of the class.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) parentClass             | Parent class of the defined class.|
| size_t optionCount                                                                | Number of items in the options array.|
| [JSVM_DefineClassOptions](capi-jsvm-jsvm-defineclassoptions.md) options[]                                             | Array of options passed for defining the class.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result                 | JSVM_Value of the constructor of a class.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that the input pointer parameter contains a null pointer.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the input utf8name| constructor | properties is invalid. As a result, the execution fails.|

### OH_JSVM_CreateExternalStringLatin1()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringLatin1(JSVM_Env env,char* str,size_t length,JSVM_Finalize finalizeCallback,void* finalizeHint,JSVM_Value* result,bool* copied)
```

**Description**

Creates an external JavaScript string using the C string encoded in ISO-8859-1. If the external string fails to be created, the native string is copied.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| char* str | Pointer to the string encoded in ISO-8859-1.|
| size_t length | Byte length of the string. If the string is null-terminated, you can directly pass JSVM_AUTO_LENGTH.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCallback | (Optional) Callback function triggered when the created string is reclaimed by the GC. For details, see the JSVM_Finalize type description.|
| void* finalizeHint | (Optional) Finalize callback passed when the string is reclaimed.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | Receives the created external JavaScript string, which is of the JSVM_Value type.|
| bool* copied | Indicates whether the external string is successfully created. The value true indicates that the external string fails to be created and a native JavaScript string is returned. The value false indicates that the external string is successfully created.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that any of env, str, and copied in the input parameters is empty.|

### OH_JSVM_CreateExternalStringUtf16()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringUtf16(JSVM_Env env,char16_t* str,size_t length,JSVM_Finalize finalizecallback,void* finalizeHint,JSVM_Value* result,bool* copied)
```

**Description**

This API uses a C string encoded in UTF16-LE to create an external JavaScript string. If the external string fails to be created, the native string is copied.

**Since**: 18


**Parameters**

| Name                                                                 | Description|
|----------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                            | Environment for calling the JSVM-API.|
| char16_t* str                                                        | Pointer to the UTF16-LE encoded string.|
| size_t length                                                        | Byte length of the string. If the string is a null-terminated string, JSVM_AUTO_LENGTH can be directly passed.|
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCallback | (Optional) Callback function triggered when the created string is reclaimed by GC. For more details, see JSVM_Finalize type description.|
| void* finalizeHint                                                   | (Optional) Finalize callback passed when the string is reclaimed.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result    | JavaScript external string that is created. The value is of the JSVM_Value type.|
| bool* copied                                                         | Flag indicating whether the external string is successfully created. true indicates that the external string fails to be created and a native JS string is returned. false indicates that the external string is successfully created.|

**Returns**

| Type| Description|
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that any of env, str, and copied in the input parameters is empty.|

### OH_JSVM_CreatePrivate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreatePrivate(JSVM_Env env,JSVM_Value description,JSVM_Data* result)
```

**Description**

Creates a JavaScript private key object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) description | (Optional) JavaScript string to be described as a private key.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md)* result | Pointer to the JavaScript private key object that is successfully created.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that either env or result in the input parameters is empty.<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input description is not a character string.|

### OH_JSVM_SetPrivate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value value)
```

**Description**

Sets a private attribute for the input object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object for which the private attribute is to be set.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) key | Private key object of the private attribute.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Value of the private attribute.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that any input parameter is empty or key is not a private key object.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input object is not a real JavaScript object.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the private attribute fails to be set and no exception occurs.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that an exception occurs.|

### OH_JSVM_GetPrivate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value *result)
```

**Description**

Obtains the private attribute corresponding to the private key from the input object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object from which the private attribute is obtained.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) key | Private key object of the private attribute.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) *result | Value of the private attribute.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that any input parameter is empty or the key is not a private key object.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input object is not a real JavaScript object.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the private attribute fails to be obtained and no exception occurs.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that an exception occurs.|

### OH_JSVM_DeletePrivate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DeletePrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key)
```

**Description**

Deletes the private attribute corresponding to the private key from the input object.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | Object from which the private attribute is deleted.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) key | Private key object of the private attribute.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) indicates that any input parameter is empty or the key is not a private key object.<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) indicates that the input object is not a real JavaScript object.<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) indicates that the private attribute fails to be deleted and no exception occurs.<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) indicates that an exception occurs.|

### OH_JSVM_CreateDataReference()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataReference(JSVM_Env env,JSVM_Data data,uint32_t initialRefcount,JSVM_Ref* result)
```

**Description**

Creates a reference to a given JSVM_Data object. The initial reference count is the value of initialRefcount.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) data | JSVM_Data object to which the reference is to be created.|
| uint32_t initialRefcount | Initial reference count.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | Newly created object reference, which is of the JSVM_Ref type.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|

### OH_JSVM_GetReferenceData()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceData(JSVM_Env env,JSVM_Ref ref,JSVM_Data* result)
EXTERN_C_END
```

**Description**

If the reference is still valid, the corresponding JSVM_Data is returned through the result parameter, indicating the JavaScript value associated with JSVM_Ref. Otherwise, the result is empty.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | Environment for calling the JSVM-API.|
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | JSVM_Ref for requesting the corresponding value.|
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md)* result | JSVM_Data referenced by JSVM_Ref.|

**Returns**

| Type| Description|
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  Status code JSVM_Status.<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) indicates that the execution is successful.|
