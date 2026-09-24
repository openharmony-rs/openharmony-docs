# ddk_types.h

## Overview

Provides BASE DDK types and declares the macros, enums, and data structures required by the BASE DDK APIs.

**Library**: libddk_base.z.so

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

**Related module**: [Ddk](capi-ddk.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [DDK_Ashmem](capi-ddk-ddk-ashmem.md) | DDK_Ashmem | Device memory map created by calling {@link OH_DDK_CreateAshmem}. A buffer using the device memory map can provide better performance. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [DDK_RetCode](#ddk_retcode) | DDK_RetCode | Enumerates error codes used in the BASE DDK. |

## Enum type description

### DDK_RetCode

```c
enum DDK_RetCode
```

**Description**

Enumerates error codes used in the BASE DDK.

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

| Enum item | Description |
| -- | -- |
| DDK_SUCCESS = 0 | Operation success. |
| DDK_FAILURE = 28600001 | Operation failed. |
| DDK_INVALID_PARAMETER = 28600002 | Invalid parameter. |
| DDK_INVALID_OPERATION = 28600003 | Invalid operation. |
| DDK_NULL_PTR = 28600004 | Null pointer. |


