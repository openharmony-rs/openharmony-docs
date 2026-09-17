# TEEC_RegisteredMemoryReference

```c
typedef struct TEEC_RegisteredMemoryReference {...} TEEC_RegisteredMemoryReference
```

## Overview

Defines a pointer to the shared memory that is registered or allocated.

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [TEEC_SharedMemory](capi-teeclient-teec-sharedmemory.md) *parent | Pointer to the parent shared memory. |
| uint32_t size | Size of the registered memory reference. |
| uint32_t offset | Offset within the parent shared memory. |


