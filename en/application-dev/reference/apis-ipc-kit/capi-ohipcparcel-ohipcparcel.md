# OHIPCParcel

<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ceec5d18179ba29b1eca79fa9240e27795b5216c translatedAt=2026-07-28T02:18:59.938Z pushedAt=2026-07-29T07:07:40.770Z -->

```c
typedef struct OHIPCParcel OHIPCParcel
```

## Overview

IPC serialization object, used for serializing and deserializing data in cross-process communication. This object must be created and destroyed through related functions. You must follow the lifecycle management specifications of the object and properly manage memory resources.

**Since**: 12

**Related module**: [OHIPCParcel](capi-ohipcparcel.md)

**Header file**: [ipc_cparcel.h](capi-ipc-cparcel-h.md)