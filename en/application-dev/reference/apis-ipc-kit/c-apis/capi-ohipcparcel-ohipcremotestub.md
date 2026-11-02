# OHIPCRemoteStub

```c
typedef struct OHIPCRemoteStub OHIPCRemoteStub
```

## Overview

Defines an IPC remote service object. This struct is used to represent a remote service on the server. As the service agent of the server in IPC, it processes requests from the client and implements cross-process communication. **OHIPCRemoteStub** is a core struct provided by IPC Kit. It simplifies the IPC service development process and provides a unified request processing mechanism, helping you quickly implement cross-process communication capabilities.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCParcel](capi-others-ohipcparcel.md)

**Header file**: [ipc_cparcel.h](capi-ipc-cparcel-h.md)

