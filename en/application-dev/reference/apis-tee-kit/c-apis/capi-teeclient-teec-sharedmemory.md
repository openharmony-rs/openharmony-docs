# TEEC_SharedMemory

```c
typedef struct TEEC_SharedMemory {...} TEEC_SharedMemory
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
| void *buffer | Pointer to the shared memory buffer. |
| uint32_t size | Size of the shared memory buffer. |
| uint32_t flags | Flags associated with the shared memory. |
| uint32_t ops_cnt | The number of operations associated with the shared memory. |
| bool is_allocated | Indicates whether the memory has been allocated. |
| union | Union for either a linked list head or implementation-specific data.<br>**Since**: 20 |
| struct [ListNode](capi-teeclient-listnode.md) head | Linked list head for shared memory-related data. |
| void* imp;
 } | Implementation-specific data. |
| [TEEC_Context](capi-teeclient-teec-context.md) *context | Pointer to the TEEC context associated with the shared memory. |


