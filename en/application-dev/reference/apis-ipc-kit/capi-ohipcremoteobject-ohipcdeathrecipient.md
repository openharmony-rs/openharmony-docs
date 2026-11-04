# OHIPCDeathRecipient
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=563b8be563e11a9d9d559f338c53d2269358d4f7 translatedAt=2026-11-03T13:13:47.241Z pushedAt=2026-11-04T08:47:59.674Z nl=1 -->

```c
typedef struct OHIPCDeathRecipient OHIPCDeathRecipient
```

## Overview

Defines the IPC death notification object, which is used to listen for the death event of a remote IPC object. After an **OHIPCDeathRecipient** object is created, it must be registered with the [OHIPCRemoteObject](capi-ohipcremoteobject.md) object to take effect. If it is not registered, death events cannot be listened for. When a remote process terminates unexpectedly or is destroyed, the local process that has registered the death listener will receive a death notification callback. This allows the local process to release related resources or handle errors in a timely manner.

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ohipcremoteobject.md)

**Header file**: [ipc_cremote_object.h](capi-ipc-cremote-object-h.md)
