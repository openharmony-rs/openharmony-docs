# TEE_ObjectInfo

```c
typedef struct TEE_ObjectInfo {...} TEE_ObjectInfo
```

## Overview

Defines an object information.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t objectType | Type of the object. |
| uint32_t objectSize | Size of the object. |
| uint32_t maxObjectSize | Maximum allowed size for the object. |
| uint32_t objectUsage | Usage flags of the object. |
| uint32_t dataSize | Size of the data associated with the object. |
| uint32_t dataPosition | Position of the data within the object. |
| uint32_t handleFlags | Flags associated with the handle. |


