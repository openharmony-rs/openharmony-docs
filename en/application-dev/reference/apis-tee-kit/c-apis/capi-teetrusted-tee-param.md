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
| [](capi-teetrusted---tee-objecthandle.md)s[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md)r[](capi-teetrusted---tee-objecthandle.md)u[](capi-teetrusted---tee-objecthandle.md)c[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md) | Describes a memory reference.<br>**Since**: 20 |
| void *buffer | Pointer to the memory buffer. |
| size_t size;
 } memref | Size of the memory buffer. |
| [](capi-teetrusted---tee-objecthandle.md)s[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md)r[](capi-teetrusted---tee-objecthandle.md)u[](capi-teetrusted---tee-objecthandle.md)c[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md) | Describes value parameters.<br>**Since**: 20 |
| unsigned int a | First value. |
| unsigned int b;
 } value | Second value. |
| [](capi-teetrusted---tee-objecthandle.md)s[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md)r[](capi-teetrusted---tee-objecthandle.md)u[](capi-teetrusted---tee-objecthandle.md)c[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md) | Describes shared memory reference.<br>**Since**: 20 |
| void *buffer | Pointer to the shared memory buffer. |
| size_t size;
 } sharedmem | Size of the shared memory buffer. |


