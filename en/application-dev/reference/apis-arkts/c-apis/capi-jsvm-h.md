# jsvm.h

## Overview

Provides the JSVM API define.<br> Provides API to Provide independent, standard, and complete JavaScript engine capabilities for developers, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross language calls, and taking snapshots.

**Library**: libjsvm.so

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| JSVM_EXTERN \_\_declspec(dllexport) | externally visible.<br>**Since**: 11 |
| JSVM_AUTO_LENGTH SIZE_MAX | auto length.<br>**Since**: 11 |

### Function

| Name | Description |
| -- | -- |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Init(const JSVM_InitOptions* options)](#oh_jsvm_init) | Init a JavaScript vm. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateVM(const JSVM_CreateVMOptions* options, JSVM_VM* result)](#oh_jsvm_createvm) | This API create a new VM instance. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetMicrotaskPolicy(JSVM_VM vm, JSVM_MicrotaskPolicy policy)](#oh_jsvm_setmicrotaskpolicy) | This function controls how Microtasks are invoked of the vm. If the method is not called, the default microtask policy of vm is JSVM_MicrotaskPolicy::JSVM_MICROTASK_AUTO. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DestroyVM(JSVM_VM vm)](#oh_jsvm_destroyvm) | Destroys VM instance. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateProxy(JSVM_Env env, JSVM_Value target, JSVM_Value handler, JSVM_Value* result)](#oh_jsvm_createproxy) | This API allocates a default JavaScript Proxy. It is the equivalent of doing new Proxy(target, handler) in JavaScript. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsProxy(JSVM_Env env, JSVM_Value value, bool* isProxy)](#oh_jsvm_isproxy) | This API checks if the value passed in is a Proxy. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ProxyGetTarget(JSVM_Env env, JSVM_Value value, JSVM_Value* result)](#oh_jsvm_proxygettarget) | This API gets target from proxy. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenVMScope(JSVM_VM vm, JSVM_VMScope* result)](#oh_jsvm_openvmscope) | This API open a new VM scope for the VM instance. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseVMScope(JSVM_VM vm, JSVM_VMScope scope)](#oh_jsvm_closevmscope) | This function close the VM scope for the VM instance. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnv(JSVM_VM vm, size_t propertyCount, const JSVM_PropertyDescriptor* properties, JSVM_Env* result)](#oh_jsvm_createenv) | This function create a new environment with optional properties for the context of the new environment. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnvFromSnapshot(JSVM_VM vm, size_t index, JSVM_Env* result)](#oh_jsvm_createenvfromsnapshot) | This function create a new environment from the start snapshot of the vm. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DestroyEnv(JSVM_Env env)](#oh_jsvm_destroyenv) | This function destroys the environment. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenEnvScope(JSVM_Env env, JSVM_EnvScope* result)](#oh_jsvm_openenvscope) | This function open a new environment scope. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseEnvScope(JSVM_Env env, JSVM_EnvScope scope)](#oh_jsvm_closeenvscope) | This function closes the environment scope of the environment. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVM(JSVM_Env env, JSVM_VM* result)](#oh_jsvm_getvm) | This function retrieves the VM instance of the given environment. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScript(JSVM_Env env, JSVM_Value script, const uint8_t* cachedData, size_t cacheDataLength, bool eagerCompile, bool* cacheRejected, JSVM_Script* result)](#oh_jsvm_compilescript) | This function compiles a string of JavaScript code and returns the compiled script. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOrigin(JSVM_Env env, JSVM_Value script, const uint8_t* cachedData, size_t cacheDataLength, bool eagerCompile, bool* cacheRejected, JSVM_ScriptOrigin* origin, JSVM_Script* result)](#oh_jsvm_compilescriptwithorigin) | This function compiles a string of JavaScript code with the source code information and returns the compiled script. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateCodeCache(JSVM_Env env, JSVM_Script script, const uint8_t** data, size_t* length)](#oh_jsvm_createcodecache) | This function creates code cache for the compiled script. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RunScript(JSVM_Env env, JSVM_Script script, JSVM_Value* result)](#oh_jsvm_runscript) | This function executes a string of JavaScript code and returns its result with the following caveats: Unlike eval, this function does not allow the script to access the current lexical scope, and therefore also does not allow to access the module scope, meaning that pseudo-globals such as require will not be available. The script can access the global scope. Function and var declarations in the script will be added to the global object. Variable declarations made using let and const will be visible globally, but will not be added to the global object.The value of this is global within the script. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetInstanceData(JSVM_Env env, void* data, JSVM_Finalize finalizeCb, void* finalizeHint)](#oh_jsvm_setinstancedata) | This API associates data with the currently running JSVM environment. data can later be retrieved using OH_JSVM_GetInstanceData(). |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetInstanceData(JSVM_Env env, void** data)](#oh_jsvm_getinstancedata) | This API retrieves data that was previously associated with the currently running JSVM environment via OH_JSVM_SetInstanceData(). If no data is set, the call will succeed and data will be set to NULL. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetLastErrorInfo(JSVM_Env env, const JSVM_ExtendedErrorInfo** result)](#oh_jsvm_getlasterrorinfo) | This API retrieves a JSVM_ExtendedErrorInfo structure with information about the last error that occurred. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Throw(JSVM_Env env, JSVM_Value error)](#oh_jsvm_throw) | This API throws the JavaScript value provided. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowError(JSVM_Env env, const char* code, const char* msg)](#oh_jsvm_throwerror) | This API throws a JavaScript Error with the text provided. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowTypeError(JSVM_Env env, const char* code, const char* msg)](#oh_jsvm_throwtypeerror) | This API throws a JavaScript TypeError with the text provided. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowRangeError(JSVM_Env env, const char* code, const char* msg)](#oh_jsvm_throwrangeerror) | This API throws a JavaScript RangeError with the text provided. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowSyntaxError(JSVM_Env env, const char* code, const char* msg)](#oh_jsvm_throwsyntaxerror) | This API throws a JavaScript SyntaxError with the text provided. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsError(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_iserror) | This API queries a JSVM_Value to check if it represents an error object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateError(JSVM_Env env, JSVM_Value code, JSVM_Value msg, JSVM_Value* result)](#oh_jsvm_createerror) | This API returns a JavaScript Error with the text provided. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypeError(JSVM_Env env, JSVM_Value code, JSVM_Value msg, JSVM_Value* result)](#oh_jsvm_createtypeerror) | This API returns a JavaScript TypeError with the text provided. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateRangeError(JSVM_Env env, JSVM_Value code, JSVM_Value msg, JSVM_Value* result)](#oh_jsvm_createrangeerror) | This API returns a JavaScript RangeError with the text provided. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSyntaxError(JSVM_Env env, JSVM_Value code, JSVM_Value msg, JSVM_Value* result)](#oh_jsvm_createsyntaxerror) | This API returns a JavaScript SyntaxError with the text provided. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetAndClearLastException(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getandclearlastexception) | This API returns a JavaScript exception if one is pending, NULL otherwise. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsExceptionPending(JSVM_Env env, bool* result)](#oh_jsvm_isexceptionpending) | This API returns true if an exception is pending, false otherwise. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenHandleScope(JSVM_Env env, JSVM_HandleScope* result)](#oh_jsvm_openhandlescope) | This API opens a new scope. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseHandleScope(JSVM_Env env, JSVM_HandleScope scope)](#oh_jsvm_closehandlescope) | This API closes the scope passed in. Scopes must be closed in the reverse order from which they were created. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenEscapableHandleScope(JSVM_Env env, JSVM_EscapableHandleScope* result)](#oh_jsvm_openescapablehandlescope) | This API opens a new scope from which one object can be promoted to the outer scope. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseEscapableHandleScope(JSVM_Env env, JSVM_EscapableHandleScope scope)](#oh_jsvm_closeescapablehandlescope) | This API closes the scope passed in. Scopes must be closed in the reverse order from which they were created. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_EscapeHandle(JSVM_Env env, JSVM_EscapableHandleScope scope, JSVM_Value escapee, JSVM_Value* result)](#oh_jsvm_escapehandle) | This API promotes the handle to the JavaScript object so that it is valid for the lifetime of the outer scope. It can only be called once per scope. If it is called more than once an error will be returned. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateReference(JSVM_Env env, JSVM_Value value, uint32_t initialRefcount, JSVM_Ref* result)](#oh_jsvm_createreference) | This API creates a new reference with the specified reference count to the value passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteReference(JSVM_Env env, JSVM_Ref ref)](#oh_jsvm_deletereference) | his API deletes the reference passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceRef(JSVM_Env env, JSVM_Ref ref, uint32_t* result)](#oh_jsvm_referenceref) | his API increments the reference count for the reference passed in and returns the resulting reference count. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceUnref(JSVM_Env env, JSVM_Ref ref, uint32_t* result)](#oh_jsvm_referenceunref) | This API decrements the reference count for the reference passed in and returns the resulting reference count. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceValue(JSVM_Env env, JSVM_Ref ref, JSVM_Value* result)](#oh_jsvm_getreferencevalue) | If still valid, this API returns the JSVM_Value representing the JavaScript value associated with the JSVM_Ref. Otherwise, result will be NULL. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArray(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_createarray) | This API returns a JSVM-API value corresponding to a JavaScript Array type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayWithLength(JSVM_Env env, size_t length, JSVM_Value* result)](#oh_jsvm_createarraywithlength) | This API returns a JSVM-API value corresponding to a JavaScript Array type. The Array's length property is set to the passed-in length parameter. However, the underlying buffer is not guaranteed to be pre-allocated by the VM when the array is created. That behavior is left to the underlying VM implementation. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArraybuffer(JSVM_Env env, size_t byteLength, void** data, JSVM_Value* result)](#oh_jsvm_createarraybuffer) | This API returns a JSVM-API value corresponding to a JavaScript ArrayBuffer. ArrayBuffers are used to represent fixed-length binary data buffers. They are normally used as a backing-buffer for TypedArray objects. The ArrayBuffer allocated will have an underlying byte buffer whose size is determined by the length parameter that's passed in. The underlying buffer is optionally returned back to the caller in case the caller wants to directly manipulate the buffer. This buffer can only be written to directly from native code. To write to this buffer from JavaScript, a typed array or DataView object would need to be created. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_AllocateArrayBufferBackingStoreData(size_t byteLength, JSVM_InitializedFlag initialized, void **data)](#oh_jsvm_allocatearraybufferbackingstoredata) | This API allocate the memory of array buffer backing store. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_FreeArrayBufferBackingStoreData(void* data)](#oh_jsvm_freearraybufferbackingstoredata) | This API release the memory of an array buffer backing store. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayBufferFromBackingStoreData(JSVM_Env env, void* data, size_t backingStoreSize, size_t offset, size_t arrayBufferSize, JSVM_Value* result)](#oh_jsvm_createarraybufferfrombackingstoredata) | This API create an array buffer using the backing store data. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDate(JSVM_Env env, double time, JSVM_Value* result)](#oh_jsvm_createdate) | This API does not observe leap seconds; they are ignored, as ECMAScript aligns with POSIX time specification. This API allocates a JavaScript Date object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternal(JSVM_Env env, void* data, JSVM_Finalize finalizeCb, void* finalizeHint, JSVM_Value* result)](#oh_jsvm_createexternal) | This API allocates a JavaScript value with external data attached to it. This is used to pass external data through JavaScript code, so it can be retrieved later by native code using OH_JSVM_GetValueExternal. The API adds a JSVM_Finalize callback which will be called when the JavaScript object just created has been garbage collected.The created value is not an object, and therefore does not support additional properties. It is considered a distinct value type calling OH_JSVM_Typeof() with an external value yields JSVM_EXTERNAL. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateObject(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_createobject) | This API allocates a default JavaScript Object. It is the equivalent of doing new Object() in JavaScript. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSymbol(JSVM_Env env, JSVM_Value description, JSVM_Value* result)](#oh_jsvm_createsymbol) | This API creates a JavaScript symbol value from a UTF8-encoded C string. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SymbolFor(JSVM_Env env, const char* utf8description, size_t length, JSVM_Value* result)](#oh_jsvm_symbolfor) | This API searches in the global registry for an existing symbol with the given description. If the symbol already exists it will be returned, otherwise a new symbol will be created in the registry. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypedarray(JSVM_Env env, JSVM_TypedarrayType type, size_t length, JSVM_Value arraybuffer, size_t byteOffset, JSVM_Value* result)](#oh_jsvm_createtypedarray) | This API creates a JavaScript TypedArray object over an existing ArrayBuffer. TypedArray objects provide an array-like view over an underlying data buffer where each element has the same underlying binary scalar datatype.It's required that (length * size_of_element) + byte_offset should be <= the size in bytes of the array passed in. If not, a RangeError exception is raised. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataview(JSVM_Env env, size_t length, JSVM_Value arraybuffer, size_t byteOffset, JSVM_Value* result)](#oh_jsvm_createdataview) | This API creates a JavaScript DataView object over an existing ArrayBuffer. DataView objects provide an array-like view over an underlying data buffer, but one which allows items of different size and type in the ArrayBuffer.It is required that byte_length + byte_offset is less than or equal to the size in bytes of the array passed in. If not, a RangeError exception is raised. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt32(JSVM_Env env, int32_t value, JSVM_Value* result)](#oh_jsvm_createint32) | This API is used to convert from the C int32_t type to the JavaScript number type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateUint32(JSVM_Env env, uint32_t value, JSVM_Value* result)](#oh_jsvm_createuint32) | This API is used to convert from the C uint32_t type to the JavaScript number type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt64(JSVM_Env env, int64_t value, JSVM_Value* result)](#oh_jsvm_createint64) | This API is used to convert from the C int64_t type to the JavaScript number type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDouble(JSVM_Env env, double value, JSVM_Value* result)](#oh_jsvm_createdouble) | This API is used to convert from the C double type to the JavaScript number type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintInt64(JSVM_Env env, int64_t value, JSVM_Value* result)](#oh_jsvm_createbigintint64) | This API converts the C int64_t type to the JavaScript BigInt type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintUint64(JSVM_Env env, uint64_t value, JSVM_Value* result)](#oh_jsvm_createbigintuint64) | This API converts the C uint64_t type to the JavaScript BigInt type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintWords(JSVM_Env env, int signBit, size_t wordCount, const uint64_t* words, JSVM_Value* result)](#oh_jsvm_createbigintwords) | This API converts an array of unsigned 64-bit words into a single BigInt value. The resulting BigInt is calculated as (–1)sign_bit (words[0] × (264)0 + words[1] × (264)1 + …) |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringLatin1(JSVM_Env env, const char* str, size_t length, JSVM_Value* result)](#oh_jsvm_createstringlatin1) | This API creates a JavaScript string value from an ISO-8859-1-encoded C string. The native string is copied. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf16(JSVM_Env env, const char16_t* str, size_t length, JSVM_Value* result)](#oh_jsvm_createstringutf16) | This API creates a JavaScript string value from a UTF16-LE-encoded C string. The native string is copied. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf8(JSVM_Env env, const char* str, size_t length, JSVM_Value* result)](#oh_jsvm_createstringutf8) | This API creates a JavaScript string value from a UTF8-encoded C string. The native string is copied. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetArrayLength(JSVM_Env env, JSVM_Value value, uint32_t* result)](#oh_jsvm_getarraylength) | This API returns the length of an array. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetArraybufferInfo(JSVM_Env env, JSVM_Value arraybuffer, void** data, size_t* byteLength)](#oh_jsvm_getarraybufferinfo) | This API is used to retrieve the underlying data buffer of an ArrayBuffer and its length. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPrototype(JSVM_Env env, JSVM_Value object, JSVM_Value* result)](#oh_jsvm_getprototype) | This API returns the length of an array. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetTypedarrayInfo(JSVM_Env env, JSVM_Value typedarray, JSVM_TypedarrayType* type, size_t* length, void** data, JSVM_Value* arraybuffer, size_t* byteOffset)](#oh_jsvm_gettypedarrayinfo) | This API returns various properties of a typed array. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetDataviewInfo(JSVM_Env env, JSVM_Value dataview, size_t* bytelength, void** data, JSVM_Value* arraybuffer, size_t* byteOffset)](#oh_jsvm_getdataviewinfo) | Any of the out parameters may be NULL if that property is unneeded. This API returns various properties of a DataView. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetDateValue(JSVM_Env env, JSVM_Value value, double* result)](#oh_jsvm_getdatevalue) | Returns JSVM_OK if the function executed successfully. If a non-date JSVM_Value is passed in it returns JSVM_date_expected.This API returns the C double primitive of time value for the given JavaScript Date. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBool(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_getvaluebool) | This API returns the C boolean primitive equivalent of the given JavaScript Boolean. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueDouble(JSVM_Env env, JSVM_Value value, double* result)](#oh_jsvm_getvaluedouble) | This API returns the C double primitive equivalent of the given JavaScript number. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintInt64(JSVM_Env env, JSVM_Value value, int64_t* result, bool* lossless)](#oh_jsvm_getvaluebigintint64) | This API returns the C int64_t primitive equivalent of the given JavaScript BigInt. If needed it will truncate the value, setting lossless to false. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintUint64(JSVM_Env env, JSVM_Value value, uint64_t* result, bool* lossless)](#oh_jsvm_getvaluebigintuint64) | This API returns the C uint64_t primitive equivalent of the given JavaScript BigInt. If needed it will truncate the value, setting lossless to false. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintWords(JSVM_Env env, JSVM_Value value, int* signBit, size_t* wordCount, uint64_t* words)](#oh_jsvm_getvaluebigintwords) | This API converts a single BigInt value into a sign bit, 64-bit little-endian array, and the number of elements in the array. signBit and words may be both set to NULL, in order to get only wordCount. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueExternal(JSVM_Env env, JSVM_Value value, void** result)](#oh_jsvm_getvalueexternal) | This API retrieves the external data pointer that was previously passed to OH_JSVM_CreateExternal(). |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt32(JSVM_Env env, JSVM_Value value, int32_t* result)](#oh_jsvm_getvalueint32) | This API returns the C int32 primitive equivalent of the given JavaScript number. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt64(JSVM_Env env, JSVM_Value value, int64_t* result)](#oh_jsvm_getvalueint64) | This API returns the C int64 primitive equivalent of the given JavaScript number. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringLatin1(JSVM_Env env, JSVM_Value value, char* buf, size_t bufsize, size_t* result)](#oh_jsvm_getvaluestringlatin1) | This API returns the ISO-8859-1-encoded string corresponding the value passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf8(JSVM_Env env, JSVM_Value value, char* buf, size_t bufsize, size_t* result)](#oh_jsvm_getvaluestringutf8) | This API returns the UTF8-encoded string corresponding the value passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf16(JSVM_Env env, JSVM_Value value, char16_t* buf, size_t bufsize, size_t* result)](#oh_jsvm_getvaluestringutf16) | This API returns the UTF16-encoded string corresponding the value passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueUint32(JSVM_Env env, JSVM_Value value, uint32_t* result)](#oh_jsvm_getvalueuint32) | This API returns the C primitive equivalent of the given JSVM_Value as a uint32_t. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetBoolean(JSVM_Env env, bool value, JSVM_Value* result)](#oh_jsvm_getboolean) | This API is used to return the JavaScript singleton object that is used to represent the given boolean value. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetGlobal(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getglobal) | This API returns the global object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNull(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getnull) | This API returns the null object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetUndefined(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getundefined) | This API returns the Undefined object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBool(JSVM_Env env, JSVM_Value value, JSVM_Value* result)](#oh_jsvm_coercetobool) | This API implements the abstract operation ToBoolean() |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToNumber(JSVM_Env env, JSVM_Value value, JSVM_Value* result)](#oh_jsvm_coercetonumber) | This API implements the abstract operation ToNumber() as defined. This function potentially runs JS code if the passed-in value is an object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToObject(JSVM_Env env, JSVM_Value value, JSVM_Value* result)](#oh_jsvm_coercetoobject) | This API implements the abstract operation ToObject(). |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToString(JSVM_Env env, JSVM_Value value, JSVM_Value* result)](#oh_jsvm_coercetostring) | This API implements the abstract operation ToString().This function potentially runs JS code if the passed-in value is an object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Typeof(JSVM_Env env, JSVM_Value value, JSVM_ValueType* result)](#oh_jsvm_typeof) | This API represents behavior similar to invoking the typeof Operator on the object as defined. However, there are some differences:It has support for detecting an External value.It detects null as a separate type, while ECMAScript typeof would detect object.If value has a type that is invalid, an error is returned. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Instanceof(JSVM_Env env, JSVM_Value object, JSVM_Value constructor, bool* result)](#oh_jsvm_instanceof) | This API represents invoking the instanceof Operator on the object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsArray(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_isarray) | This API represents invoking the IsArray operation on the object |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsArraybuffer(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_isarraybuffer) | This API checks if the Object passed in is an array buffer. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDate(JSVM_Env env, JSVM_Value value, bool* isDate)](#oh_jsvm_isdate) | This API checks if the Object passed in is a date. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsTypedarray(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_istypedarray) | This API checks if the Object passed in is a typed array. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDataview(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_isdataview) | This API checks if the Object passed in is a DataView. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_StrictEquals(JSVM_Env env, JSVM_Value lhs, JSVM_Value rhs, bool* result)](#oh_jsvm_strictequals) | This API represents the invocation of the Strict Equality algorithm. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Equals(JSVM_Env env, JSVM_Value lhs, JSVM_Value rhs, bool* result)](#oh_jsvm_equals) | This API represents the invocation of the Relaxed Equality algorithm. Returns true as long as the values are equal, regardless of type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DetachArraybuffer(JSVM_Env env, JSVM_Value arraybuffer)](#oh_jsvm_detacharraybuffer) | This API represents the invocation of the ArrayBuffer detach operation. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDetachedArraybuffer(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_isdetachedarraybuffer) | This API represents the invocation of the ArrayBuffer IsDetachedBuffer operation. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPropertyNames(JSVM_Env env, JSVM_Value object, JSVM_Value* result)](#oh_jsvm_getpropertynames) | This API returns the names of the enumerable properties of object as an array of strings. The properties of object whose key is a symbol will not be included. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetAllPropertyNames(JSVM_Env env, JSVM_Value object, JSVM_KeyCollectionMode keyMode, JSVM_KeyFilter keyFilter, JSVM_KeyConversion keyConversion, JSVM_Value* result)](#oh_jsvm_getallpropertynames) | This API returns an array containing the names of the available properties of this object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, JSVM_Value value)](#oh_jsvm_setproperty) | This API set a property on the Object passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, JSVM_Value* result)](#oh_jsvm_getproperty) | This API gets the requested property from the Object passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, bool* result)](#oh_jsvm_hasproperty) | This API checks if the Object passed in has the named property. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, bool* result)](#oh_jsvm_deleteproperty) | This API attempts to delete the key own property from object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasOwnProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, bool* result)](#oh_jsvm_hasownproperty) | This API checks if the Object passed in has the named own property. key must be a string or a symbol, or an error will be thrown. JSVM-API will not perform any conversion between data types. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetNamedProperty(JSVM_Env env, JSVM_Value object, const char* utf8name, JSVM_Value value)](#oh_jsvm_setnamedproperty) | This method is equivalent to calling OH_JSVM_SetProperty with a JSVM_Value created from the string passed in as utf8name. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNamedProperty(JSVM_Env env, JSVM_Value object, const char* utf8name, JSVM_Value* result)](#oh_jsvm_getnamedproperty) | This method is equivalent to calling OH_JSVM_SetProperty with a JSVM_Value created from the string passed in as utf8name. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasNamedProperty(JSVM_Env env, JSVM_Value object, const char* utf8name, bool* result)](#oh_jsvm_hasnamedproperty) | This method is equivalent to calling OH_JSVM_SetProperty with a JSVM_Value created from the string passed in as utf8name. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetElement(JSVM_Env env, JSVM_Value object, uint32_t index, JSVM_Value value)](#oh_jsvm_setelement) | This API sets an element on the Object passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetElement(JSVM_Env env, JSVM_Value object, uint32_t index, JSVM_Value* result)](#oh_jsvm_getelement) | This API gets the element at the requested index. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasElement(JSVM_Env env, JSVM_Value object, uint32_t index, bool* result)](#oh_jsvm_haselement) | This API returns if the Object passed in has an element at the requested index. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteElement(JSVM_Env env, JSVM_Value object, uint32_t index, bool* result)](#oh_jsvm_deleteelement) | This API attempts to delete the specified index from object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineProperties(JSVM_Env env, JSVM_Value object, size_t propertyCount, const JSVM_PropertyDescriptor* properties)](#oh_jsvm_defineproperties) | This method allows the efficient definition of multiple properties on a given object. The properties are defined using property descriptors. Given an array of such property descriptors, this API will set the properties on the object one at a time, as defined by DefineOwnProperty(). |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectFreeze(JSVM_Env env, JSVM_Value object)](#oh_jsvm_objectfreeze) | This method freezes a given object. This prevents new properties from being added to it, existing properties from being removed, prevents changing the enumerability, configurability, or writability of existing properties, and prevents the values of existing properties from being changed. It also prevents the object's prototype from being changed. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSeal(JSVM_Env env, JSVM_Value object)](#oh_jsvm_objectseal) | This method seals a given object. This prevents new properties from being added to it, as well as marking all existing properties as non-configurable. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CallFunction(JSVM_Env env, JSVM_Value recv, JSVM_Value func, size_t argc, const JSVM_Value* argv, JSVM_Value* result)](#oh_jsvm_callfunction) | This method allows a JavaScript function object to be called from a native add-on. This is the primary mechanism of calling back from the add-on's native code into JavaScript. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunction(JSVM_Env env, const char* utf8name, size_t length, JSVM_Callback cb, JSVM_Value* result)](#oh_jsvm_createfunction) | This API allows an add-on author to create a function object in native code. This is the primary mechanism to allow calling into the add-on's native code from JavaScript.The newly created function is not automatically visible from script after this call. Instead, a property must be explicitly set on any object that is visible to JavaScript, in order for the function to be accessible from script. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetCbInfo(JSVM_Env env, JSVM_CallbackInfo cbinfo, size_t* argc, JSVM_Value* argv, JSVM_Value* thisArg, void** data)](#oh_jsvm_getcbinfo) | This method is used within a callback function to retrieve details about the call like the arguments and the this pointer from a given callback info. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNewTarget(JSVM_Env env, JSVM_CallbackInfo cbinfo, JSVM_Value* result)](#oh_jsvm_getnewtarget) | This API returns the new.target of the constructor call. If the current callback is not a constructor call, the result is NULL. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_NewInstance(JSVM_Env env, JSVM_Value constructor, size_t argc, const JSVM_Value* argv, JSVM_Value* result)](#oh_jsvm_newinstance) | his method is used to instantiate a new JavaScript value using a given JSVM_Value that represents the constructor for the object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClass(JSVM_Env env, const char* utf8name, size_t length, JSVM_Callback constructor, size_t propertyCount, const JSVM_PropertyDescriptor* properties, JSVM_Value* result)](#oh_jsvm_defineclass) | When wrapping a C++ class, the C++ constructor callback passed via constructor should be a static method on the class that calls the actual class constructor, then wraps the new C++ instance in a JavaScript object, and returns the wrapper object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Wrap(JSVM_Env env, JSVM_Value jsObject, void* nativeObject, JSVM_Finalize finalizeCb, void* finalizeHint, JSVM_Ref* result)](#oh_jsvm_wrap) | Wraps a native instance in a JavaScript object. The native instance can be retrieved later using OH_JSVM_Unwrap(). |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Unwrap(JSVM_Env env, JSVM_Value jsObject, void** result)](#oh_jsvm_unwrap) | When JavaScript code invokes a method or property accessor on the class, the corresponding JSVM_Callback is invoked. If the callback is for an instance method or accessor, then the this argument to the callback is the wrapper object; the wrapped C++ instance that is the target of the call can be obtained then by calling OH_JSVM_Unwrap() on the wrapper object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RemoveWrap(JSVM_Env env, JSVM_Value jsObject, void** result)](#oh_jsvm_removewrap) | Retrieves a native instance that was previously wrapped in the JavaScript object jsObject using OH_JSVM_Wrap() and removes the wrapping. If a finalize callback was associated with the wrapping, it will no longer be called when the JavaScript object becomes garbage-collected. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_TypeTagObject(JSVM_Env env, JSVM_Value value, const JSVM_TypeTag* typeTag)](#oh_jsvm_typetagobject) | Associates the value of the typeTag pointer with the JavaScript object or external. OH_JSVM_CheckObjectTypeTag() can then be used to compare the tag that was attached to the object with one owned by the addon to ensure that the object has the right type. If the object already has an associated type tag, this API will return JSVM_INVALID_ARG. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CheckObjectTypeTag(JSVM_Env env, JSVM_Value value, const JSVM_TypeTag* typeTag, bool* result)](#oh_jsvm_checkobjecttypetag) | Compares the pointer given as typeTag with any that can be found on js object. If no tag is found on js object or, if a tag is found but it does not match typeTag, then result is set to false. If a tag is found and it matches typeTag, then result is set to true. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_AddFinalizer(JSVM_Env env, JSVM_Value jsObject, void* finalizeData, JSVM_Finalize finalizeCb, void* finalizeHint, JSVM_Ref* result)](#oh_jsvm_addfinalizer) | This API can be called multiple times on a single JavaScript object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVersion(JSVM_Env env, uint32_t* result)](#oh_jsvm_getversion) | This API returns the highest JSVM-API version supported by the JSVM runtime.<br> JSVM-API is planned to be additive such that newer releases of JSVM may support additional API functions. In order to allow an addon to use a newer function when running with versions of JSVM that support it, while providing fallback behavior when running with JSVM versions that don't support it. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVMInfo(JSVM_VMInfo* result)](#oh_jsvm_getvminfo) | Return information of the VM. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_AdjustExternalMemory(JSVM_Env env, int64_t changeInBytes, int64_t* result)](#oh_jsvm_adjustexternalmemory) | This function gives V8 an indication of the amount of externally allocated memory that is kept alive by JavaScript objects (i.e. a JavaScript object that points to its own memory allocated by a native addon). Registering externally allocated memory will trigger global garbage collections more often than it would otherwise. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_MemoryPressureNotification(JSVM_Env env, JSVM_MemoryPressureLevel level)](#oh_jsvm_memorypressurenotification) | This function notifies the VM that the system is running low on memory and optionally triggers a garbage collection. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreatePromise(JSVM_Env env, JSVM_Deferred* deferred, JSVM_Value* promise)](#oh_jsvm_createpromise) | This API creates a deferred object and a JavaScript promise. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ResolveDeferred(JSVM_Env env, JSVM_Deferred deferred, JSVM_Value resolution)](#oh_jsvm_resolvedeferred) | This API resolves a JavaScript promise by way of the deferred object with which it is associated. Thus, it can only be used to resolve JavaScript promises for which the corresponding deferred object is available. This effectively means that the promise must have been created using OH_JSVM_CreatePromise() and the deferred object returned from that call must have been retained in order to be passed to this API. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RejectDeferred(JSVM_Env env, JSVM_Deferred deferred, JSVM_Value rejection)](#oh_jsvm_rejectdeferred) | This API rejects a JavaScript promise by way of the deferred object with which it is associated. Thus, it can only be used to reject JavaScript promises for which the corresponding deferred object is available. This effectively means that the promise must have been created using OH_JSVM_CreatePromise() and the deferred object returned from that call must have been retained in order to be passed to this API. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsPromise(JSVM_Env env, JSVM_Value value, bool* isPromise)](#oh_jsvm_ispromise) | This API return indicating whether promise is a native promise object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_PromiseRegisterHandler(JSVM_Env env, JSVM_Value promise, JSVM_Value onFulfilled, JSVM_Value onRejected, JSVM_Value* result)](#oh_jsvm_promiseregisterhandler) | This API register a resolution/rejection handler with a promise. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_JsonParse(JSVM_Env env, JSVM_Value jsonString, JSVM_Value* result)](#oh_jsvm_jsonparse) | This API parses a JSON string and returns it as value if successful. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_JsonStringify(JSVM_Env env, JSVM_Value jsonObject, JSVM_Value* result)](#oh_jsvm_jsonstringify) | This API stringifies the object and returns it as string if successful. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSnapshot(JSVM_VM vm, size_t contextCount, const JSVM_Env* contexts, const char** blobData, size_t* blobSize)](#oh_jsvm_createsnapshot) | This API create the startup snapshot of the VM. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetHeapStatistics(JSVM_VM vm, JSVM_HeapStatistics* result)](#oh_jsvm_getheapstatistics) | This function returns a set of statistics data of the heap of the VM. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_StartCpuProfiler(JSVM_VM vm, JSVM_CpuProfiler* result)](#oh_jsvm_startcpuprofiler) | This function creates and starts a CPU profiler. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_StopCpuProfiler(JSVM_VM vm, JSVM_CpuProfiler profiler, JSVM_OutputStream stream, void* streamData)](#oh_jsvm_stopcpuprofiler) | This function stops the CPU profiler and output to the stream. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_TakeHeapSnapshot(JSVM_VM vm, JSVM_OutputStream stream, void* streamData)](#oh_jsvm_takeheapsnapshot) | This function takes the current heap snapshot and output to the stream. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_TakeRawHeapSnapshot(JSVM_VM vm, JSVM_OutputStream stream, void *streamData)](#oh_jsvm_takerawheapsnapshot) | This function takes the current heap snapshot and outputs it to the stream in raw heap format (binary format). The raw heap format is VM-specific and its layout is not guaranteed to be stable across different versions. This operation may pause the application temporarily, and frequent invocation may generate large snapshot files and increase disk usage, so callers should manage generated files appropriately if files are written to disk. The stream callback is invoked synchronously on the thread where the VM is running. The callback should avoid long blocking operations. If the callback returns false, the output stream is aborted, snapshot generation stops. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHeapThresholdCallback(JSVM_VM vm, uint64_t threshold, JSVM_HandlerForHeapThreshold callback, void *data)](#oh_jsvm_setheapthresholdcallback) | Set a heap threshold callback for vm and the vm can only have one heap threshold callback. The registered callback should be cleared by OH_JSVM_ClearHeapThresholdCallback when it is no longer needed. This API is not thread-safe and must be called on the thread where the vm is running. The threshold is checked around GC, and the callback is invoked when the observed heap usage is greater than or equal to threshold. The callback will be called synchronously on the same thread, and threshold checks are skipped while the callback is running. After the callback returns, if the heap usage is still greater than or equal to threshold, the callback will be invoked again around the next GC. The callback does not need to be registered again after it returns. The registered callback is identified (threshold, callback, data). |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ClearHeapThresholdCallback(JSVM_VM vm, uint64_t threshold, JSVM_HandlerForHeapThreshold callback, void *data)](#oh_jsvm_clearheapthresholdcallback) | Clear the heap threshold callback previously registered for vm. This API is not thread-safe and must be called on the thread where the vm is running. The registered callback is identified (threshold, callback, data). |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspector(JSVM_Env env, const char* host, uint16_t port)](#oh_jsvm_openinspector) | This functiong activates insepctor on host and port. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseInspector(JSVM_Env env)](#oh_jsvm_closeinspector) | This function attempts to close all remaining inspector connections. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_WaitForDebugger(JSVM_Env env, bool breakNextLine)](#oh_jsvm_waitfordebugger) | This function will block until a client (existing or connected later) has sent Runtime.runIfWaitingForDebugger command. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithPropertyHandler(JSVM_Env env, const char* utf8name, size_t length, JSVM_Callback constructor, size_t propertyCount, const JSVM_PropertyDescriptor* properties, JSVM_PropertyHandlerCfg propertyHandlerCfg, JSVM_Callback callAsFunctionCallback, JSVM_Value* result)](#oh_jsvm_defineclasswithpropertyhandler) | Define a JavaScript class with given class name, constructor, properties, callback handlers for property operations including get, set, delete, enum etc., and call as function callback. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsLocked(JSVM_Env env, bool* isLocked)](#oh_jsvm_islocked) | Determines whether the current thread holds the lock for the specified environment. Only threads that hold locks can use the environment. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_AcquireLock(JSVM_Env env)](#oh_jsvm_acquirelock) | Acquire the lock for the specified environment. Only threads that hold locks can use the environment. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseLock(JSVM_Env env)](#oh_jsvm_releaselock) | Release the lock for the specified environment. Only threads that hold locks can use the environment. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_PumpMessageLoop(JSVM_VM vm, bool* result)](#oh_jsvm_pumpmessageloop) | Starts the running of the task queue inside the VM. This task queue can be executed by an external event loop. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_PerformMicrotaskCheckpoint(JSVM_VM vm)](#oh_jsvm_performmicrotaskcheckpoint) | Check to see if there are any microtasks waiting in the queue, and if there are, execute them. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsCallable(JSVM_Env env, JSVM_Value value, bool* isCallable)](#oh_jsvm_iscallable) | This API checks if the value passed in is callable. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsUndefined(JSVM_Env env, JSVM_Value value, bool* isUndefined)](#oh_jsvm_isundefined) | This API checks if the value passed in is undefined. This equals to `value === undefined` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNull(JSVM_Env env, JSVM_Value value, bool* isNull)](#oh_jsvm_isnull) | This API checks if the value passed in is a null object. This equals to `value === null` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNullOrUndefined(JSVM_Env env, JSVM_Value value, bool* isNullOrUndefined)](#oh_jsvm_isnullorundefined) | This API checks if the value passed in is either a null or an undefined object. This is equivalent to `value == null` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBoolean(JSVM_Env env, JSVM_Value value, bool* isBoolean)](#oh_jsvm_isboolean) | This API checks if the value passed in is a boolean. This equals to `typeof value === 'boolean'` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNumber(JSVM_Env env, JSVM_Value value, bool* isNumber)](#oh_jsvm_isnumber) | This API checks if the value passed in is a number. This equals to `typeof value === 'number'` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsString(JSVM_Env env, JSVM_Value value, bool* isString)](#oh_jsvm_isstring) | This API checks if the value passed in is a string. This equals to `typeof value === 'string'` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbol(JSVM_Env env, JSVM_Value value, bool* isSymbol)](#oh_jsvm_issymbol) | This API checks if the value passed in is a symbol. This equals to `typeof value === 'symbol'` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsFunction(JSVM_Env env, JSVM_Value value, bool* isFunction)](#oh_jsvm_isfunction) | This API checks if the value passed in is a function. This equals to `typeof value === 'function'` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsObject(JSVM_Env env, JSVM_Value value, bool* isObject)](#oh_jsvm_isobject) | This API checks if the value passed in is an object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBigInt(JSVM_Env env, JSVM_Value value, bool* isBigInt)](#oh_jsvm_isbigint) | This API checks if the value passed in is a bigInt. This equals to `typeof value === 'bigint'` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateMap(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_createmap) | This API returns a JSVM-API value corresponding to a JavaScript Map type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsMap(JSVM_Env env, JSVM_Value value, bool* isMap)](#oh_jsvm_ismap) | This API checks if the value passed in is a Map. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSet(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_createset) | This API returns a JSVM-API value corresponding to a JavaScript Set type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSet(JSVM_Env env, JSVM_Value value, bool* isSet)](#oh_jsvm_isset) | This API checks if the value passed in is a Set. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOptions(JSVM_Env env, JSVM_Value script, size_t optionCount, JSVM_CompileOptions options[], JSVM_Script* result)](#oh_jsvm_compilescriptwithoptions) | This function compiles a string of JavaScript code with the compile options and returns the compiled script. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBigInt(JSVM_Env env, JSVM_Value value, JSVM_Value* result)](#oh_jsvm_coercetobigint) | This API implements the abstract operation ToBigInt(). |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsRegExp(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_isregexp) | This API checks if the value passed in is a regExp. This equals to `value instanceof RegExp` in JS. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsConstructor(JSVM_Env env, JSVM_Value value, bool* isConstructor)](#oh_jsvm_isconstructor) | This API checks if the value passed in is a constructor. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateRegExp(JSVM_Env env, JSVM_Value value, JSVM_RegExpFlags flags, JSVM_Value* result)](#oh_jsvm_createregexp) | This API returns the JavaScript value of the regular expression corresponding to the input. The interface may throw an exception. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectGetPrototypeOf(JSVM_Env env, JSVM_Value object, JSVM_Value* result)](#oh_jsvm_objectgetprototypeof) | This API returns the Object prototype. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSetPrototypeOf(JSVM_Env env, JSVM_Value object, JSVM_Value prototype)](#oh_jsvm_objectsetprototypeof) | This API set the prototype on the Object passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunctionWithScript(JSVM_Env env, const char* funcName, size_t length, size_t argc, const JSVM_Value* argv, JSVM_Value script, JSVM_Value* result)](#oh_jsvm_createfunctionwithscript) | Creates a function with a given script as its body. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RetainScript(JSVM_Env env, JSVM_Script script)](#oh_jsvm_retainscript) | This function keep persistently save a JSVM_Script and extend its lifecycle beyond the current scope. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseScript(JSVM_Env env, JSVM_Script script)](#oh_jsvm_releasescript) | This function release the script retained by OH_JSVM_RetainScript |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspectorWithName(JSVM_Env env, int pid, const char* name)](#oh_jsvm_openinspectorwithname) | This function activates insepctor with pid and alias it. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmModule(JSVM_Env env, const uint8_t *wasmBytecode, size_t wasmBytecodeLength, const uint8_t *cacheData, size_t cacheDataLength, bool *cacheRejected, JSVM_Value *wasmModule)](#oh_jsvm_compilewasmmodule) | Compile WebAssembly bytecode into a WebAssembly module. If WebAssembly cache provided, deserialization will be performed. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmFunction(JSVM_Env env, JSVM_Value wasmModule, uint32_t functionIndex, JSVM_WasmOptLevel optLevel)](#oh_jsvm_compilewasmfunction) | Compile the function with the specified index in the WebAssembly module into the specified optimization level. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsWasmModuleObject(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_iswasmmoduleobject) | Check whether the given JSVM_Value is a WebAssembly module. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateWasmCache(JSVM_Env env, JSVM_Value wasmModule, const uint8_t** data, size_t* length)](#oh_jsvm_createwasmcache) | Create cache for compiled WebAssembly module. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseCache(JSVM_Env env, const uint8_t* cacheData, JSVM_CacheType cacheType)](#oh_jsvm_releasecache) | Release cache data with specified cache type. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternalStringLatin1(JSVM_Env env, char* str, size_t length, JSVM_Finalize finalizeCallback, void* finalizeHint, JSVM_Value* result, bool* copied)](#oh_jsvm_createexternalstringlatin1) | This API creates an external JavaScript string value from an ISO-8859-1-encoded C string. The native string is copied when failed to create external string. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternalStringUtf16(JSVM_Env env, char16_t* str, size_t length, JSVM_Finalize finalizeCallback, void* finalizeHint, JSVM_Value* result, bool* copied)](#oh_jsvm_createexternalstringutf16) | This API creates an external JavaScript string value from an UTF16-LE-encoded C string. The native string is copied when failed to create external string. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreatePrivate(JSVM_Env env, JSVM_Value description, JSVM_Data* result)](#oh_jsvm_createprivate) | This API creates a JavaScript private key. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetPrivate(JSVM_Env env, JSVM_Value object, JSVM_Data key, JSVM_Value value)](#oh_jsvm_setprivate) | This API set a private property on the Object passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPrivate(JSVM_Env env, JSVM_Value object, JSVM_Data key, JSVM_Value *result)](#oh_jsvm_getprivate) | This API gets the requested private property from the Object passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeletePrivate(JSVM_Env env, JSVM_Value object, JSVM_Data key)](#oh_jsvm_deleteprivate) | This API attempts to delete the property of the private key from object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataReference(JSVM_Env env, JSVM_Data data, uint32_t initialRefcount, JSVM_Ref* result)](#oh_jsvm_createdatareference) | This API creates a new reference with the specified reference count to the data passed in. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceData(JSVM_Env env, JSVM_Ref ref, JSVM_Data* result)](#oh_jsvm_getreferencedata) | If still valid, this API returns the JSVM_Data representing the JavaScript data associated with the JSVM_Ref. Otherwise, result will be NULL. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBigIntObject(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_isbigintobject) | Check whether the given JSVM_Value is a BigInt Object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBooleanObject(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_isbooleanobject) | Check whether the given JSVM_Value is a Boolean Object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsStringObject(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_isstringobject) | Check whether the given JSVM_Value is a String Object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNumberObject(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_isnumberobject) | Check whether the given JSVM_Value is a Number Object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbolObject(JSVM_Env env, JSVM_Value value, bool* result)](#oh_jsvm_issymbolobject) | Check whether the given JSVM_Value is a Symbol Object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolAsyncIterator(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolasynciterator) | This API returns the Symbol.asyncIterator of Well-Known Symbols. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolHasInstance(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolhasinstance) | This API returns the Symbol.hasInstance of Well-Known Symbols. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIsConcatSpreadable(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolisconcatspreadable) | This API returns the Symbol.isConcatSpreadable of Well-Known Symbols |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolMatch(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolmatch) | This API returns the Symbol.match of Well-Known Symbols |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolReplace(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolreplace) | This API returns the Symbol.replace of Well-Known Symbols |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSearch(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolsearch) | This API returns the Symbol.search of Well-Known Symbols |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSplit(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolsplit) | This API returns the Symbol.split of Well-Known Symbols |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToPrimitive(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboltoprimitive) | This API returns the Symbol.toPrimitive of Well-Known Symbols |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolUnscopables(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolunscopables) | This API returns the Symbol.unscopables of Well-Known Symbols |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToStringTag(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboltostringtag) | This API returns the Symbol.toStringTag of Well-Known Symbols |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIterator(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboliterator) | This API returns the Symbol.iterator of Well-Known Symbols |
| [JSVM_EXTERN JSVM_Status OH_JSVM_TraceStart(size_t count, const JSVM_TraceCategory* categories, const char* tag, size_t eventsCount)](#oh_jsvm_tracestart) | Trace start with specified categories for all JSVM VM.(Non-thread-safe) |
| [JSVM_EXTERN JSVM_Status OH_JSVM_TraceStop(JSVM_OutputStream stream, void* streamData)](#oh_jsvm_tracestop) | Trace stop for specified categories for all JSVM VM.(Non-thread-safe) |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForOOMError(JSVM_VM vm, JSVM_HandlerForOOMError handler)](#oh_jsvm_sethandlerforoomerror) | Set Handler For OOM Error. If this function is invoked repeatedly, only the last time takes effect. When handler is null, the previous setting is canceled. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetDebugOption(JSVM_Env env, JSVM_DebugOption debugOption, bool isEnabled)](#oh_jsvm_setdebugoption) | This API is used to enable/disable the given debug option for a certain JSVM_Env. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForFatalError(JSVM_VM vm, JSVM_HandlerForFatalError handler)](#oh_jsvm_sethandlerforfatalerror) | Set Handler For Fatal Error. If this function is invoked repeatedly, only the last time takes effect. When handler is null, the previous setting is canceled. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForPromiseReject(JSVM_VM vm, JSVM_HandlerForPromiseReject handler)](#oh_jsvm_sethandlerforpromisereject) | Set Handler For Promise Reject. If this function is invoked repeatedly, only the last time takes effect. When handler is null, the previous setting is canceled. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithOptions(JSVM_Env env, const char* utf8name, size_t length, JSVM_Callback constructor, size_t propertyCount, const JSVM_PropertyDescriptor* properties, JSVM_Value parentClass, size_t option_count, JSVM_DefineClassOptions options[], JSVM_Value* result)](#oh_jsvm_defineclasswithoptions) | When wrapping a C++ class, the C++ constructor callback passed via constructor should be a static method on the class that calls the actual class constructor, then wraps the new C++ instance in a JavaScript object according to the different Options passed in, and returns the wrapper object. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_AddHandlerForGC(JSVM_VM vm, JSVM_CBTriggerTimeForGC triggerTime, JSVM_HandlerForGC handler, JSVM_GCType gcType, void* userData)](#oh_jsvm_addhandlerforgc) | Add VM GC Callback. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RemoveHandlerForGC(JSVM_VM vm, JSVM_CBTriggerTimeForGC triggerTime, JSVM_HandlerForGC handler, void* userData)](#oh_jsvm_removehandlerforgc) | Remove VM GC Callback. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_BackgroundDeserialize(JSVM_VM vm, JSVM_CodeCache cacheData, JSVM_DeserializeResult* result)](#oh_jsvm_backgrounddeserialize) | Deserialize JavaScript code cache in thread pool, and release JSVM_DeserializeResult with OH_JSVM_ReleaseDeserializeResult. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseDeserializeResult(JSVM_DeserializeResult result)](#oh_jsvm_releasedeserializeresult) | Release deserialize result. |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayBufferFromExternalMemory(JSVM_Env env, void* externalData, size_t byteLength, JSVM_FinalizeArrayBuffer finalizeCb, void* finalizeHint, bool* copied, JSVM_Value* result)](#oh_jsvm_createarraybufferfromexternalmemory) | Creates a JavaScript ArrayBuffer whose content is initialized from user-provided external memory. The implementation may either directly reference the external memory (zero-copy) or copy the data into an internally managed buffer, depending on engine implementation.<br> When zero-copy is used, the ArrayBuffer directly references the external memory. The caller must NOT free it before the finalize callback is invoked.<br> When a copy occurs, the data is copied into engine-managed memory. The copied output parameter is set to true so the caller knows their memory is no longer referenced. The resulting ArrayBuffer's data pointer (from OH_JSVM_GetArraybufferInfo) will differ from externalData. |

## Function description

### OH_JSVM_Init()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Init(const JSVM_InitOptions* options)
```

**Description**

Init a JavaScript vm.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const JSVM_InitOptions* options | The options for initialize the JavaScript VM. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the API succeeded. \n<br>        {@link JSVM_GENERIC_FAILURE } If the execution fails, it means that the current process has completed                                        JSVM initialization and there is no need to repeat the execution.\n |

### OH_JSVM_CreateVM()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateVM(const JSVM_CreateVMOptions* options, JSVM_VM* result)
```

**Description**

This API create a new VM instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const JSVM_CreateVMOptions* options | The options for create the VM instance. |
| JSVM_VM* result | The new VM instance. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } If the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } if the any of the input arguments is NULL. \n |

### OH_JSVM_SetMicrotaskPolicy()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetMicrotaskPolicy(JSVM_VM vm, JSVM_MicrotaskPolicy policy)
```

**Description**

This function controls how Microtasks are invoked of the vm. If the method is not called, the default microtask policy of vm is JSVM_MicrotaskPolicy::JSVM_MICROTASK_AUTO.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM instance to set mircrotasks policy. |
| JSVM_MicrotaskPolicy policy | Policy for running microtasks. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } If the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } If `vm` is NULL or `policy` is out of range.\n |

### OH_JSVM_DestroyVM()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DestroyVM(JSVM_VM vm)
```

**Description**

Destroys VM instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM instance to be Destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } If the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } If `vm` is NULL.\n |

### OH_JSVM_CreateProxy()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateProxy(JSVM_Env env, JSVM_Value target, JSVM_Value handler, JSVM_Value* result)
```

**Description**

This API allocates a default JavaScript Proxy. It is the equivalent of doing new Proxy(target, handler) in JavaScript.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value target | A JSVM_Value representing the JavaScript Object which you want to proxy. |
| JSVM_Value handler | A JSVM_Value representing the JavaScript Object that defines which operations will be intercepted and how to redefine intercepted operations. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript Proxy. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code.          {@link JSVM_OK } if the API succeeded. \n<br>        {@link JSVM_INVALID_ARG } if the any of the input arguments is NULL. \n<br>        {@link JSVM_OBJECT_EXPECTED} if target or handler is not Javascript Object. \n<br>        {@link JSVM_PENDING_EXCEPTION} if an exception occurs. \n |

### OH_JSVM_IsProxy()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsProxy(JSVM_Env env, JSVM_Value value, bool* isProxy)
```

**Description**

This API checks if the value passed in is a Proxy.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isProxy | Whether the given value is Proxy. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code.          {@link JSVM_OK } if the API succeeded. \n<br>        {@link JSVM_INVALID_ARG } if the any of the input arguments is NULL. \n |

### OH_JSVM_ProxyGetTarget()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ProxyGetTarget(JSVM_Env env, JSVM_Value value, JSVM_Value* result)
```

**Description**

This API gets target from proxy.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript Proxy whose target to return. |
| JSVM_Value* result | Target of the given proxy. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code.          {@link JSVM_OK } if the API succeeded. \n<br>        {@link JSVM_INVALID_ARG } if the any of the input arguments is NULL. \n<br>        {@link JSVM_INVALID_TYPE} if value is not a Javascript Proxy. \n |

### OH_JSVM_OpenVMScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenVMScope(JSVM_VM vm, JSVM_VMScope* result)
```

**Description**

This API open a new VM scope for the VM instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM instance to open scope for. |
| JSVM_VMScope* result | The new VM scope. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CloseVMScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseVMScope(JSVM_VM vm, JSVM_VMScope scope)
```

**Description**

This function close the VM scope for the VM instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM instance to close scope for. |
| JSVM_VMScope scope | The VM scope to be closed. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateEnv()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnv(JSVM_VM vm, size_t propertyCount, const JSVM_PropertyDescriptor* properties, JSVM_Env* result)
```

**Description**

This function create a new environment with optional properties for the context of the new environment.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM instance that the env will be created in. |
| size_t propertyCount | The number of elements in the properties array. |
| const JSVM_PropertyDescriptor* properties | The array of property descriptor. |
| JSVM_Env* result | The new environment created. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateEnvFromSnapshot()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnvFromSnapshot(JSVM_VM vm, size_t index, JSVM_Env* result)
```

**Description**

This function create a new environment from the start snapshot of the vm.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM instance that the env will be created in. |
| size_t index | The index of the environment in the snapshot. |
| JSVM_Env* result | The new environment created. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } If the function executed successfully.\n<br>        Returns {@link JSVM_GENERIC_FAILURE } If the snapshot context for `index` could not be created.\n |

### OH_JSVM_DestroyEnv()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DestroyEnv(JSVM_Env env)
```

**Description**

This function destroys the environment.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment to be destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_OpenEnvScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenEnvScope(JSVM_Env env, JSVM_EnvScope* result)
```

**Description**

This function open a new environment scope.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| JSVM_EnvScope* result | The new environment scope. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CloseEnvScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseEnvScope(JSVM_Env env, JSVM_EnvScope scope)
```

**Description**

This function closes the environment scope of the environment.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| JSVM_EnvScope scope | The environment scope to be closed. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetVM()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetVM(JSVM_Env env, JSVM_VM* result)
```

**Description**

This function retrieves the VM instance of the given environment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| JSVM_VM* result | The VM instance of the environment. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } in all cases.\n |

### OH_JSVM_CompileScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScript(JSVM_Env env, JSVM_Value script, const uint8_t* cachedData, size_t cacheDataLength, bool eagerCompile, bool* cacheRejected, JSVM_Script* result)
```

**Description**

This function compiles a string of JavaScript code and returns the compiled script.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| JSVM_Value script | A JavaScript string containing the script yo be compiled. |
| const uint8_t* cachedData | Optional code cache data for the script. |
| size_t cacheDataLength | The length of cachedData array. |
| bool eagerCompile | Whether to compile the script eagerly. |
| bool* cacheRejected | Whether the code cache rejected by compilation. |
| JSVM_Script* result | The compiled script. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } If the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } if the any of the input arguments is NULL. \n<br>        Returns {@link JSVM_STRING_EXPECTED } If `script` is not a string.\n<br>        Returns {@link JSVM_GENERIC_FAILURE } If compilation failed (e.g. compiler returned empty).\n<br>        Returns {@link JSVM_CANNOT_RUN_JS} if an exception occurs. \n<br>        Returns {@link JSVM_PENDING_EXCEPTION} if an exception occurs. \n |

### OH_JSVM_CompileScriptWithOrigin()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOrigin(JSVM_Env env, JSVM_Value script, const uint8_t* cachedData, size_t cacheDataLength, bool eagerCompile, bool* cacheRejected, JSVM_ScriptOrigin* origin, JSVM_Script* result)
```

**Description**

This function compiles a string of JavaScript code with the source code information and returns the compiled script.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| JSVM_Value script | A JavaScript string containing the script to be compiled. |
| const uint8_t* cachedData | Optional code cache data for the script. |
| size_t cacheDataLength | The length of cachedData array. |
| bool eagerCompile | Whether to compile the script eagerly. |
| bool* cacheRejected | Whether the code cache rejected by compilation. |
| JSVM_ScriptOrigin* origin | The information of source code. |
| JSVM_Script* result | The compiled script. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } If the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } if the any of the input arguments is NULL. \n<br>        Returns {@link JSVM_STRING_EXPECTED } If `script` is not a string.\n<br>        Returns {@link JSVM_GENERIC_FAILURE } If compilation failed.\n<br>        Returns {@link JSVM_CANNOT_RUN_JS} if an exception occurs. \n<br>        Returns {@link JSVM_PENDING_EXCEPTION} if an exception occurs. \n |

### OH_JSVM_CreateCodeCache()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateCodeCache(JSVM_Env env, JSVM_Script script, const uint8_t** data, size_t* length)
```

**Description**

This function creates code cache for the compiled script.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| JSVM_Script script | A compiled script to create code cache for. |
| const uint8_t** data | The data of the code cache. |
| size_t* length | The length of the code cache data. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_RunScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RunScript(JSVM_Env env, JSVM_Script script, JSVM_Value* result)
```

**Description**

This function executes a string of JavaScript code and returns its result with the following caveats: Unlike eval, this function does not allow the script to access the current lexical scope, and therefore also does not allow to access the module scope, meaning that pseudo-globals such as require will not be available. The script can access the global scope. Function and var declarations in the script will be added to the global object. Variable declarations made using let and const will be visible globally, but will not be added to the global object.The value of this is global within the script.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Script script | A JavaScript string containing the script to execute. |
| JSVM_Value* result | The value resulting from having executed the script. |

### OH_JSVM_SetInstanceData()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetInstanceData(JSVM_Env env, void* data, JSVM_Finalize finalizeCb, void* finalizeHint)
```

**Description**

This API associates data with the currently running JSVM environment. data can later be retrieved using OH_JSVM_GetInstanceData().

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| void* data | The data item to make available to bindings of this instance. |
| JSVM_Finalize finalizeCb | The function to call when the environment is being torn down. The function receives data so that it might free it. JSVM_Finalize provides more details. |
| void* finalizeHint | Optional hint to pass to the finalize callback during collection. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetInstanceData()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetInstanceData(JSVM_Env env, void** data)
```

**Description**

This API retrieves data that was previously associated with the currently running JSVM environment via OH_JSVM_SetInstanceData(). If no data is set, the call will succeed and data will be set to NULL.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| void** data | The data item that was previously associated with the currently running JSVM environment by a call to OH_JSVM_SetInstanceData(). |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetLastErrorInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetLastErrorInfo(JSVM_Env env, const JSVM_ExtendedErrorInfo** result)
```

**Description**

This API retrieves a JSVM_ExtendedErrorInfo structure with information about the last error that occurred.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| const JSVM_ExtendedErrorInfo** result | The JSVM_ExtendedErrorInfo structure with more information about the error. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_Throw()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Throw(JSVM_Env env, JSVM_Value error)
```

**Description**

This API throws the JavaScript value provided.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value error | The JavaScript value to be thrown. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ThrowError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowError(JSVM_Env env, const char* code, const char* msg)
```

**Description**

This API throws a JavaScript Error with the text provided.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* code | Optional error code to be set on the error. |
| const char* msg | C string representing the text to be associated with the error. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ThrowTypeError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowTypeError(JSVM_Env env, const char* code, const char* msg)
```

**Description**

This API throws a JavaScript TypeError with the text provided.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* code | Optional error code to be set on the error. |
| const char* msg | C string representing the text to be associated with the error. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ThrowRangeError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowRangeError(JSVM_Env env, const char* code, const char* msg)
```

**Description**

This API throws a JavaScript RangeError with the text provided.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* code | Optional error code to be set on the error. |
| const char* msg | C string representing the text to be associated with the error. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ThrowSyntaxError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowSyntaxError(JSVM_Env env, const char* code, const char* msg)
```

**Description**

This API throws a JavaScript SyntaxError with the text provided.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* code | Optional error code to be set on the error. |
| const char* msg | C string representing the text to be associated with the error. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsError(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

This API queries a JSVM_Value to check if it represents an error object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JSVM_Value to be checked. |
| bool* result | Boolean value that is set to true if JSVM_Value represents an error, false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateError(JSVM_Env env, JSVM_Value code, JSVM_Value msg, JSVM_Value* result)
```

**Description**

This API returns a JavaScript Error with the text provided.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value code | Optional JSVM_Value with the string for the error code to be associated with the error. |
| JSVM_Value msg | JSVM_Value that references a JavaScript string to be used as the message for the Error. |
| JSVM_Value* result | JSVM_Value representing the error created. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateTypeError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypeError(JSVM_Env env, JSVM_Value code, JSVM_Value msg, JSVM_Value* result)
```

**Description**

This API returns a JavaScript TypeError with the text provided.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value code | Optional JSVM_Value with the string for the error code to be associated with the error. |
| JSVM_Value msg | JSVM_Value that references a JavaScript string to be used as the message for the Error. |
| JSVM_Value* result | JSVM_Value representing the error created. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateRangeError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateRangeError(JSVM_Env env, JSVM_Value code, JSVM_Value msg, JSVM_Value* result)
```

**Description**

This API returns a JavaScript RangeError with the text provided.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value code | Optional JSVM_Value with the string for the error code to be associated with the error. |
| JSVM_Value msg | JSVM_Value that references a JavaScript string to be used as the message for the Error. |
| JSVM_Value* result | JSVM_Value representing the error created. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateSyntaxError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSyntaxError(JSVM_Env env, JSVM_Value code, JSVM_Value msg, JSVM_Value* result)
```

**Description**

This API returns a JavaScript SyntaxError with the text provided.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value code | Optional JSVM_Value with the string for the error code to be associated with the error. |
| JSVM_Value msg | JSVM_Value that references a JavaScript string to be used as the message for the Error. |
| JSVM_Value* result | JSVM_Value representing the error created. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetAndClearLastException()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetAndClearLastException(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns a JavaScript exception if one is pending, NULL otherwise.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The exception if one is pending, NULL otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsExceptionPending()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsExceptionPending(JSVM_Env env, bool* result)
```

**Description**

This API returns true if an exception is pending, false otherwise.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| bool* result | Boolean value that is set to true if an exception is pending. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_OpenHandleScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenHandleScope(JSVM_Env env, JSVM_HandleScope* result)
```

**Description**

This API opens a new scope.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_HandleScope* result | JSVM_Value representing the new scope. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CloseHandleScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseHandleScope(JSVM_Env env, JSVM_HandleScope scope)
```

**Description**

This API closes the scope passed in. Scopes must be closed in the reverse order from which they were created.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_HandleScope scope | JSVM_Value representing the scope to be closed. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_OpenEscapableHandleScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenEscapableHandleScope(JSVM_Env env, JSVM_EscapableHandleScope* result)
```

**Description**

This API opens a new scope from which one object can be promoted to the outer scope.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_EscapableHandleScope* result | JSVM_Value representing the new scope. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CloseEscapableHandleScope()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseEscapableHandleScope(JSVM_Env env, JSVM_EscapableHandleScope scope)
```

**Description**

This API closes the scope passed in. Scopes must be closed in the reverse order from which they were created.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_EscapableHandleScope scope | JSVM_Value representing the scope to be closed. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_EscapeHandle()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_EscapeHandle(JSVM_Env env, JSVM_EscapableHandleScope scope, JSVM_Value escapee, JSVM_Value* result)
```

**Description**

This API promotes the handle to the JavaScript object so that it is valid for the lifetime of the outer scope. It can only be called once per scope. If it is called more than once an error will be returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_EscapableHandleScope scope | JSVM_Value representing the current scope. |
| JSVM_Value escapee | JSVM_Value representing the JavaScript Object to be escaped. |
| JSVM_Value* result | JSVM_Value representing the handle to the escaped Object in the outer scope. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateReference()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateReference(JSVM_Env env, JSVM_Value value, uint32_t initialRefcount, JSVM_Ref* result)
```

**Description**

This API creates a new reference with the specified reference count to the value passed in.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JSVM_Value for which a reference is being created. |
| uint32_t initialRefcount | Initial reference count for the new reference. |
| JSVM_Ref* result | JSVM_Ref pointing to the new reference. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_DeleteReference()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteReference(JSVM_Env env, JSVM_Ref ref)
```

**Description**

his API deletes the reference passed in.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Ref ref | JSVM_Ref to be deleted. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ReferenceRef()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceRef(JSVM_Env env, JSVM_Ref ref, uint32_t* result)
```

**Description**

his API increments the reference count for the reference passed in and returns the resulting reference count.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Ref ref | JSVM_Ref for which the reference count will be incremented. |
| uint32_t* result | The new reference count. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ReferenceUnref()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceUnref(JSVM_Env env, JSVM_Ref ref, uint32_t* result)
```

**Description**

This API decrements the reference count for the reference passed in and returns the resulting reference count.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Ref ref | JSVM_Ref for which the reference count will be decremented. |
| uint32_t* result | The new reference count. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetReferenceValue()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceValue(JSVM_Env env, JSVM_Ref ref, JSVM_Value* result)
```

**Description**

If still valid, this API returns the JSVM_Value representing the JavaScript value associated with the JSVM_Ref. Otherwise, result will be NULL.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Ref ref | The JSVM_Ref for which the corresponding value is being requested. |
| JSVM_Value* result | The JSVM_Value referenced by the JSVM_Ref. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateArray()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArray(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns a JSVM-API value corresponding to a JavaScript Array type.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript Array. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateArrayWithLength()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayWithLength(JSVM_Env env, size_t length, JSVM_Value* result)
```

**Description**

This API returns a JSVM-API value corresponding to a JavaScript Array type. The Array's length property is set to the passed-in length parameter. However, the underlying buffer is not guaranteed to be pre-allocated by the VM when the array is created. That behavior is left to the underlying VM implementation.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| size_t length | The initial length of the Array. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript Array. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateArraybuffer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArraybuffer(JSVM_Env env, size_t byteLength, void** data, JSVM_Value* result)
```

**Description**

This API returns a JSVM-API value corresponding to a JavaScript ArrayBuffer. ArrayBuffers are used to represent fixed-length binary data buffers. They are normally used as a backing-buffer for TypedArray objects. The ArrayBuffer allocated will have an underlying byte buffer whose size is determined by the length parameter that's passed in. The underlying buffer is optionally returned back to the caller in case the caller wants to directly manipulate the buffer. This buffer can only be written to directly from native code. To write to this buffer from JavaScript, a typed array or DataView object would need to be created.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| size_t byteLength | The length in bytes of the array buffer to create. |
| void** data | Pointer to the underlying byte buffer of the ArrayBuffer.data can optionally be ignored by passing NULL. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript Array. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_AllocateArrayBufferBackingStoreData()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_AllocateArrayBufferBackingStoreData(size_t byteLength, JSVM_InitializedFlag initialized, void **data)
```

**Description**

This API allocate the memory of array buffer backing store.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t byteLength | size of backing store memory. |
| JSVM_InitializedFlag initialized | initialization status of the backing store memory. |
| void **data | pointer that receive the backing store memory pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if allocation succeed.\n<br>        Returns {@link JSVM_INVALID_ARG } if data is null pointer.\n<br>        Returns {@link JSVM_GENERIC_FAILURE } if allocation failed.\n |

### OH_JSVM_FreeArrayBufferBackingStoreData()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_FreeArrayBufferBackingStoreData(void* data)
```

**Description**

This API release the memory of an array buffer backing store.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| void* data | pointer to the backing store memory. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if run succeed.\n<br>        Returns {@link JSVM_INVALID_ARG } if data is null pointer.\n |

### OH_JSVM_CreateArrayBufferFromBackingStoreData()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayBufferFromBackingStoreData(JSVM_Env env, void* data, size_t backingStoreSize, size_t offset, size_t arrayBufferSize, JSVM_Value* result)
```

**Description**

This API create an array buffer using the backing store data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| void* data | pointer to the backing store memory. |
| size_t backingStoreSize | size of backing store memory. |
| size_t offset | start position of the array buffer in the backing store memory. |
| size_t arrayBufferSize | size of the array buffer. |
| JSVM_Value* result | pointer that receive the array buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if creation succeed.\n<br>        Returns {@link JSVM_INVALID_ARG } if any of the following condition reached:\n          1. offset + arrayBufferSize > backingStoreSize\n          2. backingStoreSize or arrayBufferSize equals zero          3. data or result is null pointer |

### OH_JSVM_CreateDate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDate(JSVM_Env env, double time, JSVM_Value* result)
```

**Description**

This API does not observe leap seconds; they are ignored, as ECMAScript aligns with POSIX time specification. This API allocates a JavaScript Date object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| double time | ECMAScript time value in milliseconds since 01 January, 1970 UTC. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript Date. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateExternal()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternal(JSVM_Env env, void* data, JSVM_Finalize finalizeCb, void* finalizeHint, JSVM_Value* result)
```

**Description**

This API allocates a JavaScript value with external data attached to it. This is used to pass external data through JavaScript code, so it can be retrieved later by native code using OH_JSVM_GetValueExternal. The API adds a JSVM_Finalize callback which will be called when the JavaScript object just created has been garbage collected.The created value is not an object, and therefore does not support additional properties. It is considered a distinct value type calling OH_JSVM_Typeof() with an external value yields JSVM_EXTERNAL.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| void* data | Raw pointer to the external data. |
| JSVM_Finalize finalizeCb | Optional callback to call when the external value is being collected. JSVM_Finalize provides more details. |
| void* finalizeHint | Optional hint to pass to the finalize callback during collection. |
| JSVM_Value* result | A JSVM_Value representing an external value. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateObject(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API allocates a default JavaScript Object. It is the equivalent of doing new Object() in JavaScript.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result |  A JSVM_Value representing a JavaScript Object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateSymbol()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSymbol(JSVM_Env env, JSVM_Value description, JSVM_Value* result)
```

**Description**

This API creates a JavaScript symbol value from a UTF8-encoded C string.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value description | Optional JSVM_Value which refers to a JavaScript string to be set as the description for the symbol. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript symbol. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_SymbolFor()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SymbolFor(JSVM_Env env, const char* utf8description, size_t length, JSVM_Value* result)
```

**Description**

This API searches in the global registry for an existing symbol with the given description. If the symbol already exists it will be returned, otherwise a new symbol will be created in the registry.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* utf8description | UTF-8 C string representing the text to be used as the description for the symbol. |
| size_t length | The length of the description string in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript symbol. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateTypedarray()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypedarray(JSVM_Env env, JSVM_TypedarrayType type, size_t length, JSVM_Value arraybuffer, size_t byteOffset, JSVM_Value* result)
```

**Description**

This API creates a JavaScript TypedArray object over an existing ArrayBuffer. TypedArray objects provide an array-like view over an underlying data buffer where each element has the same underlying binary scalar datatype.It's required that (length * size_of_element) + byte_offset should be <= the size in bytes of the array passed in. If not, a RangeError exception is raised.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_TypedarrayType type | Scalar datatype of the elements within the TypedArray. |
| size_t length | Number of elements in the TypedArray. |
| JSVM_Value arraybuffer | ArrayBuffer underlying the typed array. |
| size_t byteOffset | The byte offset within the ArrayBuffer from which to start projecting the TypedArray. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript TypedArray |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateDataview()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataview(JSVM_Env env, size_t length, JSVM_Value arraybuffer, size_t byteOffset, JSVM_Value* result)
```

**Description**

This API creates a JavaScript DataView object over an existing ArrayBuffer. DataView objects provide an array-like view over an underlying data buffer, but one which allows items of different size and type in the ArrayBuffer.It is required that byte_length + byte_offset is less than or equal to the size in bytes of the array passed in. If not, a RangeError exception is raised.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| size_t length | Number of elements in the DataView. |
| JSVM_Value arraybuffer | ArrayBuffer underlying the DataView. |
| size_t byteOffset | The byte offset within the ArrayBuffer from which to start projecting the DataView. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript DataView. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateInt32()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt32(JSVM_Env env, int32_t value, JSVM_Value* result)
```

**Description**

This API is used to convert from the C int32_t type to the JavaScript number type.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| int32_t value | Integer value to be represented in JavaScript. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript number. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateUint32()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateUint32(JSVM_Env env, uint32_t value, JSVM_Value* result)
```

**Description**

This API is used to convert from the C uint32_t type to the JavaScript number type.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| uint32_t value | Unsigned integer value to be represented in JavaScript. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript number. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateInt64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt64(JSVM_Env env, int64_t value, JSVM_Value* result)
```

**Description**

This API is used to convert from the C int64_t type to the JavaScript number type.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| int64_t value | Integer value to be represented in JavaScript. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript number. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateDouble()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDouble(JSVM_Env env, double value, JSVM_Value* result)
```

**Description**

This API is used to convert from the C double type to the JavaScript number type.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| double value | Double-precision value to be represented in JavaScript. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript number. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateBigintInt64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintInt64(JSVM_Env env, int64_t value, JSVM_Value* result)
```

**Description**

This API converts the C int64_t type to the JavaScript BigInt type.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| int64_t value | Integer value to be represented in JavaScript. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript BigInt. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateBigintUint64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintUint64(JSVM_Env env, uint64_t value, JSVM_Value* result)
```

**Description**

This API converts the C uint64_t type to the JavaScript BigInt type.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| uint64_t value | Unsigned integer value to be represented in JavaScript. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript BigInt. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateBigintWords()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintWords(JSVM_Env env, int signBit, size_t wordCount, const uint64_t* words, JSVM_Value* result)
```

**Description**

This API converts an array of unsigned 64-bit words into a single BigInt value. The resulting BigInt is calculated as (–1)sign_bit (words[0] × (264)0 + words[1] × (264)1 + …)

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| int signBit | Determines if the resulting BigInt will be positive or negative. |
| size_t wordCount | The length of the words array. |
| const uint64_t* words | An array of uint64_t little-endian 64-bit words. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript BigInt. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateStringLatin1()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringLatin1(JSVM_Env env, const char* str, size_t length, JSVM_Value* result)
```

**Description**

This API creates a JavaScript string value from an ISO-8859-1-encoded C string. The native string is copied.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* str | Character buffer representing an ISO-8859-1-encoded string. |
| size_t length | The length of the string in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript string. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateStringUtf16()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf16(JSVM_Env env, const char16_t* str, size_t length, JSVM_Value* result)
```

**Description**

This API creates a JavaScript string value from a UTF16-LE-encoded C string. The native string is copied.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char16_t* str | Character buffer representing a UTF16-LE-encoded string. |
| size_t length | The length of the string in two-byte code units, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript string. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateStringUtf8()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf8(JSVM_Env env, const char* str, size_t length, JSVM_Value* result)
```

**Description**

This API creates a JavaScript string value from a UTF8-encoded C string. The native string is copied.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* str | Character buffer representing a UTF8-encoded string. |
| size_t length | The length of the string in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript string. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetArrayLength()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetArrayLength(JSVM_Env env, JSVM_Value value, uint32_t* result)
```

**Description**

This API returns the length of an array.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing the JavaScript Array whose length is being queried. |
| uint32_t* result | uint32 representing length of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetArraybufferInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetArraybufferInfo(JSVM_Env env, JSVM_Value arraybuffer, void** data, size_t* byteLength)
```

**Description**

This API is used to retrieve the underlying data buffer of an ArrayBuffer and its length.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value arraybuffer | JSVM_Value representing the ArrayBuffer being queried. |
| void** data | The underlying data buffer of the ArrayBuffer. If byte_length is 0, this may be NULL or any other pointer value. |
| size_t* byteLength | Length in bytes of the underlying data buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetPrototype()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetPrototype(JSVM_Env env, JSVM_Value object, JSVM_Value* result)
```

**Description**

This API returns the length of an array.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | JSVM_Value representing JavaScript Object whose prototype to return. This returns the equivalent of Object.getPrototypeOf (which is not the same as the function's prototype property). |
| JSVM_Value* result | JSVM_Value representing prototype of the given object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetTypedarrayInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetTypedarrayInfo(JSVM_Env env, JSVM_Value typedarray, JSVM_TypedarrayType* type, size_t* length, void** data, JSVM_Value* arraybuffer, size_t* byteOffset)
```

**Description**

This API returns various properties of a typed array.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value typedarray | JSVM_Value representing the TypedArray whose properties to query. |
| JSVM_TypedarrayType* type | Scalar datatype of the elements within the TypedArray. |
| size_t* length | The number of elements in the TypedArray. |
| void** data | The data buffer underlying the TypedArray adjusted by the byte_offset value so that it points to the first element in the TypedArray. If the length of the array is 0, this may be NULL or any other pointer value. |
| JSVM_Value* arraybuffer | The ArrayBuffer underlying the TypedArray. |
| size_t* byteOffset | The byte offset within the underlying native array at which the first element of the arrays is located. The value for the data parameter has already been adjusted so that data points to the first element in the array. Therefore, the first byte of the native array would be at data - byte_offset. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetDataviewInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetDataviewInfo(JSVM_Env env, JSVM_Value dataview, size_t* bytelength, void** data, JSVM_Value* arraybuffer, size_t* byteOffset)
```

**Description**

Any of the out parameters may be NULL if that property is unneeded. This API returns various properties of a DataView.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value dataview | JSVM_Value representing the DataView whose properties to query. |
| size_t* bytelength | Number of bytes in the DataView. |
| void** data | The data buffer underlying the DataView. If byte_length is 0, this may be NULL or any other pointer value. |
| JSVM_Value* arraybuffer | ArrayBuffer underlying the DataView. |
| size_t* byteOffset | The byte offset within the data buffer from which to start projecting the DataView. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetDateValue()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetDateValue(JSVM_Env env, JSVM_Value value, double* result)
```

**Description**

Returns JSVM_OK if the function executed successfully. If a non-date JSVM_Value is passed in it returns JSVM_date_expected.This API returns the C double primitive of time value for the given JavaScript Date.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing a JavaScript Date. |
| double* result | Time value as a double represented as milliseconds since midnight at the beginning of 01 January, 1970 UTC. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_DATE_EXPECTED } If a non-date JSVM_Value is passed in it.\n |

### OH_JSVM_GetValueBool()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBool(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

This API returns the C boolean primitive equivalent of the given JavaScript Boolean.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript Boolean. |
| bool* result | C boolean primitive equivalent of the given JavaScript Boolean. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_BOOLEAN_EXPECTED }If a non-boolean JSVM_Value is passed in it.\n |

### OH_JSVM_GetValueDouble()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueDouble(JSVM_Env env, JSVM_Value value, double* result)
```

**Description**

This API returns the C double primitive equivalent of the given JavaScript number.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript number. |
| double* result | C double primitive equivalent of the given JavaScript number. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_NUMBER_EXPECTED } If a non-number JSVM_Value is passed in.\n |

### OH_JSVM_GetValueBigintInt64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintInt64(JSVM_Env env, JSVM_Value value, int64_t* result, bool* lossless)
```

**Description**

This API returns the C int64_t primitive equivalent of the given JavaScript BigInt. If needed it will truncate the value, setting lossless to false.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript BigInt. |
| int64_t* result | C int64_t primitive equivalent of the given JavaScript BigInt. |
| bool* lossless | Indicates whether the BigInt value was converted losslessly. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_BIGINT_EXPECTED } If a non-BigInt is passed in it.\n |

### OH_JSVM_GetValueBigintUint64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintUint64(JSVM_Env env, JSVM_Value value, uint64_t* result, bool* lossless)
```

**Description**

This API returns the C uint64_t primitive equivalent of the given JavaScript BigInt. If needed it will truncate the value, setting lossless to false.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript BigInt. |
| uint64_t* result | C uint64_t primitive equivalent of the given JavaScript BigInt. |
| bool* lossless | Indicates whether the BigInt value was converted losslessly. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_BIGINT_EXPECTED } If a non-BigInt is passed in it.\n |

### OH_JSVM_GetValueBigintWords()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintWords(JSVM_Env env, JSVM_Value value, int* signBit, size_t* wordCount, uint64_t* words)
```

**Description**

This API converts a single BigInt value into a sign bit, 64-bit little-endian array, and the number of elements in the array. signBit and words may be both set to NULL, in order to get only wordCount.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript BigInt. |
| int* signBit | Integer representing if the JavaScript BigInt is positive or negative. |
| size_t* wordCount | Must be initialized to the length of the words array. Upon return, it will be set to the actual number of words that would be needed to store this BigInt. |
| uint64_t* words | Pointer to a pre-allocated 64-bit word array. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetValueExternal()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueExternal(JSVM_Env env, JSVM_Value value, void** result)
```

**Description**

This API retrieves the external data pointer that was previously passed to OH_JSVM_CreateExternal().

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript external value. |
| void** result | Pointer to the data wrapped by the JavaScript external value. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } If a non-external JSVM_Value is passed in it.\n |

### OH_JSVM_GetValueInt32()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt32(JSVM_Env env, JSVM_Value value, int32_t* result)
```

**Description**

This API returns the C int32 primitive equivalent of the given JavaScript number.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript number. |
| int32_t* result | C int32 primitive equivalent of the given JavaScript number. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_NUMBER_EXPECTED } If a non-number JSVM_Value is passed in.\n |

### OH_JSVM_GetValueInt64()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt64(JSVM_Env env, JSVM_Value value, int64_t* result)
```

**Description**

This API returns the C int64 primitive equivalent of the given JavaScript number.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript number. |
| int64_t* result | C int64 primitive equivalent of the given JavaScript number. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_NUMBER_EXPECTED } If a non-number JSVM_Value is passed in.\n |

### OH_JSVM_GetValueStringLatin1()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringLatin1(JSVM_Env env, JSVM_Value value, char* buf, size_t bufsize, size_t* result)
```

**Description**

This API returns the ISO-8859-1-encoded string corresponding the value passed in.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript string. |
| char* buf | Buffer to write the ISO-8859-1-encoded string into. If NULL is passed in, the length of the string in bytes and excluding the null terminator is returned in result. |
| size_t bufsize | Size of the destination buffer. When this value is insufficient, the returned string is truncated and null-terminated. |
| size_t* result | Number of bytes copied into the buffer, excluding the null terminator. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_STRING_EXPECTED } If a non-string JSVM_Value is passed in.\n |

### OH_JSVM_GetValueStringUtf8()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf8(JSVM_Env env, JSVM_Value value, char* buf, size_t bufsize, size_t* result)
```

**Description**

This API returns the UTF8-encoded string corresponding the value passed in.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript string. |
| char* buf | Buffer to write the UTF8-encoded string into. If NULL is passed in, the length of the string in bytes and excluding the null terminator is returned in result. |
| size_t bufsize | Size of the destination buffer. When this value is insufficient, the returned string is truncated and null-terminated. |
| size_t* result | Number of bytes copied into the buffer, excluding the null terminator. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_STRING_EXPECTED } If a non-string JSVM_Value is passed in.\n |

### OH_JSVM_GetValueStringUtf16()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf16(JSVM_Env env, JSVM_Value value, char16_t* buf, size_t bufsize, size_t* result)
```

**Description**

This API returns the UTF16-encoded string corresponding the value passed in.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript string. |
| char16_t* buf | Buffer to write the UTF16-LE-encoded string into. If NULL is passed in, the length of the string in 2-byte code units and excluding the null terminator is returned. |
| size_t bufsize | Size of the destination buffer. When this value is insufficient, the returned string is truncated and null-terminated. |
| size_t* result | Number of 2-byte code units copied into the buffer, excluding the null terminator. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_STRING_EXPECTED } If a non-string JSVM_Value is passed in.\n |

### OH_JSVM_GetValueUint32()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueUint32(JSVM_Env env, JSVM_Value value, uint32_t* result)
```

**Description**

This API returns the C primitive equivalent of the given JSVM_Value as a uint32_t.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | JSVM_Value representing JavaScript number. |
| uint32_t* result | C primitive equivalent of the given JSVM_Value as a uint32_t. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_NUMBER_EXPECTED } If a non-number JSVM_Value is passed in it.\n |

### OH_JSVM_GetBoolean()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetBoolean(JSVM_Env env, bool value, JSVM_Value* result)
```

**Description**

This API is used to return the JavaScript singleton object that is used to represent the given boolean value.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| bool value | The value of the boolean to retrieve. |
| JSVM_Value* result | JSVM_Value representing JavaScript Boolean singleton to retrieve. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetGlobal()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetGlobal(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the global object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | JSVM_Value representing JavaScript global object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetNull()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetNull(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the null object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | JSVM_Value representing JavaScript null object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetUndefined()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetUndefined(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Undefined object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | JSVM_Value representing JavaScript Undefined value. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CoerceToBool()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBool(JSVM_Env env, JSVM_Value value, JSVM_Value* result)
```

**Description**

This API implements the abstract operation ToBoolean()

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to coerce. |
| JSVM_Value* result | JSVM_Value representing the coerced JavaScript Boolean. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CoerceToNumber()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToNumber(JSVM_Env env, JSVM_Value value, JSVM_Value* result)
```

**Description**

This API implements the abstract operation ToNumber() as defined. This function potentially runs JS code if the passed-in value is an object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to coerce. |
| JSVM_Value* result | JSVM_Value representing the coerced JavaScript number. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CoerceToObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToObject(JSVM_Env env, JSVM_Value value, JSVM_Value* result)
```

**Description**

This API implements the abstract operation ToObject().

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to coerce. |
| JSVM_Value* result | JSVM_Value representing the coerced JavaScript Object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CoerceToString()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToString(JSVM_Env env, JSVM_Value value, JSVM_Value* result)
```

**Description**

This API implements the abstract operation ToString().This function potentially runs JS code if the passed-in value is an object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to coerce. |
| JSVM_Value* result | JSVM_Value representing the coerced JavaScript string. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_Typeof()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Typeof(JSVM_Env env, JSVM_Value value, JSVM_ValueType* result)
```

**Description**

This API represents behavior similar to invoking the typeof Operator on the object as defined. However, there are some differences:It has support for detecting an External value.It detects null as a separate type, while ECMAScript typeof would detect object.If value has a type that is invalid, an error is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value whose type to query. |
| JSVM_ValueType* result | The type of the JavaScript value. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_Instanceof()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Instanceof(JSVM_Env env, JSVM_Value object, JSVM_Value constructor, bool* result)
```

**Description**

This API represents invoking the instanceof Operator on the object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The JavaScript value to check. |
| JSVM_Value constructor | The JavaScript function object of the constructor function to check against. |
| bool* result | Boolean that is set to true if object instanceof constructor is true. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsArray()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsArray(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

This API represents invoking the IsArray operation on the object

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given object is an array. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsArraybuffer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsArraybuffer(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

This API checks if the Object passed in is an array buffer.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given object is an ArrayBuffer. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsDate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsDate(JSVM_Env env, JSVM_Value value, bool* isDate)
```

**Description**

This API checks if the Object passed in is a date.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isDate | Whether the given JSVM_Value represents a JavaScript Date object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsTypedarray()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsTypedarray(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

This API checks if the Object passed in is a typed array.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given JSVM_Value represents a TypedArray. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsDataview()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsDataview(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

This API checks if the Object passed in is a DataView.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given JSVM_Value represents a DataView. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_StrictEquals()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_StrictEquals(JSVM_Env env, JSVM_Value lhs, JSVM_Value rhs, bool* result)
```

**Description**

This API represents the invocation of the Strict Equality algorithm.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value lhs | The JavaScript value to check. |
| JSVM_Value rhs | The JavaScript value to check against. |
| bool* result | Whether the two JSVM_Value objects are equal. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_Equals()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Equals(JSVM_Env env, JSVM_Value lhs, JSVM_Value rhs, bool* result)
```

**Description**

This API represents the invocation of the Relaxed Equality algorithm. Returns true as long as the values are equal, regardless of type.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value lhs | The JavaScript value to check. |
| JSVM_Value rhs | The JavaScript value to check against. |
| bool* result | Whether the two JSVM_Value objects are relaxed equal. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_DetachArraybuffer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DetachArraybuffer(JSVM_Env env, JSVM_Value arraybuffer)
```

**Description**

This API represents the invocation of the ArrayBuffer detach operation.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value arraybuffer | The JavaScript ArrayBuffer to be detached. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED } If a non-detachable ArrayBuffer is passed in it.\n |

### OH_JSVM_IsDetachedArraybuffer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsDetachedArraybuffer(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

This API represents the invocation of the ArrayBuffer IsDetachedBuffer operation.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript ArrayBuffer to be checked. |
| bool* result | Whether the arraybuffer is detached. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetPropertyNames()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetPropertyNames(JSVM_Env env, JSVM_Value object, JSVM_Value* result)
```

**Description**

This API returns the names of the enumerable properties of object as an array of strings. The properties of object whose key is a symbol will not be included.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object from which to retrieve the properties. |
| JSVM_Value* result | A JSVM_Value representing an array of JavaScript values that represent the property names of the object. The API can be used to iterate over result using OH_JSVM_GetArrayLength and OH_JSVM_GetElement. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetAllPropertyNames()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetAllPropertyNames(JSVM_Env env, JSVM_Value object, JSVM_KeyCollectionMode keyMode, JSVM_KeyFilter keyFilter, JSVM_KeyConversion keyConversion, JSVM_Value* result)
```

**Description**

This API returns an array containing the names of the available properties of this object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object from which to retrieve the properties. |
| JSVM_KeyCollectionMode keyMode | Whether to retrieve prototype properties as well. |
| JSVM_KeyFilter keyFilter | Which properties to retrieve (enumerable/readable/writable). |
| JSVM_KeyConversion keyConversion | Whether to convert numbered property keys to strings. |
| JSVM_Value* result | A JSVM_Value representing an array of JavaScript values that represent the property names of the object. OH_JSVM_GetArrayLength and OH_JSVM_GetElement can be used to iterate over result. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_SetProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, JSVM_Value value)
```

**Description**

This API set a property on the Object passed in.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object on which to set the property. |
| JSVM_Value key | The name of the property to set. |
| JSVM_Value value | The property value. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, JSVM_Value* result)
```

**Description**

This API gets the requested property from the Object passed in.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object from which to retrieve the property. |
| JSVM_Value key | The name of the property to retrieve. |
| JSVM_Value* result | The value of the property. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_HasProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_HasProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, bool* result)
```

**Description**

This API checks if the Object passed in has the named property.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object to query. |
| JSVM_Value key | The name of the property whose existence to check. |
| bool* result | Whether the property exists on the object or not. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_DeleteProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, bool* result)
```

**Description**

This API attempts to delete the key own property from object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object to query. |
| JSVM_Value key | The name of the property to delete. |
| bool* result | Whether the property deletion succeeded or not. result can optionally be ignored by passing NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_HasOwnProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_HasOwnProperty(JSVM_Env env, JSVM_Value object, JSVM_Value key, bool* result)
```

**Description**

This API checks if the Object passed in has the named own property. key must be a string or a symbol, or an error will be thrown. JSVM-API will not perform any conversion between data types.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object to query. |
| JSVM_Value key | The name of the own property whose existence to check. |
| bool* result |  Whether the own property exists on the object or not. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_SetNamedProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetNamedProperty(JSVM_Env env, JSVM_Value object, const char* utf8name, JSVM_Value value)
```

**Description**

This method is equivalent to calling OH_JSVM_SetProperty with a JSVM_Value created from the string passed in as utf8name.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object on which to set the property. |
| const char* utf8name | The name of the property to set. |
| JSVM_Value value | The property value. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetNamedProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetNamedProperty(JSVM_Env env, JSVM_Value object, const char* utf8name, JSVM_Value* result)
```

**Description**

This method is equivalent to calling OH_JSVM_SetProperty with a JSVM_Value created from the string passed in as utf8name.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object from which to retrieve the property. |
| const char* utf8name | The name of the property to get. |
| JSVM_Value* result | The value of the property. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_HasNamedProperty()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_HasNamedProperty(JSVM_Env env, JSVM_Value object, const char* utf8name, bool* result)
```

**Description**

This method is equivalent to calling OH_JSVM_SetProperty with a JSVM_Value created from the string passed in as utf8name.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object to query. |
| const char* utf8name | The name of the property whose existence to check. |
| bool* result | Whether the property exists on the object or not. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_SetElement()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetElement(JSVM_Env env, JSVM_Value object, uint32_t index, JSVM_Value value)
```

**Description**

This API sets an element on the Object passed in.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object from which to set the properties. |
| uint32_t index | The index of the property to set. |
| JSVM_Value value | The property value. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetElement()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetElement(JSVM_Env env, JSVM_Value object, uint32_t index, JSVM_Value* result)
```

**Description**

This API gets the element at the requested index.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object from which to retrieve the property. |
| uint32_t index | The index of the property to get. |
| JSVM_Value* result | The value of the property. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_HasElement()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_HasElement(JSVM_Env env, JSVM_Value object, uint32_t index, bool* result)
```

**Description**

This API returns if the Object passed in has an element at the requested index.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object to query. |
| uint32_t index | The index of the property whose existence to check. |
| bool* result | Whether the property exists on the object or not. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_DeleteElement()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteElement(JSVM_Env env, JSVM_Value object, uint32_t index, bool* result)
```

**Description**

This API attempts to delete the specified index from object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object to query. |
| uint32_t index | The index of the property to delete. |
| bool* result | Whether the element deletion succeeded or not. result can optionally be ignored by passing NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_DefineProperties()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DefineProperties(JSVM_Env env, JSVM_Value object, size_t propertyCount, const JSVM_PropertyDescriptor* properties)
```

**Description**

This method allows the efficient definition of multiple properties on a given object. The properties are defined using property descriptors. Given an array of such property descriptors, this API will set the properties on the object one at a time, as defined by DefineOwnProperty().

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object from which to retrieve the properties. |
| size_t propertyCount | The number of elements in the properties array. |
| const JSVM_PropertyDescriptor* properties | The array of property descriptors. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ObjectFreeze()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectFreeze(JSVM_Env env, JSVM_Value object)
```

**Description**

This method freezes a given object. This prevents new properties from being added to it, existing properties from being removed, prevents changing the enumerability, configurability, or writability of existing properties, and prevents the values of existing properties from being changed. It also prevents the object's prototype from being changed.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object to freeze. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ObjectSeal()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSeal(JSVM_Env env, JSVM_Value object)
```

**Description**

This method seals a given object. This prevents new properties from being added to it, as well as marking all existing properties as non-configurable.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object to seal. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CallFunction()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CallFunction(JSVM_Env env, JSVM_Value recv, JSVM_Value func, size_t argc, const JSVM_Value* argv, JSVM_Value* result)
```

**Description**

This method allows a JavaScript function object to be called from a native add-on. This is the primary mechanism of calling back from the add-on's native code into JavaScript.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value recv | The this value passed to the called function. |
| JSVM_Value func | JSVM_Value representing the JavaScript function to be invoked. |
| size_t argc | The count of elements in the argv array. |
| const JSVM_Value* argv | Array of JSVM_values representing JavaScript values passed in as arguments to the function. |
| JSVM_Value* result | JSVM_Value representing the JavaScript object returned. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateFunction()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunction(JSVM_Env env, const char* utf8name, size_t length, JSVM_Callback cb, JSVM_Value* result)
```

**Description**

This API allows an add-on author to create a function object in native code. This is the primary mechanism to allow calling into the add-on's native code from JavaScript.The newly created function is not automatically visible from script after this call. Instead, a property must be explicitly set on any object that is visible to JavaScript, in order for the function to be accessible from script.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* utf8name | Optional name of the function encoded as UTF8. This is visible within JavaScript as the new function object's name property. |
| size_t length | The length of the utf8name in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Callback cb | The native function which should be called when this function object is invoked and data. JSVM_Callback provides more details. |
| JSVM_Value* result | JSVM_Value representing the JavaScript function object for the newly created function. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetCbInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetCbInfo(JSVM_Env env, JSVM_CallbackInfo cbinfo, size_t* argc, JSVM_Value* argv, JSVM_Value* thisArg, void** data)
```

**Description**

This method is used within a callback function to retrieve details about the call like the arguments and the this pointer from a given callback info.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_CallbackInfo cbinfo | The callback info passed into the callback function. |
| size_t* argc | Specifies the length of the provided argv array and receives the actual count of arguments. argc can optionally be ignored by passing NULL. |
| JSVM_Value* argv | C array of JSVM_values to which the arguments will be copied. If there are more arguments than the provided count, only the requested number of arguments are copied. If there are fewer arguments provided than claimed, the rest of argv is filled with JSVM_Value values that represent undefined. argv can optionally be ignored by passing NULL. |
| JSVM_Value* thisArg | Receives the JavaScript this argument for the call. thisArg can optionally be ignored by passing NULL. |
| void** data | Receives the data pointer for the callback. data can optionally be ignored by passing NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetNewTarget()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetNewTarget(JSVM_Env env, JSVM_CallbackInfo cbinfo, JSVM_Value* result)
```

**Description**

This API returns the new.target of the constructor call. If the current callback is not a constructor call, the result is NULL.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_CallbackInfo cbinfo | The callback info passed into the callback function. |
| JSVM_Value* result | The new.target of the constructor call. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_NewInstance()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_NewInstance(JSVM_Env env, JSVM_Value constructor, size_t argc, const JSVM_Value* argv, JSVM_Value* result)
```

**Description**

his method is used to instantiate a new JavaScript value using a given JSVM_Value that represents the constructor for the object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value constructor | JSVM_Value representing the JavaScript function to be invoked as a constructor. |
| size_t argc | The count of elements in the argv array. |
| const JSVM_Value* argv | Array of JavaScript values as JSVM_Value representing the arguments to the constructor. If argc is zero this parameter may be omitted by passing in NULL. |
| JSVM_Value* result | JSVM_Value representing the JavaScript object returned, which in this case is the constructed object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_DefineClass()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClass(JSVM_Env env, const char* utf8name, size_t length, JSVM_Callback constructor, size_t propertyCount, const JSVM_PropertyDescriptor* properties, JSVM_Value* result)
```

**Description**

When wrapping a C++ class, the C++ constructor callback passed via constructor should be a static method on the class that calls the actual class constructor, then wraps the new C++ instance in a JavaScript object, and returns the wrapper object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* utf8name | Name of the JavaScript constructor function. For clarity, it is recommended to use the C++ class name when wrapping a C++ class. |
| size_t length | The length of the utf8name in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Callback constructor | Struct include callback function that handles constructing instances of the class. When wrapping a C++ class, this method must be a static member with the JSVM_Callback.callback signature. A C++ class constructor cannot be used. Include Optional data to be passed to the constructor callback as the data property of the callback info. JSVM_Callback provides more details. |
| size_t propertyCount | Number of items in the properties array argument. |
| const JSVM_PropertyDescriptor* properties | Array of property descriptors describing static and instance data properties, accessors, and methods on the class See JSVM_PropertyDescriptor. |
| JSVM_Value* result | A JSVM_Value representing the constructor function for the class. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_Wrap()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Wrap(JSVM_Env env, JSVM_Value jsObject, void* nativeObject, JSVM_Finalize finalizeCb, void* finalizeHint, JSVM_Ref* result)
```

**Description**

Wraps a native instance in a JavaScript object. The native instance can be retrieved later using OH_JSVM_Unwrap().

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value jsObject | The JavaScript object that will be the wrapper for the native object. |
| void* nativeObject | The native instance that will be wrapped in the JavaScript object. |
| JSVM_Finalize finalizeCb | Optional native callback that can be used to free the native instance when the JavaScript object has been garbage-collected. |
| void* finalizeHint | Optional contextual hint that is passed to the finalize callback. properties, accessors, and methods on the class See JSVM_PropertyDescriptor. |
| JSVM_Ref* result | Optional reference to the wrapped object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_Unwrap()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_Unwrap(JSVM_Env env, JSVM_Value jsObject, void** result)
```

**Description**

When JavaScript code invokes a method or property accessor on the class, the corresponding JSVM_Callback is invoked. If the callback is for an instance method or accessor, then the this argument to the callback is the wrapper object; the wrapped C++ instance that is the target of the call can be obtained then by calling OH_JSVM_Unwrap() on the wrapper object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value jsObject | The object associated with the native instance. |
| void** result | Pointer to the wrapped native instance. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_RemoveWrap()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RemoveWrap(JSVM_Env env, JSVM_Value jsObject, void** result)
```

**Description**

Retrieves a native instance that was previously wrapped in the JavaScript object jsObject using OH_JSVM_Wrap() and removes the wrapping. If a finalize callback was associated with the wrapping, it will no longer be called when the JavaScript object becomes garbage-collected.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value jsObject | The object associated with the native instance. |
| void** result | Pointer to the wrapped native instance. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_TypeTagObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_TypeTagObject(JSVM_Env env, JSVM_Value value, const JSVM_TypeTag* typeTag)
```

**Description**

Associates the value of the typeTag pointer with the JavaScript object or external. OH_JSVM_CheckObjectTypeTag() can then be used to compare the tag that was attached to the object with one owned by the addon to ensure that the object has the right type. If the object already has an associated type tag, this API will return JSVM_INVALID_ARG.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript object or external to be marked. |
| const JSVM_TypeTag* typeTag | The tag with which the object is to be marked. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } If the object already has an associated type tag.\n |

### OH_JSVM_CheckObjectTypeTag()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CheckObjectTypeTag(JSVM_Env env, JSVM_Value value, const JSVM_TypeTag* typeTag, bool* result)
```

**Description**

Compares the pointer given as typeTag with any that can be found on js object. If no tag is found on js object or, if a tag is found but it does not match typeTag, then result is set to false. If a tag is found and it matches typeTag, then result is set to true.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript object or external whose type tag to examine. |
| const JSVM_TypeTag* typeTag | The tag with which to compare any tag found on the object. |
| bool* result | Whether the type tag given matched the type tag on the object. false is also returned if no type tag was found on the object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_AddFinalizer()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_AddFinalizer(JSVM_Env env, JSVM_Value jsObject, void* finalizeData, JSVM_Finalize finalizeCb, void* finalizeHint, JSVM_Ref* result)
```

**Description**

This API can be called multiple times on a single JavaScript object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value jsObject | The JavaScript object to which the native data will be attached. |
| void* finalizeData | Optional data to be passed to finalizeCb. |
| JSVM_Finalize finalizeCb | Native callback that will be used to free the native data when the JavaScript object has been garbage-collected. JSVM_Finalize provides more details. |
| void* finalizeHint | Optional contextual hint that is passed to the finalize callback. |
| JSVM_Ref* result | Optional reference to the JavaScript object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetVersion()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetVersion(JSVM_Env env, uint32_t* result)
```

**Description**

This API returns the highest JSVM-API version supported by the JSVM runtime.<br> JSVM-API is planned to be additive such that newer releases of JSVM may support additional API functions. In order to allow an addon to use a newer function when running with versions of JSVM that support it, while providing fallback behavior when running with JSVM versions that don't support it.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| uint32_t* result | The highest version of JSVM-API supported. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetVMInfo()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetVMInfo(JSVM_VMInfo* result)
```

**Description**

Return information of the VM.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VMInfo* result | The information of the VM. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_AdjustExternalMemory()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_AdjustExternalMemory(JSVM_Env env, int64_t changeInBytes, int64_t* result)
```

**Description**

This function gives V8 an indication of the amount of externally allocated memory that is kept alive by JavaScript objects (i.e. a JavaScript object that points to its own memory allocated by a native addon). Registering externally allocated memory will trigger global garbage collections more often than it would otherwise.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| int64_t changeInBytes | The change in externally allocated memory that is kept alive by JavaScript objects. |
| int64_t* result | The adjusted value |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_MemoryPressureNotification()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_MemoryPressureNotification(JSVM_Env env, JSVM_MemoryPressureLevel level)
```

**Description**

This function notifies the VM that the system is running low on memory and optionally triggers a garbage collection.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_MemoryPressureLevel level | The memory pressure level set to the current VM. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreatePromise()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreatePromise(JSVM_Env env, JSVM_Deferred* deferred, JSVM_Value* promise)
```

**Description**

This API creates a deferred object and a JavaScript promise.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Deferred* deferred | A newly created deferred object which can later be passed to OH_JSVM_ResolveDeferred() or OH_JSVM_RejectDeferred() to resolve resp. reject the associated promise. |
| JSVM_Value* promise | The JavaScript promise associated with the deferred object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ResolveDeferred()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ResolveDeferred(JSVM_Env env, JSVM_Deferred deferred, JSVM_Value resolution)
```

**Description**

This API resolves a JavaScript promise by way of the deferred object with which it is associated. Thus, it can only be used to resolve JavaScript promises for which the corresponding deferred object is available. This effectively means that the promise must have been created using OH_JSVM_CreatePromise() and the deferred object returned from that call must have been retained in order to be passed to this API.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Deferred deferred | The deferred object whose associated promise to resolve. |
| JSVM_Value resolution | The value with which to resolve the promise. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_RejectDeferred()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RejectDeferred(JSVM_Env env, JSVM_Deferred deferred, JSVM_Value rejection)
```

**Description**

This API rejects a JavaScript promise by way of the deferred object with which it is associated. Thus, it can only be used to reject JavaScript promises for which the corresponding deferred object is available. This effectively means that the promise must have been created using OH_JSVM_CreatePromise() and the deferred object returned from that call must have been retained in order to be passed to this API.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Deferred deferred | The deferred object whose associated promise to resolve. |
| JSVM_Value rejection | The value with which to reject the promise. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsPromise()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsPromise(JSVM_Env env, JSVM_Value value, bool* isPromise)
```

**Description**

This API return indicating whether promise is a native promise object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The value to examine |
| bool* isPromise | Flag indicating whether promise is a native promise object |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_PromiseRegisterHandler()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_PromiseRegisterHandler(JSVM_Env env, JSVM_Value promise, JSVM_Value onFulfilled, JSVM_Value onRejected, JSVM_Value* result)
```

**Description**

This API register a resolution/rejection handler with a promise.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value promise | The promise to be handled. |
| JSVM_Value onFulfilled | The function to be invoked if promise is resolved. |
| JSVM_Value onRejected | The function to be invoked if promise is rejected. |
| JSVM_Value* result | Another promise returned from promise then/catch method. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code.          {@link JSVM_OK } if the API succeeded. \n<br>        {@link JSVM_INVALID_ARG } if the arguments are invalid. \n<br>        {@link JSVM_INVALID_TYPE } if the arguments are invalid Javascript type. \n<br>        {@link JSVM_PENDING_EXCEPTION} if an exception occurs. \n<br>        {@link JSVM_GENERIC_FAILURE} if the API failed. \n |

### OH_JSVM_JsonParse()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_JsonParse(JSVM_Env env, JSVM_Value jsonString, JSVM_Value* result)
```

**Description**

This API parses a JSON string and returns it as value if successful.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value jsonString | The string to parse. |
| JSVM_Value* result | The parse value if successful. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_JsonStringify()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_JsonStringify(JSVM_Env env, JSVM_Value jsonObject, JSVM_Value* result)
```

**Description**

This API stringifies the object and returns it as string if successful.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value jsonObject | The object to stringify. |
| JSVM_Value* result | The string if successfully stringified. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_CreateSnapshot()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSnapshot(JSVM_VM vm, size_t contextCount, const JSVM_Env* contexts, const char** blobData, size_t* blobSize)
```

**Description**

This API create the startup snapshot of the VM.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The environment that the API is invoked under. |
| size_t contextCount | The object to stringify. |
| const JSVM_Env* contexts | The array of contexts to add to the snapshot. |
| const char** blobData | The snapshot data. |
| size_t* blobSize | The size of snapshot data. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_GetHeapStatistics()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetHeapStatistics(JSVM_VM vm, JSVM_HeapStatistics* result)
```

**Description**

This function returns a set of statistics data of the heap of the VM.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM whose heap statistics are returned. |
| JSVM_HeapStatistics* result | The heap statistics data. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } in all cases.\n |

### OH_JSVM_StartCpuProfiler()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_StartCpuProfiler(JSVM_VM vm, JSVM_CpuProfiler* result)
```

**Description**

This function creates and starts a CPU profiler.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM to start CPU profiler for. |
| JSVM_CpuProfiler* result | The pointer to the CPU profiler. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } in all cases.\n |

### OH_JSVM_StopCpuProfiler()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_StopCpuProfiler(JSVM_VM vm, JSVM_CpuProfiler profiler, JSVM_OutputStream stream, void* streamData)
```

**Description**

This function stops the CPU profiler and output to the stream.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | THe VM to start CPU profiler for. |
| JSVM_CpuProfiler profiler | The CPU profiler to stop. |
| JSVM_OutputStream stream | The output stream callback for receiving the data. |
| void* streamData | Optional data to be passed to the stream callback. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } in all cases.\n |

### OH_JSVM_TakeHeapSnapshot()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_TakeHeapSnapshot(JSVM_VM vm, JSVM_OutputStream stream, void* streamData)
```

**Description**

This function takes the current heap snapshot and output to the stream.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM whose heap snapshot is taken. |
| JSVM_OutputStream stream | The output stream callback for receiving the data. |
| void* streamData | Optional data to be passed to the stream callback. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } in all cases.\n |

### OH_JSVM_TakeRawHeapSnapshot()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_TakeRawHeapSnapshot(JSVM_VM vm, JSVM_OutputStream stream, void *streamData)
```

**Description**

This function takes the current heap snapshot and outputs it to the stream in raw heap format (binary format). The raw heap format is VM-specific and its layout is not guaranteed to be stable across different versions. This operation may pause the application temporarily, and frequent invocation may generate large snapshot files and increase disk usage, so callers should manage generated files appropriately if files are written to disk. The stream callback is invoked synchronously on the thread where the VM is running. The callback should avoid long blocking operations. If the callback returns false, the output stream is aborted, snapshot generation stops.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM whose heap snapshot is taken. |
| JSVM_OutputStream stream | The output stream callback for receiving the binary data. |
| void *streamData | Optional data to be passed to the stream callback. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code.          Returns JSVM_INVALID_ARG if vm or stream is NULL.          Returns JSVM_OK in all other cases. |

### OH_JSVM_SetHeapThresholdCallback()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetHeapThresholdCallback(JSVM_VM vm, uint64_t threshold, JSVM_HandlerForHeapThreshold callback, void *data)
```

**Description**

Set a heap threshold callback for vm and the vm can only have one heap threshold callback. The registered callback should be cleared by OH_JSVM_ClearHeapThresholdCallback when it is no longer needed. This API is not thread-safe and must be called on the thread where the vm is running. The threshold is checked around GC, and the callback is invoked when the observed heap usage is greater than or equal to threshold. The callback will be called synchronously on the same thread, and threshold checks are skipped while the callback is running. After the callback returns, if the heap usage is still greater than or equal to threshold, the callback will be invoked again around the next GC. The callback does not need to be registered again after it returns. The registered callback is identified (threshold, callback, data).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM whose heap usage will be monitored. |
| uint64_t threshold | The heap usage threshold in bytes. The value must be greater than 0 and must not exceed heapSizeLimit, where heapSizeLimit is a field in JSVM_HeapStatistics. |
| JSVM_HandlerForHeapThreshold callback | The callback function to be invoked when a threshold check observes heap usage greater than or equal to threshold. |
| void *data | Optional user-provided data passed to the callback.The caller is responsible for managing the lifetime of this data. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code.          Returns JSVM_OK if the function executed successfully.          Returns JSVM_INVALID_ARG if vm or callback is NULL, or if threshold          is zero or exceeds heapSizeLimit, or if a heap threshold callback          has already been registered for the VM. |

### OH_JSVM_ClearHeapThresholdCallback()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ClearHeapThresholdCallback(JSVM_VM vm, uint64_t threshold, JSVM_HandlerForHeapThreshold callback, void *data)
```

**Description**

Clear the heap threshold callback previously registered for vm. This API is not thread-safe and must be called on the thread where the vm is running. The registered callback is identified (threshold, callback, data).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM whose heap threshold callback is to be cleared. |
| uint64_t threshold | The heap usage threshold in bytes which is previously registered. |
| JSVM_HandlerForHeapThreshold callback | The callback function previously registered by OH_JSVM_SetHeapThresholdCallback. |
| void *data | The user-provided data used during registration. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code.          Returns JSVM_OK if the function executed successfully.          Returns JSVM_INVALID_ARG if vm or callback is NULL, or if the          (threshold, callback, data) does not match registered callback. |

### OH_JSVM_OpenInspector()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspector(JSVM_Env env, const char* host, uint16_t port)
```

**Description**

This functiong activates insepctor on host and port.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* host | The host to listen to for inspector connections. |
| uint16_t port | The port to listen to for inspector connections. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if the function executed successfully.\n<br>        Returns {@link JSVM_PENDING_EXCEPTION } if an exception occurs.\n |

### OH_JSVM_CloseInspector()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CloseInspector(JSVM_Env env)
```

**Description**

This function attempts to close all remaining inspector connections.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if the function executed successfully.\n<br>        Returns {@link JSVM_PENDING_EXCEPTION } if an exception occurs.\n |

### OH_JSVM_WaitForDebugger()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_WaitForDebugger(JSVM_Env env, bool breakNextLine)
```

**Description**

This function will block until a client (existing or connected later) has sent Runtime.runIfWaitingForDebugger command.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| bool breakNextLine | Whether break on the next line of JavaScript code. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if the function executed successfully.\n<br>        Returns {@link JSVM_PENDING_EXCEPTION } if an exception occurs.\n |

### OH_JSVM_DefineClassWithPropertyHandler()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithPropertyHandler(JSVM_Env env, const char* utf8name, size_t length, JSVM_Callback constructor, size_t propertyCount, const JSVM_PropertyDescriptor* properties, JSVM_PropertyHandlerCfg propertyHandlerCfg, JSVM_Callback callAsFunctionCallback, JSVM_Value* result)
```

**Description**

Define a JavaScript class with given class name, constructor, properties, callback handlers for property operations including get, set, delete, enum etc., and call as function callback.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* utf8name | Name of the JavaScript constructor function. For clarity, it is recommended to use the C++ class name when wrapping a C++ class. |
| size_t length | The length of the utf8name in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Callback constructor | Struct include callback function that handles constructing instances of the class. When wrapping a C++ class, this method must be a static member with the JSVM_Callback.callback signature. A C++ class constructor cannot be used. Include Optional data to be passed to the constructor callback as the data property of the callback info. JSVM_Callback provides more details. |
| size_t propertyCount | Number of items in the properties array argument. |
| const JSVM_PropertyDescriptor* properties | Array of property descriptors describing static and instance data properties, accessors, and methods on the class See JSVM_PropertyDescriptor. |
| JSVM_PropertyHandlerCfg propertyHandlerCfg | The instance object triggers the corresponding callback function. |
| JSVM_Callback callAsFunctionCallback | Calling an instance object as a function will trigger this callback. |
| JSVM_Value* result | A JSVM_Value representing the constructor function for the class. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsLocked()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsLocked(JSVM_Env env, bool* isLocked)
```

**Description**

Determines whether the current thread holds the lock for the specified environment. Only threads that hold locks can use the environment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| bool* isLocked | Flag indicating whether the current thread holds the lock for the specified environment. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_AcquireLock()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_AcquireLock(JSVM_Env env)
```

**Description**

Acquire the lock for the specified environment. Only threads that hold locks can use the environment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_ReleaseLock()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseLock(JSVM_Env env)
```

**Description**

Release the lock for the specified environment. Only threads that hold locks can use the environment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_PumpMessageLoop()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_PumpMessageLoop(JSVM_VM vm, bool* result)
```

**Description**

Starts the running of the task queue inside the VM. This task queue can be executed by an external event loop.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM instance on which to start the task queue. |
| bool* result | Whether the task queue was successfully started. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_PerformMicrotaskCheckpoint()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_PerformMicrotaskCheckpoint(JSVM_VM vm)
```

**Description**

Check to see if there are any microtasks waiting in the queue, and if there are, execute them.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM instance on which to check microtasks. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsCallable()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsCallable(JSVM_Env env, JSVM_Value value, bool* isCallable)
```

**Description**

This API checks if the value passed in is callable.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isCallable | Whether the given value is callable. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } If the function executed successfully.\n |

### OH_JSVM_IsUndefined()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsUndefined(JSVM_Env env, JSVM_Value value, bool* isUndefined)
```

**Description**

This API checks if the value passed in is undefined. This equals to `value === undefined` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isUndefined | Whether the given value is Undefined. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_IsNull()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsNull(JSVM_Env env, JSVM_Value value, bool* isNull)
```

**Description**

This API checks if the value passed in is a null object. This equals to `value === null` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isNull | Whether the given value is Null. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_IsNullOrUndefined()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsNullOrUndefined(JSVM_Env env, JSVM_Value value, bool* isNullOrUndefined)
```

**Description**

This API checks if the value passed in is either a null or an undefined object. This is equivalent to `value == null` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isNullOrUndefined | Whether the given value is Null or Undefined. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_IsBoolean()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsBoolean(JSVM_Env env, JSVM_Value value, bool* isBoolean)
```

**Description**

This API checks if the value passed in is a boolean. This equals to `typeof value === 'boolean'` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isBoolean | Whether the given value is Boolean. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_IsNumber()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsNumber(JSVM_Env env, JSVM_Value value, bool* isNumber)
```

**Description**

This API checks if the value passed in is a number. This equals to `typeof value === 'number'` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isNumber | Whether the given value is Number. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_IsString()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsString(JSVM_Env env, JSVM_Value value, bool* isString)
```

**Description**

This API checks if the value passed in is a string. This equals to `typeof value === 'string'` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isString | Whether the given value is String. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_IsSymbol()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbol(JSVM_Env env, JSVM_Value value, bool* isSymbol)
```

**Description**

This API checks if the value passed in is a symbol. This equals to `typeof value === 'symbol'` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isSymbol | Whether the given value is Symbol. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_IsFunction()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsFunction(JSVM_Env env, JSVM_Value value, bool* isFunction)
```

**Description**

This API checks if the value passed in is a function. This equals to `typeof value === 'function'` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isFunction | Whether the given value is Function. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_IsObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsObject(JSVM_Env env, JSVM_Value value, bool* isObject)
```

**Description**

This API checks if the value passed in is an object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isObject | Whether the given value is Object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_IsBigInt()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsBigInt(JSVM_Env env, JSVM_Value value, bool* isBigInt)
```

**Description**

This API checks if the value passed in is a bigInt. This equals to `typeof value === 'bigint'` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The VM instance on which to check microtasks. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isBigInt | Whether the given value is BigInt. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM funtions result code.          {@link JSVM_OK } This API will not trigger any exception.\n |

### OH_JSVM_CreateMap()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateMap(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns a JSVM-API value corresponding to a JavaScript Map type.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript Map. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.\n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n |

### OH_JSVM_IsMap()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsMap(JSVM_Env env, JSVM_Value value, bool* isMap)
```

**Description**

This API checks if the value passed in is a Map.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isMap | Whether the given value is Map. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.\n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n |

### OH_JSVM_CreateSet()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSet(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns a JSVM-API value corresponding to a JavaScript Set type.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript Set. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.\n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n |

### OH_JSVM_IsSet()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsSet(JSVM_Env env, JSVM_Value value, bool* isSet)
```

**Description**

This API checks if the value passed in is a Set.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isSet | Whether the given value is Set. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.\n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n |

### OH_JSVM_CompileScriptWithOptions()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOptions(JSVM_Env env, JSVM_Value script, size_t optionCount, JSVM_CompileOptions options[], JSVM_Script* result)
```

**Description**

This function compiles a string of JavaScript code with the compile options and returns the compiled script.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the JSVM-API call is invoked under. |
| JSVM_Value script | A JavaScript string containing the script to be compiled. |
| size_t optionCount | length of option array. |
| JSVM_CompileOptions options[] | Compile options to be passed. |
| JSVM_Script* result | The compiled script. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code          {@link JSVM_OK } if the API succeeded. \n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n<br>        {@link JSVM_STRING_EXPECTED } If there are parameters passed in that are not of type string.\n<br>        {@link JSVM_GENERIC_FAILURE } If there is an unknown reason causing execution failure.\n<br>        {@link JSVM_PENDING_EXCEPTION } If a JS exception occurs during the execution process.\n |

### OH_JSVM_CoerceToBigInt()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBigInt(JSVM_Env env, JSVM_Value value, JSVM_Value* result)
```

**Description**

This API implements the abstract operation ToBigInt().

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to coerce. |
| JSVM_Value* result | JSVM_Value representing the coerced JavaScript BigInt. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n<br>        {@link JSVM_BIGINT_EXPECTED} If the JavaScript value fails to coerce.\n |

### OH_JSVM_IsRegExp()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsRegExp(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

This API checks if the value passed in is a regExp. This equals to `value instanceof RegExp` in JS.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given value is RegExp. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.\n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n |

### OH_JSVM_IsConstructor()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsConstructor(JSVM_Env env, JSVM_Value value, bool* isConstructor)
```

**Description**

This API checks if the value passed in is a constructor.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* isConstructor | Whether the given value is Constructor. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.\n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n |

### OH_JSVM_CreateRegExp()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateRegExp(JSVM_Env env, JSVM_Value value, JSVM_RegExpFlags flags, JSVM_Value* result)
```

**Description**

This API returns the JavaScript value of the regular expression corresponding to the input. The interface may throw an exception.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript string to convert to a regular expression. |
| JSVM_RegExpFlags flags | Regular expression flag bits. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript RegExp. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Only returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.\n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n<br>        {@link JSVM_STRING_EXPECTED } If the value of 'value' is not a string.\n<br>        {@link JSVM_GENERIC_FAILURE } If create RegExp failed.\n<br>        {@link JSVM_PENDING_EXCEPTION } If the API throws an exception during runtime.\n |

### OH_JSVM_ObjectGetPrototypeOf()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectGetPrototypeOf(JSVM_Env env, JSVM_Value object, JSVM_Value* result)
```

**Description**

This API returns the Object prototype.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | JSVM_Value representing JavaScript Object whose prototype to return. This returns the equivalent of Object.getPrototypeOf (which is not the same as the function's prototype property). |
| JSVM_Value* result | JSVM_Value representing prototype of the given object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.\n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n |

### OH_JSVM_ObjectSetPrototypeOf()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSetPrototypeOf(JSVM_Env env, JSVM_Value object, JSVM_Value prototype)
```

**Description**

This API set the prototype on the Object passed in.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object on which to set the prototype. |
| JSVM_Value prototype | The prototype value. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM function's result code.          {@link JSVM_OK } If the API succeeded.\n<br>        {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n |

### OH_JSVM_CreateFunctionWithScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunctionWithScript(JSVM_Env env, const char* funcName, size_t length, size_t argc, const JSVM_Value* argv, JSVM_Value script, JSVM_Value* result)
```

**Description**

Creates a function with a given script as its body.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* funcName | A string containing the function's name. Pass NULL to create an anonymous function. |
| size_t length | The length of the funcName in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| size_t argc | The count of elements in the argv array. |
| const JSVM_Value* argv | Array of JSVM_Values representing JavaScript strings passed in as arguments to the function. |
| JSVM_Value script | A JavaScript string containing the script to use as the function's body. |
| JSVM_Value* result | JSVM_Value representing the JavaScript function object for the newly created function. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM function's result code.           {@link JSVM_OK } If the API succeeded.<br>         {@link JSVM_INVALID_ARG } If the input parameter is invalid.\n<br>         {@link JSVM_GENERIC_FAILURE} If the input script fails to be compiled.\n |

### OH_JSVM_RetainScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RetainScript(JSVM_Env env, JSVM_Script script)
```

**Description**

This function keep persistently save a JSVM_Script and extend its lifecycle beyond the current scope.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Script script | A JavaScript string containing the script to be retained. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code          {@link JSVM_OK } if the API succeeded. \n<br>        {@link JSVM_INVALID_ARG } if the script is empty or already retained. \n |

### OH_JSVM_ReleaseScript()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseScript(JSVM_Env env, JSVM_Script script)
```

**Description**

This function release the script retained by OH_JSVM_RetainScript

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Script script | A JavaScript string containing the script to be retained. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code          {@link JSVM_OK } if the API succeeded. \n<br>        {@link JSVM_INVALID_ARG } if the script is empty or not retained. \n |

### OH_JSVM_OpenInspectorWithName()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspectorWithName(JSVM_Env env, int pid, const char* name)
```

**Description**

This function activates insepctor with pid and alias it.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| int pid | A process id to identify the inspector connection. |
| const char* name | An alias for the inspector that under a specific pid. default name is jsvm if a nullptr is passed in. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if the function executed successfully.\n<br>        Returns {@link JSVM_PENDING_EXCEPTION } if an exception occurs.\n |

### OH_JSVM_CompileWasmModule()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmModule(JSVM_Env env, const uint8_t *wasmBytecode, size_t wasmBytecodeLength, const uint8_t *cacheData, size_t cacheDataLength, bool *cacheRejected, JSVM_Value *wasmModule)
```

**Description**

Compile WebAssembly bytecode into a WebAssembly module. If WebAssembly cache provided, deserialization will be performed.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const uint8_t *wasmBytecode | WebAssembly bytecode. |
| size_t wasmBytecodeLength | WebAssembly bytecode length in byte. |
| const uint8_t *cacheData | Optional WebAssembly cache. |
| size_t cacheDataLength | Optional WebAssembly cache length in byte. |
| bool *cacheRejected | Output parameter representing whether the provided cacheData is rejected. |
| JSVM_Value *wasmModule | Output parameter representing compiled WebAssembly module. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } if any of env, wasmBytecode is NULL, or data length is invalid.\n<br>        Returns {@link JSVM_GENERIC_FAILURE } if compile failed.\n<br>        Returns {@link JSVM_PENDING_EXCEPTION } if an exception occurs.\n<br>        Returns {@link JSVM_JIT_MODE_EXPECTED } if run in jitless mode.\n |

### OH_JSVM_CompileWasmFunction()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmFunction(JSVM_Env env, JSVM_Value wasmModule, uint32_t functionIndex, JSVM_WasmOptLevel optLevel)
```

**Description**

Compile the function with the specified index in the WebAssembly module into the specified optimization level.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value wasmModule | The WebAssembly module to which the function to compiled belongs. |
| uint32_t functionIndex | The index of the function to be compiled, should never be out of range. |
| JSVM_WasmOptLevel optLevel | Optimization level the function will be compiled with. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } if env is NULL, or wasmModule is NULL or is not a WebAssembly module.\n<br>        Returns {@link JSVM_GENERIC_FAILURE } if functionIndex out of range or compile failed.\n<br>        Returns {@link JSVM_PENDING_EXCEPTION } if an exception occurs.\n<br>        Returns {@link JSVM_JIT_MODE_EXPECTED } if run in jitless mode.\n |

### OH_JSVM_IsWasmModuleObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsWasmModuleObject(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

Check whether the given JSVM_Value is a WebAssembly module.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given value is a WebAssembly module. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } if any of the input arguments is NULL.\n |

### OH_JSVM_CreateWasmCache()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateWasmCache(JSVM_Env env, JSVM_Value wasmModule, const uint8_t** data, size_t* length)
```

**Description**

Create cache for compiled WebAssembly module.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value wasmModule | The compiled WebAssembly module. |
| const uint8_t** data | Output parameter representing generated WebAssembly module cache. |
| size_t* length | Output parameter representing byte length of generated WebAssembly module cache. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } if any of the input arguments is NULL.\n<br>        Returns {@link JSVM_GENERIC_FAILURE } if create wasm cache failed.\n<br>        Returns {@link JSVM_JIT_MODE_EXPECTED } if run in jitless mode.\n |

### OH_JSVM_ReleaseCache()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseCache(JSVM_Env env, const uint8_t* cacheData, JSVM_CacheType cacheType)
```

**Description**

Release cache data with specified cache type.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const uint8_t* cacheData | The cache data to be released, double free is undefined behaviors. |
| JSVM_CacheType cacheType | The type of cache data. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if the function executed successfully.\n<br>        Returns {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL or cacheType is illegal.\n |

### OH_JSVM_CreateExternalStringLatin1()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternalStringLatin1(JSVM_Env env, char* str, size_t length, JSVM_Finalize finalizeCallback, void* finalizeHint, JSVM_Value* result, bool* copied)
```

**Description**

This API creates an external JavaScript string value from an ISO-8859-1-encoded C string. The native string is copied when failed to create external string.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| char* str | Character buffer representing an ISO-8859-1-encoded string. |
| size_t length | The length of the string in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Finalize finalizeCallback | Optional callback to call when the external value is being collected. JSVM_Finalize provides more details. |
| void* finalizeHint | Optional hint to pass to the finalize callback during collection. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript external string. |
| bool* copied | flag indicate whether the external string is successfully created, true for faild to create external ones and fall back to non-external strings, false for success. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if one of env, str and copied is NULL.\n |

### OH_JSVM_CreateExternalStringUtf16()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternalStringUtf16(JSVM_Env env, char16_t* str, size_t length, JSVM_Finalize finalizeCallback, void* finalizeHint, JSVM_Value* result, bool* copied)
```

**Description**

This API creates an external JavaScript string value from an UTF16-LE-encoded C string. The native string is copied when failed to create external string.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| char16_t* str | Character buffer representing an UTF16-LE-encoded string. |
| size_t length | The length of the string in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Finalize finalizeCallback | Optional callback to call when the external value is being collected. JSVM_Finalize provides more details. |
| void* finalizeHint | Optional hint to pass to the finalize callback during collection. |
| JSVM_Value* result | A JSVM_Value representing a JavaScript external string. |
| bool* copied | flag indicate whether the external string is successfully created, true for faild to create external ones and fall back to non-external strings, false for success. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if one of env, str and copied is NULL.\n |

### OH_JSVM_CreatePrivate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreatePrivate(JSVM_Env env, JSVM_Value description, JSVM_Data* result)
```

**Description**

This API creates a JavaScript private key.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value description | Optional JSVM_Value which refers to a JavaScript string to be set as the description for the private key. |
| JSVM_Data* result | A JSVM_Data representing a JavaScript private key. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if env or result is NULL.\n<br>        {@link JSVM_STRING_EXPECTED } if the description is not a string.\n |

### OH_JSVM_SetPrivate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetPrivate(JSVM_Env env, JSVM_Value object, JSVM_Data key, JSVM_Value value)
```

**Description**

This API set a private property on the Object passed in.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object on which to set the private property. |
| JSVM_Data key | The private key of the property. |
| JSVM_Value value | The private property value. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the arguments is NULL or the key is not a private key.\n<br>        {@link JSVM_OBJECT_EXPECTED } object passed in is not a real object.\n<br>        {@link JSVM_GENERIC_FAILURE } if failed to set the private key but no exception is pending.\n<br>        {@link JSVM_PENDING_EXCPTION } if an exception occurs.\n |

### OH_JSVM_GetPrivate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetPrivate(JSVM_Env env, JSVM_Value object, JSVM_Data key, JSVM_Value *result)
```

**Description**

This API gets the requested private property from the Object passed in.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object from which to retrieve the private property. |
| JSVM_Data key | The private key of the property. |
| JSVM_Value *result | The value of the private property. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the arguments is NULL or the key is not a private key.\n<br>        {@link JSVM_OBJECT_EXPECTED } object passed in is not a real object.\n<br>        {@link JSVM_GENERIC_FAILURE } if failed to get the private key but no exception is pending.\n<br>        {@link JSVM_PENDING_EXCPTION } if an exception occurs.\n |

### OH_JSVM_DeletePrivate()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DeletePrivate(JSVM_Env env, JSVM_Value object, JSVM_Data key)
```

**Description**

This API attempts to delete the property of the private key from object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value object | The object to query. |
| JSVM_Data key | The private key of the property to delete. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the arguments is NULL or the key is not a private key.\n<br>        {@link JSVM_OBJECT_EXPECTED } object passed in is not a real object.\n<br>        {@link JSVM_GENERIC_FAILURE } if failed to delete the private key but no exception is pending.\n<br>        {@link JSVM_PENDING_EXCPTION } if an exception occurs.\n |

### OH_JSVM_CreateDataReference()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataReference(JSVM_Env env, JSVM_Data data, uint32_t initialRefcount, JSVM_Ref* result)
```

**Description**

This API creates a new reference with the specified reference count to the data passed in.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Data data | The JSVM_Data for which a reference is being created. |
| uint32_t initialRefcount | Initial reference count for the new reference. |
| JSVM_Ref* result | JSVM_Ref pointing to the new reference. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any parameter is null or the value of initialRefcount is 0.\n |

### OH_JSVM_GetReferenceData()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceData(JSVM_Env env, JSVM_Ref ref, JSVM_Data* result)
```

**Description**

If still valid, this API returns the JSVM_Data representing the JavaScript data associated with the JSVM_Ref. Otherwise, result will be NULL.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Ref ref | The JSVM_Ref for which the corresponding value is being requested. |
| JSVM_Data* result | The JSVM_Data referenced by the JSVM_Ref. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any parameter is null or the ref is not a reference to JSVM_Data.\n |

### OH_JSVM_IsBigIntObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsBigIntObject(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

Check whether the given JSVM_Value is a BigInt Object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given value is a BigInt Object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_IsBooleanObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsBooleanObject(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

Check whether the given JSVM_Value is a Boolean Object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given value is a Boolean Object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_IsStringObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsStringObject(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

Check whether the given JSVM_Value is a String Object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given value is a String Object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_IsNumberObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsNumberObject(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

Check whether the given JSVM_Value is a Number Object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given value is a Number Object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_IsSymbolObject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbolObject(JSVM_Env env, JSVM_Value value, bool* result)
```

**Description**

Check whether the given JSVM_Value is a Symbol Object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value value | The JavaScript value to check. |
| bool* result | Whether the given value is a Symbol Object. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolAsyncIterator()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolAsyncIterator(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.asyncIterator of Well-Known Symbols.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.asyncIterator of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolHasInstance()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolHasInstance(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.hasInstance of Well-Known Symbols.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.hasInstance of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolIsConcatSpreadable()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIsConcatSpreadable(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.isConcatSpreadable of Well-Known Symbols

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.isConcatSpreadable of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolMatch()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolMatch(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.match of Well-Known Symbols

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.match of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolReplace()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolReplace(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.replace of Well-Known Symbols

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.replace of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolSearch()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSearch(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.search of Well-Known Symbols

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.search of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolSplit()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSplit(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.split of Well-Known Symbols

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.split of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolToPrimitive()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToPrimitive(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.toPrimitive of Well-Known Symbols

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.toPrimitive of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolUnscopables()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolUnscopables(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.unscopables of Well-Known Symbols

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.unscopables of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolToStringTag()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToStringTag(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.toStringTag of Well-Known Symbols

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.toStringTag of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_GetSymbolIterator()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIterator(JSVM_Env env, JSVM_Value* result)
```

**Description**

This API returns the Symbol.iterator of Well-Known Symbols

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_Value* result | The Symbol.iterator of Well-Known Symbols. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_TraceStart()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_TraceStart(size_t count, const JSVM_TraceCategory* categories, const char* tag, size_t eventsCount)
```

**Description**

Trace start with specified categories for all JSVM VM.(Non-thread-safe)

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t count | The count of trace categories. |
| const JSVM_TraceCategory* categories | Select internal trace events for tracing by categories. |
| const char* tag | User-defined tag of trace data. |
| size_t eventsCount | Number of trace events. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if categories or count is illegal.\n |

### OH_JSVM_TraceStop()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_TraceStop(JSVM_OutputStream stream, void* streamData)
```

**Description**

Trace stop for specified categories for all JSVM VM.(Non-thread-safe)

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_OutputStream stream | The output stream callback for receiving the data. |
| void* streamData | Data passed to the stream callback. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if stream or streamData is NULL\n |

### OH_JSVM_SetHandlerForOOMError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForOOMError(JSVM_VM vm, JSVM_HandlerForOOMError handler)
```

**Description**

Set Handler For OOM Error. If this function is invoked repeatedly, only the last time takes effect. When handler is null, the previous setting is canceled.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The environment that the API is invoked under. |
| JSVM_HandlerForOOMError handler | The handler for OOM Error. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if vm is NULL.\n |

### OH_JSVM_SetDebugOption()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetDebugOption(JSVM_Env env, JSVM_DebugOption debugOption, bool isEnabled)
```

**Description**

This API is used to enable/disable the given debug option for a certain JSVM_Env.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| JSVM_DebugOption debugOption | The debug option to be changed. |
| bool isEnabled | Whether to enable or disable the debug option. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if env is NULL.\n |

### OH_JSVM_SetHandlerForFatalError()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForFatalError(JSVM_VM vm, JSVM_HandlerForFatalError handler)
```

**Description**

Set Handler For Fatal Error. If this function is invoked repeatedly, only the last time takes effect. When handler is null, the previous setting is canceled.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The environment that the API is invoked under. |
| JSVM_HandlerForFatalError handler | The handler for Fatal Error. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if vm is NULL.\n |

### OH_JSVM_SetHandlerForPromiseReject()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForPromiseReject(JSVM_VM vm, JSVM_HandlerForPromiseReject handler)
```

**Description**

Set Handler For Promise Reject. If this function is invoked repeatedly, only the last time takes effect. When handler is null, the previous setting is canceled.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The environment that the API is invoked under. |
| JSVM_HandlerForPromiseReject handler | The handler for Promise Reject. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if vm is NULL.\n |

### OH_JSVM_DefineClassWithOptions()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithOptions(JSVM_Env env, const char* utf8name, size_t length, JSVM_Callback constructor, size_t propertyCount, const JSVM_PropertyDescriptor* properties, JSVM_Value parentClass, size_t option_count, JSVM_DefineClassOptions options[], JSVM_Value* result)
```

**Description**

When wrapping a C++ class, the C++ constructor callback passed via constructor should be a static method on the class that calls the actual class constructor, then wraps the new C++ instance in a JavaScript object according to the different Options passed in, and returns the wrapper object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| const char* utf8name | Name of the JavaScript constructor function. For clarity, it is recommended to use the C++ class name when wrapping a C++ class. |
| size_t length | The length of the utf8name in bytes, or JSVM_AUTO_LENGTH if it is null-terminated. |
| JSVM_Callback constructor | Struct include callback function that handles constructing instances of the class. When wrapping a C++ class, this method must be a static member with the JSVM_Callback.callback signature. A C++ class constructor cannot be used. Include Optional data to be passed to the constructor callback as the data property of the callback info. JSVM_Callback provides more details. |
| size_t propertyCount | Number of items in the properties array argument. |
| const JSVM_PropertyDescriptor* properties | Array of property descriptors describing static and instance data properties, accessors, and methods on the class See JSVM_PropertyDescriptor. |
| JSVM_Value parentClass | The parent-class of the currently defined class. |
| size_t option_count | Number of items in an option array argument. |
| JSVM_DefineClassOptions options[] | DefineClass options to be passed. |
| JSVM_Value* result | A JSVM_Value representing the constructor function for the class. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM functions result code.          {@link JSVM_OK } if the function executed successfully. \n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL. \n<br>        {@link JSVM_GENERIC_FAILURE} if the input utf8name \| constructor \| properties is invalid. \n |

### OH_JSVM_AddHandlerForGC()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_AddHandlerForGC(JSVM_VM vm, JSVM_CBTriggerTimeForGC triggerTime, JSVM_HandlerForGC handler, JSVM_GCType gcType, void* userData)
```

**Description**

Add VM GC Callback.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The environment that the API is invoked under. |
| JSVM_CBTriggerTimeForGC triggerTime | The timing of GC callback trigger. |
| JSVM_HandlerForGC handler | When Trigger gc, the callback function will be called. |
| JSVM_GCType gcType | The type of gc. |
| void* userData | The native pointer data. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if the vm or the handler is NULL or the handler has been added before.\n |

### OH_JSVM_RemoveHandlerForGC()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_RemoveHandlerForGC(JSVM_VM vm, JSVM_CBTriggerTimeForGC triggerTime, JSVM_HandlerForGC handler, void* userData)
```

**Description**

Remove VM GC Callback.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The environment that the API is invoked under. |
| JSVM_CBTriggerTimeForGC triggerTime | The timing of GC callback trigger. |
| JSVM_HandlerForGC handler | When Trigger gc, the callback function will be called. |
| void* userData | The native pointer data. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if the vm or the handler is NULL, or the handler has been removed,  or the handler has never been added.\n |

### OH_JSVM_BackgroundDeserialize()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_BackgroundDeserialize(JSVM_VM vm, JSVM_CodeCache cacheData, JSVM_DeserializeResult* result)
```

**Description**

Deserialize JavaScript code cache in thread pool, and release JSVM_DeserializeResult with OH_JSVM_ReleaseDeserializeResult.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_VM vm | The VM instance where background deserialize will be performed. |
| JSVM_CodeCache cacheData | Code cache data to be deserialized. |
| JSVM_DeserializeResult* result | The result of background deserialize. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_ReleaseDeserializeResult()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseDeserializeResult(JSVM_DeserializeResult result)
```

**Description**

Release deserialize result.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_DeserializeResult result | The background deserialize result to be release. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          {@link JSVM_OK } if the function executed successfully.\n<br>        {@link JSVM_INVALID_ARG } if any of the pointer arguments is NULL.\n |

### OH_JSVM_CreateArrayBufferFromExternalMemory()

```c
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayBufferFromExternalMemory(JSVM_Env env, void* externalData, size_t byteLength, JSVM_FinalizeArrayBuffer finalizeCb, void* finalizeHint, bool* copied, JSVM_Value* result)
```

**Description**

Creates a JavaScript ArrayBuffer whose content is initialized from user-provided external memory. The implementation may either directly reference the external memory (zero-copy) or copy the data into an internally managed buffer, depending on engine implementation.<br> When zero-copy is used, the ArrayBuffer directly references the external memory. The caller must NOT free it before the finalize callback is invoked.<br> When a copy occurs, the data is copied into engine-managed memory. The copied output parameter is set to true so the caller knows their memory is no longer referenced. The resulting ArrayBuffer's data pointer (from OH_JSVM_GetArraybufferInfo) will differ from externalData.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| JSVM_Env env | The environment that the API is invoked under. |
| void* externalData | Pointer to the source memory block. Must be 8-byte aligned. Can be nullptr only if byteLength is 0. |
| size_t byteLength | The length in bytes of the source memory block. Must not exceed the engine's maximum ArrayBuffer size. |
| JSVM_FinalizeArrayBuffer finalizeCb | Optional callback invoked when the ArrayBuffer object created by this API is garbage collected. The callback receives the original externalData pointer, finalizeHint, and a boolean indicating whether the data was copied. When copied is true, the engine does not reference externalData and the caller may free it immediately after this API returns. When copied is false (zero-copy), externalData is still in use and should only be freed in this callback. Can be NULL if no cleanup is needed. |
| void* finalizeHint | Optional hint passed to finalizeCb. Can be NULL. |
| bool* copied | Optional output parameter. If non-NULL, set to true when data was copied into an internal buffer, or false when zero-copy was used. Pass NULL if the caller does not need this information. |
| JSVM_Value* result | A JSVM_Value representing the created JavaScript ArrayBuffer. |

**Returns**:

| Type | Description |
| -- | -- |
| JSVM_EXTERN JSVM_Status | Returns JSVM funtions result code.          Returns {@link JSVM_OK } if creation succeeded.\n<br>        Returns {@link JSVM_INVALID_ARG } if result is null, externalData is null when          byteLength > 0, externalData is not 8-byte aligned, or byteLength exceeds the          engine's maximum ArrayBuffer size.\n |


