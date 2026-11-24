# TEEC_SharedMemory

```c
typedef struct TEEC_SharedMemory {...} TEEC_SharedMemory
```

## Overview

Defines a shared memory block, which can be registered or allocated.

<!--Device-typedef struct TEEC_SharedMemory {...} TEEC_SharedMemory--><!--Device-typedef struct TEEC_SharedMemory {...} TEEC_SharedMemory-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-tee-kit-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *buffer | Pointer to the shared memory buffer.<br><!--Device-void *buffer--><!--Device-void *buffer-End--> |
| uint32_t size | Size of the shared memory buffer.<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| uint32_t flags | Flags associated with the shared memory.<br><!--Device-uint32_t flags--><!--Device-uint32_t flags-End--> |
| uint32_t ops_cnt | The number of operations associated with the shared memory.<br><!--Device-uint32_t ops_cnt--><!--Device-uint32_t ops_cnt-End--> |
| bool is_allocated | Indicates whether the memory has been allocated.<br><!--Device-bool is_allocated--><!--Device-bool is_allocated-End--> |
| head | Linked list head for shared memory-related data.<br><!--Device-head--><!--Device-head-End--> |
| imp | Implementation-specific data.<br><!--Device-imp--><!--Device-imp-End--> |
| [TEEC_Context](capi-teeclient-teec-context.md) *context | Pointer to the TEEC context associated with the shared memory.<br><!--Device-TEEC_Context *context--><!--Device-TEEC_Context *context-End--> |


