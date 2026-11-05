# inputmethod_text_avoid_info_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing the text box avoidance information objects.

**File to Include**: <inputmethod/inputmethod_text_avoid_info_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) | InputMethod_TextAvoidInfo | Information used by the input box to avoid the keyboard. |

### Function

| Name | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)](#oh_textavoidinfo_create) | Creates an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance. |
| [void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)](#oh_textavoidinfo_destroy) | Destroys an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance. |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)](#oh_textavoidinfo_setpositiony) | Sets the Y coordinate in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)](#oh_textavoidinfo_setheight) | Sets the height in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)](#oh_textavoidinfo_getpositiony) | Obtains the Y coordinate from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)](#oh_textavoidinfo_getheight) | Obtains the height from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). |

## Function description

### OH_TextAvoidInfo_Create()

```c
InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)
```

**Description**

Creates an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| double positionY | Y coordinate of the text box, in px. |
| double height | Height of the text box, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo *](capi-inputmethod-inputmethod-textavoidinfo.md) | If the operation is successful, a pointer to the created [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance is returned. <br>If the operation failed, **NULL** is returned, which may be caused by insufficient application address space. |

### OH_TextAvoidInfo_Destroy()

```c
void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)
```

**Description**

Destroys an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance to be destroyed. |

### OH_TextAvoidInfo_SetPositionY()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)
```

**Description**

Sets the Y coordinate in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance whose value is to be set. |
| double positionY | Y coordinate, that is, the absolute value of the distance between the text box's top vertex and the top edge of the physical screen, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextAvoidInfo_SetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)
```

**Description**

Sets the height in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance whose value is to be set. |
| double height | Height, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextAvoidInfo_GetPositionY()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)
```

**Description**

Obtains the Y coordinate from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance whose value is to be obtained. |
| double *positionY | Y coordinate, that is, the absolute value of the distance between the text box's top vertex and the top edge of the physical screen, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextAvoidInfo_GetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)
```

**Description**

Obtains the height from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance whose value is to be obtained. |
| double *height | Height of the text box, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |


