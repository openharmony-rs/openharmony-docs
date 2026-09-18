# TEE_Param

```c
typedef union TEE_Param {...} TEE_Param
```

## Overview

Enumerates the TEE parameter.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct | Describes a memory reference.<br>**Since**: 20 |
| void *buffer | Pointer to the memory buffer. |
| size_t size;
 } memref | Size of the memory buffer. |
| struct | Describes value parameters.<br>**Since**: 20 |
| unsigned int a | First value. |
| unsigned int b;
 } value | Second value. |
| struct | Describes shared memory reference.<br>**Since**: 20 |
| void *buffer | Pointer to the shared memory buffer. |
| size_t size;
 } sharedmem | Size of the shared memory buffer. |


