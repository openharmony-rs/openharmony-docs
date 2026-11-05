# ipc_cremote_object.h
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ee518410be777e8e38dd982268c837f0a42a60e8 translatedAt=2026-11-04T03:43:18.815Z pushedAt=2026-11-04T10:13:14.863Z nl=1 -->

## Overview

This file provides C APIs for remote object creation, destruction, data sending, and remote object death status listening. These APIs are suitable for Inter-Process Communication (IPC) and Remote Procedure Call (RPC) communication scenarios.

For the corresponding development guide and samples, see [IPC and RPC Development (C/C++)](../../ipc/ipc-capi-development-guideline.md).

**File to include**: <IPCKit/ipc_cremote_object.h>

**Library**: libipc_capi.so

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ohipcremoteobject.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| [OH_IPC_MessageOption](capi-ohipcremoteobject-oh-ipc-messageoption.md) | OH_IPC_MessageOption | Defines the IPC message options. |
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) | OHIPCDeathRecipient | Defines an object that receives death notifications.|

### Enums

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| [OH_IPC_RequestMode](#oh_ipc_requestmode) | OH_IPC_RequestMode | Enumerates the IPC request modes.|

### Functions

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| [typedef int (\*OH_OnRemoteRequestCallback)(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData)](#oh_onremoterequestcallback) | OH_OnRemoteRequestCallback | Callback function used by the Stub side to process remote data requests. When the Proxy side sends a request through OH_IPCRemoteProxy_SendRequest, the system triggers this callback function. The callback function runs in the Binder thread pool, so thread safety must be considered. The callback function should return as soon as possible to avoid long-term blocking, which may otherwise affect the processing of other IPC requests. |
| [typedef void (\*OH_OnRemoteDestroyCallback)(void *userData)](#oh_onremotedestroycallback) | OH_OnRemoteDestroyCallback | Callback function used to listen for object destruction.|
| [OHIPCRemoteStub* OH_IPCRemoteStub_Create(const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)](#oh_ipcremotestub_create) | - | Creates an OHIPCRemoteStub object, which is used by the Stub side to create a server object and process remote data requests from the Proxy side. |
| [void OH_IPCRemoteStub_Destroy(OHIPCRemoteStub *stub)](#oh_ipcremotestub_destroy) | - | Destroys an **OHIPCRemoteStub** object.|
| [void OH_IPCRemoteProxy_Destroy(OHIPCRemoteProxy *proxy)](#oh_ipcremoteproxy_destroy) | - | Destroys an **OHIPCRemoteProxy** object.|
| [int OH_IPCRemoteProxy_SendRequest(const OHIPCRemoteProxy *proxy, uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, const OH_IPC_MessageOption *option)](#oh_ipcremoteproxy_sendrequest) | - | IPC message sending function, used by the Proxy side to send an IPC message request to the remote Stub. It supports both synchronous and asynchronous communication modes. |
| [int OH_IPCRemoteProxy_GetInterfaceDescriptor(OHIPCRemoteProxy *proxy, char **descriptor, int32_t *len, OH_IPC_MemAllocator allocator)](#oh_ipcremoteproxy_getinterfacedescriptor) | - | Obtains the interface descriptor from the Stub side. The interface descriptor is the unique identifier of the Stub object, used to identify the remote service type, perform service version compatibility checks, or verify whether the remote service implements a specific interface. The function obtains the descriptor string from the remote Stub through an IPC call and stores the result using the user-provided memory allocator. |
| [typedef void (\*OH_OnDeathRecipientCallback)(void *userData)](#oh_ondeathrecipientcallback) | OH_OnDeathRecipientCallback | Callback function type for the death notification of a remote OHIPCRemoteStub object. When the process where the remote Stub object resides exits abnormally or is killed by the system, the system triggers this callback to notify the client. The callback function runs in the Binder thread, so thread safety must be considered. Complex IPC operations are not recommended in the callback to avoid potential deadlock risks. It is commonly used when the client needs to detect abnormal exit or crash of the server, perform resource cleanup or state reset when the server object dies, and implement server liveness monitoring and fault recovery mechanisms. |
| [typedef void (\*OH_OnDeathRecipientDestroyCallback)(void *userData)](#oh_ondeathrecipientdestroycallback) | OH_OnDeathRecipientDestroyCallback | Callback function type for the destruction of an OHIPCDeathRecipient object. It is commonly used to release user private data when the death listener object is destroyed or to clean up resources related to the death listener. |
| [OHIPCDeathRecipient* OH_IPCDeathRecipient_Create(OH_OnDeathRecipientCallback deathRecipientCallback, OH_OnDeathRecipientDestroyCallback destroyCallback, void *userData)](#oh_ipcdeathrecipient_create) | - | Creates an OHIPCDeathRecipient object for the death notification of a remote OHIPCRemoteStub object. It is used to listen for the death status of the remote Stub object. It is commonly used when the client needs to listen for the death event of the server object, implement a mechanism to detect abnormal exit of the server, and perform fault handling or automatic reconnection when the server crashes. |
| [void OH_IPCDeathRecipient_Destroy(OHIPCDeathRecipient *recipient)](#oh_ipcdeathrecipient_destroy) | - | Destroys an OHIPCDeathRecipient object. It is commonly used when the death event of the remote object no longer needs to be listened for, and to clean up death listener resources when the client exits or a module is unloaded. |
| [int OH_IPCRemoteProxy_AddDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)](#oh_ipcremoteproxy_adddeathrecipient) | - | Adds a death listener to the OHIPCRemoteProxy object, used to receive the callback notification of the death of the remote OHIPCRemoteStub object. It is commonly used after the client starts to register a server death listener so as to detect server anomalies in a timely manner, implement server fault detection and automatic recovery mechanisms, and release related resources or notify the user in a timely manner when the server is unavailable. |
| [int OH_IPCRemoteProxy_RemoveDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)](#oh_ipcremoteproxy_removedeathrecipient) | - | Removes a death listener that has been added to the OHIPCRemoteProxy object. It is commonly used to unregister when the death event of the remote object no longer needs to be listened for, or to remove the old death listener when switching to another service instance. |
| [int OH_IPCRemoteProxy_IsRemoteDead(const OHIPCRemoteProxy *proxy)](#oh_ipcremoteproxy_isremotedead) | - | Determines whether the remote OHIPCRemoteStub object corresponding to the OHIPCRemoteProxy object is dead. It is commonly used to proactively check whether the server is alive before sending an IPC request, determine whether a connection needs to be re-established in a reconnection mechanism, and adopt different processing strategies in business logic based on the liveness status of the server. |

## Enum Description

### OH_IPC_RequestMode

```C
enum OH_IPC_RequestMode
```

**Description**

Enumerates the IPC request modes. The synchronous request mode is suitable for scenarios where you need to wait for a response from the remote side. The asynchronous request mode is suitable for scenarios where you do not need to wait for a response or where you need to improve concurrent performance.

**Since**: 12

| Enum Item| Description|
| ------ | ---- |
| OH_IPC_REQUEST_MODE_SYNC = 0 | Synchronous request, which is suitable for scenarios where you need to wait for a return result, such as query operations and simple request-response scenarios. |
| OH_IPC_REQUEST_MODE_ASYNC = 1 | Asynchronous request, which is suitable for scenarios where you do not need to obtain the result immediately or where operations are time-consuming, such as large-data transmission and background processing. |

## Function Description

### OH_OnRemoteRequestCallback()

```C
typedef int(*OH_OnRemoteRequestCallback)(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData)
```

**Description**

Callback function used by the stub side to process remote data requests. When the proxy side sends a request through [OH_IPCRemoteProxy_SendRequest()](#oh_ipcremoteproxy_sendrequest), the system triggers this callback function. The callback function runs in the Binder thread pool, so thread safety must be considered. The callback function should return as soon as possible to avoid long-term blocking; otherwise, the processing of other IPC requests may be affected.

- This function is used to receive and process cross-process requests from the client when the server implements a custom IPC communication protocol.
- When the server capabilities need to be called across processes, the server uses this callback to process the specific service logic.
- This function serves as the entry for message distribution and processing when the RPC server capability is implemented.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| -------- | -------- |
| uint32_t code | User-defined IPC command word, ranging from 0x01 to 0x00ffffff. It is recommended to define code values by business module to avoid command conflicts between different functions. For example, 0x01-0x100 for basic functions and 0x101-0x200 for extended functions. |
| const [OHIPCParcel](capi-ohipcparcel.md) *data | Pointer to the requested data object. It cannot be NULL or released in the function. |
| [OHIPCParcel](capi-ohipcparcel.md) *reply | Pointer to the response data object. It must not be null and must not be freed inside the function. If the function returns an error, no data should be written to this value. |
| void *userData | User private data. Pass in this parameter when the callback function needs to access user-defined data. You can pass NULL when user data access is not required. When it is NULL, the callback function cannot access the user private data. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) on success;<br> otherwise, returns a user-defined error code or a system error code. The user-defined error code ranges from 1909000 to 1909999;<br> if the user-defined error code is out of range, returns [OH_IPC_ErrorCode#OH_IPC_INVALID_USER_ERROR_CODE](capi-ipc-error-code-h.md#oh_ipc_errorcode). |

### OH_OnRemoteDestroyCallback()

```C
typedef void(*OH_OnRemoteDestroyCallback)(void *userData)
```

**Description**

Callback function used to listen for object destruction.

- Release related resources (such as memory and file handles) when the stub object is destroyed.
- Notify other modules to synchronize the status when the object is destroyed.
- Clear private user data when the object is destroyed.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ----- | ----- |
| void *userData | User private data. Pass in this parameter when the callback function needs to access user-defined data. It can be NULL when user data does not need to be accessed. When NULL is passed in, the callback function cannot access the user private data. |

### OH_IPCRemoteStub_Create()

```C
OHIPCRemoteStub* OH_IPCRemoteStub_Create(const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)
```

**Description**

Creates an [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object, which is used by the stub side to create a server object and process remote data requests from the proxy side.

- When a server needs to provide cross-process service capabilities, it can create a stub object as the server-side entity.
- It can also be used to implement the server side of custom IPC communication protocols, building RPC server capabilities.
- After a stub object is created, it usually needs to be registered with the service manager through the related APIs of [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md), so that the proxy side can discover and connect to it.
- **requestCallback** should avoid time-consuming operations, as they may block IPC communication.
- If time-consuming tasks need to be handled, you can return an error code in the callback and use a thread pool to process the tasks asynchronously.
- Ensure that the lifecycle of **userData** covers the lifecycle of the stub object to avoid dangling pointers.
- After OH_IPCRemoteStub_Create() is called to create an object, [OH_IPCRemoteStub_Destroy()](#oh_ipcremotestub_destroy) must be called to destroy the object and release resources after use.
- Failure to destroy it may result in memory leaks.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| const char *descriptor | Descriptor of the [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object, which must not be null. The string length ranges from (0, 204800] bytes. NULL is returned when the value is out of range. A unique identifier string is recommended, such as "com.example.myservice" or "MyService". The format is usually a reverse domain name or a simple service name, used to identify different IPC service interfaces. |
| [OH_OnRemoteRequestCallback()](#oh_onremoterequestcallback) requestCallback | Data request handler, which must not be null. |
| [OH_OnRemoteDestroyCallback()](#oh_onremotedestroycallback) destroyCallback | Object destruction callback function. Pass in this parameter when cleanup operations (such as releasing userData resources) need to be performed upon Stub object destruction. It can be omitted or set to NULL when no cleanup is required. If it is not passed in, no callback notification is triggered upon object destruction. |
| void *userData | User private data. This parameter is passed when user-defined data needs to be accessed in the callback function. If user data does not need to be accessed, this parameter can be set to NULL. If this parameter is set to NULL, the callback function cannot access the user's private data. |

**Returns**

| Type| Description|
| ---- | ---- |
| [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md)* | Pointer to the OHIPCRemoteStub object on success; NULL on failure. |

### OH_IPCRemoteStub_Destroy()

```C
void OH_IPCRemoteStub_Destroy(OHIPCRemoteStub *stub)
```

**Description**

Destroys an [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object.

- Release the stub object when the server no longer needs to provide the IPC service.
- Clear IPC resources when the server exits or the module is uninstalled.
- This function and [OH_IPCRemoteStub_Create()](#oh_ipcremotestub_create) must be used in pairs.
- This method must be called when the stub object is no longer used.
- After the destruction, the **destroyCallback** callback is automatically triggered to release **userData**.
- After destruction, the stub object can no longer be used for any operation.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) *stub | Pointer to the **OHIPCRemoteStub** object to destroy. It cannot be NULL. |

### OH_IPCRemoteProxy_Destroy()

```C
void OH_IPCRemoteProxy_Destroy(OHIPCRemoteProxy *proxy)
```

**Description**

Destroys an [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object.

- Release the proxy object when the client no longer needs to call the remote service.
- Clear IPC resources when the client exits or the module is uninstalled.
- [OH_IPCRemoteProxy_RemoveDeathRecipient()](#oh_ipcremoteproxy_removedeathrecipient) must be called first to remove all added death listeners.
- If the proxy object is destroyed when the listeners are not removed, the death event listener callback will be abnormal or memory leakage will occur.
- After the destruction, no method of the proxy can be called.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object to destroy. It cannot be NULL. |

### OH_IPCRemoteProxy_SendRequest()

```C
int OH_IPCRemoteProxy_SendRequest(const OHIPCRemoteProxy *proxy, uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, const OH_IPC_MessageOption *option)
```

**Description**

Sends an IPC message from the proxy to the remote stub. This function supports both synchronous and asynchronous communication modes.

- When the client needs to call server capabilities across processes, it sends a request and receives a response.
- This function enables IPC communication between the client and the server.
- This function can call service APIs of the remote service.
- The synchronous mode is suitable for requests that need to wait for a result, such as query operations, while the asynchronous mode is suitable for requests that do not need to wait for a result, such as log reporting.
- Synchronous calls block the current thread. Avoid using them in UI threads to prevent lag.
- Although asynchronous calls do not block the thread, you should still be mindful of the call frequency to avoid overloading the IPC channel.
- It is advised to check whether the remote side is alive using [OH_IPCRemoteProxy_IsRemoteDead()](#oh_ipcremoteproxy_isremotedead) before making a call.
- In case of call failure, it is advised to retry or perform error handling based on the returned error code.
- Frequent IPC calls may affect performance. It is advised to design the communication protocol properly to reduce the number of calls.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| const [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object. It cannot be NULL. |
| uint32_t code | Custom IPC command word, in the range [0x01, 0x00ffffff]. If the value is out of range, the **OH_IPC_CODE_OUT_OF_RANGE** error is returned. It is advised to define code values in segments based on service modules, and ensure that the same command word definitions are used on both the proxy side and the stub side. Different operations of the same service API should use distinct code values for identification. |
| const [OHIPCParcel](capi-ohipcparcel.md) *data | Pointer to the requested data object. It cannot be NULL. |
| [OHIPCParcel](capi-ohipcparcel.md) *reply | Pointer to the response data object. It must not be null for a synchronous request, and is used to store the response result. It can be null for an asynchronous request, in which case the response result is not stored. |
| const [OH_IPC_MessageOption](capi-ohipcremoteobject-oh-ipc-messageoption.md) *option | Pointer to the message option, which is used to configure the IPC message sending mode (synchronous/asynchronous). Pass this parameter when the asynchronous mode or custom message option is required. For asynchronous requests, the corresponding request mode must be passed and set. For synchronous requests, you may omit it or pass NULL. If omitted or NULL is passed, the synchronous mode (**OH_IPC_REQUEST_MODE_SYNC**) is used by default. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) on successful sending;<br> returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) when the parameters are invalid;<br> returns [OH_IPC_ErrorCode#OH_IPC_DEAD_REMOTE_OBJECT](capi-ipc-error-code-h.md#oh_ipc_errorcode) when the remote OHIPCRemoteStub object is dead;<br> returns [OH_IPC_ErrorCode#OH_IPC_CODE_OUT_OF_RANGE](capi-ipc-error-code-h.md#oh_ipc_errorcode) when code is out of range;<br> otherwise returns [OH_IPC_ErrorCode#OH_IPC_INNER_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) or a user-defined error code (range: [1909000, 1909999]). |

### OH_IPCRemoteProxy_GetInterfaceDescriptor()

```C
int OH_IPCRemoteProxy_GetInterfaceDescriptor(OHIPCRemoteProxy *proxy, char **descriptor, int32_t *len, OH_IPC_MemAllocator allocator)
```

**Description**

Obtains the interface descriptor from the stub side. The interface descriptor is the unique identifier of a stub object, used to identify the remote service type, perform service version compatibility checks, or verify whether the remote service implements a specific interface. This function obtains the descriptor string from the remote stub and uses a user-provided memory allocator to store the result.

- The memory of the returned descriptor string is allocated by the user-provided allocator. The user must release it proactively after use; otherwise, a memory leak will occur. Even if the function call fails, check whether **descriptor** is not null and release it.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object. It cannot be NULL. |
| char **descriptor | Pointer to the address of the memory for holding the interface descriptor. The memory is allocated by the allocator provided by the user and needs to be released. This pointer cannot be NULL. If an error code is returned, you still need to check whether the memory is empty and release the memory. Otherwise, memory leaks may occur. You are advised to release it immediately after use to prevent memory leaks. |
| int32_t *len | Pointer to the length of the data written to the descriptor, including the terminator. It cannot be NULL. |
| [OH_IPC_MemAllocator](capi-ipc-cparcel-h.md#oh_ipc_memallocator) allocator | Memory allocator specified by the user for allocating memory. It cannot be NULL. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the message is sent successfully.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the parameters are incorrect.<br> Returns [OH_IPC_ErrorCode#OH_IPC_DEAD_REMOTE_OBJECT](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the remote **OHIPCRemoteStub** object dies.<br> Returns [OH_IPC_ErrorCode#OH_IPC_MEM_ALLOCATOR_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the memory allocation fails.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) or a custom error code if the data in the serialized object fails to be read.|

### OH_OnDeathRecipientCallback()

```C
typedef void (*OH_OnDeathRecipientCallback)(void *userData)
```

**Description**

Defines the callback function type for the death notification of a remote [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object. When the process where the remote Stub object resides exits abnormally or is killed by the system, the system triggers this callback to notify the client. The callback function runs in a Binder thread, so pay attention to thread safety. Avoid complex IPC operations in the callback to prevent potential deadlock risks. It is commonly used when the client needs to detect abnormal exit or crash of the server, when resources need to be cleaned up or state reset upon server object death, and when server liveness monitoring and fault recovery mechanisms need to be implemented.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| void *userData | Pointer to the user private data. Pass in this parameter when you need to access user-defined data in the death notification callback. You can omit it or pass NULL when you do not need to access user data. When it is NULL, the callback function cannot access the user private data. |

### OH_OnDeathRecipientDestroyCallback()

```C
typedef void (*OH_OnDeathRecipientDestroyCallback)(void *userData)
```

**Description**

Defines the callback function type for the destruction of an [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) object. It is commonly used when user private data needs to be released upon destruction of the death listener object, or when resources related to the death listener need to be cleaned up.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| void *userData | Pointer to the user private data. Pass in this parameter when the user-defined data needs to be accessed in the death notification callback. If the user data does not need to be accessed, this parameter can be omitted or set to NULL. If this parameter is NULL, the callback function cannot access the user private data. |

### OH_IPCDeathRecipient_Create()

```C
OHIPCDeathRecipient* OH_IPCDeathRecipient_Create(OH_OnDeathRecipientCallback deathRecipientCallback, OH_OnDeathRecipientDestroyCallback destroyCallback, void *userData)
```

**Description**

Creates an [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) object for the death notification of a remote [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object. It is used to listen for the death state of the remote Stub object. It is commonly used when the client needs to listen for the death event of the server object, when a mechanism for detecting abnormal exit of the server needs to be implemented, and when fault handling or automatic reconnection is required upon server crash.

- The death callback is triggered when the remote Stub object is destroyed or the process crashes. It is advised to release related resources, reset state, and attempt reconnection in the callback.
- The death callback may be executed on any thread, so thread safety must be taken into account. Avoid performing time-consuming operations in the callback.
- It is recommended not to destroy the [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) object directly in the callback. Destruction should be performed outside the callback.
- Multiple proxies can share the same [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) object. Ensure that it is removed from all proxies before destruction.
- If the proxy is already dead, adding a death listener will immediately trigger the callback. Therefore, you need to check the status before adding the listener.
- It is recommended that you create and add a death listener during application initialization, and remove and destroy it when the application exits.
- After creation, the object must be added to the proxy object via [OH_IPCRemoteProxy_AddDeathRecipient()](#oh_ipcremoteproxy_adddeathrecipient).
- When the listener is no longer needed, you must first remove it via [OH_IPCRemoteProxy_RemoveDeathRecipient()](#oh_ipcremoteproxy_removedeathrecipient).
- After removal, the object must be destroyed by calling [OH_IPCDeathRecipient_Destroy()](#oh_ipcdeathrecipient_destroy).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OH_OnDeathRecipientCallback()](#oh_ondeathrecipientcallback) deathRecipientCallback | Callback for the death notification of the remote [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object. This parameter must not be null. |
| [OH_OnDeathRecipientDestroyCallback()](#oh_ondeathrecipientdestroycallback) destroyCallback | Callback for object destruction. This parameter can be NULL. If it is NULL, object destruction events are not listened to. Pass in this parameter when cleanup operations (such as releasing the userData resource) need to be performed upon destruction of the [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) object. If no cleanup is required, this parameter can be omitted or set to NULL. If it is NULL, object destruction does not trigger any callback notification. |
| void *userData | Pointer to the user private data. Pass in this parameter when user-defined data needs to be accessed in the death notification callback. If no user data needs to be accessed, this parameter can be omitted or set to NULL. If it is NULL, the callback function cannot access the user private data. |

**Returns**

| Type| Description|
| ---- | ---- |
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md)* | Returns the OHIPCDeathRecipient object pointer on success; returns NULL on failure.|

### OH_IPCDeathRecipient_Destroy()

```C
void OH_IPCDeathRecipient_Destroy(OHIPCDeathRecipient *recipient)
```

**Description**

Destroys an [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) object. It is commonly used when it is no longer necessary to listen for the death event of the remote object, and when the client exits or a module is unloaded and the death listener resources need to be cleaned up.

- This function and [OH_IPCDeathRecipient_Create()](#oh_ipcdeathrecipient_create) must be used in pairs.
- You must call [OH_IPCRemoteProxy_RemoveDeathRecipient()](#oh_ipcremoteproxy_removedeathrecipient) to remove the listener object from all proxies before destroying it.
- Destroy the death listening object when it is no longer needed.
- Destroying the listener object without removing it first may cause callback exceptions or memory leaks.
- After the destruction, **destroyCallback** is automatically triggered to release **userData**.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) *recipient | Pointer to the **OHIPCDeathRecipient** object to destroy. It cannot be NULL. |

### OH_IPCRemoteProxy_AddDeathRecipient()

```C
int OH_IPCRemoteProxy_AddDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)
```

**Description**

Adds a death listener to an [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object to receive the callback notification of the death of a remote [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object. It is commonly used when the client registers a server death listener after startup to detect server exceptions in a timely manner, when server fault detection and automatic recovery mechanisms need to be implemented, and when related resources need to be released or the user needs to be notified in a timely manner when the server is unavailable.

- Destroying the listener object without removing it first may cause callback exceptions or memory leaks.
- Call [OH_IPCDeathRecipient_Create()](#oh_ipcdeathrecipient_create) first to create the listener object.
- Call [OH_IPCRemoteProxy_AddDeathRecipient()](#oh_ipcremoteproxy_adddeathrecipient) to add the listener.
- During use, the listener callback is triggered.
- Before destroying the Proxy or Recipient, call [OH_IPCRemoteProxy_RemoveDeathRecipient()](#oh_ipcremoteproxy_removedeathrecipient) to remove the listener.
- Call [OH_IPCDeathRecipient_Destroy()](#oh_ipcdeathrecipient_destroy) to destroy the listener object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object to which the death notification is to be added. It cannot be NULL. |
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) *recipient | Pointer to the death recipient object used to receive death notifications of the remote object. It cannot be NULL. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the parameters are incorrect.<br> Returns [OH_IPC_ErrorCode#OH_IPC_INNER_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) in other cases.|

### OH_IPCRemoteProxy_RemoveDeathRecipient()

```C
int OH_IPCRemoteProxy_RemoveDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)
```

**Description**

Removes the death listener that has been added to the [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object. This is commonly used to unregister when the death event of the remote object no longer needs to be listened to, or to remove the old death listener when switching to another service instance.

- If a listener object is no longer needed, call [OH_IPCDeathRecipient_Destroy()](#oh_ipcdeathrecipient_destroy) to destroy it.
- Failure to destroy it may result in memory leaks.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object from which the death notification needs to be removed. It cannot be NULL. |
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) *recipient | Pointer to the death recipient object used to receive death notifications of the remote object. It cannot be NULL. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the parameters are incorrect.<br> Returns [OH_IPC_ErrorCode#OH_IPC_INNER_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) in other cases.|

### OH_IPCRemoteProxy_IsRemoteDead()

```C
int OH_IPCRemoteProxy_IsRemoteDead(const OHIPCRemoteProxy *proxy)
```

**Description**

Checks whether the remote [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object corresponding to the [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object is dead. It is commonly used to proactively check whether the server is alive before sending an IPC request, to determine whether a connection needs to be re-established in a reconnection mechanism, and to adopt different processing strategies based on the server's alive status in business logic.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| const [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object to check. It cannot be NULL. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns 1 if the remote [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object dies; otherwise, returns 0. If the parameter is invalid, it indicates that the remote [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object does not exist, and returns 1. |
