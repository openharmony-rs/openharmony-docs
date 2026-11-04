# OHIPCParcel

<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=98355c316452dae3a7c90b55e4a4861818921408 translatedAt=2026-11-03T13:13:01.348Z pushedAt=2026-11-04T08:47:59.670Z nl=1 -->

```c
typedef struct OHIPCParcel OHIPCParcel
```

## Overview

An IPC serialization object used to serialize and deserialize data in inter-process communication. This object must be created and destroyed through related functions. Developers must follow the lifecycle management specifications of the object to properly manage memory resources.

**Since**: 12

**Related module**: [OHIPCParcel](capi-ohipcparcel.md)

**Header file**: [ipc_cparcel.h](capi-ipc-cparcel-h.md)
