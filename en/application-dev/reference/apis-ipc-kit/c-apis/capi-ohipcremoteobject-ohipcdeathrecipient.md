# OHIPCDeathRecipient

```c
typedef struct OHIPCDeathRecipient OHIPCDeathRecipient
```

## Overview

Defines an IPC death notification object used to listen for the death event of an IPC remote object. After an **OHIPCDeathRecipient** object is created, it must be registered with an **OHIPCRemoteObject** object to take effect. If not registered, the death event cannot be detected. When the remote process terminates unexpectedly or is destroyed proactively, the local process that has registered the death event listener will receive a death notification callback, allowing it to release related resources or perform error handling in a timely manner.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ohipcremoteobject.md)

**Header file**: [ipc_cremote_object.h](capi-ipc-cremote-object-h.md)

