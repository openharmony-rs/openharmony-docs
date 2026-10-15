# OHIPCRemoteProxy

```c
typedef struct OHIPCRemoteProxy OHIPCRemoteProxy
```

## Overview

IPC remote proxy object, which is used on the client side to proxy the capabilities of a remote service to implement cross-process communication. This object encapsulates a reference to the remote service and supports sending requests to and receiving responses from the remote service. It is applicable to scenarios that require cross-process service capability invocation, such as cross-process service calls, system service access, and cross-application data sharing. Using this object simplifies the implementation of cross-process communication and improves development efficiency.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCParcel](capi-ohipcparcel.md)

**Header file**: [ipc_cparcel.h](capi-ipc-cparcel-h.md)

