# ipc_cremote_object.h

## 概述

提供远端对象创建、销毁、数据发送、远端对象死亡状态监听等功能的C接口，适用于IPC（Inter-Process Communication，进程间通信）和RPC（Remote Procedure Call，远程过程调用）通信场景。

**库：** libipc_capi.so

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**相关模块：** [OHIPCRemoteObject](capi-ohipcremoteobject.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_IPC_MessageOption](capi-ohipcremoteobject-oh-ipc-messageoption.md) | - | Defines the IPC message options. |
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) | - | IPC死亡通知对象，用于监听IPC远程对象的死亡事件。创建OHIPCDeathRecipient对象后，必须注册到OHIPCRemoteObject对象才能生效；若未注册，将无法监听死亡事件。当远程进程意外终止或主动销毁时，注册了死亡监听的本地进程将收到死亡通知回调，从而及时释放相关资源或进行错误处理。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_IPC_RequestMode](#oh_ipc_requestmode) | OH_IPC_RequestMode | IPC请求模式定义。同步请求模式适用于需要等待远端响应的场景，异步请求模式适用于不需要等待远端响应或需要提高并发性能的场景。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef int (\*OH_OnRemoteRequestCallback)(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData)](#oh_onremoterequestcallback) | OH_OnRemoteRequestCallback | Stub端用于处理远端数据请求的回调函数。当Proxy端通过[OH_IPCRemoteProxy_SendRequest](capi-ipc-cremote-object-h.md#oh_ipcremoteproxy_sendrequest)发送请求时，系统会触发此回调函数。回调函数在Binder线程池中执行，需要注意线程安全。回调函数应尽快返回，避免长时间阻塞，否则可能影响其他IPC请求的处理。 |
| [typedef void (\*OH_OnRemoteDestroyCallback)(void *userData)](#oh_onremotedestroycallback) | OH_OnRemoteDestroyCallback | 用于监听对象销毁的回调函数。 |
| [OHIPCRemoteStub* OH_IPCRemoteStub_Create(const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)](#oh_ipcremotestub_create) | - | 创建OHIPCRemoteStub对象，用于Stub端创建服务端对象，处理来自Proxy端的远端数据请求。 |
| [void OH_IPCRemoteStub_Destroy(OHIPCRemoteStub *stub)](#oh_ipcremotestub_destroy) | - | 销毁OHIPCRemoteStub对象。 |
| [void OH_IPCRemoteProxy_Destroy(OHIPCRemoteProxy *proxy)](#oh_ipcremoteproxy_destroy) | - | 销毁OHIPCRemoteProxy对象。 |
| [#pragma pack(4)
typedef struct {](#pack) | - | Defines the IPC message options. |
| [int OH_IPCRemoteProxy_SendRequest(const OHIPCRemoteProxy *proxy, uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, const OH_IPC_MessageOption *option)](#oh_ipcremoteproxy_sendrequest) | - | IPC消息发送函数，用于Proxy端向远端Stub发送IPC消息请求，支持同步和异步两种通信模式。 |
| [int OH_IPCRemoteProxy_GetInterfaceDescriptor(OHIPCRemoteProxy *proxy, char **descriptor, int32_t *len, OH_IPC_MemAllocator allocator)](#oh_ipcremoteproxy_getinterfacedescriptor) | - | 从Stub端获取接口描述符。接口描述符是Stub对象的唯一标识，用于识别远端服务类型、进行服务版本兼容性检查或者验证远端服务是否实现了特定接口。函数通过IPC调用从远端Stub获取描述符字符串，并使用用户提供的内存分配器存储结果。 |
| [typedef void (\*OH_OnDeathRecipientCallback)(void *userData)](#oh_ondeathrecipientcallback) | OH_OnDeathRecipientCallback | 远端OHIPCRemoteStub对象死亡通知的回调函数类型。当远端Stub对象所在进程异常退出或被系统杀死时，系统会触发此回调通知客户端。回调函数在Binder线程中执行，注意线程安全。回调中不建议进行复杂的IPC操作，避免潜在的死锁风险。常用于客户端需要感知服务端异常退出或崩溃、需要在服务端对象死亡时进行资源清理或状态重置以及需要实现服务端存活监控和故障恢复机制。 |
| [typedef void (\*OH_OnDeathRecipientDestroyCallback)(void *userData)](#oh_ondeathrecipientdestroycallback) | OH_OnDeathRecipientDestroyCallback | OHIPCDeathRecipient对象销毁回调函数类型。常用于需要在死亡监听对象销毁时释放用户私有数据或需要清理死亡监听相关的资源。 |
| [OHIPCDeathRecipient* OH_IPCDeathRecipient_Create(OH_OnDeathRecipientCallback deathRecipientCallback, OH_OnDeathRecipientDestroyCallback destroyCallback, void *userData)](#oh_ipcdeathrecipient_create) | - | 创建远端OHIPCRemoteStub对象死亡通知对象OHIPCDeathRecipient。用于监听远端Stub对象的死亡状态。常用于客户端需要监听服务端对象的死亡事件、需要实现服务端异常退出的感知机制以及需要在服务端崩溃时进行故障处理或自动重连。 |
| [void OH_IPCDeathRecipient_Destroy(OHIPCDeathRecipient *recipient)](#oh_ipcdeathrecipient_destroy) | - | 销毁OHIPCDeathRecipient对象。常用于不再需要监听远端对象死亡事件以及客户端退出或模块卸载时，清理死亡监听资源。 |
| [int OH_IPCRemoteProxy_AddDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)](#oh_ipcremoteproxy_adddeathrecipient) | - | 向OHIPCRemoteProxy对象添加死亡监听，用于接收远端OHIPCRemoteStub对象死亡的回调通知。常用于客户端启动后，注册服务端死亡监听以便及时感知服务端异常、需要实现服务端故障检测和自动恢复机制以及需要在服务端不可用时及时释放相关资源或通知用户。 |
| [int OH_IPCRemoteProxy_RemoveDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)](#oh_ipcremoteproxy_removedeathrecipient) | - | 移除向OHIPCRemoteProxy对象已经添加的死亡监听。常用于不再需要监听远端对象死亡事件时取消注册或切换到其他服务实例时移除旧的死亡监听。 |
| [int OH_IPCRemoteProxy_IsRemoteDead(const OHIPCRemoteProxy *proxy)](#oh_ipcremoteproxy_isremotedead) | - | 判断OHIPCRemoteProxy对象对应的远端OHIPCRemoteStub对象是否死亡。常用于在发送IPC请求前，主动检查服务端是否存活、在重连机制中判断是否需要重新建立连接以及在业务逻辑中需要根据服务端存活状态采取不同处理策略。 |

## 枚举类型说明

### OH_IPC_RequestMode

```c
enum OH_IPC_RequestMode
```

**描述**

IPC请求模式定义。同步请求模式适用于需要等待远端响应的场景，异步请求模式适用于不需要等待远端响应或需要提高并发性能的场景。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_IPC_REQUEST_MODE_SYNC = 0 | 同步请求模式。适用于需要等待返回结果的场景，如查询操作、简单请求响应场景。 |
| OH_IPC_REQUEST_MODE_ASYNC = 1 | 异步请求模式。适用于不需要立即获取结果或耗时操作的场景，如大批量数据传输、后台处理等。 |


## 函数说明

### OH_OnRemoteRequestCallback()

```c
typedef int (*OH_OnRemoteRequestCallback)(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData)
```

**描述**

Stub端用于处理远端数据请求的回调函数。当Proxy端通过[OH_IPCRemoteProxy_SendRequest](capi-ipc-cremote-object-h.md#oh_ipcremoteproxy_sendrequest)发送请求时，系统会触发此回调函数。回调函数在Binder线程池中执行，需要注意线程安全。回调函数应尽快返回，避免长时间阻塞，否则可能影响其他IPC请求的处理。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (uint32_t code | 用户定义的IPC命令字，范围：[0x01, 0x00ffffff]。建议按业务模块分段定义code值，避免不同功能命令冲突。例如：0x01-0x100用于基础功能，0x101-0x200用于扩展功能。 |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) \*data | 请求数据对象指针，不会为空，函数内不允许释放。 |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) \*reply | 响应数据对象指针，不会为空，函数内不允许释放。如果函数返回错误，该值不允许写入数据。 |
| void \*userData | 用户私有数据，当需要在回调函数中访问用户自定义数据时传入此参数，不需要访问用户数据时可以传NULL。为NULL时回调函数无法访问用户私有数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 否则返回用户自定义错误码或系统错误码，自定义错误码范围：[1909001, 1909999]；<br> 如果用户自定义错误码超出范围，将返回{@link OH_IPC_ErrorCode#OH_IPC_INVALID_USER_ERROR_CODE}。 |

### OH_OnRemoteDestroyCallback()

```c
typedef void (*OH_OnRemoteDestroyCallback)(void *userData)
```

**描述**

用于监听对象销毁的回调函数。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (void \*userData | 用户私有数据，当需要在回调函数中访问用户自定义数据时传入此参数，不需要访问用户数据时可为NULL。传入NULL时回调函数无法访问用户私有数据。 |

### OH_IPCRemoteStub_Create()

```c
OHIPCRemoteStub* OH_IPCRemoteStub_Create(const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)
```

**描述**

创建OHIPCRemoteStub对象，用于Stub端创建服务端对象，处理来自Proxy端的远端数据请求。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *descriptor | OHIPCRemoteStub对象描述符，不能为空。字符串长度取值范围：(0, 204800]字节。超出范围时返回NULL。建议使用唯一的标识符字符串，如："com.example.myservice"或"MyService"。格式通常为反向域名或简单服务名称，用于标识不同的IPC服务接口。 |
| [OH_OnRemoteRequestCallback](capi-ipc-cremote-object-h.md#oh_onremoterequestcallback) requestCallback | 数据请求处理函数，不能为空。 |
| [OH_OnRemoteDestroyCallback](capi-ipc-cremote-object-h.md#oh_onremotedestroycallback) destroyCallback | 对象销毁回调函数，当需要在Stub对象销毁时执行清理操作（如释放userData资源）时传入此参数，不需要清理操作时可以不传或传空。不传入时对象销毁不会触发任何回调通知。 |
| void *userData | 用户私有数据，当需要在回调函数中访问用户自定义数据时传入此参数，不需要访问用户数据时可为NULL。为NULL时回调函数中无法访问用户私有数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OHIPCRemoteStub*](capi-ohipcparcel-ohipcremotestub.md) | 成功返回OHIPCRemoteStub对象指针，否则返回NULL。 |

### OH_IPCRemoteStub_Destroy()

```c
void OH_IPCRemoteStub_Destroy(OHIPCRemoteStub *stub)
```

**描述**

销毁OHIPCRemoteStub对象。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) *stub | 要销毁的OHIPCRemoteStub对象指针，不能为空。 |

### OH_IPCRemoteProxy_Destroy()

```c
void OH_IPCRemoteProxy_Destroy(OHIPCRemoteProxy *proxy)
```

**描述**

销毁OHIPCRemoteProxy对象。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | 要销毁的OHIPCRemoteProxy对象指针，不能为空。 |

### pack()

```c
#pragma pack(4)
typedef struct {
```

**描述**

Defines the IPC message options.

**起始版本：** 12

### OH_IPCRemoteProxy_SendRequest()

```c
int OH_IPCRemoteProxy_SendRequest(const OHIPCRemoteProxy *proxy, uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, const OH_IPC_MessageOption *option)
```

**描述**

IPC消息发送函数，用于Proxy端向远端Stub发送IPC消息请求，支持同步和异步两种通信模式。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | OHIPCRemoteProxy对象指针，不能为空。 |
| uint32_t code | 用户定义的IPC命令字，范围：[0x01, 0x00ffffff]。超出范围时返回OH_IPC_CODE_OUT_OF_RANGE错误码。建议按业务模块分段定义code值，确保Proxy端和Stub端使用相同的命令字定义。同一服务接口的不同操作使用不同的code值区分。 |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *data | 请求数据对象指针，不能为空。 |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *reply | 回应数据对象指针。同步请求时不能为空，用于存储响应结果；异步请求时可以为空，为空时不存储响应结果。 |
| [const OH_IPC_MessageOption](capi-ohipcremoteobject-oh-ipc-messageoption.md) *option | 消息选项指针，用于配置IPC消息发送模式（同步/异步）。当需要使用异步模式或自定义消息选项时传入此参数。异步请求时必须传入并设置相应的请求模式，同步请求时可以不传或传NULL。不传入或传NULL时默认使用同步模式（OH_IPC_REQUEST_MODE_SYNC）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 发送成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 远端OHIPCRemoteStub对象死亡返回{@link OH_IPC_ErrorCode#OH_IPC_DEAD_REMOTE_OBJECT}；<br> code超出范围返回{@link OH_IPC_ErrorCode#OH_IPC_CODE_OUT_OF_RANGE}；<br> 其它返回{@link OH_IPC_ErrorCode#OH_IPC_INNER_ERROR}或用户自定义错误码（范围：[1909001, 1909999]）。 |

### OH_IPCRemoteProxy_GetInterfaceDescriptor()

```c
int OH_IPCRemoteProxy_GetInterfaceDescriptor(OHIPCRemoteProxy *proxy, char **descriptor, int32_t *len, OH_IPC_MemAllocator allocator)
```

**描述**

从Stub端获取接口描述符。接口描述符是Stub对象的唯一标识，用于识别远端服务类型、进行服务版本兼容性检查或者验证远端服务是否实现了特定接口。函数通过IPC调用从远端Stub获取描述符字符串，并使用用户提供的内存分配器存储结果。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | OHIPCRemoteProxy对象指针，不能为空。 |
| char **descriptor | 用于存储描述符的内存地址，该内存由用户提供的分配器进行内存分配，用户使用完后需要主动释放，不能为空。接口返回失败时，用户依然需要判断该内存是否为空，并主动释放，否则会造成内存泄漏。建议使用完成后立即释放，避免内存泄漏。 |
| int32_t *len | 写入descriptor的数据长度，包含结束符，不能为空。 |
| [OH_IPC_MemAllocator](capi-ipc-cparcel-h.md#oh_ipc_memallocator) allocator | 用户指定的用来分配descriptor的内存分配器，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 发送成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数错误返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 远端OHIPCRemoteStub对象死亡返回{@link OH_IPC_ErrorCode#OH_IPC_DEAD_REMOTE_OBJECT}；<br> 内存分配失败返回{@link OH_IPC_ErrorCode#OH_IPC_MEM_ALLOCATOR_ERROR}；<br> 序列化读失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}或用户自定义错误码。 |

### OH_OnDeathRecipientCallback()

```c
typedef void (*OH_OnDeathRecipientCallback)(void *userData)
```

**描述**

远端OHIPCRemoteStub对象死亡通知的回调函数类型。当远端Stub对象所在进程异常退出或被系统杀死时，系统会触发此回调通知客户端。回调函数在Binder线程中执行，注意线程安全。回调中不建议进行复杂的IPC操作，避免潜在的死锁风险。常用于客户端需要感知服务端异常退出或崩溃、需要在服务端对象死亡时进行资源清理或状态重置以及需要实现服务端存活监控和故障恢复机制。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (void \*userData | 用户私有数据指针，当需要在死亡通知回调中访问用户自定义数据时传入此参数，不需要访问用户数据时可以不传或传NULL。为NULL时回调函数中无法访问用户私有数据。 |

### OH_OnDeathRecipientDestroyCallback()

```c
typedef void (*OH_OnDeathRecipientDestroyCallback)(void *userData)
```

**描述**

OHIPCDeathRecipient对象销毁回调函数类型。常用于需要在死亡监听对象销毁时释放用户私有数据或需要清理死亡监听相关的资源。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (void \*userData | 用户私有数据指针，当需要在死亡通知回调中访问用户自定义数据时传入此参数，不需要访问用户数据时可以不传或传NULL。为NULL时回调函数中无法访问用户私有数据。 |

### OH_IPCDeathRecipient_Create()

```c
OHIPCDeathRecipient* OH_IPCDeathRecipient_Create(OH_OnDeathRecipientCallback deathRecipientCallback, OH_OnDeathRecipientDestroyCallback destroyCallback, void *userData)
```

**描述**

创建远端OHIPCRemoteStub对象死亡通知对象OHIPCDeathRecipient。用于监听远端Stub对象的死亡状态。常用于客户端需要监听服务端对象的死亡事件、需要实现服务端异常退出的感知机制以及需要在服务端崩溃时进行故障处理或自动重连。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_OnDeathRecipientCallback](capi-ipc-cremote-object-h.md#oh_ondeathrecipientcallback) deathRecipientCallback | 远端OHIPCRemoteStub对象死亡通知的回调处理函数，不能为空。 |
| [OH_OnDeathRecipientDestroyCallback](capi-ipc-cremote-object-h.md#oh_ondeathrecipientdestroycallback) destroyCallback | 对象销毁回调处理函数，可以为NULL。为NULL时不监听对象销毁事件。当需要在OHIPCDeathRecipient对象销毁时执行清理操作（如释放userData资源）时传入此参数，不需要清理操作时可以不传或传NULL。传NULL时对象销毁不会触发任何回调通知。 |
| void *userData | 用户私有数据指针，当需要在死亡通知回调中访问用户自定义数据时传入此参数，不需要访问用户数据时可以不传或传NULL。为NULL时回调函数无法访问用户私有数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OHIPCDeathRecipient*](capi-ohipcremoteobject-ohipcdeathrecipient.md) | 成功返回OHIPCDeathRecipient对象指针；否则返回NULL。 |

### OH_IPCDeathRecipient_Destroy()

```c
void OH_IPCDeathRecipient_Destroy(OHIPCDeathRecipient *recipient)
```

**描述**

销毁OHIPCDeathRecipient对象。常用于不再需要监听远端对象死亡事件以及客户端退出或模块卸载时，清理死亡监听资源。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) *recipient | 要销毁的OHIPCDeathRecipient对象指针，不能为空。 |

### OH_IPCRemoteProxy_AddDeathRecipient()

```c
int OH_IPCRemoteProxy_AddDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)
```

**描述**

向OHIPCRemoteProxy对象添加死亡监听，用于接收远端OHIPCRemoteStub对象死亡的回调通知。常用于客户端启动后，注册服务端死亡监听以便及时感知服务端异常、需要实现服务端故障检测和自动恢复机制以及需要在服务端不可用时及时释放相关资源或通知用户。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | 需要添加死亡通知的OHIPCRemoteProxy对象指针，不能为空。 |
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) *recipient | 用于接收远程对象死亡通知的死亡对象指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数错误返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 其它返回{@link OH_IPC_ErrorCode#OH_IPC_INNER_ERROR}。 |

### OH_IPCRemoteProxy_RemoveDeathRecipient()

```c
int OH_IPCRemoteProxy_RemoveDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)
```

**描述**

移除向OHIPCRemoteProxy对象已经添加的死亡监听。常用于不再需要监听远端对象死亡事件时取消注册或切换到其他服务实例时移除旧的死亡监听。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | 需要移除死亡通知的OHIPCRemoteProxy对象指针，不能为空。 |
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) *recipient | 用于接收远程对象死亡通知的死亡对象指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数错误返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 其它返回{@link OH_IPC_ErrorCode#OH_IPC_INNER_ERROR}。 |

### OH_IPCRemoteProxy_IsRemoteDead()

```c
int OH_IPCRemoteProxy_IsRemoteDead(const OHIPCRemoteProxy *proxy)
```

**描述**

判断OHIPCRemoteProxy对象对应的远端OHIPCRemoteStub对象是否死亡。常用于在发送IPC请求前，主动检查服务端是否存活、在重连机制中判断是否需要重新建立连接以及在业务逻辑中需要根据服务端存活状态采取不同处理策略。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | 需要判断远端是否死亡的OHIPCRemoteProxy对象指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 远端OHIPCRemoteStub对象死亡返回1；否则，返回0。参数非法时，说明其远端OHIPCRemoteStub对象不存在，返回1。 |


