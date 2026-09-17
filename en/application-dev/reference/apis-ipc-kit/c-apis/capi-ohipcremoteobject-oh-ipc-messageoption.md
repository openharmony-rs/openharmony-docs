# OH_IPC_MessageOption

```c
typedef struct OH_IPC_MessageOption {...} OH_IPC_MessageOption
```

## Overview

Defines the IPC message options.

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ohipcremoteobject.md)

**Header file**: [ipc_cremote_object.h](capi-ipc-cremote-object-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_IPC_RequestMode](capi-ipc-cremote-object-h.md#oh_ipc_requestmode) mode | Message request mode. |
| uint32_t timeout | Parameter reserved for RPC, which is invalid for IPC. |
| void* reserved | Reserved parameter, which must be NULL. |


