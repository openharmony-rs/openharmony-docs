# ddk_types.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=6be4fce6dcc641d6f56c59a16ae6449540255825 translatedAt=2026-10-14T04:35:27.870Z pushedAt=2026-10-19T07:16:26.367Z -->

## Overview

Provides BASE DDK types and declares enums and data structures required by the BASE DDK APIs.

**Header file:** <ddk/ddk_types.h>

**Library**: libddk_base.z.so

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

**Related module**: [Ddk](capi-baseddk.md)

## Summary

### Structs

| Name                                      | typedef Keyword| Description|
|------------------------------------------| -- | -- |
| [DDK_Ashmem](capi-baseddk-ddk-ashmem.md) | DDK_Ashmem | Defines the shared memory created by calling [OH_DDK_CreateAshmem](capi-ddk-api-h.md#oh_ddk_createashmem). The buffer of the shared memory provides better performance and is applicable to scenarios that require high-performance data sharing, such as efficient sharing of a large amount of data between multiple modules and fast data exchange between drivers and apps. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [DDK_RetCode](#ddk_retcode) | DDK_RetCode | Enumerates error codes used in the BASE DDK. After calling a DDK API, you can check the return value to determine whether the operation is successful, and handle the error based on the specific error code (for example, invalid parameter or null pointer error). |

## Enum Description

### DDK_RetCode

```c
enum DDK_RetCode
```

**Description**

Enumerates error codes used in the BASE DDK. After calling a DDK API, you can check the return value to determine whether the operation is successful, and handle the error based on the specific error code (for example, invalid parameter or null pointer error).

**Since**: 12

| Enum| Description|
| -- | -- |
| DDK_SUCCESS = 0 | The API call is successful, and the operation is performed as expected. |
| DDK_FAILURE = 28600001 | A common error occurs during the API call, and the operation cannot be completed. The operation fails due to unspecified reasons (such as common errors like insufficient resources or internal errors). |
| DDK_INVALID_PARAMETER = 28600002 | The input parameter does not meet the API requirements. For example, the parameter value is empty, out of range, or does not match the expected type. |
| DDK_INVALID_OPERATION = 28600003 | An unsupported or prohibited operation is performed, for example, an operation is performed when the device is in an incorrect state. |
| DDK_NULL_PTR = 28600004 | A mandatory pointer parameter is null, and the operation cannot be performed. |


