# OHIPCDeathRecipient

```c
typedef struct OHIPCDeathRecipient OHIPCDeathRecipient
```

## Overview

Defines the IPC death notification object, which is used to listen for the death event of a remote IPC object. After an **OHIPCDeathRecipient** object is created, it must be registered with the OHIPCRemoteObject object to take effect. If it is not registered, death events cannot be listened for. When a remote process terminates unexpectedly or is destroyed, the local process that has registered the death listener will receive a death notification callback. This allows the local process to release related resources or handle errors in a timely manner.

<!--Device-typedef struct OHIPCDeathRecipient OHIPCDeathRecipient--><!--Device-typedef struct OHIPCDeathRecipient OHIPCDeathRecipient-End-->

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ipc-kit-ohipcremoteobject.md)

**Header file**: [ipc_cremote_object.h](capi-ipc-cremote-object-h.md)

