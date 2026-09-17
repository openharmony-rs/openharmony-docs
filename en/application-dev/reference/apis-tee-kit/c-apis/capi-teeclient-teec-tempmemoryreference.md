# TEEC_TempMemoryReference

```c
typedef struct TEEC_TempMemoryReference {...} TEEC_TempMemoryReference
```

## Overview

Defines a pointer to a temporary buffer.

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *buffer | Pointer to the temporary memory buffer. |
| uint32_t size | Size of the temporary memory buffer. |


