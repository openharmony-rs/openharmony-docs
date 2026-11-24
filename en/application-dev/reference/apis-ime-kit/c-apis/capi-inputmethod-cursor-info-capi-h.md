# inputmethod_cursor_info_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing cursor information objects.

**File to Include**: <inputmethod/inputmethod_cursor_info_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) | InputMethod_CursorInfo | InputMethod_CursorInfo is the opaque type of cursor information. It is used to describe the position and size of the cursor on the physical screen during text input. include that horizontal coordinate(left), vertical coordinate(top), width(width), and height(height) of the cursor. The unit is px. <br> <br> Purpose: Provide the accurate position and size of the cursor for the input method service. The input method implements the following functions based on the information: <br>- Cursor Follow: The keyboard panel adjusts the display position based on the cursor position to ensure that the keyboard does not block the area where the cursor is located. <br>- Candidate word positioning: The candidate word area of the input method is displayed near the cursor, providing accurate input experience. <br>-Avoidance calculation: The input method calculates the area to be avoided based on the cursor height and position. <br> <br>Application scenario: <br>1. The cursor information is carried in TextConfig: When the application returns TextConfig in [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h. md#oh_texteditorproxy_gettextconfigfunc) callback, CursorInfo notifies the input method of the current cursor position and size. <br>2. Actively notify cursor update: when the cursor position changes(e.g. cursor shift caused by user moving or text insertion) The application notifies the input method of the latest cursor position through the [OH_InputMethodProxy_NotifyCursorUpdate](capi-inputmethod-inputmethod-proxy-capi-h. md#oh_inputmethodproxy_notifycursorupdate). <br> <br>Relationship with other structures:<br>-Relationship with InputMethod_TextConfig: CursorInfo is a sub-attribute of TextConfig. When the application returns TextConfig in the [OH_TextEditorProxy_GetTextConfigFunc]( capi-inputmethod-text-editor-proxy-capi-h. md#oh_texteditorproxy_gettextconfigfunc) callback, TextConfig contains CursorInfo. The input method obtains cursor information through [OH_TextConfig_GetCursorInfo](capi-inputmethod-text-config-capi-h. md#oh_textconfig_getcursorinfo). Therefore, the application needs to create CursorInfo, set the correct cursor coordinates, and then put CursorInfo into TextConfig in the GetTextConfig callback. <br>-Relationship with OH_InputMethodProxy_NotifyCursorUpdate: CursorInfo is directly transferred as a parameter of the NotifyCursorUpdate function and is used to notify the input method when the cursor position changes. After an app creates or updates CursorInfo, the app sends the latest cursor information to the input method through NotifyCursorUpdate. <br>- Relationship with InputMethod_InputMethodProxy: The NotifyCursorUpdate function requires the InputMethod_InputMethodProxy parameter(returned by Attach) and the InputMethod_CursorInfo parameter. The inputMethodProxy parameter identifies the interaction channel and the cursorInfo parameter carries the cursor information. <br> <br>Handles and ownership: Only valid handles created by this API or borrowed handles provided by the framework can be used. Only independently created objects can be destroyed. The object provided by the callback and the child object view of TextConfig are borrowed objects. The provider returns IME_ERR_PARAMCHECK for an unregistered or invalid handle. The null parameter still returns an error according to the original rule. <br>Protection boundary: Lifecycle check does not ensure thread safety of object members, nor does it identify all invalid addresses after address reuse. After the object is destroyed, the pointer should be null. The callback object must not be retained after the callback ends. |

### Functions

| Name | Description |
| -- | -- |
| [InputMethod_CursorInfo *OH_CursorInfo_Create(double left, double top, double width, double height)](#oh_cursorinfo_create) | Creates an [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance. |
| [void OH_CursorInfo_Destroy(InputMethod_CursorInfo *cursorInfo)](#oh_cursorinfo_destroy) | Destroys a [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance to release the memory resources allocated by the Create function. <br> <br> Paired invoking: This interface must be invoked together with OH_CursorInfo_Create. Destroy must be called only once per Create instance. <br> <br>Lifecycle management: <br>- After Destroy, the cursorInfo pointer is no longer valid and cannot be used. <br>- Do not call Destroy twice for the same cursorInfo pointer. Otherwise, double-free will occur. <br>- If cursorInfo is being used by the input method callback(for example, during the GetTextConfig callback), Destroy cannot be invoked during this period. Destroy should be destroyed after the callback is returned. <br>-Only independently created objects are owned by the caller. The TextConfig interface returns a borrowed view and cannot be transferred to this interface. A request to destroy a borrowed view is rejected and the TextConfig to which it belongs is not released. The original pointer cannot be used after it is destroyed. |
| [InputMethod_ErrorCode OH_CursorInfo_SetRect(InputMethod_CursorInfo *cursorInfo, double left, double top, double width, double height)](#oh_cursorinfo_setrect) | Sets the cursor information and updates the position and size of the cursor. This method is used to modify the cursor information on an existing CursorInfo instance without creating a new instance. <br> <br> Prerequisites: cursorInfo must be a valid instance created through OH_CursorInfo_Create, or a valid borrowed view returned by TextConfig. |
| [InputMethod_ErrorCode OH_CursorInfo_GetRect(InputMethod_CursorInfo *cursorInfo, double *left, double *top, double *width, double *height)](#oh_cursorinfo_getrect) | Obtains the cursor information content, and reads the position and size of the cursor. <br> <br> Prerequisites: cursorInfo must be a valid instance created through OH_CursorInfo_Create, or a valid borrowed view returned by TextConfig. left, top, width, and height must point to valid double variables. |

## Function description

### OH_CursorInfo_Create()

```c
InputMethod_CursorInfo *OH_CursorInfo_Create(double left, double top, double width, double height)
```

**Description**

Creates an [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance.

<!--Device-InputMethod_CursorInfo *OH_CursorInfo_Create(double left, double top, double width, double height)--><!--Device-InputMethod_CursorInfo *OH_CursorInfo_Create(double left, double top, double width, double height)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| double left | Absolute value of the distance between the cursor's leftmost point and the left edge of the physical screen, in px. |
| double top | Absolute value of the distance between the cursor's top point and the top edge of the physical screen, in px. |
| double width | Width, in px. |
| double height | Height, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_CursorInfo *](capi-inputmethod-inputmethod-cursorinfo.md) | If the operation is successful, a pointer to the created [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance is returned. <br>If the operation fails, **NULL** is returned. This may occur when the application's address space is exhausted. |

### OH_CursorInfo_Destroy()

```c
void OH_CursorInfo_Destroy(InputMethod_CursorInfo *cursorInfo)
```

**Description**

Destroys a [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance to release the memory resources allocated by the Create function. <br> <br> Paired invoking: This interface must be invoked together with OH_CursorInfo_Create. Destroy must be called only once per Create instance. <br> <br>Lifecycle management: <br>- After Destroy, the cursorInfo pointer is no longer valid and cannot be used. <br>- Do not call Destroy twice for the same cursorInfo pointer. Otherwise, double-free will occur. <br>- If cursorInfo is being used by the input method callback(for example, during the GetTextConfig callback), Destroy cannot be invoked during this period. Destroy should be destroyed after the callback is returned. <br>-Only independently created objects are owned by the caller. The TextConfig interface returns a borrowed view and cannot be transferred to this interface. A request to destroy a borrowed view is rejected and the TextConfig to which it belongs is not released. The original pointer cannot be used after it is destroyed.

<!--Device-void OH_CursorInfo_Destroy(InputMethod_CursorInfo *cursorInfo)--><!--Device-void OH_CursorInfo_Destroy(InputMethod_CursorInfo *cursorInfo)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) *cursorInfo | Pointer to the [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance to be destroyed. |

### OH_CursorInfo_SetRect()

```c
InputMethod_ErrorCode OH_CursorInfo_SetRect(InputMethod_CursorInfo *cursorInfo, double left, double top, double width, double height)
```

**Description**

Sets the cursor information and updates the position and size of the cursor. This method is used to modify the cursor information on an existing CursorInfo instance without creating a new instance. <br> <br> Prerequisites: cursorInfo must be a valid instance created through OH_CursorInfo_Create, or a valid borrowed view returned by TextConfig.

<!--Device-InputMethod_ErrorCode OH_CursorInfo_SetRect(InputMethod_CursorInfo *cursorInfo, double left, double top, double width, double height)--><!--Device-InputMethod_ErrorCode OH_CursorInfo_SetRect(InputMethod_CursorInfo *cursorInfo, double left, double top, double width, double height)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) *cursorInfo | Input pointer to the InputMethod_CursorInfo instance. <br>**Meaning/Function: * * Specifies the CursorInfo instance to be modified. <br>**NULL pointer processing: * * cannot be NULL. If NULL is input, IME_ERR_NULL_POINTER is returned. <br>**Prerequisites: * * Must be a valid instance created for OH_CursorInfo_Create, or a still valid borrowed view returned by TextConfig. |
| double left | Absolute value of the distance between the cursor's leftmost point and the left edge of the physical screen, in px. |
| double top | Absolute value of the distance between the cursor's top point and the top edge of the physical screen, in px. |
| double width | Width, in px. |
| double height | Height, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. Cursor information has been updated. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. This parameter is returned when cursorInfo is NULL. Before invoking this interface, ensure that cursorInfo is a valid pointer. </li> <li>** Error handling suggestion: * * If IME_ERR_NULL_POINTER is returned, check whether cursorInfo is a valid pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_CursorInfo_GetRect()

```c
InputMethod_ErrorCode OH_CursorInfo_GetRect(InputMethod_CursorInfo *cursorInfo, double *left, double *top, double *width, double *height)
```

**Description**

Obtains the cursor information content, and reads the position and size of the cursor. <br> <br> Prerequisites: cursorInfo must be a valid instance created through OH_CursorInfo_Create, or a valid borrowed view returned by TextConfig. left, top, width, and height must point to valid double variables.

<!--Device-InputMethod_ErrorCode OH_CursorInfo_GetRect(InputMethod_CursorInfo *cursorInfo, double *left, double *top, double *width, double *height)--><!--Device-InputMethod_ErrorCode OH_CursorInfo_GetRect(InputMethod_CursorInfo *cursorInfo, double *left, double *top, double *width, double *height)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) *cursorInfo | Input pointer to the InputMethod_CursorInfo instance. <br>**Meaning/Function: * * Specifies the CursorInfo instance to be read. <br>**NULL pointer processing: * * cannot be NULL. If NULL is input, IME_ERR_NULL_POINTER is returned. <br>**Prerequisites: * * Must be a valid instance created for OH_CursorInfo_Create, or a still valid borrowed view returned by TextConfig. |
| double *left | Absolute value of the distance between the cursor's leftmost point and the left edge of the physical screen, in px. |
| double *top | Absolute value of the distance between the cursor's top point and the top edge of the physical screen, in px. |
| double *width | Width, in px. |
| double *height | Height, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. The values of left, top, width, and height have been assigned to the correct cursor information. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. This parameter is returned when cursorInfo, left, top, width, or height is NULL. Before invoking this interface, ensure that all All parameters are valid pointers. </li> <li>** Error handling suggestion: * * If IME_ERR_NULL_POINTER is returned, check whether all parameters are valid pointers. If IME_ERR_OK is returned, the four output parameters are correct. Cursor information value. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |


