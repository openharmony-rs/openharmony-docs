# jsvm.h
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## 概述

提供JSVM-API接口定义。通过API接口为开发者提供独立、标准、完整的JavaScript引擎能力，包括管理引擎生命周期、编译运行JS代码、实现JS/C++跨语言调用、拍摄快照等。

**引用文件：** <ark_runtime/jsvm.h>

**库：** libjsvm.so

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**相关模块：** [JSVM](capi-jsvm.md)

## 汇总

### 宏定义

| 名称                                               | 描述                                                                                                                                                 |
|--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| **JSVM_VERSION_EXPERIMENTAL** 2147483647           | JSVM 实验性版本号。                                                                                                                                       |
| **JSVM_VERSION** 8                                 | JSVM 版本号。                                                                                                                                          |
| **JSVM_EXTERN  attribute**(visibility("default")))  | 指定符号对外部可见。                                                                                                                                         |
| **JSVM_AUTO_LENGTH**   SIZE_MAX | 自动长度。                                                                                                                                              |
| **EXTERN_C_START**                                 | 用于告知编译器按C Code编译以下代码段的段起始标识：<br>当预处理指令__cplusplus检查到C++编译器正在进行编译时：EXTERN_C_START被赋值为"extern "C" {" ，表示其后代码为C代码。当预处理指令__cplusplus检查到不是C++编译器时，无须标记。 |
| **EXTERN_C_END**                                   | 用于告知编译器按C Code编译以下代码段的段终止标识：<br>当使用预处理指令__cplusplus检查到C++编译器正在编译时：EXTERN_C_START被赋值为"}" ，表示C代码到此为止。当预处理指令__cplusplus检查到不是C++编译器时，无须标记。                                                                                                                   |

### 函数

| 名称 | 描述 |
| -- | -- |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Init(const JSVM_InitOptions* options)](#oh_jsvm_init) | 初始化一个JavaScript虚拟机。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateVM(const JSVM_CreateVMOptions* options,JSVM_VM* result)](#oh_jsvm_createvm) | 创建一个虚拟机实例。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetMicrotaskPolicy(JSVM_VM vm,JSVM_MicrotaskPolicy policy)](#oh_jsvm_setmicrotaskpolicy) | 用于设置虚拟机实例的微任务执行策略。如果该方法未被调用，虚拟机实例的默认策略为 JSVM_MicrotaskPolicy::JSVM_MICROTASK_AUTO。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DestroyVM(JSVM_VM vm)](#oh_jsvm_destroyvm) | 销毁一个虚拟机实例。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateProxy(JSVM_Env env,JSVM_Value target,JSVM_Value handler,JSVM_Value* result)](#oh_jsvm_createproxy) | 创建JavaScript Proxy，等价于在 JavaScript 中执行 new Proxy(target, handler)。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_IsProxy(JSVM_Env env,JSVM_Value value,bool* isProxy)](#oh_jsvm_isproxy) | 判断传入值value是否为 JavaScript Proxy。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_ProxyGetTarget(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_proxygettarget) | 获取 JavaScript Proxy 中的目标对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenVMScope(JSVM_VM vm,JSVM_VMScope* result)](#oh_jsvm_openvmscope) | 为虚拟机实例打开一个新的虚拟机作用域。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseVMScope(JSVM_VM vm,JSVM_VMScope scope)](#oh_jsvm_closevmscope) | 关闭虚拟机实例的虚拟机作用域。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnv(JSVM_VM vm,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Env* result)](#oh_jsvm_createenv) | 基于新环境上下文的可选属性，创建一个新环境。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnvFromSnapshot(JSVM_VM vm,size_t index,JSVM_Env* result)](#oh_jsvm_createenvfromsnapshot) | 基于虚拟机的起始快照，创建一个新的环境。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DestroyEnv(JSVM_Env env)](#oh_jsvm_destroyenv) | 销毁环境。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenEnvScope(JSVM_Env env,JSVM_EnvScope* result)](#oh_jsvm_openenvscope) | 打开一个新的环境作用域。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseEnvScope(JSVM_Env env,JSVM_EnvScope scope)](#oh_jsvm_closeenvscope) | 关闭环境作用域。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVM(JSVM_Env env,JSVM_VM* result)](#oh_jsvm_getvm) | 检索给定环境的虚拟机实例。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScript(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_Script* result)](#oh_jsvm_compilescript) | 编译一串JavaScript代码，并返回编译后的脚本。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOrigin(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_ScriptOrigin* origin,JSVM_Script* result)](#oh_jsvm_compilescriptwithorigin) | 编译一串包含 sourcemap 信息的 JavaScript 代码，并返回编译后的脚本。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOptions(JSVM_Env env,JSVM_Value script,size_t optionCount,JSVM_CompileOptions options[],JSVM_Value* result)](#oh_jsvm_compilescriptwithoptions) | 编译一串JavaScript代码，并返回编译后的脚本。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateCodeCache(JSVM_Env env,JSVM_Script script,const uint8_t** data,size_t* length)](#oh_jsvm_createcodecache) | 为编译后的脚本创建代码缓存。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RunScript(JSVM_Env env,JSVM_Script script,JSVM_Value* result)](#oh_jsvm_runscript) | 执行一串JavaScript代码并返回其结果，其中包含以下注意事项：与eval不同的是，该函数不允许脚本访问当前词法作用域，因此也不允许访问模块作用域，这意味着require等伪全局变量将不可用。脚本可以访问全局作用域。脚本中的函数和var声明将被添加到全局对象。使用let和const的变量声明将全局可见，但不会被添加到全局对象。this的值在脚本内是global。如果没有 JIT 权限支持，则打印一行日志提示开发者。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetInstanceData(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint)](#oh_jsvm_setinstancedata) | 将data与当前运行的JSVM环境相关联。后续可以使用OH_JSVM_GetInstanceData()检索data。通过先前调用OH_JSVM_SetInstanceData()设置的任何与当前运行的JSVM环境相关联的现有数据都将被覆盖。如果先前提供了finalizeCb，则不会调用它。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetInstanceData(JSVM_Env env,void** data)](#oh_jsvm_getinstancedata) | 检索通过调用OH_JSVM_SetInstanceData()与当前运行JSVM环境产生关联的数据。如果未设置任何关联数据，该函数调用将成功，且data设置为NULL。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetLastErrorInfo(JSVM_Env env,const JSVM_ExtendedErrorInfo** result)](#oh_jsvm_getlasterrorinfo) | 检索JSVM_ExtendedErrorInfo结构，其中包含发生的最后一个错误的有关信息。返回的JSVM_ExtendedErrorInfo的内容仅在对同一env调用JSVM-API函数之前有效。这包括对OH_JSVM_IsExceptionPending的调用，因此可能经常需要复制信息以便以后使用。error_message中返回的指针指向一个静态定义的字符串，因此如果你在调用另一个JSVM-API函数之前将它从error_message字段（将被覆盖）中复制出来，则可以安全地使用该指针。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Throw(JSVM_Env env,JSVM_Value error)](#oh_jsvm_throw) | 抛出提供的JavaScript值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwerror) | 抛出带有所提供文本的JavaScript Error。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowTypeError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwtypeerror) | 抛出带有所提供文本的JavaScript TypeError。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowRangeError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwrangeerror) | 抛出带有所提供文本的JavaScript RangeError。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ThrowSyntaxError(JSVM_Env env,const char* code,const char* msg)](#oh_jsvm_throwsyntaxerror) | 抛出带有所提供文本的JavaScript SyntaxError。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsError(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_iserror) | 查询JSVM_Value以检查它是否表示错误对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createerror) | 返回带有所提供文本的JavaScript Error。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createtypeerror) | 返回带有所提供文本的JavaScript TypeError。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateRangeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createrangeerror) | 返回带有所提供文本的JavaScript RangeError。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSyntaxError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)](#oh_jsvm_createsyntaxerror) | 返回带有所提供文本的JavaScript SyntaxError。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetAndClearLastException(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getandclearlastexception) | 获取并清除上一次异常。如果出现挂起，则返回JavaScript异常，否则返回NULL。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsExceptionPending(JSVM_Env env,bool* result)](#oh_jsvm_isexceptionpending) | 查询上一次异常是否由挂起导致的。如果由异常导致，则返回true，否则返回false。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenHandleScope(JSVM_Env env,JSVM_HandleScope* result)](#oh_jsvm_openhandlescope) | 开辟了一个新的作用域。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseHandleScope(JSVM_Env env,JSVM_HandleScope scope)](#oh_jsvm_closehandlescope) | （必须）按照创建作用域的相反顺序关闭传入的作用域。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope* result)](#oh_jsvm_openescapablehandlescope) | 打开一个可以将某对象从其中提到外部作用域的新作用域。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope scope)](#oh_jsvm_closeescapablehandlescope) | （必须）按照创建作用域的相反顺序关闭传入的作用域。即使存在挂起的JavaScript异常，也可以调用此JSVM_API。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_EscapeHandle(JSVM_Env env,JSVM_EscapableHandleScope scope,JSVM_Value escapee,JSVM_Value* result)](#oh_jsvm_escapehandle) | 提升JavaScript对象的句柄，使其在外部作用域的生命周期内有效。每个作用域只能调用一次。如果多次调用，将返回错误。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateReference(JSVM_Env env,JSVM_Value value,uint32_t initialRefcount,JSVM_Ref* result)](#oh_jsvm_createreference) | 对传入的值创建一个具有指定引用计数的新引用。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteReference(JSVM_Env env,JSVM_Ref ref)](#oh_jsvm_deletereference) | 删除传入的引用。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceRef(JSVM_Env env,JSVM_Ref ref,uint32_t* result)](#oh_jsvm_referenceref) | 增加传入引用的引用计数并返回生成的引用计数。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceUnref(JSVM_Env env,JSVM_Ref ref,uint32_t* result)](#oh_jsvm_referenceunref) | 递减传入引用的引用计数并返回生成的引用计数。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceValue(JSVM_Env env,JSVM_Ref ref,JSVM_Value* result)](#oh_jsvm_getreferencevalue) | 如果仍然有效，此JSVM-API将返回JSVM_Value，表示与JSVM_Ref关联的JavaScript值。否则，结果将为NULL。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArray(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_createarray) | 返回对应于JavaScript Array类型的JSVM-API值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayWithLength(JSVM_Env env,size_t length,JSVM_Value* result)](#oh_jsvm_createarraywithlength) | 返回对应于JavaScript Array类型的JSVM-API值。Array的长度属性设置为传入的长度参数。但是，不保证底层缓冲区在创建数组时由VM预先分配。该行为留给底层VM实现。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateArraybuffer(JSVM_Env env,size_t byteLength,void** data,JSVM_Value* result)](#oh_jsvm_createarraybuffer) | 返回JavaScript ArrayBuffer类型对应的JSVM-API值。ArrayBuffer用于表示固定长度的二进制数据缓冲区。通常用作TypedArray对象的后备缓冲区。分配的ArrayBuffer有一个底层字节缓冲区，其大小由传入的length参数决定。底层缓冲区可选择返回给调用方，调用方可直接操作该缓冲区。此缓冲区只能直接从native代码写入。如果想从JavaScript写入该缓冲区，需创建TypedArray或DataView对象。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_AllocateArrayBufferBackingStoreData(size_t byteLength,JSVM_InitializedFlag initialized,void **data)](#oh_jsvm_allocatearraybufferbackingstoredata) | 申请一段 BackingStore 内存给 array buffer 使用。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_FreeArrayBufferBackingStoreData(void *data)](#oh_jsvm_freearraybufferbackingstoredata) | 释放由 OH_JSVM_AllocateArrayBufferBackingStoreData 申请的 BackingStore 内存。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateArrayBufferFromBackingStoreData(JSVM_Env env,void *data,size_t backingStoreSize,size_t offset,size_t arrayBufferSize,JSVM_Value *result)](#oh_jsvm_createarraybufferfrombackingstoredata) | 在申请得到的 BackingStore 内存上创建 array buffer。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDate(JSVM_Env env,double time,JSVM_Value* result)](#oh_jsvm_createdate) | 分配一个JavaScript Date对象。此API不处理闰秒。这是因为ECMAScript遵循POSIX时间规范，对闰秒进行忽略。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternal(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Value* result)](#oh_jsvm_createexternal) | 分配一个带有外部数据的JavaScript值。这用于通过JavaScript代码传递外部数据。后续可以使用OH_JSVM_GetValueExternal由native代码检索。该API添加了一个JSVM_Finalize回调，当刚刚创建的JavaScript对象被垃圾回收时将调用该回调。创建的值不是一个对象，因此不支持附加属性。它被认为是一个独特的值类型：使用外部值调用OH_JSVM_Typeof()会生成JSVM_EXTERNAL。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateObject(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_createobject) | 分配一个默认的JavaScript对象。该函数功能等同于在JavaScript中执行new Object()。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSymbol(JSVM_Env env,JSVM_Value description,JSVM_Value* result)](#oh_jsvm_createsymbol) | 用UTF8编码的C字符串创建JavaScript symbol值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SymbolFor(JSVM_Env env,const char* utf8description,size_t length,JSVM_Value* result)](#oh_jsvm_symbolfor) | 在全局注册表中搜索具有给定描述的现有符号。如果该符号已经存在，它将被返回，否则将在注册表中创建一个新符号。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypedarray(JSVM_Env env,JSVM_TypedarrayType type,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)](#oh_jsvm_createtypedarray) | 基于已有的ArrayBuffer对象，创建一个JavaScript TypedArray对象。TypedArray对象在底层数据缓冲区上提供了一个类似数组的视图，其中每个元素都具有相同的底层二进制标量数据类型。要求：length * 元素标量byte值 + byteOffset 不大于传入数组的ByteLength()，否则抛出范围错误（RangeError）。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataview(JSVM_Env env,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)](#oh_jsvm_createdataview) | 基于已有的ArrayBuffer对象，创建一个JavaScript DataView对象。DataView对象在底层数据缓冲区上提供了一个类似数组的视图，其中的元素可以具有不同的大小和类型。要求：二进制的length + byteOffset不大于传入数组的大小（byte数）。否则，抛出范围错误（RangeError）。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt32(JSVM_Env env,int32_t value,JSVM_Value* result)](#oh_jsvm_createint32) | 将一个C int32_t类型值转换为JavaScript number类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateUint32(JSVM_Env env,uint32_t value,JSVM_Value* result)](#oh_jsvm_createuint32) | 将一个C uint32_t类型值转换为JavaScript number类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt64(JSVM_Env env,int64_t value,JSVM_Value* result)](#oh_jsvm_createint64) | 将一个C int64_t类型值转换为JavaScript number类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDouble(JSVM_Env env,double value,JSVM_Value* result)](#oh_jsvm_createdouble) | 将一个C double类型值转换为JavaScript number类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintInt64(JSVM_Env env,int64_t value,JSVM_Value* result)](#oh_jsvm_createbigintint64) | 将一个C int64_t类型值转换为JavaScript BigInt类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintUint64(JSVM_Env env,uint64_t value,JSVM_Value* result)](#oh_jsvm_createbigintuint64) | 将一个C uint64_t类型值转换为JavaScript BigInt类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintWords(JSVM_Env env,int signBit,size_t wordCount,const uint64_t* words,JSVM_Value* result)](#oh_jsvm_createbigintwords) | 将一组64位无符号比特位转换为单个BigInt值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringLatin1(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)](#oh_jsvm_createstringlatin1) | 将ISO-8859-1编码的C字符串转换为JavaScript字符串值。复制原生字符串。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf16(JSVM_Env env,const char16_t* str,size_t length,JSVM_Value* result)](#oh_jsvm_createstringutf16) | 将UTF16-LE编码的C字符串转换为JavaScript字符串值。复制原生字符串。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf8(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)](#oh_jsvm_createstringutf8) | 用UTF8编码的C字符串创建JavaScript字符串值。复制原生字符串。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetArrayLength(JSVM_Env env,JSVM_Value value,uint32_t* result)](#oh_jsvm_getarraylength) | 返回数组的长度。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetArraybufferInfo(JSVM_Env env,JSVM_Value arraybuffer,void** data,size_t* byteLength)](#oh_jsvm_getarraybufferinfo) | 用于检索ArrayBuffer的底层数据缓冲区及其长度。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPrototype(JSVM_Env env,JSVM_Value object,JSVM_Value* result)](#oh_jsvm_getprototype) | 返回对象的原型。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetTypedarrayInfo(JSVM_Env env,JSVM_Value typedarray,JSVM_TypedarrayType* type,size_t* length,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)](#oh_jsvm_gettypedarrayinfo) | 返回类型化数组的各种属性。如果不需要该属性，则任何输出参数都可以是 NULL。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetDataviewInfo(JSVM_Env env,JSVM_Value dataview,size_t* bytelength,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)](#oh_jsvm_getdataviewinfo) | 返回DataView的各种属性。如果不需要某一属性，则任何出参都可以设置为NULL。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetDateValue(JSVM_Env env,JSVM_Value value,double* result)](#oh_jsvm_getdatevalue) | 返回与给定的JavaScript Date时间值等价的C双精度基础类型值。如果调用成功，返回JSVM_OK。如果传入一个非JavaScript Date类型的JSVM_Value，返回JSVM_DATA_EXPECTED。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBool(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_getvaluebool) | 返回与给定的JavaScript Boolean等价的C布尔基础类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueDouble(JSVM_Env env,JSVM_Value value,double* result)](#oh_jsvm_getvaluedouble) | 返回与给定的JavaScript number等价的C双精度基础类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintInt64(JSVM_Env env,JSVM_Value value,int64_t* result,bool* lossless)](#oh_jsvm_getvaluebigintint64) | 返回与给定的JavaScript BigInt等价的C int64_t基础类型值。如果需要，它将截断该值，将lossless设置为false。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintUint64(JSVM_Env env,JSVM_Value value,uint64_t* result,bool* lossless)](#oh_jsvm_getvaluebigintuint64) | 返回与给定的JavaScript BigInt等价的C uint64_t基础类型值。如果需要，它将截断该值，将lossless设置为false。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintWords(JSVM_Env env,JSVM_Value value,int* signBit,size_t* wordCount,uint64_t* words)](#oh_jsvm_getvaluebigintwords) | 将单个BigInt值转换为符号位、64位小端数组和数组中的元素数。signBit和words参数可以都设置为NULL。这种情况下，只获取wordCount。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueExternal(JSVM_Env env,JSVM_Value value,void** result)](#oh_jsvm_getvalueexternal) | 检索之前传递给OH_JSVM_CreateExternal()的外部数据指针。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt32(JSVM_Env env,JSVM_Value value,int32_t* result)](#oh_jsvm_getvalueint32) | 返回与给定的JavaScript number等价的C int32基础类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt64(JSVM_Env env,JSVM_Value value,int64_t* result)](#oh_jsvm_getvalueint64) | 返回与给定的JavaScript number等价的C int64基础类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringLatin1(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)](#oh_jsvm_getvaluestringlatin1) | 返回与传入值对应的ISO-8859-1编码字符串。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf8(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)](#oh_jsvm_getvaluestringutf8) | 返回与传入值对应的UTF8编码字符串。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf16(JSVM_Env env,JSVM_Value value,char16_t* buf,size_t bufsize,size_t* result)](#oh_jsvm_getvaluestringutf16) | 查询与传入值对应的UTF16编码字符串。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetValueUint32(JSVM_Env env,JSVM_Value value,uint32_t* result)](#oh_jsvm_getvalueuint32) | 返回与给定的JavaScript number等价的C uint_32基础类型值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetBoolean(JSVM_Env env,bool value,JSVM_Value* result)](#oh_jsvm_getboolean) | 返回表示给定布尔值的JavaScript单例对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetGlobal(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getglobal) | 返回global对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNull(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getnull) | 返回null对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetUndefined(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_getundefined) | 返回Undefined对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBool(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetobool) | 实现抽象操作ToBoolean()。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToNumber(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetonumber) | 实现抽象操作ToNumber()。如果传入的值是对象，则函数可能会运行JavaScript代码。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToObject(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetoobject) | 实现抽象操作ToObject()。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToString(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetostring) | 实现抽象操作ToString()。如果传入的值是对象，则函数可能会运行JavaScript代码。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Typeof(JSVM_Env env,JSVM_Value value,JSVM_ValueType* result)](#oh_jsvm_typeof) | 提供类似于在定义的对象上调用typeof运算符的行为。不同点在于，该函数支持检测外部值；它将null检测为单独的类型，而ECMAScript typeof将用于检测object。如果value的类型无效，则返回错误。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Instanceof(JSVM_Env env,JSVM_Value object,JSVM_Value constructor,bool* result)](#oh_jsvm_instanceof) | 提供类似于在对象上调用instanceof运算符的行为。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsArray(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isarray) | 提供类似于在对象上调用IsArray的行为。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isarraybuffer) | 检查传入的对象是否为ArrayBuffer。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDate(JSVM_Env env,JSVM_Value value,bool* isDate)](#oh_jsvm_isdate) | 检查传入的Object是否为日期。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsTypedarray(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_istypedarray) | 检查传入的Object是否为类型化数组。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDataview(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isdataview) | 检查传入的对象是否是DataView。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_StrictEquals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)](#oh_jsvm_strictequals) | 提供类似调用严格相等算法的行为。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Equals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)](#oh_jsvm_equals) | 提供类似调用宽松相等算法的行为。无论JavaScript值类型如何，只要值相等，就返回true。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DetachArraybuffer(JSVM_Env env,JSVM_Value arraybuffer)](#oh_jsvm_detacharraybuffer) | 提供类似于调用ArrayBuffer detach操作的行为。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsDetachedArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isdetachedarraybuffer) | 提供类似调用ArrayBuffer IsDetachedBuffer操作的行为。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_Value* result)](#oh_jsvm_getpropertynames) | 以字符数数组的形式返回object的可枚举属性的名称。key为符号的object的属性将不会被包含在内。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetAllPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_KeyCollectionMode keyMode,JSVM_KeyFilter keyFilter,JSVM_KeyConversion keyConversion,JSVM_Value* result)](#oh_jsvm_getallpropertynames) | 返回包含object所有可用属性名称的数组。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value value)](#oh_jsvm_setproperty) | 为传入的object设置名为key的属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value* result)](#oh_jsvm_getproperty) | 从传入的object中获取名为key的属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)](#oh_jsvm_hasproperty) | 检查传入的Object是否具有命名为key的属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)](#oh_jsvm_deleteproperty) | 尝试从object中删除名为key的属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasOwnProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)](#oh_jsvm_hasownproperty) | 检查传入的Object是否具有名为key的属性。key必须是string或symbol，否则将抛出错误。JSVM-API不会执行任何数据类型之间的转换。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value value)](#oh_jsvm_setnamedproperty) | 此方法等效于object调用OH_JSVM_SetProperty设置名为`utf8Name`的属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value* result)](#oh_jsvm_getnamedproperty) | 此方法等效于object调用OH_JSVM_GetProperty获取名为`utf8Name`的属性对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,bool* result)](#oh_jsvm_hasnamedproperty) | 此方法等效于object对象调用OH_JSVM_HasProperty查询其内部是否存在名为`utf8Name`的属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value value)](#oh_jsvm_setelement) | 在传入的Object上设置一个元素。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value* result)](#oh_jsvm_getelement) | 获取请求索引处的元素。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_HasElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)](#oh_jsvm_haselement) | 如果传入的Object在指定的索引处有一个元素，则此JSVM-API返回true。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeleteElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)](#oh_jsvm_deleteelement) | 尝试从object中删除指定index处的元素。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineProperties(JSVM_Env env,JSVM_Value object,size_t propertyCount,const JSVM_PropertyDescriptor* properties)](#oh_jsvm_defineproperties) | 通过此方法可以在给定对象上高效定义多个属性，这些属性使用属性描述符进行定义。通过一个属性描述符的数组，此API将为对象依次设置数组中的属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectFreeze(JSVM_Env env,JSVM_Value object)](#oh_jsvm_objectfreeze) | 冻结指定的对象，防止为其添加新的属性、删除现有属性、更改现有属性的可枚举性/可配置性/可写性、更改现有属性的值、改变对象原型等操作。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSeal(JSVM_Env env,JSVM_Value object)](#oh_jsvm_objectseal) | 封装指定的对象，防止为其添加新的属性并将所有现有属性标记为不可配置。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CallFunction(JSVM_Env env,JSVM_Value recv,JSVM_Value func,size_t argc,const JSVM_Value* argv,JSVM_Value* result)](#oh_jsvm_callfunction) | 支持从native代码调用JavaScript函数对象，这是从native代码回调到JavaScript的主要机制。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunction(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback cb,JSVM_Value* result)](#oh_jsvm_createfunction) | 支持在native代码中创建函数对象，这是从JavaScript调用native代码的主要机制。在此调用之后，新创建的函数在脚本中不再自动可见。相反，必须在JavaScript可见的任何对象上显示设置属性，才能从脚本访问该函数。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetCbInfo(JSVM_Env env,JSVM_CallbackInfo cbinfo,size_t* argc,JSVM_Value* argv,JSVM_Value* thisArg,void** data)](#oh_jsvm_getcbinfo) | 此方法在回调函数中用于检索有关调用的详细信息，例如来自给定回调信息的参数和this指针。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetNewTarget(JSVM_Env env,JSVM_CallbackInfo cbinfo,JSVM_Value* result)](#oh_jsvm_getnewtarget) | 返回构造函数调用的new target。如果当前回调不是构造函数调用，结果为NULL。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_NewInstance(JSVM_Env env,JSVM_Value constructor,size_t argc,const JSVM_Value* argv,JSVM_Value* result)](#oh_jsvm_newinstance) | 使用给定的JSVM_Value表示的构造函数来实例化新的JavaScript值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClass(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value* result)](#oh_jsvm_defineclass) | 定义一个JavaScript类。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Wrap(JSVM_Env env,JSVM_Value jsObject,void* nativeObject,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)](#oh_jsvm_wrap) | 在JavaScript对象中封装native实例，该实例后续可以通过OH_JSVM_Unwrap()进行检索。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_Unwrap(JSVM_Env env,JSVM_Value jsObject,void** result)](#oh_jsvm_unwrap) | 当JavaScript代码调用类的方法或属性访问器时，对应的JSVM_Callback将被调用。如果回调是针对实例方法或访问器的，则回调的this参数是封装器对象；然后可以通过调用封装器对象的OH_JSVM_Unwrap()获得作为调用目标的C++实例。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RemoveWrap(JSVM_Env env,JSVM_Value jsObject,void** result)](#oh_jsvm_removewrap) | 使用OH_JSVM_Wrap()检索先前封装在JavaScript对象——js_object中的native实例并移除封装。如果finalize回调与封装相关联，则当JavaScript对象被垃圾回收时将不再调用它。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_TypeTagObject(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag)](#oh_jsvm_typetagobject) | 将typeTag指针的值与JavaScript对象或外部值相关联。可调用OH_JSVM_CheckObjectTypeTag()判断附加在对象上的标记类型，以确保对象的类型正确。如果对象已经有关联的类型标记，则返回JSVM_INVALID_ARG。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CheckObjectTypeTag(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag,bool* result)](#oh_jsvm_checkobjecttypetag) | 将类型标签typeTag与JavaScript对象或外部值上的标签作对比。如果找到相同标签，设置result为true，否则为false。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_AddFinalizer(JSVM_Env env,JSVM_Value jsObject,void* finalizeData,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)](#oh_jsvm_addfinalizer) | 为JavaScript对象添加JSVM_Finalize回调，当JavaScript对象被垃圾回收时调用该回调函数。可以在单个JavaScript对象上多次调用OH_JSVM_AddFinalizer。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVersion(JSVM_Env env,uint32_t* result)](#oh_jsvm_getversion) | 返回JSVM运行时支持的最高JSVM-API版本。后续将新增JSVM-API，以便支持更多的功能。引入该API的目的：在支持某功能的JSVM版本，可以使用新的功能；在不支持某功能的JSVM版本，可以提供回调行为。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetVMInfo(JSVM_VMInfo* result)](#oh_jsvm_getvminfo) | 返回虚拟机的信息。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_AdjustExternalMemory(JSVM_Env env,int64_t changeInBytes,int64_t* result)](#oh_jsvm_adjustexternalmemory) | 此函数将因JavaScript对象而保持活跃的外部分配的内存大小通知给底层虚拟机。注册外部分配的内存将比其他方式更频繁地触发全局垃圾回收。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_MemoryPressureNotification(JSVM_Env env,JSVM_MemoryPressureLevel level)](#oh_jsvm_memorypressurenotification) | 通知虚拟机系统内存不足并有选择地触发垃圾回收。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreatePromise(JSVM_Env env,JSVM_Deferred* deferred,JSVM_Value* promise)](#oh_jsvm_createpromise) | 创建一个延迟对象和一个JavaScript promise。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ResolveDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value resolution)](#oh_jsvm_resolvedeferred) | 通过与之关联的延迟对象来解析JavaScript promise。它只能用于解析对应的可用的延迟对象的JavaScript Promise。这意味着Promise必须使用OH_JSVM_CreatePromise()创建，并且从该调用返回的对象必须保留，才能将其传递给此API。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RejectDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value rejection)](#oh_jsvm_rejectdeferred) | 通过与之关联的延迟对象来拒绝JavaScript Promise。它只能用于拒绝对应的可用延迟对象的JavaScript Promise。这意味着Promise必须使用OH_JSVM_CreatePromise()创建，并且从该调用返回的对象必须保留，才能将其传递给此API。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsPromise(JSVM_Env env,JSVM_Value value,bool* isPromise)](#oh_jsvm_ispromise) | 查询Promise是否为原生Promise对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_PromiseRegisterHandler(JSVM_Env env,JSVM_Value promise,JSVM_Value onFulfilled,JSVM_Value onRejected,JSVM_Value* result)](#oh_jsvm_promiseregisterhandler) | 注册 处理Promise兑现/拒绝的 回调函数。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_JsonParse(JSVM_Env env,JSVM_Value jsonString,JSVM_Value* result)](#oh_jsvm_jsonparse) | 解析JSON字符串，并返回成功解析的值。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_JsonStringify(JSVM_Env env,JSVM_Value jsonObject,JSVM_Value* result)](#oh_jsvm_jsonstringify) | 将对象字符串化，并返回成功转换后的字符串。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSnapshot(JSVM_VM vm,size_t contextCount,const JSVM_Env* contexts,const char** blobData,size_t* blobSize)](#oh_jsvm_createsnapshot) | 创建虚拟机的启动快照。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetHeapStatistics(JSVM_VM vm,JSVM_HeapStatistics* result)](#oh_jsvm_getheapstatistics) | 返回一组虚拟机堆的统计数据。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_StartCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler* result)](#oh_jsvm_startcpuprofiler) | 创建并启动一个CPU profiler。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_StopCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler profiler,JSVM_OutputStream stream,void* streamData)](#oh_jsvm_stopcpuprofiler) | 停止CPU profiler并将结果输出到流。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_TakeHeapSnapshot(JSVM_VM vm,JSVM_OutputStream stream,void* streamData)](#oh_jsvm_takeheapsnapshot) | 获取当前堆快照并将其输出到流。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspector(JSVM_Env env,const char* host,uint16_t port)](#oh_jsvm_openinspector) | 在指定的主机和端口上激活inspector，将用来调试JS代码。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CloseInspector(JSVM_Env env)](#oh_jsvm_closeinspector) | 尝试关闭剩余的所有inspector连接。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_WaitForDebugger(JSVM_Env env,bool breakNextLine)](#oh_jsvm_waitfordebugger) | 等待主机与inspector建立socket连接，连接建立后程序将继续运行。发送Runtime.runIfWaitingForDebugger命令。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithPropertyHandler(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_PropertyHandlerCfg propertyHandlerCfg,JSVM_Callback callAsFunctionCallback,JSVM_Value* result)](#oh_jsvm_defineclasswithpropertyhandler) | 定义一个具有给定类名、构造函数、属性和回调处理程序的JavaScript类，属性操作包括getter、setter、deleter、enumerator等，并作为函数回调进行调用。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsUndefined(JSVM_Env env,JSVM_Value value,bool* isUndefined)](#oh_jsvm_isundefined) | 此API检查传入的值是否为Undefined。这相当于JS中的`value === undefined`。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNull(JSVM_Env env,JSVM_Value value,bool* isNull)](#oh_jsvm_isnull) | 此API检查传入的值是否为Null对象。这相当于JS中的`value === null`。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNullOrUndefined(JSVM_Env env,JSVM_Value value,bool* isNullOrUndefined)](#oh_jsvm_isnullorundefined) | 此API检查传入的值是否为Null或Undefined。这相当于JS中的`value == null`。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBoolean(JSVM_Env env,JSVM_Value value,bool* isBoolean)](#oh_jsvm_isboolean) | 此API检查传入的值是否为Boolean。这相当于JS中的`typeof value === 'boolean'`。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNumber(JSVM_Env env,JSVM_Value value,bool* isNumber)](#oh_jsvm_isnumber) | 此API检查传入的值是否为Number。这相当于JS中的`typeof value === 'number'`。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsString(JSVM_Env env,JSVM_Value value,bool* isString)](#oh_jsvm_isstring) | 此API检查传入的值是否为String。这相当于JS中的`typeof value === 'string'`。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbol(JSVM_Env env,JSVM_Value value,bool* isSymbol)](#oh_jsvm_issymbol) | 此API检查传入的值是否为Symbol。这相当于JS中的`typeof value === 'symbol'`。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsFunction(JSVM_Env env,JSVM_Value value,bool* isFunction)](#oh_jsvm_isfunction) | 此API检查传入的值是否为Function。这相当于JS中的`typeof value === 'function'`。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsObject(JSVM_Env env,JSVM_Value value,bool* isObject)](#oh_jsvm_isobject) | 此API检查传入的值是否为Object。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBigInt(JSVM_Env env,JSVM_Value value,bool* isBigInt)](#oh_jsvm_isbigint) | 此API检查传入的值是否为BigInt。这相当于JS中的`typeof value === 'bigint'`。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateMap(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_createmap) | 此API返回与JavaScript Map类型对应的JavaScript值。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_IsMap(JSVM_Env env,JSVM_Value value,bool* isMap)](#oh_jsvm_ismap) | 此API检查传入的值是否为Map。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_IsConstructor(JSVM_Env env,JSVM_Value value,bool* isConstructor)](#oh_jsvm_isconstructor) | 此API检查传入的值是否为构造函数。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateRegExp(JSVM_Env env,JSVM_Value value,JSVM_RegExpFlags flags,JSVM_Value* result)](#oh_jsvm_createregexp) | 此API返回与输入的JavaScript字符串对应的正则表达式对象。接口可能会抛出异常。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectGetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value* result)](#oh_jsvm_objectgetprototypeof) | 获取JavaScript object的原型。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value prototype)](#oh_jsvm_objectsetprototypeof) | 设置给定的JavaScript object的原型。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateSet(JSVM_Env env,JSVM_Value* result)](#oh_jsvm_createset) | 创建JavaScript Set对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSet(JSVM_Env env,JSVM_Value value,bool* isSet)](#oh_jsvm_isset) | 判断给定的对象是否是Set类型。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBigInt(JSVM_Env env,JSVM_Value value,JSVM_Value* result)](#oh_jsvm_coercetobigint) | 实现抽象操作`ToBigInt()`。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsRegExp(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isregexp) | 此API检查传入的值是否为JavaScript RegExp对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunctionWithScript(JSVM_Env env,const char* funcName,size_t length,size_t argc,const JSVM_Value* argv,JSVM_Value script,JSVM_Value* result)](#oh_jsvm_createfunctionwithscript) | 创建一个以给定JavaScript为函数体的函数。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_PumpMessageLoop(JSVM_VM vm,bool* result)](#oh_jsvm_pumpmessageloop) | 启动虚拟机内任务队列，这个任务队列可以通过外部事件循环执行。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_PerformMicrotaskCheckpoint(JSVM_VM vm)](#oh_jsvm_performmicrotaskcheckpoint) | 检查队列中是否有微任务等待，如果存在则执行它们。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RetainScript(JSVM_Env env, JSVM_Script script)](#oh_jsvm_retainscript) | 持久保存一个JSVM_Script并将其生命周期延长到当前作用域之外。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseScript(JSVM_Env env, JSVM_Script script)](#oh_jsvm_releasescript) | 释放由 OH_JSVM_RetainScript 保留的脚本，释放后应避免对传入 script 的再次使用。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspectorWithName(JSVM_Env env,int pid,const char* name)](#oh_jsvm_openinspectorwithname) | 打开一个名为 name 的 inspector，为其打开对应 pid 的 unix domain 端口。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmModule(JSVM_Env env,const uint8_t *wasmBytecode,size_t wasmBytecodeLength,const uint8_t *cacheData,size_t cacheDataLength,bool *cacheRejected,JSVM_Value *wasmModule)](#oh_jsvm_compilewasmmodule) | 将 WebAssembly 字节码编译得到一个 WebAssembly 模块。如果提供了 WebAssembly 缓存，则会先尝试对缓存进行反序列化。如果没有 JIT 权限支持，则打印一行日志提示开发者。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmFunction(JSVM_Env env,JSVM_Value wasmModule,uint32_t functionIndex,JSVM_WasmOptLevel optLevel)](#oh_jsvm_compilewasmfunction) | 对当前 WebAssembly 模块中指定索引的函数进行指定优化等级的编译优化。如果没有 JIT 权限支持，则打印一行日志提示开发者。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsWasmModuleObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_iswasmmoduleobject) | 判断给定的 JSVM_Value 是否是一个 WebAssembly 模块。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateWasmCache(JSVM_Env env,JSVM_Value wasmModule,const uint8_t** data,size_t* length)](#oh_jsvm_createwasmcache) | 为给定的 WebAssembly 模块生成缓存。如果没有 JIT 权限支持，则打印一行日志提示开发者。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseCache(JSVM_Env env,const uint8_t* cacheData,JSVM_CacheType cacheType)](#oh_jsvm_releasecache) | 释放给定类型的缓存数据。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBigIntObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isbigintobject) | 判断给定的 JSVM_Value 是否是一个 BigInt对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsBooleanObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isbooleanobject) | 判断给定的 JSVM_Value 是否是一个 Boolean对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsStringObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isstringobject) | 判断给定的 JSVM_Value 是否是一个 String对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsNumberObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_isnumberobject) | 判断给定的 JSVM_Value 是否是一个 Number对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbolObject(JSVM_Env env,JSVM_Value value,bool* result)](#oh_jsvm_issymbolobject) | 判断给定的 JSVM_Value 是否是一个 Symbol对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolAsyncIterator(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolasynciterator) | 获取Well-Known symbol里的Symbol.AsyncIterator能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolHasInstance(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolhasinstance) | 获取Well-Known symbol里的Symbol.HasInstance能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIsConcatSpreadable(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolisconcatspreadable) | 获取Well-Known symbol里的Symbol.IsConcatSpreadable能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolMatch(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolmatch) | 获取Well-Known symbol里的Symbol.Match能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolReplace(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolreplace) | 获取Well-Known symbol里的Symbol.Replace能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSearch(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolsearch) | 获取Well-Known symbol里的Symbol.Search能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSplit(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolsplit) | 获取Well-Known symbol里的Symbol.Split能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToPrimitive(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboltoprimitive) | 获取Well-Known symbol里的Symbol.ToPrimitive能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolUnscopables(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymbolunscopables) | 获取Well-Known symbol里的Symbol.Unscopables能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToStringTag(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboltostringtag) | 获取Well-Known symbol里的Symbol.ToStringTag能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIterator(JSVM_Env env, JSVM_Value* result)](#oh_jsvm_getsymboliterator) | 获取Well-Known symbol里的Symbol.Iterator能力。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_TraceStart(size_t count,const JSVM_TraceCategory* categories,const char* tag,size_t eventsCount)](#oh_jsvm_tracestart) | 对所有 JSVM 运行时实例，开始采集指定 Trace 类别的信息（线程不安全）。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_TraceStop(JSVM_OutputStream stream, void* streamData)](#oh_jsvm_tracestop) | 对所有 JSVM 运行时，停止采集指定 Trace 类别的信息（线程不安全）。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_AddHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,JSVM_GCType gcType,void* userData)](#oh_jsvm_addhandlerforgc) | 在VM中添加GC的回调函数。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_RemoveHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,void* userData)](#oh_jsvm_removehandlerforgc) | 在VM中移除GC的回调函数。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForOOMError(JSVM_VM vm,JSVM_HandlerForOOMError handler)](#oh_jsvm_sethandlerforoomerror) | 为OOM错误设置回调处理。当接口被重复调用时，仅最后一次生效。当传入的handler为null时，表示取消之前的设置。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetDebugOption(JSVM_Env env, JSVM_DebugOption debugOption, bool isEnabled)](#oh_jsvm_setdebugoption) | 启用/禁用特定JSVM_Env的指定调试选项。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForFatalError(JSVM_VM vm,JSVM_HandlerForFatalError handler)](#oh_jsvm_sethandlerforfatalerror) | 为Fatal错误设置回调处理。当接口被重复调用时，仅最后一次生效。当传入的handler为null时，表示取消之前的设置。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForPromiseReject(JSVM_VM vm,JSVM_HandlerForPromiseReject handler)](#oh_jsvm_sethandlerforpromisereject) | 为PromiseReject错误设置回调处理。当接口被重复调用时，仅最后一次生效。当传入的handler为null时，表示取消之前的设置。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithOptions(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value parentClass,size_t optionCount,JSVM_DefineClassOptions options[],JSVM_Value* result)](#oh_jsvm_defineclasswithoptions) | 在封装一个 C++ 类时，通过构造函数传递的 C++ 构造函数回调应该是类中的一个静态方法，该方法调用实际的类构造函数，然后根据传入的不同选项，将新的 C++ 实例封装在一个 JavaScript 对象中并返回封装对象。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringLatin1(JSVM_Env env,char* str,size_t length,JSVM_Finalize finalizeCallback,void* finalizeHint,JSVM_Value* result,bool* copied)](#oh_jsvm_createexternalstringlatin1) | 此 API 使用 ISO-8859-1 编码的 C 字符串，创建一个外部的 JavaScript 字符串。创建外部字符串失败时会复制原生字符串。 |
| [JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringUtf16(JSVM_Env env,char16_t* str,size_t length,JSVM_Finalize finalizecallback,void* finalizeHint,JSVM_Value* result,bool* copied)](#oh_jsvm_createexternalstringutf16) | 此 API 使用 UTF16-LE 编码的 C 字符串，创建一个外部的 JavaScript 字符串。创建外部字符串失败时会复制原生字符串。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreatePrivate(JSVM_Env env,JSVM_Value description,JSVM_Data* result)](#oh_jsvm_createprivate) | 创建一个 JavaScript private key 对象。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_SetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value value)](#oh_jsvm_setprivate) | 为传入的object设置一个 private 属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value *result)](#oh_jsvm_getprivate) | 从传入的object获取 private key 对应的 private 属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_DeletePrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key)](#oh_jsvm_deleteprivate) | 从传入的 object 上删除 private key 对应的 private 属性。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataReference(JSVM_Env env,JSVM_Data data,uint32_t initialRefcount,JSVM_Ref* result)](#oh_jsvm_createdatareference) | 创建一个对于给定 JSVM_Data 对象的引用，初始的引用计数为传入的 initialRefcount。 |
| [JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceData(JSVM_Env env,JSVM_Ref ref,JSVM_Data* result)](#oh_jsvm_getreferencedata) | 如果引用仍然有效，通过 result 参数返回对应的 JSVM_Data，表示与 JSVM_Ref 关联的 JavaScript 值。否则结果将为空。 |

## 函数说明

### OH_JSVM_Init()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Init(const JSVM_InitOptions* options)
```

**描述**

初始化一个JavaScript虚拟机。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const JSVM_InitOptions](capi-jsvm-jsvm-initoptions.md)* options | 用于初始化JavaScript虚拟机的选项。 |

**返回：**

| 类型                                                          | 说明 |
|-------------------------------------------------------------| -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) | 返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示执行失败，说明当前进程已完成JSVM初始化，无需重复执行。 |

### OH_JSVM_CreateVM()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateVM(const JSVM_CreateVMOptions* options,JSVM_VM* result)
```

**描述**

创建一个虚拟机实例。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const JSVM_CreateVMOptions](capi-jsvm-jsvm-createvmoptions.md)* options | 用于创建虚拟机实例的选项。 |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md)* result | 新的虚拟机实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。 |

### OH_JSVM_SetMicrotaskPolicy()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetMicrotaskPolicy(JSVM_VM vm,JSVM_MicrotaskPolicy policy)
```

**描述**

用于设置虚拟机实例的微任务执行策略。如果该方法未被调用，虚拟机实例的默认策略为 JSVM_MicrotaskPolicy::JSVM_MICROTASK_AUTO。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 用于设置微任务执行策略的虚拟机实例。 |
| [JSVM_MicrotaskPolicy](capi-jsvm-types-h.md#jsvm_microtaskpolicy) policy | 执行微任务的策略。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  如果接口调用成功，返回 JSVM_OK。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入参数不合法。 |

### OH_JSVM_DestroyVM()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DestroyVM(JSVM_VM vm)
```

**描述**

销毁一个虚拟机实例。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 待销毁的虚拟机实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入参数不合法。 |

### OH_JSVM_CreateProxy()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateProxy(JSVM_Env env,JSVM_Value target,JSVM_Value handler,JSVM_Value* result)
```

**描述**

创建JavaScript Proxy，等价于在 JavaScript 中执行 new Proxy(target, handler)。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) target | 表示用于创建代理的 JavaScript 对象 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) handler | 表示定义了拦截什么操作及如何处理被拦截操作的 JavaScript 对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示创建的 JavaScript 代理。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示接口调用成功。<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 如果 target 或 handler 非 JS 对象。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_IsProxy()

```
JSVM_Status JSVM_CDECL OH_JSVM_IsProxy(JSVM_Env env,JSVM_Value value,bool* isProxy)
```

**描述**

判断传入值value是否为 JavaScript Proxy。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 需要检查的值。 |
| bool* isProxy | 表示是否为 JavaScript Proxy。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示接口调用成功。 |

### OH_JSVM_ProxyGetTarget()

```
JSVM_Status JSVM_CDECL OH_JSVM_ProxyGetTarget(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**描述**

获取 JavaScript Proxy 中的目标对象。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 需要获取目标对象的代理。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代理的目标对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示接口调用成功。<br>         [JSVM_INVALID_TYPE](capi-jsvm-types-h.md#jsvm_status) 如果 value 非 Javascript Proxy。 |

### OH_JSVM_OpenVMScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenVMScope(JSVM_VM vm,JSVM_VMScope* result)
```

**描述**

为虚拟机实例打开一个新的虚拟机作用域。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 目标虚拟机实例。 |
| [JSVM_VMScope](capi-jsvm-jsvm-vmscope--8h.md)* result | 新的虚拟机作用域。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CloseVMScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseVMScope(JSVM_VM vm,JSVM_VMScope scope)
```

**描述**

关闭虚拟机实例的虚拟机作用域。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 目标虚拟机实例。 |
| [JSVM_VMScope](capi-jsvm-jsvm-vmscope--8h.md) scope | 将要关闭的虚拟机作用域。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateEnv()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnv(JSVM_VM vm,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Env* result)
```

**描述**

基于新环境上下文的可选属性，创建一个新环境。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 虚拟机实例，新环境将在该实例中创建。 |
| size_t propertyCount | 属性数组中元素的个数。 |
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | 属性描述符的数组。 |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md)* result | 创建的新环境。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateEnvFromSnapshot()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateEnvFromSnapshot(JSVM_VM vm,size_t index,JSVM_Env* result)
```

**描述**

基于虚拟机的起始快照，创建一个新的环境。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 虚拟机实例，新环境将在该实例中创建。 |
| size_t index | 环境在快照中的索引。 |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md)* result | 创建的新环境。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_DestroyEnv()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DestroyEnv(JSVM_Env env)
```

**描述**

销毁环境。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 待销毁的环境。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_OpenEnvScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenEnvScope(JSVM_Env env,JSVM_EnvScope* result)
```

**描述**

打开一个新的环境作用域。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 目标环境，JSVM-API接口将在该环境下调用。 |
| [JSVM_EnvScope](capi-jsvm-jsvm-envscope--8h.md)* result | 新的环境作用域。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CloseEnvScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseEnvScope(JSVM_Env env,JSVM_EnvScope scope)
```

**描述**

关闭环境作用域。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 目标环境，JSVM-API接口将在该环境下调用。 |
| [JSVM_EnvScope](capi-jsvm-jsvm-envscope--8h.md) scope | 将要关闭的环境作用域。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetVM()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetVM(JSVM_Env env,JSVM_VM* result)
```

**描述**

检索给定环境的虚拟机实例。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 目标环境，JSVM-API接口将在该环境下调用。 |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md)* result | 给定环境的虚拟机实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CompileScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScript(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_Script* result)
```

**描述**

编译一串JavaScript代码，并返回编译后的脚本。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 目标环境，JSVM-API接口将在该环境下调用。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | 包含要编译的脚本的JavaScript代码。 |
| const uint8_t* cachedData | 可选。脚本的代码缓存数据。 |
| size_t cacheDataLength | cachedData数组的长度。 |
| bool eagerCompile | 是否立即编译脚本。 |
| bool* cacheRejected | 代码缓存是否被编译拒绝。 |
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md)* result | 编译后的脚本。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_CompileScriptWithOrigin()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOrigin(JSVM_Env env,JSVM_Value script,const uint8_t* cachedData,size_t cacheDataLength,bool eagerCompile,bool* cacheRejected,JSVM_ScriptOrigin* origin,JSVM_Script* result)
```

**描述**

编译一串包含 sourcemap 信息的 JavaScript 代码，并返回编译后的脚本。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 目标环境，JSVM-API接口将在该环境下调用。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | 包含要编译的脚本的JavaScript代码。 |
| const uint8_t* cachedData | 可选。脚本的代码缓存数据。 |
| size_t cacheDataLength | cachedData数组的长度。 |
| bool eagerCompile | 是否立即编译脚本。 |
| bool* cacheRejected | 代码缓存是否被编译拒绝。 |
| [JSVM_ScriptOrigin](capi-jsvm-jsvm-scriptorigin.md)* origin | 源代码信息，包括 source map 的位置和源代码文件名等信息。 |
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md)* result | 编译后的脚本。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_CompileScriptWithOptions()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileScriptWithOptions(JSVM_Env env,JSVM_Value script,size_t optionCount,JSVM_CompileOptions options[],JSVM_Value* result)
```

**描述**

编译一串JavaScript代码，并返回编译后的脚本。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 目标环境，JSVM-API接口将在该环境下调用。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | 包含要编译的脚本的JavaScript代码。 |
| size_t optionCount | 传入的 option 数组的长度。 |
| JSVM_CompileOptions options[] | option 数组，存放所有的编译选项。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 编译后的脚本。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的 data 是空指针。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_CreateCodeCache()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateCodeCache(JSVM_Env env,JSVM_Script script,const uint8_t** data,size_t* length)
```

**描述**

为编译后的脚本创建代码缓存。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 目标环境，JSVM-API接口将在该环境下调用。 |
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | 目标编译脚本。 |
| const uint8_t** data | 代码缓存的数据。 |
| size_t* length | 代码缓存数据的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示执行失败。 |

### OH_JSVM_RunScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RunScript(JSVM_Env env,JSVM_Script script,JSVM_Value* result)
```

**描述**

执行一串JavaScript代码并返回其结果，其中包含以下注意事项：与eval不同的是，该函数不允许脚本访问当前词法作用域，因此也不允许访问模块作用域，这意味着require等伪全局变量将不可用。脚本可以访问全局作用域。脚本中的函数和var声明将被添加到全局对象。使用let和const的变量声明将全局可见，但不会被添加到全局对象。this的值在脚本内是global。如果没有 JIT 权限支持，则打印一行日志提示开发者。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | 包含要执行的脚本的JavaScript字符串。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 执行脚本产生的值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_SetInstanceData()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetInstanceData(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint)
```

**描述**

将data与当前运行的JSVM环境相关联。后续可以使用OH_JSVM_GetInstanceData()检索data。通过先前调用OH_JSVM_SetInstanceData()设置的任何与当前运行的JSVM环境相关联的现有数据都将被覆盖。如果先前提供了finalizeCb，则不会调用它。

**起始版本：** 11


**参数：**

| 参数项                                                            | 描述 |
|----------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                      | 调用JSVM-API的环境。 |
| void* data                                                     | 可用于此实例的绑定的数据项。 |
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | 销毁环境时调用的函数，该函数接收data以便释放它。 |
| void* finalizeHint                                             | 在收集期间传递给最终回调的可选提示。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetInstanceData()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetInstanceData(JSVM_Env env,void** data)
```

**描述**

检索通过调用OH_JSVM_SetInstanceData()与当前运行JSVM环境产生关联的数据。如果未设置任何关联数据，该函数调用将成功，且data设置为NULL。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| void** data | 之前通过调用OH_JSVM_SetInstanceData()与当前运行的JSVM环境关联的数据项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetLastErrorInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetLastErrorInfo(JSVM_Env env,const JSVM_ExtendedErrorInfo** result)
```

**描述**

检索JSVM_ExtendedErrorInfo结构，其中包含发生的最后一个错误的有关信息。返回的JSVM_ExtendedErrorInfo的内容仅在对同一env调用JSVM-API函数之前有效。这包括对OH_JSVM_IsExceptionPending的调用，因此可能经常需要复制信息以便以后使用。error_message中返回的指针指向一个静态定义的字符串，因此如果你在调用另一个JSVM-API函数之前将它从error_message字段（将被覆盖）中复制出来，则可以安全地使用该指针。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [const JSVM_ExtendedErrorInfo](capi-jsvm-jsvm-extendederrorinfo.md)** result | 包含有关错误的更多信息的JSVM_ExtendedErrorInfo结构。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_Throw()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Throw(JSVM_Env env,JSVM_Value error)
```

**描述**

抛出提供的JavaScript值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) error | 要抛出的JavaScript值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_ThrowError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowError(JSVM_Env env,const char* code,const char* msg)
```

**描述**

抛出带有所提供文本的JavaScript Error。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* code | 要在错误上设置的可选错误代码。 |
| const char* msg | 表示与错误关联的文本的C字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_ThrowTypeError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowTypeError(JSVM_Env env,const char* code,const char* msg)
```

**描述**

抛出带有所提供文本的JavaScript TypeError。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* code | 要在错误上设置的可选错误代码。 |
| const char* msg | 表示与错误关联的文本的C字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_ThrowRangeError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowRangeError(JSVM_Env env,const char* code,const char* msg)
```

**描述**

抛出带有所提供文本的JavaScript RangeError。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* code | 要在错误上设置的可选错误代码。 |
| const char* msg | 表示与错误关联的文本的C字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_ThrowSyntaxError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ThrowSyntaxError(JSVM_Env env,const char* code,const char* msg)
```

**描述**

抛出带有所提供文本的JavaScript SyntaxError。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* code | 要在错误上设置的可选错误代码。 |
| const char* msg | 表示与错误关联的文本的C字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_IsError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsError(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

查询JSVM_Value以检查它是否表示错误对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* result | 如果JSVM_Value表示错误，则设置为true的布尔值，否则设置为false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**描述**

返回带有所提供文本的JavaScript Error。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | 可选的JSVM_Value，带有与错误关联的错误代码的字符串。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | 引用JavaScript string用作Error的消息。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示创建的错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。 |

### OH_JSVM_CreateTypeError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**描述**

返回带有所提供文本的JavaScript TypeError。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | 可选的JSVM_Value，带有与错误关联的错误代码的字符串。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | 引用JavaScript string用作Error的消息。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示创建的错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。 |

### OH_JSVM_CreateRangeError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateRangeError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**描述**

返回带有所提供文本的JavaScript RangeError。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | 可选的JSVM_Value，带有与错误关联的错误代码的字符串。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | 引用JavaScript string用作Error的消息。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示创建的错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。 |

### OH_JSVM_CreateSyntaxError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSyntaxError(JSVM_Env env,JSVM_Value code,JSVM_Value msg,JSVM_Value* result)
```

**描述**

返回带有所提供文本的JavaScript SyntaxError。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) code | 可选的JSVM_Value，带有与错误关联的错误代码的字符串。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) msg | 引用JavaScript string用作Error的消息。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示创建的错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。 |

### OH_JSVM_GetAndClearLastException()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetAndClearLastException(JSVM_Env env,JSVM_Value* result)
```

**描述**

获取并清除上一次异常。如果出现挂起，则返回JavaScript异常，否则返回NULL。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 如果出现挂起则返回异常，否则为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_IsExceptionPending()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsExceptionPending(JSVM_Env env,bool* result)
```

**描述**

查询上一次异常是否由挂起导致的。如果由异常导致，则返回true，否则返回false。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| bool* result | 如果异常挂起，则设置为true的布尔值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_OpenHandleScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenHandleScope(JSVM_Env env,JSVM_HandleScope* result)
```

**描述**

开辟了一个新的作用域。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_HandleScope](capi-jsvm-jsvm-handlescope--8h.md)* result | 代表新作用域。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CloseHandleScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseHandleScope(JSVM_Env env,JSVM_HandleScope scope)
```

**描述**

（必须）按照创建作用域的相反顺序关闭传入的作用域。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_HandleScope](capi-jsvm-jsvm-handlescope--8h.md) scope | 表示要关闭的作用域。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_HANDLE_SCOPE_MISMATCH](capi-jsvm-types-h.md#jsvm_status) 表示执行失败。 |

### OH_JSVM_OpenEscapableHandleScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope* result)
```

**描述**

打开一个可以将某对象从其中提到外部作用域的新作用域。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_EscapableHandleScope](capi-jsvm-jsvm-escapablehandlescope--8h.md)* result | 代表新作用域。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CloseEscapableHandleScope()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseEscapableHandleScope(JSVM_Env env,JSVM_EscapableHandleScope scope)
```

**描述**

（必须）按照创建作用域的相反顺序关闭传入的作用域。即使存在挂起的JavaScript异常，也可以调用此JSVM_API。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_EscapableHandleScope](capi-jsvm-jsvm-escapablehandlescope--8h.md) scope | 表示要关闭的作用域。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_HANDLE_SCOPE_MISMATCH](capi-jsvm-types-h.md#jsvm_status) 表示执行失败。 |

### OH_JSVM_EscapeHandle()

```
JSVM_EXTERN JSVM_Status OH_JSVM_EscapeHandle(JSVM_Env env,JSVM_EscapableHandleScope scope,JSVM_Value escapee,JSVM_Value* result)
```

**描述**

提升JavaScript对象的句柄，使其在外部作用域的生命周期内有效。每个作用域只能调用一次。如果多次调用，将返回错误。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_EscapableHandleScope](capi-jsvm-jsvm-escapablehandlescope--8h.md) scope | 表示当前的作用域。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) escapee | 表示要提升的JavaScript Object。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 被提升的Object在外部作用域中的句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_ESCAPE_CALLED_TWICE](capi-jsvm-types-h.md#jsvm_status) 表示scope对象已被关闭。 |

### OH_JSVM_CreateReference()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateReference(JSVM_Env env,JSVM_Value value,uint32_t initialRefcount,JSVM_Ref* result)
```

**描述**

对传入的值创建一个具有指定引用计数的新引用。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 正在为其创建引用的JSVM_Value。 |
| uint32_t initialRefcount | 新引用的初始引用计数。 |
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | 指向新的引用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_DeleteReference()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteReference(JSVM_Env env,JSVM_Ref ref)
```

**描述**

删除传入的引用。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | 需删除的JSVM_Ref。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_ReferenceRef()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceRef(JSVM_Env env,JSVM_Ref ref,uint32_t* result)
```

**描述**

增加传入引用的引用计数并返回生成的引用计数。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | 传入的引用，其引用计数将增加。 |
| uint32_t* result | 新的引用计数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_ReferenceUnref()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ReferenceUnref(JSVM_Env env,JSVM_Ref ref,uint32_t* result)
```

**描述**

递减传入引用的引用计数并返回生成的引用计数。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | 将减少其引用计数的JSVM_Ref。 |
| uint32_t* result | 新的引用计数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示执行失败。 |

### OH_JSVM_GetReferenceValue()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceValue(JSVM_Env env,JSVM_Ref ref,JSVM_Value* result)
```

**描述**

如果仍然有效，此JSVM-API将返回JSVM_Value，表示与JSVM_Ref关联的JavaScript值。否则，结果将为NULL。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | 请求相应值的JSVM_Ref。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | JSVM_Ref引用的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateArray()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArray(JSVM_Env env,JSVM_Value* result)
```

**描述**

返回对应于JavaScript Array类型的JSVM-API值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript Array的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateArrayWithLength()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArrayWithLength(JSVM_Env env,size_t length,JSVM_Value* result)
```

**描述**

返回对应于JavaScript Array类型的JSVM-API值。Array的长度属性设置为传入的长度参数。但是，不保证底层缓冲区在创建数组时由VM预先分配。该行为留给底层VM实现。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| size_t length | 数组的初始长度。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript Array的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateArraybuffer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateArraybuffer(JSVM_Env env,size_t byteLength,void** data,JSVM_Value* result)
```

**描述**

返回JavaScript ArrayBuffer类型对应的JSVM-API值。ArrayBuffer用于表示固定长度的二进制数据缓冲区。通常用作TypedArray对象的后备缓冲区。分配的ArrayBuffer有一个底层字节缓冲区，其大小由传入的length参数决定。底层缓冲区可选择返回给调用方，调用方可直接操作该缓冲区。此缓冲区只能直接从native代码写入。如果想从JavaScript写入该缓冲区，需创建TypedArray或DataView对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| size_t byteLength | 要创建的数组缓冲区的字节长度。 |
| void** data | 指向ArrayBuffer的底层字节缓冲区的指针。data可以选择性地通过传递NULL来忽略。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript ArrayBuffer的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_AllocateArrayBufferBackingStoreData()

```
JSVM_Status JSVM_CDECL OH_JSVM_AllocateArrayBufferBackingStoreData(size_t byteLength,JSVM_InitializedFlag initialized,void **data)
```

**描述**

申请一段 BackingStore 内存给 array buffer 使用。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| size_t byteLength | BackingStore 内存的大小。 |
| [JSVM_InitializedFlag](capi-jsvm-types-h.md#jsvm_initializedflag) initialized | BackingStore 内存初始化的方式。 |
| void **data | 用于接受申请 BackingStore 内存地址的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的 data 是空指针。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示内存申请失败。 |

### OH_JSVM_FreeArrayBufferBackingStoreData()

```
JSVM_Status JSVM_CDECL OH_JSVM_FreeArrayBufferBackingStoreData(void *data)
```

**描述**

释放由 OH_JSVM_AllocateArrayBufferBackingStoreData 申请的 BackingStore 内存。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| void *data| 申请得到的 BackingStore 内存。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的 data 是空指针。 |

### OH_JSVM_CreateArrayBufferFromBackingStoreData()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateArrayBufferFromBackingStoreData(JSVM_Env env,void *data,size_t backingStoreSize,size_t offset,size_t arrayBufferSize,JSVM_Value *result)
```

**描述**

在申请得到的 BackingStore 内存上创建 array buffer。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| void *data | 申请得到的 BackingStore 内存。 |
| size_t backingStoreSize | BackingStore 内存的大小。 |
| size_t offset | array buffer 在这段内存上的起始位置与内存头之间的相对偏移，单位是字节。 |
| size_t arrayBufferSize | array buffer 的大小，单位是字节。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) *result | 接收 array buffer 地址的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示触发了下面描述的异常情况之一：<br>         1. offset + arrayBufferSize > backingStoreSize。<br>         2. backingStoreSize 或者 arrayBufferSize 为 0。<br>         3. data 或者 result 为空。 |

### OH_JSVM_CreateDate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDate(JSVM_Env env,double time,JSVM_Value* result)
```

**描述**

分配一个JavaScript Date对象。此API不处理闰秒。这是因为ECMAScript遵循POSIX时间规范，对闰秒进行忽略。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| double time | 自1970年1月1日UTC以来的ECMAScript时间值（以毫秒为单位）。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript Date对象的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_CreateExternal()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateExternal(JSVM_Env env,void* data,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Value* result)
```

**描述**

分配一个带有外部数据的JavaScript值。这用于通过JavaScript代码传递外部数据。后续可以使用OH_JSVM_GetValueExternal由native代码检索。该API添加了一个JSVM_Finalize回调，当刚刚创建的JavaScript对象被垃圾回收时将调用该回调。创建的值不是一个对象，因此不支持附加属性。它被认为是一个独特的值类型：使用外部值调用OH_JSVM_Typeof()会生成JSVM_EXTERNAL。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| void* data | 指向外部数据的原始指针。 |
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | 收集外部值时调用的可选回调。JSVM_Finalize提供了更多详细信息。 |
| void* finalizeHint | 在收集期间传递给最终回调的可选提示。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示外部值的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateObject(JSVM_Env env,JSVM_Value* result)
```

**描述**

分配一个默认的JavaScript对象。该函数功能等同于在JavaScript中执行new Object()。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript对象的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateSymbol()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSymbol(JSVM_Env env,JSVM_Value description,JSVM_Value* result)
```

**描述**

用UTF8编码的C字符串创建JavaScript symbol值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) description | 可选的JSVM_Value，它指的是要设置为符号描述的JavaScript string。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript symbol的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。 |

### OH_JSVM_SymbolFor()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SymbolFor(JSVM_Env env,const char* utf8description,size_t length,JSVM_Value* result)
```

**描述**

在全局注册表中搜索具有给定描述的现有符号。如果该符号已经存在，它将被返回，否则将在注册表中创建一个新符号。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* utf8description | UTF-8 C 字符串，表示用作符号描述的文本。 |
| size_t length | 描述字符串的长度，以字节为单位。如果字符串以null结尾，则为JSVM_AUTO_LENGTH。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript 符号的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateTypedarray()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateTypedarray(JSVM_Env env,JSVM_TypedarrayType type,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)
```

**描述**

基于已有的ArrayBuffer对象，创建一个JavaScript TypedArray对象。TypedArray对象在底层数据缓冲区上提供了一个类似数组的视图，其中每个元素都具有相同的底层二进制标量数据类型。要求：length * 元素标量byte值 + byteOffset 不大于传入数组的ByteLength()，否则抛出范围错误（RangeError）。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_TypedarrayType](capi-jsvm-types-h.md#jsvm_typedarraytype) type | TypedArray中元素的标量数据类型。 |
| size_t length | TypedArray中的元素个数。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | ArrayBuffer是类型化数组的基础。 |
| size_t byteOffset | ArrayBuffer中开始投影TypedArray的字节偏移量。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript TypedArray的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_CreateDataview()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataview(JSVM_Env env,size_t length,JSVM_Value arraybuffer,size_t byteOffset,JSVM_Value* result)
```

**描述**

基于已有的ArrayBuffer对象，创建一个JavaScript DataView对象。DataView对象在底层数据缓冲区上提供了一个类似数组的视图，其中的元素可以具有不同的大小和类型。要求：二进制的length + byteOffset不大于传入数组的大小（byte数）。否则，抛出范围错误（RangeError）。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| size_t length | DataView中的元素个数。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | 位于DataView底层的ArrayBuffer。 |
| size_t byteOffset | ArrayBuffer中的字节偏移量，指示投影DataView的开始位置。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript DataView对象的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_CreateInt32()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt32(JSVM_Env env,int32_t value,JSVM_Value* result)
```

**描述**

将一个C int32_t类型值转换为JavaScript number类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| int32_t value | 要在JavaScript中表示的整数值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript number类型的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateUint32()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateUint32(JSVM_Env env,uint32_t value,JSVM_Value* result)
```

**描述**

将一个C uint32_t类型值转换为JavaScript number类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| uint32_t value | 要在JavaScript中表示的无符号整数值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript number类型的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateInt64()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateInt64(JSVM_Env env,int64_t value,JSVM_Value* result)
```

**描述**

将一个C int64_t类型值转换为JavaScript number类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| int64_t value | 要在JavaScript中表示的整数值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript number类型的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateDouble()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDouble(JSVM_Env env,double value,JSVM_Value* result)
```

**描述**

将一个C double类型值转换为JavaScript number类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| double value | 要在JavaScript中表现的双精度值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript number类型的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateBigintInt64()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintInt64(JSVM_Env env,int64_t value,JSVM_Value* result)
```

**描述**

将一个C int64_t类型值转换为JavaScript BigInt类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| int64_t value | 要在JavaScript中表现的整数值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript BigInt类型的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateBigintUint64()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintUint64(JSVM_Env env,uint64_t value,JSVM_Value* result)
```

**描述**

将一个C uint64_t类型值转换为JavaScript BigInt类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| uint64_t value | 要在JavaScript中表示的无符号整数值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript BigInt类型的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateBigintWords()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateBigintWords(JSVM_Env env,int signBit,size_t wordCount,const uint64_t* words,JSVM_Value* result)
```

**描述**

将一组64位无符号比特位转换为单个BigInt值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| int signBit | 确定生成的BigInt是正数还是负数。 |
| size_t wordCount | words数组的长度。 |
| const uint64_t* words | uint64_t little-endian 64位字数组。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript BigInt类型的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_CreateStringLatin1()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringLatin1(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)
```

**描述**

将ISO-8859-1编码的C字符串转换为JavaScript字符串值。复制原生字符串。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* str | 表示ISO-8859-1编码的字符串的字符缓冲区。 |
| size_t length | 字符串的长度，以字节为单位。如果它以null结尾，则为JSVM_AUTO_LENGTH。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript字符串的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_CreateStringUtf16()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf16(JSVM_Env env,const char16_t* str,size_t length,JSVM_Value* result)
```

**描述**

将UTF16-LE编码的C字符串转换为JavaScript字符串值。复制原生字符串。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char16_t* str | 表示UTF16-LE编码的字符串的字符缓冲区。 |
| size_t length | 以两字节代码单元表示的字符串长度，如果它以null终止，则为JSVM_AUTO_LENGTH。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript string的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_CreateStringUtf8()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateStringUtf8(JSVM_Env env,const char* str,size_t length,JSVM_Value* result)
```

**描述**

用UTF8编码的C字符串创建JavaScript字符串值。复制原生字符串。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* str | 表示UTF8编码字符串的字符缓冲区。 |
| size_t length | 字符串的长度，以字节为单位。如果字符串以null结尾，则为JSVM_AUTO_LENGTH。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript字符串的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_GetArrayLength()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetArrayLength(JSVM_Env env,JSVM_Value value,uint32_t* result)
```

**描述**

返回数组的长度。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表查询长度的JavaScript Array。 |
| uint32_t* result | uint32代表数组的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_ARRAY_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是Array类型。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_GetArraybufferInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetArraybufferInfo(JSVM_Env env,JSVM_Value arraybuffer,void** data,size_t* byteLength)
```

**描述**

用于检索ArrayBuffer的底层数据缓冲区及其长度。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | 代表被查询的ArrayBuffer。 |
| void** data | ArrayBuffer的底层数据缓冲区。如果byte_length为0，则该值可能为NULL或任何其他指针值。 |
| size_t* byteLength | 底层数据缓冲区的字节长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。 |

### OH_JSVM_GetPrototype()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetPrototype(JSVM_Env env,JSVM_Value object,JSVM_Value* result)
```

**描述**

返回对象的原型。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 表示待返回其原型的JavaScript object。这将返回Object.getPrototypeOf的等价值（与函数的prototype属性不同）。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示给定对象的原型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_GetTypedarrayInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetTypedarrayInfo(JSVM_Env env,JSVM_Value typedarray,JSVM_TypedarrayType* type,size_t* length,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)
```

**描述**

返回类型化数组的各种属性。如果不需要该属性，则任何输出参数都可以是 NULL。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) typedarray | 表示要查询其属性的TypedArray。 |
| [JSVM_TypedarrayType](capi-jsvm-types-h.md#jsvm_typedarraytype)* type | TypedArray中元素的标量数据类型。 |
| size_t* length | TypedArray中的元素数。 |
| void** data | TypedArray底层的数据缓冲区由byte_offset值调整，使其指向TypedArray中的第一个元素。如果数组的长度是0，这可能是NULL或任何其他指针值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* arraybuffer | 位于TypedArray下的ArrayBuffer。 |
| size_t* byteOffset | 数组的第一个元素所在的基础原生数组中的字节偏移量。data 参数的值已经过调整，因此data指向数组中的第一个元素。因此，原生数组的第一个字节将位于data - byte_offset。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。 |

### OH_JSVM_GetDataviewInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetDataviewInfo(JSVM_Env env,JSVM_Value dataview,size_t* bytelength,void** data,JSVM_Value* arraybuffer,size_t* byteOffset)
```

**描述**

返回DataView的各种属性。如果不需要某一属性，则任何出参都可以设置为NULL。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) dataview |  表示要查询其属性的DataView。 |
| size_t* bytelength | DataView中的字节个数。 |
| void** data | DataView下的数据缓冲区。如果bytelength是0则可能是NULL或任何其他指针值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* arraybuffer | ArrayBuffer是DataView的基础。 |
| size_t* byteOffset | 开始投影DataView的数据缓冲区中的字节偏移量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入参数非外部的JSVM_Value。 |

### OH_JSVM_GetDateValue()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetDateValue(JSVM_Env env,JSVM_Value value,double* result)
```

**描述**

返回与给定的JavaScript Date时间值等价的C双精度基础类型值。如果调用成功，返回JSVM_OK。如果传入一个非JavaScript Date类型的JSVM_Value，返回JSVM_DATA_EXPECTED。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表一个JavaScript Date。 |
| double* result | 作为double的时间值表示为自1970年1月1日UTC午夜以来的毫秒数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_DATE_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入参数不是Date类型。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_GetValueBool()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBool(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

返回与给定的JavaScript Boolean等价的C布尔基础类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表输入的JavaScript Boolean对象。 |
| bool* result | 返回与给定JavaScript Boolean对象等价的bool值，value对象值为true则result为true，反之亦然。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_BOOLEAN_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是boolean类型。 |

### OH_JSVM_GetValueDouble()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueDouble(JSVM_Env env,JSVM_Value value,double* result)
```

**描述**

返回与给定的JavaScript number等价的C双精度基础类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript number。 |
| double* result | 给定的JavaScript number的C双精度基础类型等价值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是number类型。 |

### OH_JSVM_GetValueBigintInt64()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintInt64(JSVM_Env env,JSVM_Value value,int64_t* result,bool* lossless)
```

**描述**

返回与给定的JavaScript BigInt等价的C int64_t基础类型值。如果需要，它将截断该值，将lossless设置为false。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript BigInt。 |
| int64_t* result | 给定的JavaScript BigInt的C int64_t基础类型等价值。 |
| bool* lossless | 指示BigInt值是否已无损转换。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是BitInt类型。 |

### OH_JSVM_GetValueBigintUint64()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintUint64(JSVM_Env env,JSVM_Value value,uint64_t* result,bool* lossless)
```

**描述**

返回与给定的JavaScript BigInt等价的C uint64_t基础类型值。如果需要，它将截断该值，将lossless设置为false。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript BigInt。 |
| uint64_t* result | 给定的JavaScript BigInt的C uint64_t基础类型等价值。 |
| bool* lossless | 指示BigInt值是否已无损转换。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是BitInt类型。 |

### OH_JSVM_GetValueBigintWords()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueBigintWords(JSVM_Env env,JSVM_Value value,int* signBit,size_t* wordCount,uint64_t* words)
```

**描述**

将单个BigInt值转换为符号位、64位小端数组和数组中的元素数。signBit和words参数可以都设置为NULL。这种情况下，只获取wordCount。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript BigInt。 |
| int* signBit | 表示JavaScript BigInt是正数还是负数的整数。 |
| size_t* wordCount | 必须初始化为words数组的长度。返回后，将被设置为存储此BigInt所需的实际字数。 |
| uint64_t* words | 指向预分配的64位字数组的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是BitInt类型。 |

### OH_JSVM_GetValueExternal()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueExternal(JSVM_Env env,JSVM_Value value,void** result)
```

**描述**

检索之前传递给OH_JSVM_CreateExternal()的外部数据指针。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript外部值。 |
| void** result | 指向被JavaScript外部值封装的数据的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入参数非外部的JSVM_Value。 |

### OH_JSVM_GetValueInt32()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt32(JSVM_Env env,JSVM_Value value,int32_t* result)
```

**描述**

返回与给定的JavaScript number等价的C int32基础类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript number。 |
| int32_t* result | 给定的JavaScript number的C int32基础类型等价值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是number类型。 |

### OH_JSVM_GetValueInt64()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueInt64(JSVM_Env env,JSVM_Value value,int64_t* result)
```

**描述**

返回与给定的JavaScript number等价的C int64基础类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript number。 |
| int64_t* result | 给定的JavaScript number的C int64基础类型等价值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是number类型。 |

### OH_JSVM_GetValueStringLatin1()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringLatin1(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)
```

**描述**

返回与传入值对应的ISO-8859-1编码字符串。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript number。 |
| char* buf | 写入ISO-8859-1编码字符串的缓冲区。如果传入NULL，则将在result中返回字符串的长度（以字节为单位，不包括null结束符）。 |
| size_t bufsize | 目的缓冲区大小。当大小不够时，返回的字符串将被截断并以null结尾。 |
| size_t* result | 复制到缓冲区中的字节数，不包括空终止符。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。 |

### OH_JSVM_GetValueStringUtf8()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf8(JSVM_Env env,JSVM_Value value,char* buf,size_t bufsize,size_t* result)
```

**描述**

返回与传入值对应的UTF8编码字符串。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript字符串。 |
| char* buf | 将UTF8编码的字符串写入的缓冲区。如果传入NULL，则在result中返回以字节为单位的字符串长度，不包括空终止符。 |
| size_t bufsize | 目标缓冲区的大小。当此值不足时，返回的字符串将被截断并以null终止。 |
| size_t* result | 复制到缓冲区的字节数，不包括null结束符。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。 |

### OH_JSVM_GetValueStringUtf16()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueStringUtf16(JSVM_Env env,JSVM_Value value,char16_t* buf,size_t bufsize,size_t* result)
```

**描述**

查询与传入值对应的UTF16编码字符串。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript字符串。 |
| char16_t* buf | 将UTF16-LE编码字符串写入的缓冲区。如果传入NULL，则返回字符串的2字节代码单元长度，不包括空终止符。 |
| size_t bufsize | 目标缓冲区的大小。当此值不足时，返回的字符串将被截断并以null终止。 |
| size_t* result | 复制到缓冲区中的2字节代码单元数，不包括空终止符。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。 |

### OH_JSVM_GetValueUint32()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetValueUint32(JSVM_Env env,JSVM_Value value,uint32_t* result)
```

**描述**

返回与给定的JavaScript number等价的C uint_32基础类型值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 代表JavaScript number。 |
| uint32_t* result | 将给定的JSVM_Value等效为uint32_t 的C基础类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是number类型。 |

### OH_JSVM_GetBoolean()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetBoolean(JSVM_Env env,bool value,JSVM_Value* result)
```

**描述**

返回表示给定布尔值的JavaScript单例对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| bool value | 要检索的布尔值，取值为true或false。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示待检索的JavaScript Boolean单例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetGlobal()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetGlobal(JSVM_Env env,JSVM_Value* result)
```

**描述**

返回global对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript global对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetNull()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetNull(JSVM_Env env,JSVM_Value* result)
```

**描述**

返回null对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript null对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetUndefined()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetUndefined(JSVM_Env env,JSVM_Value* result)
```

**描述**

返回Undefined对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript undefined值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CoerceToBool()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBool(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**描述**

实现抽象操作ToBoolean()。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 要强制转换的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表强制的JavaScript Boolean。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_CoerceToNumber()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToNumber(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**描述**

实现抽象操作ToNumber()。如果传入的值是对象，则函数可能会运行JavaScript代码。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 要强制转换的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表强制的JavaScript number。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_NUMBER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 如果传入的JavaScript值无法转换成Number。 |

### OH_JSVM_CoerceToObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToObject(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**描述**

实现抽象操作ToObject()。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 要强制转换的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表强制的JavaScript object。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 如果传入的JavaScript值无法转换成Object。 |

### OH_JSVM_CoerceToString()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToString(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**描述**

实现抽象操作ToString()。如果传入的值是对象，则函数可能会运行JavaScript代码。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 要强制转换的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表强制的JavaScript string。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 如果传入的JavaScript值无法转换成String。 |

### OH_JSVM_Typeof()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Typeof(JSVM_Env env,JSVM_Value value,JSVM_ValueType* result)
```

**描述**

提供类似于在定义的对象上调用typeof运算符的行为。不同点在于，该函数支持检测外部值；它将null检测为单独的类型，而ECMAScript typeof将用于检测object。如果value的类型无效，则返回错误。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 要查询其类型的JavaScript值。 |
| [JSVM_ValueType](capi-jsvm-types-h.md#jsvm_valuetype)* result | JavaScript值的类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。 |

### OH_JSVM_Instanceof()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Instanceof(JSVM_Env env,JSVM_Value object,JSVM_Value constructor,bool* result)
```

**描述**

提供类似于在对象上调用instanceof运算符的行为。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 要检查的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) constructor | 要检查的构造函数的JavaScript函数对象。 |
| bool* result | 如果object instanceof constructor为true，则设置为true的布尔值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_FUNCTION_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是Function类型。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_IsArray()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsArray(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

提供类似于在对象上调用IsArray的行为。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JavaScript值。 |
| bool* result | 表示给定的对象是否为数组。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_IsArraybuffer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

检查传入的对象是否为ArrayBuffer。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JavaScript值。 |
| bool* result | 表示指定的对象是否为ArrayBuffer。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_IsDate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsDate(JSVM_Env env,JSVM_Value value,bool* isDate)
```

**描述**

检查传入的Object是否为日期。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JavaScript值。 |
| bool* isDate | 给定的JSVM_Value是否表示JavaScript Date对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_IsTypedarray()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsTypedarray(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

检查传入的Object是否为类型化数组。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JavaScript值。 |
| bool* result | 给定的JSVM_Value是否代表TypedArray。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_IsDataview()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsDataview(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

检查传入的对象是否是DataView。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JavaScript值。 |
| bool* result | 给定的JSVM_Value是否代表DataView。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_StrictEquals()

```
JSVM_EXTERN JSVM_Status OH_JSVM_StrictEquals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)
```

**描述**

提供类似调用严格相等算法的行为。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) lhs | 待检查的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rhs | 要检查的JavaScript值。 |
| bool* result | 表示两个JSVM_Value对象是否严格相等（===）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_Equals()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Equals(JSVM_Env env,JSVM_Value lhs,JSVM_Value rhs,bool* result)
```

**描述**

提供类似调用宽松相等算法的行为。无论JavaScript值类型如何，只要值相等，就返回true。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) lhs | 待检查的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rhs | 要检查的JavaScript值。 |
| bool* result | 表示两个JSVM_Value对象是否宽松相等（==）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_DetachArraybuffer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DetachArraybuffer(JSVM_Env env,JSVM_Value arraybuffer)
```

**描述**

提供类似于调用ArrayBuffer detach操作的行为。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) arraybuffer | 待分离的JavaScript ArrayBuffer。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         如果[JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_DETACHABLE_ARRAYBUFFER_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是可分析的ArrayBuffer。 |

### OH_JSVM_IsDetachedArraybuffer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsDetachedArraybuffer(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

提供类似调用ArrayBuffer IsDetachedBuffer操作的行为。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JavaScript ArrayBuffer。 |
| bool* result | 表示ArrayBuffer是否被分离。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetPropertyNames()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_Value* result)
```

**描述**

以字符数数组的形式返回object的可枚举属性的名称。key为符号的object的属性将不会被包含在内。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待进行属性检索的对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示一个JavaScript值的数组，这些值表示对象的属性名称。可以使用OH_JSVM_GetArrayLength以及OH_JSVM_GetElement对结果进行迭代。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_GetAllPropertyNames()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetAllPropertyNames(JSVM_Env env,JSVM_Value object,JSVM_KeyCollectionMode keyMode,JSVM_KeyFilter keyFilter,JSVM_KeyConversion keyConversion,JSVM_Value* result)
```

**描述**

返回包含object所有可用属性名称的数组。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 从中检索属性的对象。 |
| [JSVM_KeyCollectionMode](capi-jsvm-types-h.md#jsvm_keycollectionmode) keyMode | 是否也检索原型属性。 |
| [JSVM_KeyFilter](capi-jsvm-types-h.md#jsvm_keyfilter) keyFilter | 要检索哪些属性（可枚举/可读/可写）。 |
| [JSVM_KeyConversion](capi-jsvm-types-h.md#jsvm_keyconversion) keyConversion | 表示是否将编号的属性键转换为字符串。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示JavaScript值的数组，这些值表示对象的属性名称。可以使用OH_JSVM_GetArrayLength和OH_JSVM_GetElement对结果进行迭代。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_SetProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value value)
```

**描述**

为传入的object设置名为key的属性。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 将进行属性设置的对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | 待设置的属性名。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 属性值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_GetProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,JSVM_Value* result)
```

**描述**

从传入的object中获取名为key的属性。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 从中检索属性的对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | 要检索的属性的名称。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 属性值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_HasProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_HasProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)
```

**描述**

检查传入的Object是否具有命名为key的属性。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待查询的对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | 要检查其存在的属性的名称。 |
| bool* result | 该属性是否存在于对象上。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_DeleteProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)
```

**描述**

尝试从object中删除名为key的属性。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待查询的对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | 待删除的属性名。 |
| bool* result | 表示属性删除是否成功。result可以选择性地通过传递NULL来忽略。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_HasOwnProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_HasOwnProperty(JSVM_Env env,JSVM_Value object,JSVM_Value key,bool* result)
```

**描述**

检查传入的Object是否具有名为key的属性。key必须是string或symbol，否则将抛出错误。JSVM-API不会执行任何数据类型之间的转换。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待查询的对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) key | 要检查的是否存在的属性名称。 |
| bool* result | 表示对象是否存在该属性。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_NAME_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示期望传入名字不合法。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_SetNamedProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value value)
```

**描述**

此方法等效于object调用OH_JSVM_SetProperty设置名为`utf8Name`的属性。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 要对其设置属性的对象。 |
| const char* utf8name | 要设置的属性的名称。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 属性值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_GetNamedProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,JSVM_Value* result)
```

**描述**

此方法等效于object调用OH_JSVM_GetProperty获取名为`utf8Name`的属性对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 从中检索属性的对象。 |
| const char* utf8name | 要获取的属性名。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 属性值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_HasNamedProperty()

```
JSVM_EXTERN JSVM_Status OH_JSVM_HasNamedProperty(JSVM_Env env,JSVM_Value object,const char* utf8name,bool* result)
```

**描述**

此方法等效于object对象调用OH_JSVM_HasProperty查询其内部是否存在名为`utf8Name`的属性。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待查询的对象。 |
| const char* utf8name | 待检查的属性名。 |
| bool* result | 该属性是否存在于对象上。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_SetElement()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value value)
```

**描述**

在传入的Object上设置一个元素。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待进行属性设置的对象。 |
| uint32_t index | 要设置的属性的索引。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 属性值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_GetElement()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetElement(JSVM_Env env,JSVM_Value object,uint32_t index,JSVM_Value* result)
```

**描述**

获取请求索引处的元素。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待进行属性检索的对象。 |
| uint32_t index | 要获取的属性的索引。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 属性值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_HasElement()

```
JSVM_EXTERN JSVM_Status OH_JSVM_HasElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)
```

**描述**

如果传入的Object在指定的索引处有一个元素，则此JSVM-API返回true。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待查询的对象。 |
| uint32_t index | 待确定是否存在元素的索引位置。 |
| bool* result | 该属性是否存在于对象上。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_DeleteElement()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DeleteElement(JSVM_Env env,JSVM_Value object,uint32_t index,bool* result)
```

**描述**

尝试从object中删除指定index处的元素。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待查询的对象。 |
| uint32_t index | 要删除的属性的索引。 |
| bool* result | 表示元素删除是否成功。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_DefineProperties()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DefineProperties(JSVM_Env env,JSVM_Value object,size_t propertyCount,const JSVM_PropertyDescriptor* properties)
```

**描述**

通过此方法可以在给定对象上高效定义多个属性，这些属性使用属性描述符进行定义。通过一个属性描述符的数组，此API将为对象依次设置数组中的属性。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待进行属性检索的对象。 |
| size_t propertyCount | properties数组中的元素数。 |
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | 属性描述符的数组。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_ObjectFreeze()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectFreeze(JSVM_Env env,JSVM_Value object)
```

**描述**

冻结指定的对象，防止为其添加新的属性、删除现有属性、更改现有属性的可枚举性/可配置性/可写性、更改现有属性的值、改变对象原型等操作。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待冻结的对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_ObjectSeal()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSeal(JSVM_Env env,JSVM_Value object)
```

**描述**

封装指定的对象，防止为其添加新的属性并将所有现有属性标记为不可配置。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 待封装的对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_CallFunction()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CallFunction(JSVM_Env env,JSVM_Value recv,JSVM_Value func,size_t argc,const JSVM_Value* argv,JSVM_Value* result)
```

**描述**

支持从native代码调用JavaScript函数对象，这是从native代码回调到JavaScript的主要机制。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) recv | 传递给被调用函数的this值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) func | 表示将调用的JavaScript函数。 |
| size_t argc | argv数组中的元素个数。 |
| [const JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | JSVM_values数组，表示将作为参数传递给函数的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示返回的JavaScript对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_CreateFunction()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunction(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback cb,JSVM_Value* result)
```

**描述**

支持在native代码中创建函数对象，这是从JavaScript调用native代码的主要机制。在此调用之后，新创建的函数在脚本中不再自动可见。相反，必须在JavaScript可见的任何对象上显示设置属性，才能从脚本访问该函数。

**起始版本：** 11


**参数：**

| 参数项                                                               | 描述 |
|-------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                         | 调用JSVM-API的环境。 |
| const char* utf8name                                              | 编码为UTF8的函数的可选名称。这在JavaScript中是可见的，作为新函数对象的name属性。 |
| size_t length                                                     | utf8name的长度（以字节为单位）或JSVM_AUTO_LENGTH（如果以 null 结尾）。 |
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) cb          | 调用此函数对象时应调用的native函数。详情请参考[JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md)。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示新创建函数的JavaScript函数对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_GetCbInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetCbInfo(JSVM_Env env,JSVM_CallbackInfo cbinfo,size_t* argc,JSVM_Value* argv,JSVM_Value* thisArg,void** data)
```

**描述**

此方法在回调函数中用于检索有关调用的详细信息，例如来自给定回调信息的参数和this指针。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_CallbackInfo](capi-jsvm-jsvm-callbackinfo--8h.md) cbinfo | 传入回调函数的回调信息。 |
| size_t* argc | 指定所提供的argv数组的长度并接收参数的实际数量，可以通过传递NULL来选择性地忽略。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | JSVM_Value的C数组，用于存储复制的参数。如果参数数量超过提供的数量，则只复制请求数量的参数。如果提供的参数比声明的少，则argv的其余部分将由代表undefined的JSVM_Value值填充。可以通过传递NULL来忽略argv。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* thisArg | 接收调用的JavaScript this参数。thisArg可以通过传递NULL来进行忽略。 |
| void** data | 接收回调的数据指针。data可以通过传递NULL来进行忽略。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetNewTarget()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetNewTarget(JSVM_Env env,JSVM_CallbackInfo cbinfo,JSVM_Value* result)
```

**描述**

返回构造函数调用的new target。如果当前回调不是构造函数调用，结果为NULL。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_CallbackInfo](capi-jsvm-jsvm-callbackinfo--8h.md) cbinfo | 传递给回调函数的回调信息。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 构造函数调用的new target。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_NewInstance()

```
JSVM_EXTERN JSVM_Status OH_JSVM_NewInstance(JSVM_Env env,JSVM_Value constructor,size_t argc,const JSVM_Value* argv,JSVM_Value* result)
```

**描述**

使用给定的JSVM_Value表示的构造函数来实例化新的JavaScript值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) constructor | 表示将作为构造函数调用的JavaScript函数。 |
| size_t argc | argv数组中的元素个数。 |
| [const JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | JavaScript值数组。其中JSVM_Value表示构造函数的参数。如果argc为零，则可以通过传入NULL来忽略此参数。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示返回的JavaScript对象，在本例中是构造的对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_DefineClass()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClass(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value* result)
```

**描述**

定义一个JavaScript类。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* utf8name | JavaScript构造函数的名称，建议在包装C++类时使用C++类名。 |
| size_t length | utf8name的长度（以字节为单位）或JSVM_AUTO_LENGTH（如果以 null 结尾）。 |
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) constructor | 用于创建类的构造函数的回调函数。包装C++类时，此方法必须是符合JSVM_Callback。callback签名的静态成员。不能使用C++类构造函数。详情请参考[JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md)。 |
| size_t propertyCount | properties数组参数中的项数。 |
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | 类的属性描述符，用于定义类的属性和方法。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示类的构造函数的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_Wrap()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Wrap(JSVM_Env env,JSVM_Value jsObject,void* nativeObject,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)
```

**描述**

在JavaScript对象中封装native实例，该实例后续可以通过OH_JSVM_Unwrap()进行检索。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | 将成为原生对象封装器的JavaScript对象。 |
| void* nativeObject | 将封装在JavaScript对象中的native实例。 |
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | 可选的原生回调，可用于在 JavaScript 对象被垃圾回收时释放native实例。 |
| void* finalizeHint | 传递给完成回调的可选上下文提示。 |
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | 对封装对象的可选引用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_Unwrap()

```
JSVM_EXTERN JSVM_Status OH_JSVM_Unwrap(JSVM_Env env,JSVM_Value jsObject,void** result)
```

**描述**

当JavaScript代码调用类的方法或属性访问器时，对应的JSVM_Callback将被调用。如果回调是针对实例方法或访问器的，则回调的this参数是封装器对象；然后可以通过调用封装器对象的OH_JSVM_Unwrap()获得作为调用目标的C++实例。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | 与native实例关联的对象。 |
| void** result | 指向封装的native实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_RemoveWrap()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RemoveWrap(JSVM_Env env,JSVM_Value jsObject,void** result)
```

**描述**

使用OH_JSVM_Wrap()检索先前封装在JavaScript对象——js_object中的native实例并移除封装。如果finalize回调与封装相关联，则当JavaScript对象被垃圾回收时将不再调用它。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | 与native实例关联的对象。 |
| void** result | 指向封装的native实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_TypeTagObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_TypeTagObject(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag)
```

**描述**

将typeTag指针的值与JavaScript对象或外部值相关联。可调用OH_JSVM_CheckObjectTypeTag()判断附加在对象上的标记类型，以确保对象的类型正确。如果对象已经有关联的类型标记，则返回JSVM_INVALID_ARG。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 要标记的JavaScript对象或外部值。 |
| [const JSVM_TypeTag](capi-jsvm-jsvm-typetag.md)* typeTag | 要标记对象的标签。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_CheckObjectTypeTag()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CheckObjectTypeTag(JSVM_Env env,JSVM_Value value,const JSVM_TypeTag* typeTag,bool* result)
```

**描述**

将类型标签typeTag与JavaScript对象或外部值上的标签作对比。如果找到相同标签，设置result为true，否则为false。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查类型标记的JavaScript对象或外部值。 |
| [const JSVM_TypeTag](capi-jsvm-jsvm-typetag.md)* typeTag | 用于比较在对象上找到的任何标签的标签。 |
| bool* result | 表示指定的类型标记是否与对象上的类型标记匹配。如果在对象上找不到该类型标记，也会返回false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_AddFinalizer()

```
JSVM_EXTERN JSVM_Status OH_JSVM_AddFinalizer(JSVM_Env env,JSVM_Value jsObject,void* finalizeData,JSVM_Finalize finalizeCb,void* finalizeHint,JSVM_Ref* result)
```

**描述**

为JavaScript对象添加JSVM_Finalize回调，当JavaScript对象被垃圾回收时调用该回调函数。可以在单个JavaScript对象上多次调用OH_JSVM_AddFinalizer。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsObject | 关联native数据的JavaScript对象。 |
| void* finalizeData | 要传递给finalizeCb的可选数据。 |
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCb | 当JavaScript对象被垃圾回收时，将用于释放native数据的原生回调。JSVM_Finalize提供了更多详细信息。 |
| void* finalizeHint | 传递给finalize回调的可选上下文提示。 |
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | 可选的对JavaScript对象的引用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不合法。 |

### OH_JSVM_GetVersion()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetVersion(JSVM_Env env,uint32_t* result)
```

**描述**

返回JSVM运行时支持的最高JSVM-API版本。后续将新增JSVM-API，以便支持更多的功能。引入该API的目的：在支持某功能的JSVM版本，可以使用新的功能；在不支持某功能的JSVM版本，可以提供回调行为。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| uint32_t* result | 支持的最高版本的JSVM-API。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetVMInfo()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetVMInfo(JSVM_VMInfo* result)
```

**描述**

返回虚拟机的信息。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VMInfo](capi-jsvm-jsvm-vminfo.md)* result | 虚拟机的信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_AdjustExternalMemory()

```
JSVM_EXTERN JSVM_Status OH_JSVM_AdjustExternalMemory(JSVM_Env env,int64_t changeInBytes,int64_t* result)
```

**描述**

此函数将因JavaScript对象而保持活跃的外部分配的内存大小通知给底层虚拟机。注册外部分配的内存将比其他方式更频繁地触发全局垃圾回收。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| int64_t changeInBytes | 因JavaScript对象而保持活动状态的外部分配内存的变化。 |
| int64_t* result | 调整值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_MemoryPressureNotification()

```
JSVM_EXTERN JSVM_Status OH_JSVM_MemoryPressureNotification(JSVM_Env env,JSVM_MemoryPressureLevel level)
```

**描述**

通知虚拟机系统内存不足并有选择地触发垃圾回收。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_MemoryPressureLevel](capi-jsvm-types-h.md#jsvm_memorypressurelevel) level | 要为当前虚拟机设置的内存压力等级。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreatePromise()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreatePromise(JSVM_Env env,JSVM_Deferred* deferred,JSVM_Value* promise)
```

**描述**

创建一个延迟对象和一个JavaScript promise。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Deferred](capi-jsvm-jsvm-deferred--8h.md)* deferred | 一个新创建的延迟对象，后续可以传递给OH_JSVM_ResolveDeferred()或OH_JSVM_RejectDeferred()以解析resp。或拒绝相关的Promise。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* promise | 与延迟对象关联的JavaScript Promise。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_ResolveDeferred()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ResolveDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value resolution)
```

**描述**

通过与之关联的延迟对象来解析JavaScript promise。它只能用于解析对应的可用的延迟对象的JavaScript Promise。这意味着Promise必须使用OH_JSVM_CreatePromise()创建，并且从该调用返回的对象必须保留，才能将其传递给此API。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Deferred](capi-jsvm-jsvm-deferred--8h.md) deferred | 要解析其关联promise的延迟对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) resolution | 用来解决Promise的值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_RejectDeferred()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RejectDeferred(JSVM_Env env,JSVM_Deferred deferred,JSVM_Value rejection)
```

**描述**

通过与之关联的延迟对象来拒绝JavaScript Promise。它只能用于拒绝对应的可用延迟对象的JavaScript Promise。这意味着Promise必须使用OH_JSVM_CreatePromise()创建，并且从该调用返回的对象必须保留，才能将其传递给此API。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Deferred](capi-jsvm-jsvm-deferred--8h.md) deferred | 要解析其关联promise的延迟对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) rejection | 用来拒绝Promise的值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_IsPromise()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsPromise(JSVM_Env env,JSVM_Value value,bool* isPromise)
```

**描述**

查询Promise是否为原生Promise对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的值。 |
| bool* isPromise | 表示是否为原生Promise对象（即底层引擎创建的promise对象）的标志。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_PromiseRegisterHandler()

```
JSVM_EXTERN JSVM_Status OH_JSVM_PromiseRegisterHandler(JSVM_Env env,JSVM_Value promise,JSVM_Value onFulfilled,JSVM_Value onRejected,JSVM_Value* result)
```

**描述**

注册 处理Promise兑现/拒绝的 回调函数。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) promise | 需要注册回调的 promise。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) onFulfilled | 该函数在 promise 兑现后调用。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) onRejected | 该函数在 promise 拒绝后调用。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，返回 promise 调用 then/catch 接口后生成的新的 promise。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 如果 env 或 promise 为空，或 onFulfilled 和 onRejected 同时为空。<br>         [JSVM_INVALID_TYPE](capi-jsvm-types-h.md#jsvm_status) 如果 promise 非 JS 的 Promise 类型，或 onFulfilled、onRejected 非 JS 的 Function 类型。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 如果存在 JS 异常待处理。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 如果 API 执行错误。 |

### OH_JSVM_JsonParse()

```
JSVM_EXTERN JSVM_Status OH_JSVM_JsonParse(JSVM_Env env,JSVM_Value jsonString,JSVM_Value* result)
```

**描述**

解析JSON字符串，并返回成功解析的值。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsonString | 待解析的字符串。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 成功解析的值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的参数不是string类型。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_JsonStringify()

```
JSVM_EXTERN JSVM_Status OH_JSVM_JsonStringify(JSVM_Env env,JSVM_Value jsonObject,JSVM_Value* result)
```

**描述**

将对象字符串化，并返回成功转换后的字符串。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) jsonObject | 待字符串化的对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 成功转换后返回的字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。 |

### OH_JSVM_CreateSnapshot()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSnapshot(JSVM_VM vm,size_t contextCount,const JSVM_Env* contexts,const char** blobData,size_t* blobSize)
```

**描述**

创建虚拟机的启动快照。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 目标环境，API接口将在该环境下调用。 |
| size_t contextCount | 上下文个数。 |
| [const JSVM_Env](capi-jsvm-jsvm-env--8h.md)* contexts | 要添加到快照的上下文数组。 |
| const char** blobData | 快照数据。 |
| size_t* blobSize | 快照数据的大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_GetHeapStatistics()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetHeapStatistics(JSVM_VM vm,JSVM_HeapStatistics* result)
```

**描述**

返回一组虚拟机堆的统计数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 返回堆统计信息的虚拟机。 |
| [JSVM_HeapStatistics](capi-jsvm-jsvm-heapstatistics.md)* result | 堆统计数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_StartCpuProfiler()

```
JSVM_EXTERN JSVM_Status OH_JSVM_StartCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler* result)
```

**描述**

创建并启动一个CPU profiler。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 启动CPU profiler的虚拟机。 |
| [JSVM_CpuProfiler](capi-jsvm-jsvm-cpuprofiler--8h.md)* result | 指向CPU profiler的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_StopCpuProfiler()

```
JSVM_EXTERN JSVM_Status OH_JSVM_StopCpuProfiler(JSVM_VM vm,JSVM_CpuProfiler profiler,JSVM_OutputStream stream,void* streamData)
```

**描述**

停止CPU profiler并将结果输出到流。

**起始版本：** 12


**参数：**

| 参数项                                                                | 描述 |
|--------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                             | 启动CPU profiler的虚拟机。 |
| [JSVM_CpuProfiler](capi-jsvm-jsvm-cpuprofiler--8h.md) profiler     | 要停止的CPU profiler。 |
| [JSVM_OutputStream](capi-jsvm-types-h.md#jsvm_outputstream) stream | 接收数据的输出流回调。 |
| void* streamData                                                   | 传递给输出流回调的可选数据。例如，可以是一个文件流，用来将输出流回调中传递的采样数据写入文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_TakeHeapSnapshot()

```
JSVM_EXTERN JSVM_Status OH_JSVM_TakeHeapSnapshot(JSVM_VM vm,JSVM_OutputStream stream,void* streamData)
```

**描述**

获取当前堆快照并将其输出到流。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 将被获取堆快照的虚拟机。 |
| [JSVM_OutputStream](capi-jsvm-types-h.md#jsvm_outputstream) stream | 接收数据的输出流回调。 |
| void* streamData | 传递给输出流回调的可选数据。例如，可以是一个文件流，用来将输出流回调中传递的采样数据写入文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_OpenInspector()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspector(JSVM_Env env,const char* host,uint16_t port)
```

**描述**

在指定的主机和端口上激活inspector，将用来调试JS代码。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* host | 要监听inspector连接的主机IP地址。 |
| uint16_t port | 要监听inspector连接的端口。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_CloseInspector()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CloseInspector(JSVM_Env env)
```

**描述**

尝试关闭剩余的所有inspector连接。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_WaitForDebugger()

```
JSVM_EXTERN JSVM_Status OH_JSVM_WaitForDebugger(JSVM_Env env,bool breakNextLine)
```

**描述**

等待主机与inspector建立socket连接，连接建立后程序将继续运行。发送Runtime.runIfWaitingForDebugger命令。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| bool breakNextLine | 是否在下一行JavaScript代码中中断。breakNextLine为true将暂停运行下一行JS代码，开发者需要通过调试器的调试按钮控制JS继续执行。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_DefineClassWithPropertyHandler()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithPropertyHandler(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_PropertyHandlerCfg propertyHandlerCfg,JSVM_Callback callAsFunctionCallback,JSVM_Value* result)
```

**描述**

定义一个具有给定类名、构造函数、属性和回调处理程序的JavaScript类，属性操作包括getter、setter、deleter、enumerator等，并作为函数回调进行调用。

**起始版本：** 12


**参数：**

| 参数项                                                                               | 描述 |
|-----------------------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                                         | 调用JSVM-API的环境。 |
| const char* utf8name                                                              | JavaScript类构造函数的名称。 |
| size_t length                                                                     | utf8name的长度（以字节为单位）或JSVM_AUTO_LENGTH（如果以 null 结尾）。 |
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) constructor                     | 用于创建类的构造函数的回调函数。此方法必须是JSVM_Callback类型。constructor中callback回调需为静态成员。不能使用C++类构造函数。详情请参考[JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md)。 |
| size_t propertyCount                                                              | properties数组参数中的项数。 |
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | 描述静态数据和实例数据的属性描述符数组类上的属性、访问器和方法请参考JSVM_PropertyDescriptor。 |
| [JSVM_PropertyHandlerCfg](capi-jsvm-jsvm-propertyhandlerconfigurationstruct.md) propertyHandlerCfg                                    | 访问实例对象属性触发相应的回调函数。 |
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) callAsFunctionCallback          | 将实例对象作为函数调用将触发此回调。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result                 | 表示JavaScript类的构造函数的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示执行的过程中产生了JS异常。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示有未知的原因导致执行失败。 |

### OH_JSVM_IsUndefined()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsUndefined(JSVM_Env env,JSVM_Value value,bool* isUndefined)
```

**描述**

此API检查传入的值是否为Undefined。这相当于JS中的`value === undefined`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isUndefined | 表示给定的JSVM_Value是否为Undefined。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_IsNull()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsNull(JSVM_Env env,JSVM_Value value,bool* isNull)
```

**描述**

此API检查传入的值是否为Null对象。这相当于JS中的`value === null`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isNull | 表示给定的JSVM_Value是否为Null。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_IsNullOrUndefined()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsNullOrUndefined(JSVM_Env env,JSVM_Value value,bool* isNullOrUndefined)
```

**描述**

此API检查传入的值是否为Null或Undefined。这相当于JS中的`value == null`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isNullOrUndefined | 表示给定的JSVM_Value是否为Null或Undefined。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_IsBoolean()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsBoolean(JSVM_Env env,JSVM_Value value,bool* isBoolean)
```

**描述**

此API检查传入的值是否为Boolean。这相当于JS中的`typeof value === 'boolean'`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isBoolean | 表示给定的JSVM_Value是否为Boolean。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_IsNumber()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsNumber(JSVM_Env env,JSVM_Value value,bool* isNumber)
```

**描述**

此API检查传入的值是否为Number。这相当于JS中的`typeof value === 'number'`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isNumber | 表示给定的JSVM_Value是否为Number。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_IsString()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsString(JSVM_Env env,JSVM_Value value,bool* isString)
```

**描述**

此API检查传入的值是否为String。这相当于JS中的`typeof value === 'string'`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isString | 表示给定的JSVM_Value是否为String。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_IsSymbol()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbol(JSVM_Env env,JSVM_Value value,bool* isSymbol)
```

**描述**

此API检查传入的值是否为Symbol。这相当于JS中的`typeof value === 'symbol'`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isSymbol | 表示给定的JSVM_Value是否为Symbol。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_IsFunction()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsFunction(JSVM_Env env,JSVM_Value value,bool* isFunction)
```

**描述**

此API检查传入的值是否为Function。这相当于JS中的`typeof value === 'function'`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isFunction | 表示给定的JSVM_Value是否为Function。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_IsObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsObject(JSVM_Env env,JSVM_Value value,bool* isObject)
```

**描述**

此API检查传入的值是否为Object。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isObject | 表示给定的JSVM_Value是否为Object。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_IsBigInt()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsBigInt(JSVM_Env env,JSVM_Value value,bool* isBigInt)
```

**描述**

此API检查传入的值是否为BigInt。这相当于JS中的`typeof value === 'bigint'`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isBigInt | 表示给定的JSVM_Value是否为BigInt。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功，这个API不会触发任何异常。 |

### OH_JSVM_CreateMap()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateMap(JSVM_Env env, JSVM_Value* result)
```

**描述**

此API返回与JavaScript Map类型对应的JavaScript值。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript Map的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示输入参数不合法。 |

### OH_JSVM_IsMap()

```
JSVM_Status JSVM_CDECL OH_JSVM_IsMap(JSVM_Env env,JSVM_Value value,bool* isMap)
```

**描述**

此API检查传入的值是否为Map。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isMap | 给定的值是否为Map。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示输入参数不合法。 |

### OH_JSVM_IsConstructor()

```
JSVM_Status JSVM_CDECL OH_JSVM_IsConstructor(JSVM_Env env,JSVM_Value value,bool* isConstructor)
```

**描述**

此API检查传入的值是否为构造函数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* isConstructor | 给定的值是否为构造函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示输入参数不合法。 |

### OH_JSVM_CreateRegExp()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateRegExp(JSVM_Env env,JSVM_Value value,JSVM_RegExpFlags flags,JSVM_Value* result)
```

**描述**

此API返回与输入的JavaScript字符串对应的正则表达式对象。接口可能会抛出异常。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 要转换为正则表达式的JavaScript字符串。 |
| [JSVM_RegExpFlags](capi-jsvm-types-h.md#jsvm_regexpflags) flags | 正则表达式标志位。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 代表JavaScript RegExp的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示输入参数不合法。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示API在运行时抛出异常。 |

### OH_JSVM_ObjectGetPrototypeOf()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectGetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value* result)
```

**描述**

获取JavaScript object的原型。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object |  表示待返回其原型的JavaScript object。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示给定对象的原型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示输入参数不合法。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示API在运行时抛出异常。 |

### OH_JSVM_ObjectSetPrototypeOf()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ObjectSetPrototypeOf(JSVM_Env env,JSVM_Value object,JSVM_Value prototype)
```

**描述**

设置给定的JavaScript object的原型。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 表示需要设置原型的JavaScript object。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) prototype | 对象原型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示输入参数不合法。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示设置原型失败。如循环设置原型时，会触发该失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示API在运行时抛出异常。 |

### OH_JSVM_CreateSet()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateSet(JSVM_Env env,JSVM_Value* result)
```

**描述**

创建JavaScript Set对象。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示已经创建的JavaScript Set对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示输入参数不合法。 |

### OH_JSVM_IsSet()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsSet(JSVM_Env env,JSVM_Value value,bool* isSet)
```

**描述**

判断给定的对象是否是Set类型。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的对象。 |
| bool* isSet | 给定的对象是否是Set类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示输入参数不合法。 |

### OH_JSVM_CoerceToBigInt()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CoerceToBigInt(JSVM_Env env,JSVM_Value value,JSVM_Value* result)
```

**描述**

实现抽象操作`ToBigInt()`。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用该JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 要进行强制转换的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示成功转换成BigInt后的JavaScript值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_BIGINT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 如果传入的JavaScript值无法转换成BitInt。 |

### OH_JSVM_IsRegExp()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsRegExp(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

此API检查传入的值是否为JavaScript RegExp对象。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的JSVM_Value。 |
| bool* result | 表示给定的JSVM_Value是否为JavaScript RegExp对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_CreateFunctionWithScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateFunctionWithScript(JSVM_Env env,const char* funcName,size_t length,size_t argc,const JSVM_Value* argv,JSVM_Value script,JSVM_Value* result)
```

**描述**

创建一个以给定JavaScript为函数体的函数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| const char* funcName | 包含函数名称的字符串。如果传入NULL，则创建一个匿名函数。 |
| size_t length | funcName的长度（以字节为单位）或JSVM_AUTO_LENGTH（如果以 null 结尾）。 |
| size_t argc | argv数组中的元素个数。 |
| [const JSVM_Value](capi-jsvm-jsvm-value--8h.md)* argv | JSVM_values数组，表示将作为参数传递给函数的JavaScript值。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) script | 包含作为函数体的JavaScript字符串。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 表示新创建函数的JavaScript函数对象的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示输入的JavaScript无法编译成功。 |

### OH_JSVM_PumpMessageLoop()

```
JSVM_EXTERN JSVM_Status OH_JSVM_PumpMessageLoop(JSVM_VM vm,bool* result)
```

**描述**

启动虚拟机内任务队列，这个任务队列可以通过外部事件循环执行。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 启动任务队列的虚拟机实例。 |
| bool* result | 表示任务队列是否成功启动。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回JSVM函数结果代码。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_PerformMicrotaskCheckpoint()

```
JSVM_EXTERN JSVM_Status OH_JSVM_PerformMicrotaskCheckpoint(JSVM_VM vm)
```

**描述**

检查队列中是否有微任务等待，如果存在则执行它们。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 要检查微任务的虚拟机实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回JSVM函数结果代码。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_RetainScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RetainScript(JSVM_Env env, JSVM_Script script)
```

**描述**

持久保存一个JSVM_Script并将其生命周期延长到当前作用域之外。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用该API的环境。 |
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | 包含要持久化保存脚本的JavaScript字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示脚本为空或已被保存过。 |

### OH_JSVM_ReleaseScript()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseScript(JSVM_Env env, JSVM_Script script)
```

**描述**

释放由 OH_JSVM_RetainScript 保留的脚本，释放后应避免对传入 script 的再次使用。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用该API的环境。 |
| [JSVM_Script](capi-jsvm-jsvm-script--8h.md) script | 包含要释放的脚本的JavaScript字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示脚本为空或未被保存过。 |

### OH_JSVM_OpenInspectorWithName()

```
JSVM_EXTERN JSVM_Status OH_JSVM_OpenInspectorWithName(JSVM_Env env,int pid,const char* name)
```

**描述**

打开一个名为 name 的 inspector，为其打开对应 pid 的 unix domain 端口。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用该API的环境。 |
| int pid | 用于标识 inspector 连接的进程ID。 |
| const char* name | inspector 的名字。 如果传入nullptr, 则默认名称为jsvm。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示发生了异常。 |

### OH_JSVM_CompileWasmModule()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmModule(JSVM_Env env,const uint8_t *wasmBytecode,size_t wasmBytecodeLength,const uint8_t *cacheData,size_t cacheDataLength,bool *cacheRejected,JSVM_Value *wasmModule)
```

**描述**

将 WebAssembly 字节码编译得到一个 WebAssembly 模块。如果提供了 WebAssembly 缓存，则会先尝试对缓存进行反序列化。如果没有 JIT 权限支持，则打印一行日志提示开发者。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| const uint8_t *wasmBytecode | WebAssembly 字节码。 |
| size_t wasmBytecodeLength | WebAssembly 字节码的长度，单位：字节。 |
| const uint8_t *cacheData | 可选的 WebAssembly 缓存。 |
| size_t cacheDataLength | 可选的 WebAssembly 缓存长度，单位：字节。 |
| bool *cacheRejected | 输出参数，表示提供的 WebAssembly 缓存是否被引擎拒绝。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) *wasmModule | 输出参数，表示生成的 WebAssembly 模块。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示 env 或 wasmBytecode 参数为空，或传入的数据长度参数无效。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示编译失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示发生了异常。<br>         [JSVM_JIT_MODE_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示当前环境没有 JIT 权限支持。 |

### OH_JSVM_CompileWasmFunction()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CompileWasmFunction(JSVM_Env env,JSVM_Value wasmModule,uint32_t functionIndex,JSVM_WasmOptLevel optLevel)
```

**描述**

对当前 WebAssembly 模块中指定索引的函数进行指定优化等级的编译优化。如果没有 JIT 权限支持，则打印一行日志提示开发者。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) wasmModule | 待编译函数所在的 WebAssembly 模块。 |
| uint32_t functionIndex | 待编译函数的索引，索引必须位于合法范围。 |
| [JSVM_WasmOptLevel](capi-jsvm-types-h.md#jsvm_wasmoptlevel) optLevel | 优化等级，当前只支持高优化等级。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示 env 或 wasmModule 参数为空，或 wasmModule 不是一个真正的 WebAssembly 模块。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示函数索引越界，或编译失败。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示发生了异常。<br>         [JSVM_JIT_MODE_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示当前环境没有 JIT 权限支持。 |

### OH_JSVM_IsWasmModuleObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsWasmModuleObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

判断给定的 JSVM_Value 是否是一个 WebAssembly 模块。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的 JavaScript 值。 |
| bool* result | 输出参数，表示给定的值是否是一个 WebAssembly 模块。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_CreateWasmCache()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateWasmCache(JSVM_Env env,JSVM_Value wasmModule,const uint8_t** data,size_t* length)
```

**描述**

为给定的 WebAssembly 模块生成缓存。如果没有 JIT 权限支持，则打印一行日志提示开发者。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) wasmModule | 编译好的 WebAssembly 模块。 |
| const uint8_t** data | 输出参数，表示生成的 WebAssembly 缓存。 |
| size_t* length | 输出参数，表示生成的 WebAssembly 缓存的长度，单位：字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示缓存生成失败。<br>         [JSVM_JIT_MODE_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示当前环境没有 JIT 权限支持。 |

### OH_JSVM_ReleaseCache()

```
JSVM_EXTERN JSVM_Status OH_JSVM_ReleaseCache(JSVM_Env env,const uint8_t* cacheData,JSVM_CacheType cacheType)
```

**描述**

释放给定类型的缓存数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| const uint8_t* cacheData | 待释放的缓存数据，重复释放是未定义行为。 |
| [JSVM_CacheType](capi-jsvm-types-h.md#jsvm_cachetype) cacheType | 缓存的类型，缓存的生成和释放必须一一对应。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数，或 cacheType 参数不合法。 |

### OH_JSVM_IsBigIntObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsBigIntObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

判断给定的 JSVM_Value 是否是一个 BigInt对象。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的 JavaScript 值。 |
| bool* result | 输出参数，表示给定的值是否是一个BigInt对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_IsBooleanObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsBooleanObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

判断给定的 JSVM_Value 是否是一个 Boolean对象。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的 JavaScript 值。 |
| bool* result | 输出参数，表示给定的值是否是一个Boolean对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_IsStringObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsStringObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

判断给定的 JSVM_Value 是否是一个 String对象。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的 JavaScript 值。 |
| bool* result | 输出参数，表示给定的值是否是一个String对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_IsNumberObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsNumberObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

判断给定的 JSVM_Value 是否是一个 Number对象。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的 JavaScript 值。 |
| bool* result | 输出参数，表示给定的值是否是一个Number对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_IsSymbolObject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_IsSymbolObject(JSVM_Env env,JSVM_Value value,bool* result)
```

**描述**

判断给定的 JSVM_Value 是否是一个 Symbol对象。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 待检查的 JavaScript 值。 |
| bool* result | 输出参数，表示给定的值是否是一个Symbol对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolAsyncIterator()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolAsyncIterator(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.AsyncIterator能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.AsyncIterator。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolHasInstance()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolHasInstance(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.HasInstance能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.HasInstance。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolIsConcatSpreadable()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIsConcatSpreadable(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.IsConcatSpreadable能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.IsConcatSpreadable。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolMatch()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolMatch(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.Match能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.Match。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolReplace()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolReplace(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.Replace能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.Replace。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolSearch()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSearch(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.Search能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.Search。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolSplit()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolSplit(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.Split能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.Split。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolToPrimitive()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToPrimitive(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.ToPrimitive能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.ToPrimitive。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolUnscopables()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolUnscopables(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.Unscopables能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.Unscopables。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolToStringTag()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolToStringTag(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.ToStringTag能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.ToStringTag。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_GetSymbolIterator()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetSymbolIterator(JSVM_Env env, JSVM_Value* result)
```

**描述**

获取Well-Known symbol里的Symbol.Iterator能力。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 输出参数，Well-Known symbol里的Symbol.Iterator。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入了空指针参数。 |

### OH_JSVM_TraceStart()

```
JSVM_EXTERN JSVM_Status OH_JSVM_TraceStart(size_t count,const JSVM_TraceCategory* categories,const char* tag,size_t eventsCount)
```

**描述**

对所有 JSVM 运行时实例，开始采集指定 Trace 类别的信息（线程不安全）。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| size_t count | 进行 Trace 采集的分类数量。 |
| [const JSVM_TraceCategory](capi-jsvm-types-h.md#jsvm_tracecategory)* categories | 进行 Trace 采集的具体分类数组。 |
| const char* tag | 用户定义并赋予 Trace 数据的标签。 |
| size_t eventsCount | 存储的 Trace 事件数量上限。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。 。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) categories 或者 count 输入不合法。 |

### OH_JSVM_TraceStop()

```
JSVM_EXTERN JSVM_Status OH_JSVM_TraceStop(JSVM_OutputStream stream, void* streamData)
```

**描述**

对所有 JSVM 运行时，停止采集指定 Trace 类别的信息（线程不安全）。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_OutputStream](capi-jsvm-types-h.md#jsvm_outputstream) stream | 输出流回调函数，实现接收 Trace 数据功能。 |
| void* streamData | 的输出流指针，用于辅助输出流回调函数进行数据输出。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。 。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) stream 或者 streamData 为空。 |

### OH_JSVM_AddHandlerForGC()

```
JSVM_EXTERN JSVM_Status OH_JSVM_AddHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,JSVM_GCType gcType,void* userData)
```

**描述**

在VM中添加GC的回调函数。

**起始版本：** 18


**参数：**

| 参数项                                                                                 | 描述 |
|-------------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                              | 调用JSVM-API的环境。 |
| [JSVM_CBTriggerTimeForGC](capi-jsvm-types-h.md#jsvm_cbtriggertimeforgc) triggerTime | 触发GC回调函数的时机。 |
| [JSVM_HandlerForGC](capi-jsvm-types-h.md#jsvm_handlerforgc) handler                 | 当触发GC时，传入的回调函数会被调用。 |
| [JSVM_GCType](capi-jsvm-types-h.md#jsvm_gctype) gcType                              | GC类型。 |
| void* userData                                                                      | 原生指针数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示函数执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的vm或者handler为空或者handler已经被添加过了。 |

### OH_JSVM_RemoveHandlerForGC()

```
JSVM_EXTERN JSVM_Status OH_JSVM_RemoveHandlerForGC(JSVM_VM vm,JSVM_CBTriggerTimeForGC triggerTime,JSVM_HandlerForGC handler,void* userData)
```

**描述**

在VM中移除GC的回调函数。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm | 调用JSVM-API的环境。 |
| [JSVM_CBTriggerTimeForGC](capi-jsvm-types-h.md#jsvm_cbtriggertimeforgc) triggerTime | 触发GC回调函数的时机。 |
| [JSVM_HandlerForGC](capi-jsvm-types-h.md#jsvm_handlerforgc) handler | 当触发GC时，传入的回调函数会被调用。 |
| void* userData | 原生指针数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示函数执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的vm或者handler为空或者handler已经被删除过了或者<br> 这个handler从来没有被添加过。 |

### OH_JSVM_SetHandlerForOOMError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForOOMError(JSVM_VM vm,JSVM_HandlerForOOMError handler)
```

**描述**

为OOM错误设置回调处理。当接口被重复调用时，仅最后一次生效。当传入的handler为null时，表示取消之前的设置。

**起始版本：** 18


**参数：**

| 参数项                                                                             | 描述 |
|---------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                          | 调用JSVM-API的环境。 |
| [JSVM_HandlerForOOMError](capi-jsvm-types-h.md#jsvm_handlerforoomerror) handler | OOM错误的处理器。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示函数执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示vm为空。 |

### OH_JSVM_SetDebugOption()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetDebugOption(JSVM_Env env, JSVM_DebugOption debugOption, bool isEnabled)
```

**描述**

启用/禁用特定JSVM_Env的指定调试选项。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_DebugOption](capi-jsvm-types-h.md#jsvm_debugoption) debugOption | 需要更改的调试选项。 |
| bool isEnabled | 是否启用或禁用调试选项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示函数执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 如果传入的env为空指针，返回此错误码。 |

### OH_JSVM_SetHandlerForFatalError()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForFatalError(JSVM_VM vm,JSVM_HandlerForFatalError handler)
```

**描述**

为Fatal错误设置回调处理。当接口被重复调用时，仅最后一次生效。当传入的handler为null时，表示取消之前的设置。

**起始版本：** 18


**参数：**

| 参数项                                                                                 | 描述 |
|-------------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                              | 调用JSVM-API的环境。 |
| [JSVM_HandlerForFatalError](capi-jsvm-types-h.md#jsvm_handlerforfatalerror) handler | Fatal错误的处理器。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示函数执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示vm为空。 |

### OH_JSVM_SetHandlerForPromiseReject()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetHandlerForPromiseReject(JSVM_VM vm,JSVM_HandlerForPromiseReject handler)
```

**描述**

为PromiseReject错误设置回调处理。当接口被重复调用时，仅最后一次生效。当传入的handler为null时，表示取消之前的设置。

**起始版本：** 18


**参数：**

| 参数项                                                                                       | 描述 |
|-------------------------------------------------------------------------------------------| -- |
| [JSVM_VM](capi-jsvm-jsvm-vm--8h.md) vm                                                    | 调用JSVM-API的环境。 |
| [JSVM_HandlerForPromiseReject](capi-jsvm-types-h.md#jsvm_handlerforpromisereject) handler | PromiseReject错误的处理器。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示函数执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示vm为空。 |

### OH_JSVM_DefineClassWithOptions()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DefineClassWithOptions(JSVM_Env env,const char* utf8name,size_t length,JSVM_Callback constructor,size_t propertyCount,const JSVM_PropertyDescriptor* properties,JSVM_Value parentClass,size_t optionCount,JSVM_DefineClassOptions options[],JSVM_Value* result)
```

**描述**

在封装一个 C++ 类时，通过构造函数传递的 C++ 构造函数回调应该是类中的一个静态方法，该方法调用实际的类构造函数，然后根据传入的不同选项，将新的 C++ 实例封装在一个 JavaScript 对象中并返回封装对象。

**起始版本：** 18


**参数：**

| 参数项                                                                               | 描述 |
|-----------------------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                                         | 调用JSVM-API的环境。 |
| const char* utf8name                                                              | JavaScript构造函数的名称，建议在包装C++类时使用C++类名。 |
| size_t length                                                                     | utf8name的长度（以字节为单位）或JSVM_AUTO_LENGTH（如果以 null 结尾）。 |
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md) constructor                     | 用于创建类的构造函数的回调函数。包装C++类时，此方法必须是符合JSVM_Callback。callback签名的静态成员。不能使用C++类构造函数。详情请参考[JSVM_Callback](capi-jsvm-jsvm-callbackstruct.md)。 |
| size_t propertyCount                                                              | properties数组参数中的项目数量。 |
| [const JSVM_PropertyDescriptor](capi-jsvm-jsvm-propertydescriptor.md)* properties | 类的属性描述符，用于定义类的属性和方法。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) parentClass             | 当前所定义的class的父类class。 |
| size_t optionCount                                                                | options数组参数中的项目数量。 |
| [JSVM_DefineClassOptions](capi-jsvm-jsvm-defineclassoptions.md) options[]                                             | 传入的用于定义class的选项数组。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result                 | 表示类的构造函数的JSVM_Value。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入的指针参数里面存在空指针。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示传入的utf8name | constructor | properties无效，导致执行失败。 |

### OH_JSVM_CreateExternalStringLatin1()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringLatin1(JSVM_Env env,char* str,size_t length,JSVM_Finalize finalizeCallback,void* finalizeHint,JSVM_Value* result,bool* copied)
```

**描述**

此 API 使用 ISO-8859-1 编码的 C 字符串，创建一个外部的 JavaScript 字符串。创建外部字符串失败时会复制原生字符串。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| char* str | 指向 ISO-8859-1 编码字符串的指针。 |
| size_t length | 字符串的字节长度，如果是空终止字符串可以直接传入 JSVM_AUTO_LENGTH。 |
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCallback | 可选项，是当创建的字符串被 GC 回收时会触发的回调函数。更多细节详见 JSVM_Finalize 类型说明。 |
| void* finalizeHint | 可选项，当字符串被回收时会传递给触发的 finalize callback。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result | 接收创建完成的 JavaScript 外部字符串，表示为 JSVM_Value 类型。 |
| bool* copied | 指示外部字符串是否成功创建的标志，为真表示创建外部字符串失败并返回一个原生 JS 字符串，否表示成功。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入参数中 env, str 和 copied 中任一值为空。 |

### OH_JSVM_CreateExternalStringUtf16()

```
JSVM_Status JSVM_CDECL OH_JSVM_CreateExternalStringUtf16(JSVM_Env env,char16_t* str,size_t length,JSVM_Finalize finalizecallback,void* finalizeHint,JSVM_Value* result,bool* copied)
```

**描述**

此 API 使用 UTF16-LE 编码的 C 字符串，创建一个外部的 JavaScript 字符串。创建外部字符串失败时会复制原生字符串。

**起始版本：** 12


**参数：**

| 参数项                                                                  | 描述 |
|----------------------------------------------------------------------| -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env                            | 调用 JSVM-API 的环境。 |
| char16_t* str                                                        | 指向 UTF16-LE 编码字符串的指针。 |
| size_t length                                                        | 字符串的字节长度，如果是空终止字符串可以直接传入 JSVM_AUTO_LENGTH。 |
| [JSVM_Finalize](capi-jsvm-types-h.md#jsvm_finalize) finalizeCallback | 可选项，是当创建的字符串被 GC 回收时会触发的回调函数。更多细节详见 JSVM_Finalize 类型说明。 |
| void* finalizeHint                                                   | 可选项，当字符串被回收时会传递给触发的 finalize callback。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md)* result    | 接收创建完成的 JavaScript 外部字符串，表示为 JSVM_Value 类型。 |
| bool* copied                                                         | 指示外部字符串是否成功创建的标志，为真表示创建外部字符串失败并返回一个原生 JS 字符串，否表示成功。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) JSVM_CDECL | 返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入参数中 env, str 和 copied 中任一值为空。 |

### OH_JSVM_CreatePrivate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreatePrivate(JSVM_Env env,JSVM_Value description,JSVM_Data* result)
```

**描述**

创建一个 JavaScript private key 对象。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) description | 可选项，它指的是要作为 private key 描述的 JavaScript 字符串。 |
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md)* result | 接收创建成功的 JavaScript private key 对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示传入参数中 env 和 result 中任一值为空。<br>         [JSVM_STRING_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的 description 不是字符串。 |

### OH_JSVM_SetPrivate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_SetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value value)
```

**描述**

为传入的object设置一个 private 属性。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 将要进行 private 属性设置的对象。 |
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) key | private 属性的 private key 对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | private 属性值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示任一传入参数为空或者 key 不是一个 private key 对象。<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的 object 不是一个真正的 JavaScript object。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示设置 private 属性失败，同时没有异常产生。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示发生了异常。 |

### OH_JSVM_GetPrivate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetPrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key,JSVM_Value *result)
```

**描述**

从传入的object获取 private key 对应的 private 属性。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 获取 private 属性的对象。 |
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) key | private 属性的 private key 对象。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) *result | private 属性值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示任一传入参数为空或者 key 不是一个 private key 对象。<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的 object 不是一个真正的 JavaScript object。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示获取 private 属性失败，同时没有异常产生。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示发生了异常。 |

### OH_JSVM_DeletePrivate()

```
JSVM_EXTERN JSVM_Status OH_JSVM_DeletePrivate(JSVM_Env env,JSVM_Value object,JSVM_Data key)
```

**描述**

从传入的 object 上删除 private key 对应的 private 属性。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) object | 删除 private 属性的对象。 |
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) key | private 属性的 private key 对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。<br>         [JSVM_INVALID_ARG](capi-jsvm-types-h.md#jsvm_status) 表示任一传入参数为空或者 key 不是一个 private key 对象。<br>         [JSVM_OBJECT_EXPECTED](capi-jsvm-types-h.md#jsvm_status) 表示传入的 object 不是一个真正的 JavaScript object。<br>         [JSVM_GENERIC_FAILURE](capi-jsvm-types-h.md#jsvm_status) 表示删除 private 属性失败，同时没有异常产生。<br>         [JSVM_PENDING_EXCEPTION](capi-jsvm-types-h.md#jsvm_status) 表示发生了异常。 |

### OH_JSVM_CreateDataReference()

```
JSVM_EXTERN JSVM_Status OH_JSVM_CreateDataReference(JSVM_Env env,JSVM_Data data,uint32_t initialRefcount,JSVM_Ref* result)
```

**描述**

创建一个对于给定 JSVM_Data 对象的引用，初始的引用计数为传入的 initialRefcount。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用 JSVM-API 的环境。 |
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md) data | 将要创建引用的 JSVM_Data 对象。 |
| uint32_t initialRefcount | 初始引用计数值。 |
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md)* result | 接收新创建的对象引用，表示为 JSVM_Ref 类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |

### OH_JSVM_GetReferenceData()

```
JSVM_EXTERN JSVM_Status OH_JSVM_GetReferenceData(JSVM_Env env,JSVM_Ref ref,JSVM_Data* result)
EXTERN_C_END
```

**描述**

如果引用仍然有效，通过 result 参数返回对应的 JSVM_Data，表示与 JSVM_Ref 关联的 JavaScript 值。否则结果将为空。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [JSVM_Env](capi-jsvm-jsvm-env--8h.md) env | 调用JSVM-API的环境。 |
| [JSVM_Ref](capi-jsvm-jsvm-ref--8h.md) ref | 请求相应值的JSVM_Ref。 |
| [JSVM_Data](capi-jsvm-jsvm-data--8h.md)* result | JSVM_Ref 引用的 JSVM_Data。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| JSVM_EXTERN [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) |  返回执行状态码 JSVM_Status。<br>         [JSVM_OK](capi-jsvm-types-h.md#jsvm_status) 表示执行成功。 |


