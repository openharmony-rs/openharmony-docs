# TEE_Param

```c
typedef union TEE_Param {...} TEE_Param
```

## Overview

Enumerates the TEE parameter.

<!--Device-typedef union TEE_Param {...} TEE_Param--><!--Device-typedef union TEE_Param {...} TEE_Param-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| memref.buffer | Pointer to the memory buffer.<br><!--Device-memref.buffer--><!--Device-memref.buffer-End--> |
| memref.size | Size of the memory buffer.<br><!--Device-memref.size--><!--Device-memref.size-End--> |
| value.a | First value.<br><!--Device-value.a--><!--Device-value.a-End--> |
| value.b | Second value.<br><!--Device-value.b--><!--Device-value.b-End--> |
| sharedmem.buffer | Pointer to the shared memory buffer.<br><!--Device-sharedmem.buffer--><!--Device-sharedmem.buffer-End--> |
| sharedmem.size | Size of the shared memory buffer.<br><!--Device-sharedmem.size--><!--Device-sharedmem.size-End--> |


