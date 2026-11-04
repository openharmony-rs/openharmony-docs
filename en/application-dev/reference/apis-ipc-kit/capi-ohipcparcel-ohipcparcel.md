# OHIPCParcel

<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=98355c316452dae3a7c90b55e4a4861818921408 translatedAt=2026-11-04T03:42:49.637Z pushedAt=2026-11-04T10:13:14.850Z nl=1 -->

```c
typedef struct OHIPCParcel OHIPCParcel
```

## Overview

IPC serialization object used to serialize and deserialize data in cross-process communication. This object must be created and destroyed through related functions. Developers must follow the lifecycle management specifications of the object to properly manage memory resources.

**Since**: 12

**Related module**: [OHIPCParcel](capi-ohipcparcel.md)

**Header file**: [ipc_cparcel.h](capi-ipc-cparcel-h.md)
