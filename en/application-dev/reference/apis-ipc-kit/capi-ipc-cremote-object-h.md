# ipc_cremote_object.h
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->

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
| [OH_IPC_MessageOption](capi-ohipcremoteobject-oh-ipc-messageoption.md) | - | Defines an IPC message.|
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) | OHIPCDeathRecipient | Defines an object that receives death notifications.|

### Enums

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| [OH_IPC_RequestMode](#oh_ipc_requestmode) | OH_IPC_RequestMode | Enumerates the IPC request modes.|

### Function

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| [typedef int (\*OH_OnRemoteRequestCallback)(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData)](#oh_onremoterequestcallback) | OH_OnRemoteRequestCallback | Called to process the peer request at the stub.|
| [typedef void (\*OH_OnRemoteDestroyCallback)(void *userData)](#oh_onremotedestroycallback) | OH_OnRemoteDestroyCallback | Called when an observed object is destroyed.|
| [OHIPCRemoteStub* OH_IPCRemoteStub_Create(const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)](#oh_ipcremotestub_create) | - | Creates an **OHIPCRemoteStub** object.|
| [void OH_IPCRemoteStub_Destroy(OHIPCRemoteStub *stub)](#oh_ipcremotestub_destroy) | - | Destroys an **OHIPCRemoteStub** object.|
| [void OH_IPCRemoteProxy_Destroy(OHIPCRemoteProxy *proxy)](#oh_ipcremoteproxy_destroy) | - | Destroys an **OHIPCRemoteProxy** object.|
| [int OH_IPCRemoteProxy_SendRequest(const OHIPCRemoteProxy *proxy, uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, const OH_IPC_MessageOption *option)](#oh_ipcremoteproxy_sendrequest) | - | Sends an IPC message.|
| [int OH_IPCRemoteProxy_GetInterfaceDescriptor(OHIPCRemoteProxy *proxy, char **descriptor, int32_t *len, OH_IPC_MemAllocator allocator)](#oh_ipcremoteproxy_getinterfacedescriptor) | - | Obtains the interface descriptor from the stub.|
| [typedef void (\*OH_OnDeathRecipientCallback)(void *userData)](#oh_ondeathrecipientcallback) | OH_OnDeathRecipientCallback | Defines a callback to be invoked when the remote **OHIPCRemoteStub** object dies unexpectedly.|
| [typedef void (\*OH_OnDeathRecipientDestroyCallback)(void *userData)](#oh_ondeathrecipientdestroycallback) | OH_OnDeathRecipientDestroyCallback | Defines a callback to be invoked when the **OHIPCDeathRecipient** object is destroyed.|
| [OHIPCDeathRecipient* OH_IPCDeathRecipient_Create(OH_OnDeathRecipientCallback deathRecipientCallback, OH_OnDeathRecipientDestroyCallback destroyCallback, void *userData)](#oh_ipcdeathrecipient_create) | - | Creates an **OHIPCDeathRecipient** object.|
| [void OH_IPCDeathRecipient_Destroy(OHIPCDeathRecipient *recipient)](#oh_ipcdeathrecipient_destroy) | - | Destroys an **OHIPCDeathRecipient** object.|
| [int OH_IPCRemoteProxy_AddDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)](#oh_ipcremoteproxy_adddeathrecipient) | - | Subscribes to the death of an **OHIPCRemoteStub** object for an **OHIPCRemoteProxy** object.|
| [int OH_IPCRemoteProxy_RemoveDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)](#oh_ipcremoteproxy_removedeathrecipient) | - | Unsubscribes from the death of the **OHIPCRemoteStub** object for an **OHIPCRemoteProxy** object.|
| [int OH_IPCRemoteProxy_IsRemoteDead(const OHIPCRemoteProxy *proxy)](#oh_ipcremoteproxy_isremotedead) | - | Checks whether the **OHIPCRemoteStub** object corresponding to the **OHIPCRemoteProxy** object is dead.|

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
| OH_IPC_REQUEST_MODE_SYNC = 0 | Synchronous request. Suitable for scenarios where you need to wait for a return result, such as query operations and simple request-response scenarios.|
| OH_IPC_REQUEST_MODE_ASYNC = 1 | Asynchronous request. Suitable for scenarios where you do not need to obtain the result immediately or where operations are time-consuming, such as large-data transmission and background processing.|

## Function Description

### OH_OnRemoteRequestCallback()

```C
typedef int(*OH_OnRemoteRequestCallback)(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData)
```

**Description**

Called to process the peer request at the stub. This callback is triggered when the proxy sends a request through [OH_IPCRemoteProxy_SendRequest](#oh_ipcremoteproxy_sendrequest). The callback is executed in the Binder thread pool. Therefore, pay attention to thread security. The callback should return as soon as possible to avoid long-time blocking. Otherwise, the processing of other IPC requests may be affected.

- This function is used to receive and process cross-process requests from the client when the server implements a custom IPC communication protocol.
- When the server capabilities need to be called across processes, the server uses this callback to process the specific service logic.
- This function serves as the entry for message distribution and processing when the RPC server capability is implemented.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| -------- | -------- |
| uint32_t code | Custom IPC command word, in the range [0x01, 0x00ffffff]. It is advised to define code values in segments based on service modules to avoid conflicts between different functional commands. For example, 0x01 to 0x100 can be used for basic functions, and 0x101 to 0x200 for extended functions.|
| const [OHIPCParcel](capi-ohipcparcel.md) *data | Pointer to the requested data object. It cannot be NULL or released in the function.|
| [OHIPCParcel](capi-ohipcparcel.md) *reply | Pointer to the response data object. It cannot be NULL or released in the function. If this function returns an error, data cannot be written to this parameter.|
| void *userData | User private data. Pass this parameter when you need to access user-defined data in the callback function. If user data is not required, you can pass NULL. If this parameter is set to NULL, the callback function cannot access the user's private data.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns a custom error code in the range [1909001, 1909999] or a system error code otherwise.<br> If the custom error code is out of range, [OH_IPC_ErrorCode#OH_IPC_INVALID_USER_ERROR_CODE](capi-ipc-error-code-h.md#oh_ipc_errorcode) is returned.|

### OH_OnRemoteDestroyCallback()

```C
typedef void(*OH_OnRemoteDestroyCallback)(void *userData)
```

**Description**

Called when an observed object is destroyed.

- Release related resources (such as memory and file handles) when the stub object is destroyed.
- Notify other modules to synchronize the status when the object is destroyed.
- Clear private user data when the object is destroyed.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ----- | ----- |
| void *userData | User private data. This parameter is passed when user-defined data needs to be accessed in the callback function. If user data does not need to be accessed, this parameter can be set to NULL. If this parameter is set to NULL, the callback function cannot access the user's private data.|

### OH_IPCRemoteStub_Create()

```C
OHIPCRemoteStub* OH_IPCRemoteStub_Create(const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)
```

**Description**

Creates an **OHIPCRemoteStub** object, which is used on the stub side to create a server-side object for processing remote data requests from the proxy side.

- When a server needs to provide cross-process service capabilities, it can create a stub object as the server-side entity.
- It can also be used to implement the server side of custom IPC communication protocols, building RPC server capabilities.
- After the stub object is created, it is typically registered with the service manager through the **OH_IPCRemoteProxy** related APIs, so that the proxy side can discover and connect to it.
- **requestCallback** should avoid time-consuming operations, as they may block IPC communication.
- If time-consuming tasks need to be handled, you can return an error code in the callback and use a thread pool to process the tasks asynchronously.
- Ensure that the lifecycle of **userData** covers the lifecycle of the stub object to avoid dangling pointers.
- After the object is created via [OH_IPCRemoteStub_Create()](#oh_ipcremotestub_create), it must be destroyed using [OH_IPCRemoteStub_Destroy()](#oh_ipcremotestub_destroy) after use to release resources.
- If the object is not destroyed, memory leak occurs.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| const char *descriptor | Pointer to the descriptor of the **OHIPCRemoteStub** object to create. It cannot be NULL. The string length range is (0, 204800], in bytes. If the value is out of range, NULL is returned. You are advised to use a unique identifier string, for example, **com.example.myservice** or **MyService**. The format is typically a reverse domain name or a simple service name, used to identify different IPC service APIs.|
| [OH_OnRemoteRequestCallback](#oh_onremoterequestcallback) requestCallback | Data request processing function. It cannot be NULL.|
| [OH_OnRemoteDestroyCallback](#oh_onremotedestroycallback) destroyCallback | Callback function for object destruction. Pass this parameter when you need to perform cleanup operations (such as releasing **userData** resources) when the stub object is destroyed. If cleanup is not required, you can omit it or pass NULL. If not passed, no callback notifications will be triggered upon object destruction.|
| void *userData |  User private data. This parameter is passed when user-defined data needs to be accessed in the callback function. If user data does not need to be accessed, this parameter can be set to NULL. If this parameter is set to NULL, the callback function cannot access the user's private data.|

**Returns**

| Type| Description|
| ---- | ---- |
| OHIPCRemoteStub* | Returns the pointer to the **OHIPCRemoteStub** object created if the operation is successful; returns NULL otherwise.|

### OH_IPCRemoteStub_Destroy()

```C
void OH_IPCRemoteStub_Destroy(OHIPCRemoteStub *stub)
```

**Description**

Destroys an **OHIPCRemoteStub** object.

- Release the stub object when the server no longer needs to provide the IPC service.
- Clear IPC resources when the server exits or the module is uninstalled.
- This function and [OH_IPCRemoteStub_Create()](#oh_ipcremotestub_create) must be used in pairs.
- This method must be called when the stub object is no longer used.
- After the destruction, the **destroyCallback** callback is automatically triggered to release **userData**.
- After the destruction, the stub object cannot be used for any operation.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) *stub | Pointer to the **OHIPCRemoteStub** object to destroy. It cannot be NULL.|

### OH_IPCRemoteProxy_Destroy()

```C
void OH_IPCRemoteProxy_Destroy(OHIPCRemoteProxy *proxy)
```

**Description**

Destroys an **OHIPCRemoteProxy** object.

- Release the proxy object when the client no longer needs to call the remote service.
- Clear IPC resources when the client exits or the module is uninstalled.
- You must call [OH_IPCRemoteProxy_RemoveDeathRecipient()](#oh_ipcremoteproxy_removedeathrecipient) to remove all added death event listeners before destroying the proxy object.
- If the proxy object is destroyed when the listeners are not removed, the death event listener callback will be abnormal or memory leakage will occur.
- After the destruction, no method of the proxy can be called.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object to destroy. It cannot be NULL.|

### OH_IPCRemoteProxy_SendRequest()

```C
int OH_IPCRemoteProxy_SendRequest(const OHIPCRemoteProxy *proxy, uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, const OH_IPC_MessageOption *option)
```

**Description**

Sends an IPC message from the proxy to the remote stub. This function supports both synchronous and asynchronous communication modes.

- When the client needs to call server capabilities across processes, it sends a request and receives a response.
- This function enables IPC communication between the client and the server.
- This function can call service of remote services.
- Synchronous mode is suitable for requests that need to wait for a result, such as query operations, while asynchronous mode is suitable for requests that do not need to wait for a result, such as log reporting.
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
| const [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object. It cannot be NULL.|
| uint32_t code | Custom IPC command word, in the range [0x01, 0x00ffffff]. If the value is out of range, the **OH_IPC_CODE_OUT_OF_RANGE** error is returned. It is advised to define code values in segments based on service modules, and ensure that the same command word definitions are used on both the proxy side and the stub side. Different operations of the same service API should use distinct code values for identification.|
| const [OHIPCParcel](capi-ohipcparcel.md) *data | Pointer to the requested data object. It cannot be NULL.|
| [OHIPCParcel](capi-ohipcparcel.md) *reply | Pointer to the response data object. For a synchronous request, this parameter cannot be null and is used to store the response result. For an asynchronous request, this parameter can be null, in which case the response result is not stored.|
| const [OH_IPC_MessageOption](capi-ohipcremoteobject-oh-ipc-messageoption.md) *option | Pointer to the message option, which is used to configure the IPC message sending mode (synchronous/asynchronous). Pass this parameter when the asynchronous mode or custom message option is required. For asynchronous requests, the corresponding request mode must be passed and set. For synchronous requests, you may omit it or pass NULL. If omitted or NULL is passed, the synchronous mode (**OH_IPC_REQUEST_MODE_SYNC**) is used by default.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the message is sent successfully.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_DEAD_REMOTE_OBJECT](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the remote **OHIPCRemoteStub** object dies.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CODE_OUT_OF_RANGE](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the code is out of range.<br> Returns [OH_IPC_ErrorCode#OH_IPC_INNER_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) or a custom error code (range: [1909001, 1909999]) in other cases.|

### OH_IPCRemoteProxy_GetInterfaceDescriptor()

```C
int OH_IPCRemoteProxy_GetInterfaceDescriptor(OHIPCRemoteProxy *proxy, char **descriptor, int32_t *len, OH_IPC_MemAllocator allocator)
```

**Description**

Obtains the interface descriptor from the stub. The interface descriptor is the unique identifier of the stub object. It is used to identify the remote service type, check service version compatibility, or verify whether the remote service implements a specific API. This function obtains the descriptor string from the remote stub via IPC call and stores the result using the user-provided memory allocator.

- The memory of the returned descriptor string is allocated by the user-provided allocator. The user must actively release it after use; otherwise, memory leaks will occur. Even if the function call fails, you should still check whether the descriptor is not NULL and release it accordingly.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object. It cannot be NULL.|
| char **descriptor | Pointer to the address of the memory for holding the interface descriptor. The memory is allocated by the allocator provided by the user and needs to be released. This pointer cannot be NULL. If an error code is returned, you still need to check whether the memory is empty and release the memory. Otherwise, memory leaks may occur. You are advised to release it immediately after use to prevent memory leaks.|
| int32_t *len | Pointer to the length of the data written to the descriptor, including the terminator. It cannot be NULL.|
| [OH_IPC_MemAllocator](capi-ipc-cparcel-h.md#oh_ipc_memallocator) allocator | Memory allocator specified by the user for allocating memory. It cannot be empty.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the message is sent successfully.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the parameters are incorrect.<br> Returns [OH_IPC_ErrorCode#OH_IPC_DEAD_REMOTE_OBJECT](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the remote **OHIPCRemoteStub** object dies.<br> Returns [OH_IPC_ErrorCode#OH_IPC_MEM_ALLOCATOR_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the memory allocation fails.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) or a custom error code if the data in the serialized object fails to be read.|

### OH_OnDeathRecipientCallback()

```C
typedef void (*OH_OnDeathRecipientCallback)(void *userData)
```

**Description**

Defines a callback to be invoked when the remote **OHIPCRemoteStub** object dies unexpectedly. When the process where the remote stub object resides exits abnormally or is killed by the system, the system triggers this callback to notify the client. The callback is executed in the Binder thread. Therefore, pay attention to thread security. Complex IPC operations are not recommended in callback to avoid potential deadlock risks. This function is commonly used when the client needs to detect abnormal exit or crash of the server, perform resource cleanup or state reset when the server object dies, or implement server liveness monitoring and fault recovery mechanisms.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| void *userData | Pointer to user private data.Pass this parameter when user-defined data needs to be accessed in the death notification callback. If user data does not need to be accessed, this parameter can be omitted or set to NULL. If this parameter is set to NULL, the callback function cannot access the user's private data.|

### OH_OnDeathRecipientDestroyCallback()

```C
typedef void (*OH_OnDeathRecipientDestroyCallback)(void *userData)
```

**Description**

Defines a callback to be invoked when the **OHIPCDeathRecipient** object is destroyed. This function is usually used to release user private data or clear resources related to death listening when the death listening object is destroyed.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| void *userData | Pointer to user private data.Pass this parameter when user-defined data needs to be accessed in the death notification callback. If user data does not need to be accessed, this parameter can be omitted or set to NULL. If this parameter is set to NULL, the callback function cannot access the user's private data.|

### OH_IPCDeathRecipient_Create()

```C
OHIPCDeathRecipient* OH_IPCDeathRecipient_Create(OH_OnDeathRecipientCallback deathRecipientCallback, OH_OnDeathRecipientDestroyCallback destroyCallback, void *userData)
```

**Description**

Creates an **OHIPCDeathRecipient** object, which triggers a notification when the **OHIPCRemoteStub** object dies unexpectedly. Listens for the death status of a remote stub object. It is commonly used when the client needs to listen for death events of the server object, implement a mechanism for detecting abnormal server exits, or perform fault handling or automatic reconnection when the server crashes.

- The death callback is triggered when the remote stub object is destroyed or the process crashes. It is advised to release related resources, reset state, and attempt reconnection in the callback.
- The death callback may be executed on any thread, so thread safety must be taken into account. Avoid performing time-consuming operations in the callback.
- It is recommended not to destroy the [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) object directly in the callback. Destruction should be performed outside the callback.
- Multiple proxies can share the same [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) object, but you must ensure that it is removed from all proxies before destruction.
- If the proxy is already dead, adding a death listener will immediately trigger the callback. Therefore, you need to check the status before adding the listener.
- It is recommended that you create and add a death listener during application initialization, and remove and destroy it when the application exits.
- After creation, it must be added to the proxy object via [OH_IPCRemoteProxy_AddDeathRecipient()](#oh_ipcremoteproxy_adddeathrecipient).
- When the listener is no longer needed, you must first remove it via [OH_IPCRemoteProxy_RemoveDeathRecipient()](#oh_ipcremoteproxy_removedeathrecipient).
- After removal, the object must be destroyed by calling [OH_IPCDeathRecipient_Destroy()](#oh_ipcdeathrecipient_destroy).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OH_OnDeathRecipientCallback](#oh_ondeathrecipientcallback) deathRecipientCallback | Callback to be invoked when the **OHIPCRemoteStub** object is dead. It cannot be NULL.|
| [OH_OnDeathRecipientDestroyCallback](#oh_ondeathrecipientdestroycallback) destroyCallback | Callback to be invoked when an object is destroyed. It can be NULL. If this parameter is NULL, the object destruction event is not listened to. Pass this parameter when you need to perform cleanup operations (such as releasing **userData** resources) when the **OHIPCDeathRecipient** object is destroyed. If cleanup is not required, you can omit it or pass NULL. If this parameter is set to NULL, no callback notifications will be triggered upon object destruction.|
| void *userData | Pointer to user private data. Pass this parameter when user-defined data needs to be accessed in the death notification callback. If user data does not need to be accessed, this parameter can be omitted or set to NULL. If this parameter is set to NULL, the callback function cannot access the user's private data.|

**Returns**

| Type| Description|
| ---- | ---- |
| OHIPCDeathRecipient* | Returns the pointer to the **OHIPCDeathRecipient** object created if the operation is successful; returns NULL otherwise.|

### OH_IPCDeathRecipient_Destroy()

```C
void OH_IPCDeathRecipient_Destroy(OHIPCDeathRecipient *recipient)
```

**Description**

Destroys an **OHIPCDeathRecipient** object. This function is commonly used to clear death listening resources when the death events of remote objects no longer need to be listened for, or when the client exits or the module is uninstalled.


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
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) *recipient | Pointer to the **OHIPCDeathRecipient** object to destroy. It cannot be NULL.|

### OH_IPCRemoteProxy_AddDeathRecipient()

```C
int OH_IPCRemoteProxy_AddDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)
```

**Description**

Subscribes to the death of an **OHIPCRemoteStub** object for an **OHIPCRemoteProxy** object. This function is commonly used after the client starts, to register a server death listener so that server exceptions can be detected in a timely manner, to implement server fault detection and automatic recovery mechanisms, and to release related resources or notify the user when the server becomes unavailable.

- Destroying the listener object without removing it first may cause callback exceptions or memory leaks.
- First call [OH_IPCDeathRecipient_Create()](#oh_ipcdeathrecipient_create) to create a listener object.
- Call [OH_IPCRemoteProxy_AddDeathRecipient()](#oh_ipcremoteproxy_adddeathrecipient) to add a listener.
- The listener callback will be triggered during use.
- Before destroying the proxy or recipient, call [OH_IPCRemoteProxy_RemoveDeathRecipient()](#oh_ipcremoteproxy_removedeathrecipient) to remove the listener.
- Call [OH_IPCDeathRecipient_Destroy()](#oh_ipcdeathrecipient_destroy) to destroy the listener object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object to which the death notification is to be added. It cannot be NULL.|
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) *recipient | Pointer to the death recipient object used to receive death notifications of the remote object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the parameters are incorrect.<br> Returns [OH_IPC_ErrorCode#OH_IPC_INNER_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) in other cases.|

### OH_IPCRemoteProxy_RemoveDeathRecipient()

```C
int OH_IPCRemoteProxy_RemoveDeathRecipient(OHIPCRemoteProxy *proxy, OHIPCDeathRecipient *recipient)
```

**Description**

Unsubscribes from the death of the **OHIPCRemoteStub** object for an **OHIPCRemoteProxy** object. This function is commonly used to unregister the death event listener when the remote object's death events no longer need to be monitored, or to remove the old death listener when switching to another service instance.

- If a listener object is no longer needed, call [OH_IPCDeathRecipient_Destroy()](#oh_ipcdeathrecipient_destroy) to destroy it.
- Failure to destroy it may result in memory leaks.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object from which the death notification needs to be removed. It cannot be NULL.|
| [OHIPCDeathRecipient](capi-ohipcremoteobject-ohipcdeathrecipient.md) *recipient | Pointer to the death recipient object used to receive death notifications of the remote object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the parameters are incorrect.<br> Returns [OH_IPC_ErrorCode#OH_IPC_INNER_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) in other cases.|

### OH_IPCRemoteProxy_IsRemoteDead()

```C
int OH_IPCRemoteProxy_IsRemoteDead(const OHIPCRemoteProxy *proxy)
```

**Description**

Checks whether the **OHIPCRemoteStub** object corresponding to the **OHIPCRemoteProxy** object is dead. This function is commonly used to proactively check whether the server is alive before sending an IPC request, to determine whether a reconnection is needed in the reconnection mechanism, and to adopt different handling strategies based on the server's liveness status in the service logic.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| const [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object to check. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns **1** if the **OHIPCRemoteStub** object is dead or invalid parameters are found; returns **0** otherwise. If invalid parameters are found, the **OHIPCRemoteStub** object does not exist, and **1** is returned.|
