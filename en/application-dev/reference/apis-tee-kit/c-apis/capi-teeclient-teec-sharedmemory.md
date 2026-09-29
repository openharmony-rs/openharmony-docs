# TEEC_SharedMemory

```c
typedef union TEEC_SharedMemory {...} TEEC_SharedMemory
```

## Overview

Defines a shared memory block, which can be registered or allocated.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [struct ListNode](capi-teeclient-listnode.md) head | Linked list head for shared memory-related data. |
| void* imp;
 } | Implementation-specific data. |
| TEEC_Context *context | Pointer to the TEEC context associated with the shared memory. |


