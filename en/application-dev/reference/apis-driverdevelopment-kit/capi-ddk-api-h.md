# ddk_api.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2b35905173f6b6551a4b1b6d4c371ae340832d27 translatedAt=2026-10-14T04:36:27.271Z pushedAt=2026-10-19T07:07:15.970Z -->

## Overview

Declares the BASE DDK APIs used by the host and provides APIs for creating, mapping, unmapping, and destroying the shared memory. This module helps you efficiently manage shared memory resources in drivers. It is applicable to scenarios where data needs to be shared with the driver, helping simplify memory management and improve data transmission efficiency.

**File to include**: <ddk/ddk_api.h>

**Library**: libddk_base.z.so

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

**Related module**: [Ddk](capi-baseddk.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [DDK_RetCode OH_DDK_CreateAshmem(const uint8_t *name, uint32_t size, DDK_Ashmem **ashmem)](#oh_ddk_createashmem) | Creates shared memory. To prevent resource leaks, call [OH_DDK_DestroyAshmem](#oh_ddk_destroyashmem) to destroy the shared memory when it is no longer needed. |
| [DDK_RetCode OH_DDK_MapAshmem(DDK_Ashmem *ashmem, const uint8_t ashmemMapType)](#oh_ddk_mapashmem) | Maps the created shared memory to the user space. Call [OH_DDK_CreateAshmem](#oh_ddk_createashmem) to create shared memory first. Call [OH_DDK_UnmapAshmem](#oh_ddk_unmapashmem) to unmap the shared memory that is no longer needed. |
| [DDK_RetCode OH_DDK_UnmapAshmem(DDK_Ashmem *ashmem)](#oh_ddk_unmapashmem) | Unmaps the shared memory. Call [OH_DDK_MapAshmem](#oh_ddk_mapashmem) to map the shared memory first. Unmap the shared memory when it is no longer accessed to save address space. |
| [DDK_RetCode OH_DDK_DestroyAshmem(DDK_Ashmem *ashmem)](#oh_ddk_destroyashmem) | Destroys the shared memory created by [OH_DDK_CreateAshmem](#oh_ddk_createashmem). You are advised to call [OH_DDK_UnmapAshmem](#oh_ddk_unmapashmem) to unmap the shared memory first. Destroy the shared memory in a timely manner when it is no longer used to release system resources. |

## Function Description

### OH_DDK_CreateAshmem()

```c
DDK_RetCode OH_DDK_CreateAshmem(const uint8_t *name, uint32_t size, DDK_Ashmem **ashmem)
```

**Description**

Creates shared memory. To prevent resource leaks, call [OH_DDK_DestroyAshmem](#oh_ddk_destroyashmem) to destroy the shared memory when it is no longer needed.

**Since**: 12


**Parameters**

| Name                                              | Description|
|---------------------------------------------------| -- |
| const uint8_t *name                               | Pointer to the name string of the shared memory. The name is used to identify the shared memory. The value of **name** cannot be null. You are advised to use a unique name to avoid conflicts. |
| uint32_t size                                     | Size of the buffer corresponding to the shared memory, in bytes. The value must be greater than 0. If the value is too large, the memory usage will be too high, affecting the running performance. |
| [DDK_Ashmem](capi-baseddk-ddk-ashmem.md) **ashmem | Pointer to the shared memory object created. |

**Returns**

| Type| Description|
| -- | -- |
| [DDK_RetCode](capi-ddk-types-h.md#ddk_retcode) | [DDK_SUCCESS](capi-ddk-types-h.md#ddk_retcode): The API call is successful. The shared memory has been successfully created and initialized.<br>         [DDK_INVALID_PARAMETER](capi-ddk-types-h.md#ddk_retcode): The input **name** is a null pointer, the value of **size** is **0**, or the input **ashmem** is a null pointer. Check the input parameter values.<br>         [DDK_FAILURE](capi-ddk-types-h.md#ddk_retcode): The shared memory or the **DDK_Ashmem** struct fails to be created. Check the size of the allocated memory and related permissions. |

### OH_DDK_MapAshmem()

```c
DDK_RetCode OH_DDK_MapAshmem(DDK_Ashmem *ashmem, const uint8_t ashmemMapType)
```

**Description**

Maps the created shared memory to the user space. Call [OH_DDK_CreateAshmem](#oh_ddk_createashmem) to create shared memory first. Call [OH_DDK_UnmapAshmem](#oh_ddk_unmapashmem) to unmap the shared memory that is no longer needed.

**Since**: 12


**Parameters**

| Name                                             | Description|
|--------------------------------------------------| -- |
| [DDK_Ashmem](capi-baseddk-ddk-ashmem.md) *ashmem | Pointer to the descriptor of the shared memory to be mapped. |
| const uint8_t ashmemMapType                      | Protection permission value of the shared memory. For details, see the general definition of the Ashmem protection permission. |

**Returns**

| Type| Description|
| -- | -- |
| [DDK_RetCode](capi-ddk-types-h.md#ddk_retcode) | [DDK_SUCCESS](capi-ddk-types-h.md#ddk_retcode): The API call is successful. The shared memory has been mapped to the user space.<br>         [DDK_NULL_PTR](capi-ddk-types-h.md#ddk_retcode): The input **ashmem** is a null pointer. Check the input parameter values.<br>         [DDK_FAILURE](capi-ddk-types-h.md#ddk_retcode): The file descriptor of the shared memory is invalid or the shared memory has not been created. Check whether the shared memory has been created and ensure that the file descriptor is not closed.<br>         [DDK_INVALID_OPERATION](capi-ddk-types-h.md#ddk_retcode): The shared memory fails to be mapped. The possible causes include abnormal mapping status or insufficient permissions. Check the mapping status and permissions of the shared memory and try again. |

### OH_DDK_UnmapAshmem()

```c
DDK_RetCode OH_DDK_UnmapAshmem(DDK_Ashmem *ashmem)
```

**Description**

Unmaps the shared memory. Call [OH_DDK_MapAshmem](#oh_ddk_mapashmem) to map the shared memory first. Unmap the shared memory when it is no longer accessed to save address space.

**Since**: 12


**Parameters**

| Name                                             | Description|
|--------------------------------------------------| -- |
| [DDK_Ashmem](capi-baseddk-ddk-ashmem.md) *ashmem | Pointer to the descriptor of the shared memory to be unmapped. |

**Returns**

| Type| Description|
| -- | -- |
| [DDK_RetCode](capi-ddk-types-h.md#ddk_retcode) | [DDK_SUCCESS](capi-ddk-types-h.md#ddk_retcode): The API call is successful. The shared memory has been successfully unmapped from the user space.<br>         [DDK_NULL_PTR](capi-ddk-types-h.md#ddk_retcode): The input **ashmem** is a null pointer. Check the input parameter values.<br>         [DDK_FAILURE](capi-ddk-types-h.md#ddk_retcode): The file descriptor of the shared memory is invalid or the mapping has not been performed. |

### OH_DDK_DestroyAshmem()

```c
DDK_RetCode OH_DDK_DestroyAshmem(DDK_Ashmem *ashmem)
```

**Description**

Destroys the shared memory created by [OH_DDK_CreateAshmem](#oh_ddk_createashmem). You are advised to call [OH_DDK_UnmapAshmem](#oh_ddk_unmapashmem) to unmap the shared memory first. Destroy the shared memory in a timely manner when it is no longer used to release system resources.

**Since**: 12


**Parameters**

| Name                                             | Description|
|--------------------------------------------------| -- |
| [DDK_Ashmem](capi-baseddk-ddk-ashmem.md) *ashmem | Pointer to the descriptor of the shared memory to be destroyed. |

**Returns**

| Type| Description|
| -- | -- |
| [DDK_RetCode](capi-ddk-types-h.md#ddk_retcode) | [DDK_SUCCESS](capi-ddk-types-h.md#ddk_retcode): The API call is successful. The shared memory has been successfully destroyed and released.<br>         [DDK_NULL_PTR](capi-ddk-types-h.md#ddk_retcode): The input ashmem is a null pointer. Check the input parameter values.<br>         [DDK_FAILURE](capi-ddk-types-h.md#ddk_retcode): The file descriptor of the shared memory is invalid. The possible cause is that the shared memory has been released or destroyed multiple times. Check the status of the shared memory. |


