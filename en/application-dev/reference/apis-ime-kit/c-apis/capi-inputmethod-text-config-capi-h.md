# inputmethod_text_config_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing the text box configuration information objects.

**File to Include**: <inputmethod/inputmethod_text_config_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) | InputMethod_TextConfig | Structure for configuring the text input behavior of the text input box. The input box transfers core input rules to the input method framework. The input method framework executes the corresponding input behavior based on the configuration. You can configure input attributes (such as the input type and text format) to meet input requirements in different scenarios and improve user input experience. This mode is applicable to text input scenarios that require refined control of input behavior. This structure is of the opaque type. The caller cannot directly access its internal members and can perform operations only through the function interface provided by this module. <br> <br>Function of the structure: <br>InputMethod_TextConfig carries the configuration information of the edit box. including input type, enter key type, pre-screen support, selection range, cursor information, avoidance information, window ID, placeholder text, abilityName, etc. The configuration information is used in the [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h. md#oh_texteditorproxy_gettextconfigfunc) callback. Developers need to set configuration items in the config parameter in the callback. The input method framework adjusts the keyboard layout and input behavior accordingly. <br><br>InputMethod_TextConfig contains the following substructure information: <br>- [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md): cursor information, including the cursor position and height. This command can be obtained through [OH_TextConfig_GetCursorInfo](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getcursorinfo). It returns a writable borrowable view with embedded cursor information by outputting double pointers. No new object is allocated and no ownership is transferred. <br>- [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md): avoidance information, including the location and size of the avoidance area. It can be obtained through [OH_TextConfig_GetTextAvoidInfo](capi-inputmethod-text-config-capi-h.md#oh_textconfig_gettextavoidinfo). The output double pointer returns a writable borrowable view with embedded avoidance information. No new object is allocated and no ownership is transferred. <br> <br> Related functions: <br> <br> - Create/Destroy function: <br>
\| Function \| Description \| \| -- \| -- \| \| [OH_TextConfig_Create](capi-inputmethod-text-config-capi-h.md#oh_textconfig_create) \| Creates a new InputMethod_TextConfig instance. \| \| [OH_TextConfig_Destroy](capi-inputmethod-text-config-capi-h.md#oh_textconfig_destroy) \| Destroys an instance of InputMethod_TextConfig. \| <br> <br>-Setting function (Set*): <br> \| Function \| Describes the text box type in the
\| \| -- \| -- \| \| [OH_TextConfig_SetInputType](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setinputtype) \| setting text configuration information. \| \| [OH_TextConfig_SetEnterKeyType](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setenterkeytype) \| Sets the function type of the Enter key in the text configuration information. \| \| [OH_TextConfig_SetPreviewTextSupport](capi-inputmethod-text-config-capi-h. md#oh_textconfig_setpreviewtextsupport) \| Sets whether the pre-up screen is supported. \| \| [OH_TextConfig_SetSelection](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setselection) \| Sets the selected text range. Indicates the ID of the window to which the \| \| [OH_TextConfig_SetWindowId](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setwindowid) \| parameter is set.
\| \| [OH_TextConfig_SetPlaceholder](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setplaceholder) \| Sets placeholder text information. The \| \| [OH_TextConfig_SetAbilityName](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setabilityname) \| sets the ability name information. The \| \| [OH_TextConfig_SetConsumeKeyEvents](capi-inputmethod-text-config-capi-h. md#oh_textconfig_setconsumekeyevents) \| sets whether the editing box has the capability of completely processing keys such as letters, characters, and functions in the text configuration information. <br/>**Start version: ** 26.0.0 \| <br> <br>-Get function (Get*): <br> \| Function \| Description \| \| -- \| -- \| \| [OH_TextConfig_GetInputType](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getinputtype) \| Obtains the text box type. \| \| [OH_TextConfig_GetEnterKeyType](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getenterkeytype) \| Obtains the function type of the Enter key. \| \| [OH_TextConfig_IsPreviewTextSupported](capi-inputmethod-text-config-capi-h. md#oh_textconfig_ispreviewtextsupported) \| Obtains whether pre-screen display is supported. \| \| [OH_TextConfig_GetCursorInfo](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getcursorinfo) \| Obtaining Cursor Information (Returns a writable borrowed view of the embedded object by outputting a double pointer, without allocating a new object). \| \| [OH_TextConfig_GetTextAvoidInfo](capi-inputmethod-text-config-capi-h.md#oh_textconfig_gettextavoidinfo) \| Obtaining Avoidance Information (Returns a writable borrowed view of the embedded object by outputting a double pointer, without allocating a new object). The \| \| [OH_TextConfig_GetSelection](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getselection) \| obtains the selection area information. \| \| [OH_TextConfig_GetWindowId](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getwindowid) \| Obtains the ID of the owning window. \| \| [OH_TextConfig_GetPlaceholder](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getplaceholder) \| Gets the placeholder text information. The \| \| [OH_TextConfig_GetAbilityName](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getabilityname) \| obtains the information about the ability name. The \| \| [OH_TextConfig_GetConsumeKeyEvents](capi-inputmethod-text-config-capi-h. md#oh_textconfig_getconsumekeyevents) \| obtains whether the edit box in the text configuration has the capability of completely processing letters, characters, and function keys. <br/>**Start version: ** 26.0.0 \| <br> <br>Handles and ownership: Only valid handles created by this API or borrowed handles provided by the framework can be used. Only independently created objects can be destroyed. The object provided by the callback and the child object view of TextConfig are borrowed objects. The provider returns IME_ERR_PARAMCHECK for an unregistered or invalid handle. The null parameter still returns an error according to the original rule. <br>Protection boundary: Lifecycle check does not guarantee thread safety of object members, nor does it identify all invalid addresses after address reuse. After the object is destroyed, the pointer should be null. The callback object must not be retained after the callback ends. |

### Functions

| Name | Description |
| -- | -- |
| [InputMethod_TextConfig *OH_TextConfig_Create(void)](#oh_textconfig_create) | Creates an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance. |
| [void OH_TextConfig_Destroy(InputMethod_TextConfig *config)](#oh_textconfig_destroy) | Destroy a [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance. The config pointer cannot be used after being destroyed. You are advised to set the pointer to NULL to avoid misuse. <br> <br> Usage scenario: This function is invoked to release resources when the TextConfig object is no longer needed. <br> <br> Effect: The config object is released and its internal resources are reclaimed. After that, no function can be invoked through the config pointer. <br> <br>Lifecycle Management: used with [OH_TextConfig_Create](#oh_textconfig_create). An instance can be destroyed only once. If the value of config is NULL, the function does not perform any processing. <br>Only independently created objects can be destroyed. Framework callbacks provide borrowed objects that cannot be destroyed even during callback execution. Destroy requests for borrowed or unregistered objects are rejected and logged. |
| [InputMethod_ErrorCode OH_TextConfig_SetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType inputType)](#oh_textconfig_setinputtype) | Sets the text box type. |
| [InputMethod_ErrorCode OH_TextConfig_SetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType enterKeyType)](#oh_textconfig_setenterkeytype) | Sets the Enter key type. |
| [InputMethod_ErrorCode OH_TextConfig_SetPreviewTextSupport(InputMethod_TextConfig *config, bool supported)](#oh_textconfig_setpreviewtextsupport) | Sets the text preview feature. |
| [InputMethod_ErrorCode OH_TextConfig_SetSelection(InputMethod_TextConfig *config, int32_t start, int32_t end)](#oh_textconfig_setselection) | Sets the selected text area. |
| [InputMethod_ErrorCode OH_TextConfig_SetWindowId(InputMethod_TextConfig *config, int32_t windowId)](#oh_textconfig_setwindowid) | Sets the window ID. |
| [InputMethod_ErrorCode OH_TextConfig_SetPlaceholder(InputMethod_TextConfig *config, const char16_t *placeholder, size_t length)](#oh_textconfig_setplaceholder) | Sets the placeholder text. |
| [InputMethod_ErrorCode OH_TextConfig_SetAbilityName(InputMethod_TextConfig *config, const char16_t *abilityName, size_t length)](#oh_textconfig_setabilityname) | Sets the ability name. |
| [InputMethod_ErrorCode OH_TextConfig_SetConsumeKeyEvents(InputMethod_TextConfig *config, bool consumeKeyEvents)](#oh_textconfig_setconsumekeyevents) | Set whether the editor supports consuming key events into TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_GetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType *inputType)](#oh_textconfig_getinputtype) | Obtains the text box type. |
| [InputMethod_ErrorCode OH_TextConfig_GetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType *enterKeyType)](#oh_textconfig_getenterkeytype) | Obtains the Enter key type. |
| [InputMethod_ErrorCode OH_TextConfig_IsPreviewTextSupported(InputMethod_TextConfig *config, bool *supported)](#oh_textconfig_ispreviewtextsupported) | Obtains whether the text preview feature is supported. |
| [InputMethod_ErrorCode OH_TextConfig_GetCursorInfo(InputMethod_TextConfig *config, InputMethod_CursorInfo **cursorInfo)](#oh_textconfig_getcursorinfo) | Obtains the writable borrowing view of the cursor information in the text configuration information. No new object is allocated and no ownership is transferred. <br> <br>Application scenario: This function is called when you need to read the set cursor information. <br> <br> Effect: cursorInfo points to the cursor information embedded in config. Modifying information in this view will update config synchronously. <br>Lifecycle: The view is valid only during the config validity period. If the config is provided by a callback, the view is only valid for the duration of the callback. |
| [InputMethod_ErrorCode OH_TextConfig_GetTextAvoidInfo(InputMethod_TextConfig *config, InputMethod_TextAvoidInfo **avoidInfo)](#oh_textconfig_gettextavoidinfo) | Obtains the writable borrowing view of the avoidance information in the text configuration information. No new object is allocated and no ownership is transferred. <br> <br> Usage scenario: This function is called when you need to read the configured avoidance information. <br> <br> Effect: avoidInfo points to the avoidance information embedded in config. Modifying information in this view will update config synchronously. <br> <br>Memory management: avoidInfo returns the writable borrowing view of [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) embedded in config. No new object is allocated and ownership is transferred. You cannot call [OH_TextAvoidInfo_Destroy](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_destroy) or free to release the view. <br> <br>Lifecycle: The view is valid only during the config validity period. If config is provided by a callback, the view is valid only for the duration of the callback. Do not call OH_TextAvoidInfo_Destroy or free to release the view. |
| [InputMethod_ErrorCode OH_TextConfig_GetSelection(InputMethod_TextConfig *config, int32_t *start, int32_t *end)](#oh_textconfig_getselection) | Obtains the selected text area. |
| [InputMethod_ErrorCode OH_TextConfig_GetWindowId(InputMethod_TextConfig *config, int32_t *windowId)](#oh_textconfig_getwindowid) | Obtains the window ID. |
| [InputMethod_ErrorCode OH_TextConfig_GetPlaceholder(InputMethod_TextConfig *config, char16_t *placeholder, size_t *length)](#oh_textconfig_getplaceholder) | Obtains the placeholder text. |
| [InputMethod_ErrorCode OH_TextConfig_GetAbilityName(InputMethod_TextConfig *config, char16_t *abilityName, size_t *length)](#oh_textconfig_getabilityname) | Obtains the ability name. |
| [InputMethod_ErrorCode OH_TextConfig_GetConsumeKeyEvents(InputMethod_TextConfig *config, bool *consumeKeyEvents)](#oh_textconfig_getconsumekeyevents) | Get whether the editor supports consuming key events from TextConfig. |

## Function description

### OH_TextConfig_Create()

```c
InputMethod_TextConfig *OH_TextConfig_Create(void)
```

**Description**

Creates an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance.

<!--Device-InputMethod_TextConfig *OH_TextConfig_Create(void)--><!--Device-InputMethod_TextConfig *OH_TextConfig_Create(void)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_TextConfig *](capi-inputmethod-inputmethod-textconfig.md) | If the operation is successful, a pointer to the created [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance is returned. <br>If the operation failed, **NULL** is returned, which may be caused by insufficient application address space. |

### OH_TextConfig_Destroy()

```c
void OH_TextConfig_Destroy(InputMethod_TextConfig *config)
```

**Description**

Destroy a [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance. The config pointer cannot be used after being destroyed. You are advised to set the pointer to NULL to avoid misuse. <br> <br> Usage scenario: This function is invoked to release resources when the TextConfig object is no longer needed. <br> <br> Effect: The config object is released and its internal resources are reclaimed. After that, no function can be invoked through the config pointer. <br> <br>Lifecycle Management: used with [OH_TextConfig_Create](#oh_textconfig_create). An instance can be destroyed only once. If the value of config is NULL, the function does not perform any processing. <br>Only independently created objects can be destroyed. Framework callbacks provide borrowed objects that cannot be destroyed even during callback execution. Destroy requests for borrowed or unregistered objects are rejected and logged.

<!--Device-void OH_TextConfig_Destroy(InputMethod_TextConfig *config)--><!--Device-void OH_TextConfig_Destroy(InputMethod_TextConfig *config)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance to be destroyed. If NULL is input, the function does not perform any processing and does not break down. The pointer becomes invalid after being destroyed. You are advised to set it to NULL. Note: The memory of the config parameter provided by the GetTextConfigFunc callback framework is managed by the framework. After the callback is returned, the memory is automatically released and cannot be destroyed by calling Destroy inside or outside the callback framework. |

### OH_TextConfig_SetInputType()

```c
InputMethod_ErrorCode OH_TextConfig_SetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType inputType)
```

**Description**

Sets the text box type.

<!--Device-InputMethod_ErrorCode OH_TextConfig_SetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType inputType)--><!--Device-InputMethod_ErrorCode OH_TextConfig_SetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType inputType)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be set. |
| [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) inputType | Input type of the text box. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>IME_ERR_OK = 0: success. </li> <li>IME_ERR_PARAMCHECK = 401: The object handle is not registered or has expired. </li> <li>IME_ERR_NULL_POINTER = 12802000: Unexpected null pointer. The value of config is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_SetEnterKeyType()

```c
InputMethod_ErrorCode OH_TextConfig_SetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType enterKeyType)
```

**Description**

Sets the Enter key type.

<!--Device-InputMethod_ErrorCode OH_TextConfig_SetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType enterKeyType)--><!--Device-InputMethod_ErrorCode OH_TextConfig_SetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType enterKeyType)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be set. |
| [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) enterKeyType | Enter key type. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_SetPreviewTextSupport()

```c
InputMethod_ErrorCode OH_TextConfig_SetPreviewTextSupport(InputMethod_TextConfig *config, bool supported)
```

**Description**

Sets the text preview feature.

<!--Device-InputMethod_ErrorCode OH_TextConfig_SetPreviewTextSupport(InputMethod_TextConfig *config, bool supported)--><!--Device-InputMethod_ErrorCode OH_TextConfig_SetPreviewTextSupport(InputMethod_TextConfig *config, bool supported)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be set. |
| bool supported | Whether text preview is supported. **true**: Text preview is supported. **false**: Text preview is not supported. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_SetSelection()

```c
InputMethod_ErrorCode OH_TextConfig_SetSelection(InputMethod_TextConfig *config, int32_t start, int32_t end)
```

**Description**

Sets the selected text area.

<!--Device-InputMethod_ErrorCode OH_TextConfig_SetSelection(InputMethod_TextConfig *config, int32_t start, int32_t end)--><!--Device-InputMethod_ErrorCode OH_TextConfig_SetSelection(InputMethod_TextConfig *config, int32_t start, int32_t end)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be set. |
| int32_t start | Start position of the selected text. |
| int32_t end | End position of the selected text. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_SetWindowId()

```c
InputMethod_ErrorCode OH_TextConfig_SetWindowId(InputMethod_TextConfig *config, int32_t windowId)
```

**Description**

Sets the window ID.

<!--Device-InputMethod_ErrorCode OH_TextConfig_SetWindowId(InputMethod_TextConfig *config, int32_t windowId)--><!--Device-InputMethod_ErrorCode OH_TextConfig_SetWindowId(InputMethod_TextConfig *config, int32_t windowId)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be set. |
| int32_t windowId | Window ID of the application bound to the input method. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_SetPlaceholder()

```c
InputMethod_ErrorCode OH_TextConfig_SetPlaceholder(InputMethod_TextConfig *config, const char16_t *placeholder, size_t length)
```

**Description**

Sets the placeholder text.

<!--Device-InputMethod_ErrorCode OH_TextConfig_SetPlaceholder(InputMethod_TextConfig *config, const char16_t *placeholder, size_t length)--><!--Device-InputMethod_ErrorCode OH_TextConfig_SetPlaceholder(InputMethod_TextConfig *config, const char16_t *placeholder, size_t length)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be set. |
| const char16_t *placeholder | Pointer to a UTF-16 encoded double-byte string. If a null pointer is passed, the placeholder text is an empty string. |
| size_t length | Number of elements in the memory to which **placeholder** points, including the null character of the double-byte string.1. If **length** is **0**, the placeholder text is an empty string.2. The maximum length of UTF-16 encoding is 255 characters (the null character of the string is not included in the count). If the length exceeds 255 characters, the extra characters will be truncated. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): <ul> <li>IME_ERR_OK = 0: success. </li> <li>IME_ERR_PARAMCHECK = 401: The object handle is not registered or has expired. </li> <li>IME_ERR_NULL_POINTER = 12802000: Unexpected null pointer. The value of config is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_SetAbilityName()

```c
InputMethod_ErrorCode OH_TextConfig_SetAbilityName(InputMethod_TextConfig *config, const char16_t *abilityName, size_t length)
```

**Description**

Sets the ability name.

<!--Device-InputMethod_ErrorCode OH_TextConfig_SetAbilityName(InputMethod_TextConfig *config, const char16_t *abilityName, size_t length)--><!--Device-InputMethod_ErrorCode OH_TextConfig_SetAbilityName(InputMethod_TextConfig *config, const char16_t *abilityName, size_t length)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be set. |
| const char16_t *abilityName | Pointer to a UTF-16 encoded double-byte string. If a null pointer is passed, the ability name is an empty string. |
| size_t length | Number of elements in the memory to which **abilityName** points, including the null character of the double-byte string.1. If **length** is **0**, the ability name is set to an empty string.2. The maximum length of UTF-16 encoding is 127 characters (the null character of the string is not included in the count). If the length exceeds 127 characters, the extra characters will be truncated. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): <ul> <li>IME_ERR_OK = 0: success. </li> <li>IME_ERR_PARAMCHECK = 401: The object handle is not registered or has expired. </li> <li>IME_ERR_NULL_POINTER = 12802000: Unexpected null pointer. The value of config is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_SetConsumeKeyEvents()

```c
InputMethod_ErrorCode OH_TextConfig_SetConsumeKeyEvents(InputMethod_TextConfig *config, bool consumeKeyEvents)
```

**Description**

Set whether the editor supports consuming key events into TextConfig.

<!--Device-InputMethod_ErrorCode OH_TextConfig_SetConsumeKeyEvents(InputMethod_TextConfig *config, bool consumeKeyEvents)--><!--Device-InputMethod_ErrorCode OH_TextConfig_SetConsumeKeyEvents(InputMethod_TextConfig *config, bool consumeKeyEvents)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be set. |
| bool consumeKeyEvents | Indicates whether the editor supports consuming key events. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_GetInputType()

```c
InputMethod_ErrorCode OH_TextConfig_GetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType *inputType)
```

**Description**

Obtains the text box type.

<!--Device-InputMethod_ErrorCode OH_TextConfig_GetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType *inputType)--><!--Device-InputMethod_ErrorCode OH_TextConfig_GetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType *inputType)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be obtained. |
| [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) *inputType | Pointer to the [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) instance. Input type of the text box. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config or inputType is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_GetEnterKeyType()

```c
InputMethod_ErrorCode OH_TextConfig_GetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType *enterKeyType)
```

**Description**

Obtains the Enter key type.

<!--Device-InputMethod_ErrorCode OH_TextConfig_GetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType *enterKeyType)--><!--Device-InputMethod_ErrorCode OH_TextConfig_GetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType *enterKeyType)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be obtained. |
| [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) *enterKeyType | Pointer to the [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) instance. Enter key type of the text box. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config or enterKeyType is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_IsPreviewTextSupported()

```c
InputMethod_ErrorCode OH_TextConfig_IsPreviewTextSupported(InputMethod_TextConfig *config, bool *supported)
```

**Description**

Obtains whether the text preview feature is supported.

<!--Device-InputMethod_ErrorCode OH_TextConfig_IsPreviewTextSupported(InputMethod_TextConfig *config, bool *supported)--><!--Device-InputMethod_ErrorCode OH_TextConfig_IsPreviewTextSupported(InputMethod_TextConfig *config, bool *supported)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be obtained. |
| bool *supported | Whether text preview is supported. **true**: Text preview is supported. **false**: Text preview is not supported. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config or supported is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_GetCursorInfo()

```c
InputMethod_ErrorCode OH_TextConfig_GetCursorInfo(InputMethod_TextConfig *config, InputMethod_CursorInfo **cursorInfo)
```

**Description**

Obtains the writable borrowing view of the cursor information in the text configuration information. No new object is allocated and no ownership is transferred. <br> <br>Application scenario: This function is called when you need to read the set cursor information. <br> <br> Effect: cursorInfo points to the cursor information embedded in config. Modifying information in this view will update config synchronously. <br>Lifecycle: The view is valid only during the config validity period. If the config is provided by a callback, the view is only valid for the duration of the callback.

<!--Device-InputMethod_ErrorCode OH_TextConfig_GetCursorInfo(InputMethod_TextConfig *config, InputMethod_CursorInfo **cursorInfo)--><!--Device-InputMethod_ErrorCode OH_TextConfig_GetCursorInfo(InputMethod_TextConfig *config, InputMethod_CursorInfo **cursorInfo)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | [in] Input pointer to the TextConfig instance whose value is to be obtained. Cannot be NULL. |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) **cursorInfo | [out] Output dual pointer, which cannot be NULL. Returns a writeable borrowed view of [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) embedded in config. You cannot call [OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy) or free to release the view or continue to access the view after the config expires. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config or cursorInfo is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_GetTextAvoidInfo()

```c
InputMethod_ErrorCode OH_TextConfig_GetTextAvoidInfo(InputMethod_TextConfig *config, InputMethod_TextAvoidInfo **avoidInfo)
```

**Description**

Obtains the writable borrowing view of the avoidance information in the text configuration information. No new object is allocated and no ownership is transferred. <br> <br> Usage scenario: This function is called when you need to read the configured avoidance information. <br> <br> Effect: avoidInfo points to the avoidance information embedded in config. Modifying information in this view will update config synchronously. <br> <br>Memory management: avoidInfo returns the writable borrowing view of [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) embedded in config. No new object is allocated and ownership is transferred. You cannot call [OH_TextAvoidInfo_Destroy](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_destroy) or free to release the view. <br> <br>Lifecycle: The view is valid only during the config validity period. If config is provided by a callback, the view is valid only for the duration of the callback. Do not call OH_TextAvoidInfo_Destroy or free to release the view.

<!--Device-InputMethod_ErrorCode OH_TextConfig_GetTextAvoidInfo(InputMethod_TextConfig *config, InputMethod_TextAvoidInfo **avoidInfo)--><!--Device-InputMethod_ErrorCode OH_TextConfig_GetTextAvoidInfo(InputMethod_TextConfig *config, InputMethod_TextAvoidInfo **avoidInfo)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | [in] Input pointer, indicating text configuration information. Cannot be NULL. |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) **avoidInfo | [out] Output dual pointer, which cannot be NULL. Returns a writeable borrowed view of [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) embedded in config. You cannot call [OH_TextAvoidInfo_Destroy](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_destroy) or free to release the view or continue to access the view after the config expires. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config or avoidInfo is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_GetSelection()

```c
InputMethod_ErrorCode OH_TextConfig_GetSelection(InputMethod_TextConfig *config, int32_t *start, int32_t *end)
```

**Description**

Obtains the selected text area.

<!--Device-InputMethod_ErrorCode OH_TextConfig_GetSelection(InputMethod_TextConfig *config, int32_t *start, int32_t *end)--><!--Device-InputMethod_ErrorCode OH_TextConfig_GetSelection(InputMethod_TextConfig *config, int32_t *start, int32_t *end)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be obtained. |
| int32_t *start | Start position of the selected text. |
| int32_t *end | End position of the selected text. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config, start, or end is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_GetWindowId()

```c
InputMethod_ErrorCode OH_TextConfig_GetWindowId(InputMethod_TextConfig *config, int32_t *windowId)
```

**Description**

Obtains the window ID.

<!--Device-InputMethod_ErrorCode OH_TextConfig_GetWindowId(InputMethod_TextConfig *config, int32_t *windowId)--><!--Device-InputMethod_ErrorCode OH_TextConfig_GetWindowId(InputMethod_TextConfig *config, int32_t *windowId)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be obtained. |
| int32_t *windowId | Window ID of the application bound to the input method. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config or windowId is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_GetPlaceholder()

```c
InputMethod_ErrorCode OH_TextConfig_GetPlaceholder(InputMethod_TextConfig *config, char16_t *placeholder, size_t *length)
```

**Description**

Obtains the placeholder text.

<!--Device-InputMethod_ErrorCode OH_TextConfig_GetPlaceholder(InputMethod_TextConfig *config, char16_t *placeholder, size_t *length)--><!--Device-InputMethod_ErrorCode OH_TextConfig_GetPlaceholder(InputMethod_TextConfig *config, char16_t *placeholder, size_t *length)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be obtained. |
| char16_t *placeholder | Pointer to the placeholder text. The memory of this pointer is maintained by the caller. |
| size_t *length | Pointer to the length of the placeholder text, in double bytes. The length includes the null character of the string.1. As an input parameter, **length** indicates the available length of the memory to which **<br>placeholder** points. As an output parameter, it indicates the actual length of the placeholder text.2. If **<br>placeholder** is a null pointer and **length** points to valid memory, **length** will be set to the actual length of the placeholder text, and an error will be thrown.3. If both **placeholder** and **length** point to valid memory, but the value of **length** is less than the actual length of the placeholder text, **length**<br>will be set to the actual length of the placeholder text, and an error will be thrown. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): <ul> <li>IME_ERR_OK = 0: success. </li> <li>IME_ERR_PARAMCHECK = 401: Parameter check failed. The possible cause is that placeholder is null or length is insufficient. In this case, length is set to the actual length. The object handle may also be unregistered or invalid. </li> <li>IME_ERR_NULL_POINTER = 12802000: Unexpected null pointer. The value of config or length is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_GetAbilityName()

```c
InputMethod_ErrorCode OH_TextConfig_GetAbilityName(InputMethod_TextConfig *config, char16_t *abilityName, size_t *length)
```

**Description**

Obtains the ability name.

<!--Device-InputMethod_ErrorCode OH_TextConfig_GetAbilityName(InputMethod_TextConfig *config, char16_t *abilityName, size_t *length)--><!--Device-InputMethod_ErrorCode OH_TextConfig_GetAbilityName(InputMethod_TextConfig *config, char16_t *abilityName, size_t *length)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be obtained. |
| char16_t *abilityName | Pointer to the ability name. The memory of this pointer is maintained by the caller. |
| size_t *length | Pointer to the length of the ability name, in double bytes. The length includes the null character of the string.1. As an input parameter, **length** indicates the available length of the memory to which **<br>abilityName** points. As an output parameter, it indicates the actual length of the ability name.2. If **<br>abilityName** is a null pointer and **length** points to valid memory, **length** will be set to the actual length of the ability name, and an error will be thrown.3. If both **abilityName** and **length** point to valid memory, but the value of **length** is less than the actual length of the ability name, **length** will be set to the actual length of the ability name, and an error will be thrown. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): <ul> <li>IME_ERR_OK = 0: success. </li> <li>IME_ERR_PARAMCHECK = 401: The parameter check fails, or the object handle is not registered or invalid. </li> <li>IME_ERR_NULL_POINTER = 12802000: Unexpected null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_TextConfig_GetConsumeKeyEvents()

```c
InputMethod_ErrorCode OH_TextConfig_GetConsumeKeyEvents(InputMethod_TextConfig *config, bool *consumeKeyEvents)
```

**Description**

Get whether the editor supports consuming key events from TextConfig.

<!--Device-InputMethod_ErrorCode OH_TextConfig_GetConsumeKeyEvents(InputMethod_TextConfig *config, bool *consumeKeyEvents)--><!--Device-InputMethod_ErrorCode OH_TextConfig_GetConsumeKeyEvents(InputMethod_TextConfig *config, bool *consumeKeyEvents)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be get from. |
| bool *consumeKeyEvents | Indicates whether the editor supports consuming key events. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of config or consumeKeyEvents is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |


