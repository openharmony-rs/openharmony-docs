# OH_IPC_MessageOption

```c
typedef struct OH_IPC_MessageOption {...} OH_IPC_MessageOption
```

## Overview

Defines IPC message options, which are used to configure request parameters during IPC communication.

<!--Device-typedef struct OH_IPC_MessageOption {...} OH_IPC_MessageOption--><!--Device-typedef struct OH_IPC_MessageOption {...} OH_IPC_MessageOption-End-->

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ipc-kit-ohipcremoteobject.md)

**Header file**: [ipc_cremote_object.h](capi-ipc-cremote-object-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_IPC_RequestMode](capi-ipc-cremote-object-h.md#oh_ipc_requestmode) mode | Message request mode, which is used to specify the request mode of IPC messages. You can select the synchronous or asynchronous mode. The synchronous mode is applicable to scenarios where you need to wait for the result, and the asynchronous mode is applicable to scenarios where you do not need to wait for the result. After the synchronous mode is set, the call blocks the current thread and waits for the result. After the asynchronous mode is set, the call returns immediately without waiting for the result. This member must be explicitly initialized in the C language. You are advised to initialize the synchronous mode (when the result needs to be obtained) or asynchronous mode (when the result does not need to be returned).<br>**Since**: 12 |
| uint32_t timeout | Parameter reserved for RPC. In RPC communication, you can set the timeout interval (in seconds). This parameter is invalid for IPC communication and can be ignored when IPC is used. The value range is [0,<br>&nbsp;4294967295]. In RPC scenarios, you are advised to set a proper timeout interval based on service requirements to avoid long-time blocking. If the timeout interval expires, the RPC call fails and a timeout error is returned. This member must be explicitly initialized in the C language. The recommended initial value is **0**.<br>**Since**: 12 |
| void* reserved | Reserved parameter, which must be NULL. If a non-null pointer is passed, the API call may fail or undefined behavior may occur.<br>**Since**: 12 |


