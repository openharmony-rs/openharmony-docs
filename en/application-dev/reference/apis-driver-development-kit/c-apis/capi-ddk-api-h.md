# ddk_api.h

## Overview

Declares the BASE DDK APIs used by the USB host to access USB devices.

**Library**: libddk_base.z.so

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

**Related module**: [Ddk](capi-ddk.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [DDK_RetCode OH_DDK_CreateAshmem(const uint8_t *name, uint32_t size, DDK_Ashmem **ashmem)](#oh_ddk_createashmem) | Creates an **Ashmem** object. To prevent resource leakage, call [OH_DDK_DestroyAshmem](capi-ddk-api-h.md#oh_ddk_destroyashmem) to destroy the **Ashmem** object when it is no longer needed. |
| [DDK_RetCode OH_DDK_MapAshmem(DDK_Ashmem *ashmem, const uint8_t ashmemMapType)](#oh_ddk_mapashmem) | Maps the created **Ashmem** object to the user space. Call [OH_DDK_UnmapAshmem](capi-ddk-api-h.md#oh_ddk_unmapashmem) to unmap the **Ashmem**<br>object when it is no longer needed. |
| [DDK_RetCode OH_DDK_UnmapAshmem(DDK_Ashmem *ashmem)](#oh_ddk_unmapashmem) | Unmaps an **Ashmem** object. |
| [DDK_RetCode OH_DDK_DestroyAshmem(DDK_Ashmem *ashmem)](#oh_ddk_destroyashmem) | Destroys an **Ashmem** object. |

## Function description

### OH_DDK_CreateAshmem()

```c
DDK_RetCode OH_DDK_CreateAshmem(const uint8_t *name, uint32_t size, DDK_Ashmem **ashmem)
```

**Description**

Creates an **Ashmem** object. To prevent resource leakage, call [OH_DDK_DestroyAshmem](capi-ddk-api-h.md#oh_ddk_destroyashmem) to destroy the **Ashmem** object when it is no longer needed.

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const uint8_t *name | Pointer to the name of the **Ashmem** object. |
| uint32_t size | Buffer size of the **Ashmem** object. |
| DDK_Ashmem **ashmem | Pointer to the **Ashmem** object. |

**Returns**:

| Type | Description |
| -- | -- |
| DDK_RetCode | [DDK_SUCCESS](capi-ddk-types-h.md#ddk_retcode): The API call is successful.      [DDK_INVALID_PARAMETER](capi-ddk-types-h.md#ddk_retcode): The input name is a null pointer, the value of size is 0, or the input      ashmem is a null pointer.      [DDK_FAILURE](capi-ddk-types-h.md#ddk_retcode): The attempt to create an Ashmem object or the DDK_Ashmem structure fails. |

### OH_DDK_MapAshmem()

```c
DDK_RetCode OH_DDK_MapAshmem(DDK_Ashmem *ashmem, const uint8_t ashmemMapType)
```

**Description**

Maps the created **Ashmem** object to the user space. Call [OH_DDK_UnmapAshmem](capi-ddk-api-h.md#oh_ddk_unmapashmem) to unmap the **Ashmem**<br>object when it is no longer needed.

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| DDK_Ashmem *ashmem | Pointer to the **Ashmem** object. |
| const uint8_t ashmemMapType | Mapping type for the **Ashmem** object. |

**Returns**:

| Type | Description |
| -- | -- |
| DDK_RetCode | [DDK_SUCCESS](capi-ddk-types-h.md#ddk_retcode): The API call is successful.      [DDK_NULL_PTR](capi-ddk-types-h.md#ddk_retcode): The input ashmem is a null pointer.      [DDK_FAILURE](capi-ddk-types-h.md#ddk_retcode): The file descriptor of the Ashmem object is invalid.      [DDK_INVALID_OPERATION](capi-ddk-types-h.md#ddk_retcode): The attempt to call MapAshmem fails. |

### OH_DDK_UnmapAshmem()

```c
DDK_RetCode OH_DDK_UnmapAshmem(DDK_Ashmem *ashmem)
```

**Description**

Unmaps an **Ashmem** object.

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| DDK_Ashmem *ashmem | Pointer to the **Ashmem** object. |

**Returns**:

| Type | Description |
| -- | -- |
| DDK_RetCode | [DDK_SUCCESS](capi-ddk-types-h.md#ddk_retcode): The API call is successful.      [DDK_NULL_PTR](capi-ddk-types-h.md#ddk_retcode): The input ashmem is a null pointer.      [DDK_FAILURE](capi-ddk-types-h.md#ddk_retcode): The file descriptor of the Ashmem object is invalid. |

### OH_DDK_DestroyAshmem()

```c
DDK_RetCode OH_DDK_DestroyAshmem(DDK_Ashmem *ashmem)
```

**Description**

Destroys an **Ashmem** object.

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| DDK_Ashmem *ashmem | Pointer to the **Ashmem** object. |

**Returns**:

| Type | Description |
| -- | -- |
| DDK_RetCode | [DDK_SUCCESS](capi-ddk-types-h.md#ddk_retcode): The API call is successful.      [DDK_NULL_PTR](capi-ddk-types-h.md#ddk_retcode): The input ashmem is a null pointer.      [DDK_FAILURE](capi-ddk-types-h.md#ddk_retcode): The file descriptor of the Ashmem object is invalid. |


