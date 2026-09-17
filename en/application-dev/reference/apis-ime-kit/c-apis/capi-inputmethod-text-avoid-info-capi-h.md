# inputmethod_text_avoid_info_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing the text box avoidance information objects.

**Include**: <inputmethod/inputmethod_text_avoid_info_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) | InputMethod_TextAvoidInfo | Represents the information used by the input box to avoid the keyboard. |

### Function

| Name | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)](#oh_textavoidinfo_create) | Create a new [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance. |
| [void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)](#oh_textavoidinfo_destroy) | Destroy a [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance. |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)](#oh_textavoidinfo_setpositiony) | Set positionY value into [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)](#oh_textavoidinfo_setheight) | Set height value into [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)](#oh_textavoidinfo_getpositiony) | Get positionY value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)](#oh_textavoidinfo_getheight) | Get height value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). |

## Function description

### OH_TextAvoidInfo_Create()

```c
InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)
```

**Description**

Create a new [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| double positionY | Y coordinate of the text box, in px. |
| double height | Height of the text box, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo *](capi-inputmethod-inputmethod-textavoidinfo.md) | If the creation succeeds, a pointer to the newly created [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)  instance is returned. If the creation fails, NULL is returned, possible cause is insufficient memory. |

### OH_TextAvoidInfo_Destroy()

```c
void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)
```

**Description**

Destroy a [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Represents a pointer to an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance which will be destroyed. |

### OH_TextAvoidInfo_SetPositionY()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)
```

**Description**

Set positionY value into [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Represents a pointer to an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance which will be set value. |
| double positionY | Y coordinate, that is, the absolute value of the distance between the text box's top vertex and the top edge of the physical screen, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_TextAvoidInfo_SetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)
```

**Description**

Set height value into [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Represents a pointer to an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance which will be set value. |
| double height | Height, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_TextAvoidInfo_GetPositionY()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)
```

**Description**

Get positionY value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Represents a pointer to an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance which will be get value from. |
| double *positionY | Y coordinate, that is, the absolute value of the distance between the text box's top vertex and the top edge of the physical screen, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_TextAvoidInfo_GetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)
```

**Description**

Get height value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Represents a pointer to an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance which will be get value from. |
| double *height | Height of the text box, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |


