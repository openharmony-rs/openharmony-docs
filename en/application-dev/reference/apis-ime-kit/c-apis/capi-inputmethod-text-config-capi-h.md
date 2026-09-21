# inputmethod_text_config_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing the text box configuration information objects.

**Include**: <inputmethod/inputmethod_text_config_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) | InputMethod_TextConfig | Define the InputMethod_TextConfig structure type.<br> The configuration of the text editor. |

### Function

| Name | Description |
| -- | -- |
| [InputMethod_TextConfig *OH_TextConfig_Create(void)](#oh_textconfig_create) | Create a new [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance. |
| [void OH_TextConfig_Destroy(InputMethod_TextConfig *config)](#oh_textconfig_destroy) | Destroy a [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance. |
| [InputMethod_ErrorCode OH_TextConfig_SetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType inputType)](#oh_textconfig_setinputtype) | Set input type into TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_SetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType enterKeyType)](#oh_textconfig_setenterkeytype) | Set enter key type into TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_SetPreviewTextSupport(InputMethod_TextConfig *config, bool supported)](#oh_textconfig_setpreviewtextsupport) | Set preview text support into TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_SetSelection(InputMethod_TextConfig *config, int32_t start, int32_t end)](#oh_textconfig_setselection) | Set selection into TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_SetWindowId(InputMethod_TextConfig *config, int32_t windowId)](#oh_textconfig_setwindowid) | Set window id into TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_SetPlaceholder(InputMethod_TextConfig *config, const char16_t *placeholder, size_t length)](#oh_textconfig_setplaceholder) | Sets the placeholder text of an InputMethod_TextConfig instance. |
| [InputMethod_ErrorCode OH_TextConfig_SetAbilityName(InputMethod_TextConfig *config, const char16_t *abilityName, size_t length)](#oh_textconfig_setabilityname) | Sets the ability name of an InputMethod_TextConfig instance. |
| [InputMethod_ErrorCode OH_TextConfig_SetConsumeKeyEvents(InputMethod_TextConfig *config, bool consumeKeyEvents)](#oh_textconfig_setconsumekeyevents) | Set whether the editor supports consuming key events into TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_GetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType *inputType)](#oh_textconfig_getinputtype) | Get input type from TextConfig |
| [InputMethod_ErrorCode OH_TextConfig_GetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType *enterKeyType)](#oh_textconfig_getenterkeytype) | Get enter key type from TextConfig |
| [InputMethod_ErrorCode OH_TextConfig_IsPreviewTextSupported(InputMethod_TextConfig *config, bool *supported)](#oh_textconfig_ispreviewtextsupported) | Get is preview text supported from TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_GetCursorInfo(InputMethod_TextConfig *config, InputMethod_CursorInfo **cursorInfo)](#oh_textconfig_getcursorinfo) | Get cursor info from TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_GetTextAvoidInfo(InputMethod_TextConfig *config, InputMethod_TextAvoidInfo **avoidInfo)](#oh_textconfig_gettextavoidinfo) | Get text avoid information from text configuration. |
| [InputMethod_ErrorCode OH_TextConfig_GetSelection(InputMethod_TextConfig *config, int32_t *start, int32_t *end)](#oh_textconfig_getselection) | Get selection from TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_GetWindowId(InputMethod_TextConfig *config, int32_t *windowId)](#oh_textconfig_getwindowid) | Get window id from TextConfig. |
| [InputMethod_ErrorCode OH_TextConfig_GetPlaceholder(InputMethod_TextConfig *config, char16_t *placeholder, size_t *length)](#oh_textconfig_getplaceholder) | Obtains the placeholder text of an InputMethod_TextConfig instance. |
| [InputMethod_ErrorCode OH_TextConfig_GetAbilityName(InputMethod_TextConfig *config, char16_t *abilityName, size_t *length)](#oh_textconfig_getabilityname) | Obtains the ability name of an InputMethod_TextConfig instance. |
| [InputMethod_ErrorCode OH_TextConfig_GetConsumeKeyEvents(InputMethod_TextConfig *config, bool *consumeKeyEvents)](#oh_textconfig_getconsumekeyevents) | Get whether the editor supports consuming key events from TextConfig. |

## Function description

### OH_TextConfig_Create()

```c
InputMethod_TextConfig *OH_TextConfig_Create(void)
```

**Description**

Create a new [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_TextConfig *](capi-inputmethod-inputmethod-textconfig.md) | If the creation succeeds, a pointer to the newly created [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md)  instance is returned. If the creation fails, NULL is returned, possible cause is insufficient memory. |

### OH_TextConfig_Destroy()

```c
void OH_TextConfig_Destroy(InputMethod_TextConfig *config)
```

**Description**

Destroy a [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be destroyed. |

### OH_TextConfig_SetInputType()

```c
InputMethod_ErrorCode OH_TextConfig_SetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType inputType)
```

**Description**

Set input type into TextConfig.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be set. |
| InputMethod_TextInputType inputType | The text input type of text Editor, which is defined in [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype). |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetEnterKeyType()

```c
InputMethod_ErrorCode OH_TextConfig_SetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType enterKeyType)
```

**Description**

Set enter key type into TextConfig.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be set. |
| InputMethod_EnterKeyType enterKeyType | The enter key type of text Editor, which is defined in [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype). |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetPreviewTextSupport()

```c
InputMethod_ErrorCode OH_TextConfig_SetPreviewTextSupport(InputMethod_TextConfig *config, bool supported)
```

**Description**

Set preview text support into TextConfig.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be set. |
| bool supported | Indicates whether the preview text is supported. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetSelection()

```c
InputMethod_ErrorCode OH_TextConfig_SetSelection(InputMethod_TextConfig *config, int32_t start, int32_t end)
```

**Description**

Set selection into TextConfig.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be set. |
| int32_t start | The start position of selection. |
| int32_t end | The end position of selection. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetWindowId()

```c
InputMethod_ErrorCode OH_TextConfig_SetWindowId(InputMethod_TextConfig *config, int32_t windowId)
```

**Description**

Set window id into TextConfig.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be set. |
| int32_t windowId | The window ID of the application currently bound to the input method. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetPlaceholder()

```c
InputMethod_ErrorCode OH_TextConfig_SetPlaceholder(InputMethod_TextConfig *config, const char16_t *placeholder, size_t length)
```

**Description**

Sets the placeholder text of an InputMethod_TextConfig instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the InputMethod_TextConfig instance. |
| const char16_t *placeholder | Pointer to a UTF-16 encoded double-byte string. If a null pointer is passed, the placeholder text is an empty string. |
| size_t length | Number of elements in the memory to which placeholder points, including the null character of the double-byte string. <br>1. If length is 0, the placeholder text is an empty string. <br>2. The maximum length of UTF-16 encoding is 255 characters (the null character of the string is not included in the count). <br>3. If the length exceeds 255 characters, the extra characters will be truncated. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetAbilityName()

```c
InputMethod_ErrorCode OH_TextConfig_SetAbilityName(InputMethod_TextConfig *config, const char16_t *abilityName, size_t length)
```

**Description**

Sets the ability name of an InputMethod_TextConfig instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the InputMethod_TextConfig instance. |
| const char16_t *abilityName | Pointer to a UTF-16 encoded double-byte string. If a null pointer is passed, the ability name is an empty string. |
| size_t length | Number of elements in the memory to which abilityName points, including the null character of the double-byte string. <br>1. If length is 0, the ability name is set to an empty string. <br>2. The maximum length of UTF-16 encoding is 127 characters (the null character of the string is not included in the count). <br>3. If the length exceeds 127 characters, the extra characters will be truncated. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetConsumeKeyEvents()

```c
InputMethod_ErrorCode OH_TextConfig_SetConsumeKeyEvents(InputMethod_TextConfig *config, bool consumeKeyEvents)
```

**Description**

Set whether the editor supports consuming key events into TextConfig.

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
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetInputType()

```c
InputMethod_ErrorCode OH_TextConfig_GetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType *inputType)
```

**Description**

Get input type from TextConfig

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be get from. |
| InputMethod_TextInputType *inputType | Represents a pointer to an [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) instance. The text input type of text Editor |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetEnterKeyType()

```c
InputMethod_ErrorCode OH_TextConfig_GetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType *enterKeyType)
```

**Description**

Get enter key type from TextConfig

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be get from. |
| InputMethod_EnterKeyType *enterKeyType | Represents a pointer to an [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) instance. Indicates the enter key type of text Editor |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_IsPreviewTextSupported()

```c
InputMethod_ErrorCode OH_TextConfig_IsPreviewTextSupported(InputMethod_TextConfig *config, bool *supported)
```

**Description**

Get is preview text supported from TextConfig.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be get from. |
| bool *supported | Indicates whether the preview text is supported. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetCursorInfo()

```c
InputMethod_ErrorCode OH_TextConfig_GetCursorInfo(InputMethod_TextConfig *config, InputMethod_CursorInfo **cursorInfo)
```

**Description**

Get cursor info from TextConfig.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be get from. |
| InputMethod_CursorInfo **cursorInfo | Represents a pointer to an [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetTextAvoidInfo()

```c
InputMethod_ErrorCode OH_TextConfig_GetTextAvoidInfo(InputMethod_TextConfig *config, InputMethod_TextAvoidInfo **avoidInfo)
```

**Description**

Get text avoid information from text configuration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Indicates the text configuration. |
| InputMethod_TextAvoidInfo **avoidInfo | Indicates the text avoid information. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetSelection()

```c
InputMethod_ErrorCode OH_TextConfig_GetSelection(InputMethod_TextConfig *config, int32_t *start, int32_t *end)
```

**Description**

Get selection from TextConfig.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be get from. |
| int32_t *start | Represents selection start position. |
| int32_t *end | Represents selection end position. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetWindowId()

```c
InputMethod_ErrorCode OH_TextConfig_GetWindowId(InputMethod_TextConfig *config, int32_t *windowId)
```

**Description**

Get window id from TextConfig.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance which will be get from. |
| int32_t *windowId | The window ID of the application currently bound to the input method. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetPlaceholder()

```c
InputMethod_ErrorCode OH_TextConfig_GetPlaceholder(InputMethod_TextConfig *config, char16_t *placeholder, size_t *length)
```

**Description**

Obtains the placeholder text of an InputMethod_TextConfig instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the InputMethod_TextConfig instance. |
| char16_t *placeholder | Pointer to the placeholder text. The memory of this pointer is maintained by the caller. |
| size_t *length | Pointer to the length of the placeholder text, in double bytes. The length includes the null character of the string. 1) As an input parameter, <b>length</b> indicates the available length of the memory to which <b>placeholder</b> points. As an output parameter, it indicates the actual length of the placeholder text. 2) If <b>placeholder</b> is a null pointer and <b>length</b> points to valid memory, <b>length</b> will be set to the actual length of the placeholder text, and an error will be return. 3) If both <b>placeholder</b> and <b>length</b> point to valid memory, but the value of <b>length</b> is less than the actual length of the placeholder text, <b>length</b> will be set to the actual length of the placeholder text, and an error will be return. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - parameter check failed.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetAbilityName()

```c
InputMethod_ErrorCode OH_TextConfig_GetAbilityName(InputMethod_TextConfig *config, char16_t *abilityName, size_t *length)
```

**Description**

Obtains the ability name of an InputMethod_TextConfig instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Pointer to the InputMethod_TextConfig instance. |
| char16_t *abilityName | Pointer to the ability name. The memory of this pointer is maintained by the caller. |
| size_t *length | Pointer to the length of the ability name, in double bytes. The length includes the null character of the string. 1) As an input parameter, <b>length</b> indicates the available length of the memory to which <b>abilityName</b> points. As an output parameter, it indicates the actual length of the ability name. 2) If <b>abilityName</b> is a null pointer and <b>length</b> points to valid memory, <b>length</b> will be set to the actual length of the ability name, and an error will be return. 3) If both <b>abilityName</b> and <b>length</b> point to valid memory, but the value of <b>length</b> is less than the actual length of the ability name, <b>length</b> will be set to the actual length of the ability name, and an error will be return. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - parameter check failed.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetConsumeKeyEvents()

```c
InputMethod_ErrorCode OH_TextConfig_GetConsumeKeyEvents(InputMethod_TextConfig *config, bool *consumeKeyEvents)
```

**Description**

Get whether the editor supports consuming key events from TextConfig.

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
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |


