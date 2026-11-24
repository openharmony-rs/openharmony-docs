# inputmethod_text_avoid_info_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing the text box avoidance information objects.

**File to Include**: <inputmethod/inputmethod_text_avoid_info_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) | InputMethod_TextAvoidInfo | Text box avoidance information structure, which describes the position and height of the text box on the physical screen. The input method framework calculates the avoidance area based on positionY and height in TextAvoidInfo. When the soft keyboard pops up, the edit box can automatically move up or adjust the layout. This ensures that the input area is not blocked by the keyboard and the input content can be viewed and operated by users. <br> <br>Use: Serves as a parameter carrier for the edit box to avoid the keyboard area and transmits the vertical position and height information of the edit box to the input method framework. Input method framework based on positionY (Y coordinate at the top of the edit box. The value must be greater than or equal to 0.) and height (height of the edit box. The value must be a valid height value greater than 0.) Determine the complete vertical range (positionY to positionY+height) of the edit box on the screen, compare it with the screen area occupied by the keyboard, and calculate whether to avoid and the offset. <br> <br>Application scenario: After the edit box is bound to the input method service (through OH_InputMethodController_Attach), the edit box client transfers TextAvoidInfo to the input method framework through InputMethod_TextConfig. When the keyboard pops up, the input method framework reads the avoidance information, determines whether the edit box is in the keyboard block area, and triggers the corresponding avoidance adjustment. This structure can also be read by the input method application to understand the screen position of the edit box to optimize the keyboard layout. <br> <br> Related functions: <br> \| Function \| Description \| \| --- \| --- \| \| [OH_TextAvoidInfo_Create](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_create) \| Creating an InputMethod_TextAvoidInfo Instance \| \| [OH_TextAvoidInfo_Destroy](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_destroy) \| Destroying an InputMethod_TextAvoidInfo Instance \| \| [OH_TextAvoidInfo_SetPositionY](capi-inputmethod-text-avoid-info-capi-h. md#oh_textavoidinfo_setpositiony) \| Setting the Y Coordinate Value \| \| [OH_TextAvoidInfo_SetHeight](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_setheight) \| Setting the Height Value \| \| [OH_TextAvoidInfo_GetPositionY](capi-inputmethod-text-avoid-info-capi-h. md#oh_textavoidinfo_getpositiony) \| Obtaining the Y Coordinate Value \| \| [OH_TextAvoidInfo_GetHeight](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_getheight) \| Obtaining the Height Value \| \| [OH_TextConfig_GetTextAvoidInfo](capi-inputmethod-text-config-capi-h. md#oh_textconfig_gettextavoidinfo) \| Obtains TextAvoidInfo from TextConfig \| <br> <br> Related structures: <br> \| Structure \| Description \| \| --- \| --- \| \| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) \| Text box configuration structure. TextAvoidInfo is contained as its sub-attribute. \| <br> <br> Handle and ownership: Only valid handles created by this API or borrowed handles provided by the framework can be used. Only independently created objects can be destroyed. The object provided by the callback and the child object view of TextConfig are borrowed objects. The provider returns IME_ERR_PARAMCHECK for an unregistered or invalid handle. The null parameter still returns an error according to the original rule. <br>Protection boundary: Life cycle check does not guarantee the thread safety of object members, nor does it identify all invalid addresses after address reuse. After the object is destroyed, the pointer should be null. The callback object must not be retained after the callback ends. |

### Functions

| Name | Description |
| -- | -- |
| [InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)](#oh_textavoidinfo_create) | Creates an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance. |
| [void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)](#oh_textavoidinfo_destroy) | Destroy a [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance to release the memory resources occupied by the instance. <br> <br> Usage scenario: When the TextAvoidInfo instance is no longer used, this function is called to destroy the instance. It must be called after the Create function returns successfully and the instance is no longer referenced by any other object. <br> <br>Lifecycle management: OH_TextAvoidInfo_Create and OH_TextAvoidInfo_Destroy must be used together. Each instance created by Create must have a corresponding Destroy call. Otherwise, memory leakage occurs. After Destroy is called, the original pointer becomes invalid and cannot be used any more. <br> <br>Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create. <br>Only independently created objects are owned by the caller. The TextConfig interface returns a borrowed view and cannot be transferred to this interface. A request to destroy a borrowed view is rejected and the TextConfig to which it belongs is not released. The original pointer cannot be used after it is destroyed. <br> <br> Effect: The memory pointed to by info is released, and the info pointer becomes invalid. Any subsequent access to a destroyed pointer is an undefined behavior. |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)](#oh_textavoidinfo_setpositiony) | Sets the Y coordinate in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The Y coordinate indicates the absolute distance between the vertex of the text box and the upper side of the physical screen. <br> <br>Application scenario: When the position of the edit box changes(for example, the window moves or the layout is adjusted), the Y coordinate in the avoidance information needs to be updated so that the input method framework can recalculate the avoidance area based on the latest position. <br> <br> Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create successfully, or a valid borrowed view returned by TextConfig. |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)](#oh_textavoidinfo_setheight) | Sets the height value in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The height value represents the vertical pixel size of the edit box on the screen. <br> <br>Application scenario: When the height of the edit box changes(for example, the layout is adjusted or the window is zoomed), the height value in the avoidance information needs to be updated so that the input method framework can recalculate the avoidance area based on the latest height. The calculation of the avoidance area depends on the combination of positionY and height to ensure that the edit box is not blocked when the keyboard is displayed. <br> <br> Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create successfully, or a valid borrowed view returned by TextConfig. |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)](#oh_textavoidinfo_getpositiony) | Obtain the Y coordinate value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The Y coordinate is the absolute value of the distance between the vertex of the text box and the upper side of the physical screen. <br> <br>Application scenario: When processing the avoidance logic, the input method application needs to obtain the Y coordinate value of the edit box to determine the vertical position of the edit box on the screen and determine whether to adjust the position or layout of the edit box. <br> <br> Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create successfully, or a valid borrowed view returned by TextConfig. The output parameter positionY must be a non-null pointer of the double type, and the memory is allocated by the caller. |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)](#oh_textavoidinfo_getheight) | Obtains the height value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The height value represents the vertical pixel size of the edit box on the screen. <br> <br>Application scenario: When processing the avoidance logic, the input method application needs to obtain the height of the edit box and determine the complete vertical range(from positionY to positionY+height) of the edit box on the screen based on the Y coordinate value. In this way, you can determine whether the edit box is blocked by the keyboard. <br> <br> Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create successfully, or a valid borrowed view returned by TextConfig. The output parameter height must be a non-null pointer of the double type, and the memory is allocated by the caller. |

## Function description

### OH_TextAvoidInfo_Create()

```c
InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)
```

**Description**

Creates an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance.

<!--Device-InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)--><!--Device-InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)-End-->

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

Destroy a [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance to release the memory resources occupied by the instance. <br> <br> Usage scenario: When the TextAvoidInfo instance is no longer used, this function is called to destroy the instance. It must be called after the Create function returns successfully and the instance is no longer referenced by any other object. <br> <br>Lifecycle management: OH_TextAvoidInfo_Create and OH_TextAvoidInfo_Destroy must be used together. Each instance created by Create must have a corresponding Destroy call. Otherwise, memory leakage occurs. After Destroy is called, the original pointer becomes invalid and cannot be used any more. <br> <br>Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create. <br>Only independently created objects are owned by the caller. The TextConfig interface returns a borrowed view and cannot be transferred to this interface. A request to destroy a borrowed view is rejected and the TextConfig to which it belongs is not released. The original pointer cannot be used after it is destroyed. <br> <br> Effect: The memory pointed to by info is released, and the info pointer becomes invalid. Any subsequent access to a destroyed pointer is an undefined behavior.

<!--Device-void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)--><!--Device-void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)-End-->

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

Sets the Y coordinate in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The Y coordinate indicates the absolute distance between the vertex of the text box and the upper side of the physical screen. <br> <br>Application scenario: When the position of the edit box changes(for example, the window moves or the layout is adjusted), the Y coordinate in the avoidance information needs to be updated so that the input method framework can recalculate the avoidance area based on the latest position. <br> <br> Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create successfully, or a valid borrowed view returned by TextConfig.

<!--Device-InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)--><!--Device-InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)-End-->

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
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The info parameter is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextAvoidInfo_SetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)
```

**Description**

Sets the height value in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The height value represents the vertical pixel size of the edit box on the screen. <br> <br>Application scenario: When the height of the edit box changes(for example, the layout is adjusted or the window is zoomed), the height value in the avoidance information needs to be updated so that the input method framework can recalculate the avoidance area based on the latest height. The calculation of the avoidance area depends on the combination of positionY and height to ensure that the edit box is not blocked when the keyboard is displayed. <br> <br> Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create successfully, or a valid borrowed view returned by TextConfig.

<!--Device-InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)--><!--Device-InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)-End-->

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
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The info parameter is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextAvoidInfo_GetPositionY()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)
```

**Description**

Obtain the Y coordinate value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The Y coordinate is the absolute value of the distance between the vertex of the text box and the upper side of the physical screen. <br> <br>Application scenario: When processing the avoidance logic, the input method application needs to obtain the Y coordinate value of the edit box to determine the vertical position of the edit box on the screen and determine whether to adjust the position or layout of the edit box. <br> <br> Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create successfully, or a valid borrowed view returned by TextConfig. The output parameter positionY must be a non-null pointer of the double type, and the memory is allocated by the caller.

<!--Device-InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)--><!--Device-InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)-End-->

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
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): indicates that the operation is successful and the Y coordinate value has been written to the memory to which the positionY pointer points. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The info or positionY parameter is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextAvoidInfo_GetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)
```

**Description**

Obtains the height value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The height value represents the vertical pixel size of the edit box on the screen. <br> <br>Application scenario: When processing the avoidance logic, the input method application needs to obtain the height of the edit box and determine the complete vertical range(from positionY to positionY+height) of the edit box on the screen based on the Y coordinate value. In this way, you can determine whether the edit box is blocked by the keyboard. <br> <br> Prerequisites: The info parameter must be a non-null pointer returned by OH_TextAvoidInfo_Create successfully, or a valid borrowed view returned by TextConfig. The output parameter height must be a non-null pointer of the double type, and the memory is allocated by the caller.

<!--Device-InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)--><!--Device-InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)-End-->

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
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): indicates that the operation is successful and the height value has been written to the memory to which the height pointer points. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The info or height parameter is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |


