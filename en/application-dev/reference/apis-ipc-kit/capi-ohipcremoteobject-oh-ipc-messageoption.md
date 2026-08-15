# OH_IPC_MessageOption

<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ceec5d18179ba29b1eca79fa9240e27795b5216c translatedAt=2026-07-28T02:20:11.228Z pushedAt=2026-07-29T06:58:32.009Z -->

```c
typedef struct {...} OH_IPC_MessageOption
```

## Overview

Defines the IPC message options, which are used to configure request parameters for IPC communication.

**System capability:** SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ohipcremoteobject.md)

**Header file**: [ipc_cremote_object.h](capi-ipc-cremote-object-h.md)

## Summary

### Member Variables

| Name | Description |
| ---- | ---- |
| [OH_IPC_RequestMode](capi-ipc-cremote-object-h.md#oh_ipc_requestmode) mode | Message request mode, which specifies the request method for IPC messages. Synchronous mode is suitable for scenarios where you need to wait for the return result, while asynchronous mode is suitable for scenarios where you do not need to wait for the result. When the synchronous mode is set, the call blocks the current thread to wait for the return result. When the asynchronous mode is set, the call returns immediately without waiting for the result. In C language, this member must be explicitly initialized. It is advised to initialize it to the synchronous mode (when a return result is required) or the asynchronous mode (when no return result is required). |
| uint32_t timeout | Reserved parameter for RPC. In RPC communication scenarios, this parameter can be used to set the timeout interval. This parameter is invalid for IPC communication and can be ignored when IPC is used. The unit is seconds. The value range is [0, 4294967295]. In RPC scenarios, it is recommended to set a reasonable timeout interval based on service requirements to avoid prolonged blocking. After the timeout, the RPC call fails and returns a timeout error. In C language, this member must be explicitly initialized. It is recommended to initialize it to **0**. |
| void* reserved | Reserved parameter. NULL must be passed. Passing a non-null pointer may cause the API call to fail or result in undefined behavior. |