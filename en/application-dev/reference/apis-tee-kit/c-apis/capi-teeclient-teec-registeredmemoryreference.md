# TEEC_RegisteredMemoryReference

```c
typedef struct TEEC_RegisteredMemoryReference {...} TEEC_RegisteredMemoryReference
```

## Overview

Defines a pointer to the shared memory that is registered or allocated.

<!--Device-typedef struct TEEC_RegisteredMemoryReference {...} TEEC_RegisteredMemoryReference--><!--Device-typedef struct TEEC_RegisteredMemoryReference {...} TEEC_RegisteredMemoryReference-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-tee-kit-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [TEEC_SharedMemory](capi-teeclient-teec-sharedmemory.md) *parent | Pointer to the parent shared memory.<br><!--Device-TEEC_SharedMemory *parent--><!--Device-TEEC_SharedMemory *parent-End--> |
| uint32_t size | Size of the registered memory reference.<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| uint32_t offset | Offset within the parent shared memory.<br><!--Device-uint32_t offset--><!--Device-uint32_t offset-End--> |


