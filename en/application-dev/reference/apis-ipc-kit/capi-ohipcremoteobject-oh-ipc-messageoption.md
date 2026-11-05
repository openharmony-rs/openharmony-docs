# OH_IPC_MessageOption
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=98355c316452dae3a7c90b55e4a4861818921408 translatedAt=2026-11-04T03:44:15.907Z pushedAt=2026-11-04T10:13:14.856Z nl=1 -->

```c
typedef struct {...} OH_IPC_MessageOption
```

## Overview

Defines IPC message options, which are used to configure request parameters during IPC communication.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ohipcremoteobject.md)

**Header file**: [ipc_cremote_object.h](capi-ipc-cremote-object-h.md)

## Summary

### Member Variables

| Name| Description|
| ---- | ---- |
| [OH_IPC_RequestMode](capi-ipc-cremote-object-h.md#oh_ipc_requestmode) mode | Message request mode, which specifies the request method for IPC messages. You can select the synchronous mode or asynchronous mode. The synchronous mode is suitable for scenarios where you need to wait for the return result, while the asynchronous mode is suitable for scenarios where you do not need to wait for the result. When the synchronous mode is set, the call blocks the current thread to wait for the return result. When the asynchronous mode is set, the call returns immediately without waiting for the result. In C language, this member must be explicitly initialized. It is advised to initialize it to the synchronous mode (when a return result is required) or the asynchronous mode (when no return result is required). |
| uint32_t timeout | Parameter reserved for RPC. In RPC communication, you can set the timeout interval (in seconds). This parameter is invalid for IPC communication and can be ignored when IPC is used. The value range is [0, 4294967295]. In RPC scenarios, you are advised to set a proper timeout interval based on service requirements to avoid long-time blocking. If the timeout interval expires, the RPC call fails and a timeout error is returned. This member must be explicitly initialized in the C language. The recommended initial value is **0**. |
| void* reserved | Reserved parameter. NULL must be passed. Passing a non-null pointer may cause the API call to fail or result in undefined behavior. |
