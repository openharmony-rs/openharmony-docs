# OHIPCDeathRecipient

<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ceec5d18179ba29b1eca79fa9240e27795b5216c translatedAt=2026-07-28T02:20:10.108Z pushedAt=2026-07-29T06:53:57.029Z -->

```c
typedef struct OHIPCDeathRecipient OHIPCDeathRecipient
```

## Overview

Defines an IPC death notification object used to listen for the death event of an IPC remote object. After an **OHIPCDeathRecipient** object is created, it must be registered with an **OHIPCRemoteObject** object to take effect. If not registered, the death event cannot be detected. When the remote process terminates unexpectedly or is destroyed proactively, the local process that has registered the death event listener will receive a death notification callback, allowing it to release related resources or perform error handling in a timely manner.

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ohipcremoteobject.md)

**Header file**: [ipc_cremote_object.h](capi-ipc-cremote-object-h.md)