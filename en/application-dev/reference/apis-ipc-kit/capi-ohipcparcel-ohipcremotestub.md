# OHIPCRemoteStub
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=5214a7c0c0e0489abab20fb7eb1ac76644028e73 translatedAt=2026-10-19T08:30:02.333Z pushedAt=2026-10-19T11:46:57.648Z nl=1 -->

```c
typedef struct OHIPCRemoteStub OHIPCRemoteStub;
```

## Overview

Defines an IPC remote service object. This struct is used to represent a remote service on the server. As the service agent of the server in IPC, it processes requests from the client and implements cross-process communication. **OHIPCRemoteStub** is a core struct provided by IPC Kit. It simplifies the IPC service development process and provides a unified request processing mechanism, helping you quickly implement cross-process communication capabilities.

**System capability:** SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCParcel](capi-ohipcparcel.md)

**Header file**: [ipc_cparcel.h](capi-ipc-cparcel-h.md)
