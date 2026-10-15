# TEE_Param

```c
typedef union TEE_Param {...} TEE_Param
```

## Overview

Enumerates the TEE parameter.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| memref->buffer | Pointer to the memory buffer. |
| memref.size | Size of the memory buffer. |
| value.a | First value. |
| value.b | Second value. |
| sharedmem->buffer | Pointer to the shared memory buffer. |
| sharedmem.size | Size of the shared memory buffer. |


