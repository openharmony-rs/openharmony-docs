# TEE_Param

```c
typedef union TEE_Param {...} TEE_Param
```

## Overview

Enumerates the TEE parameter.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-others-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| memref | Describes a memory reference.<br>**Since**: 20 |
| memref.buffer | Pointer to the memory buffer. |
| memref.size | Size of the memory buffer. |
| value | Describes value parameters.<br>**Since**: 20 |
| value.a | First value. |
| value.b | Second value. |
| sharedmem | Describes shared memory reference.<br>**Since**: 20 |
| sharedmem.buffer | Pointer to the shared memory buffer. |
| sharedmem.size | Size of the shared memory buffer. |


