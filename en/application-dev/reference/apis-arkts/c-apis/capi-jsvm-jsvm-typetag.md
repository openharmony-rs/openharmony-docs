# JSVM_TypeTag

```c
typedef struct JSVM_TypeTag {...} JSVM_TypeTag
```

## Overview

A 128-bit value stored as two unsigned 64-bit integers. It serves as a UUID with which JavaScript objects or externals can be "tagged" in order to ensure that they are of a certain type.

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t lower | lower type. |
| uint64_t upper | upper type. |


