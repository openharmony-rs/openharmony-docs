# inputmethod_text_config_capi.h

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=8e856b06a34a819612cae112a81452d688b21bcf translatedAt=2026-08-20T07:06:37.724Z pushedAt=2026-08-24T07:32:28.767Z -->

## Overview

Provides methods for creating, destroying, reading, and writing the input box configuration object. **InputMethod_TextConfig** carries edit box configuration information and is used in the **GetTextConfigFunc** callback. You need to set each configuration item on the **config** parameter within the callback.

**File to include**: <inputmethod/inputmethod_text_config_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) | InputMethod_TextConfig | Text box configuration.|

### Function

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig *OH_TextConfig_Create(void)](#oh_textconfig_create) | Creates a new **InputMethod_TextConfig** instance. |
| [void OH_TextConfig_Destroy(InputMethod_TextConfig *config)](#oh_textconfig_destroy) | Destroys an **InputMethod_TextConfig** instance. |
| [InputMethod_ErrorCode OH_TextConfig_SetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType inputType)](#oh_textconfig_setinputtype) | Sets the text box type.|
| [InputMethod_ErrorCode OH_TextConfig_SetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType enterKeyType)](#oh_textconfig_setenterkeytype) | Sets the Enter key type.|
| [InputMethod_ErrorCode OH_TextConfig_SetPreviewTextSupport(InputMethod_TextConfig *config, bool supported)](#oh_textconfig_setpreviewtextsupport) | Sets the text preview feature.|
| [InputMethod_ErrorCode OH_TextConfig_SetSelection(InputMethod_TextConfig *config, int32_t start, int32_t end)](#oh_textconfig_setselection) | Sets the selected text area.|
| [InputMethod_ErrorCode OH_TextConfig_SetWindowId(InputMethod_TextConfig *config, int32_t windowId)](#oh_textconfig_setwindowid) | Sets the window ID.|
| [InputMethod_ErrorCode OH_TextConfig_SetPlaceholder(InputMethod_TextConfig *config, const char16_t *placeholder,size_t length)](#oh_textconfig_setplaceholder) | Sets the placeholder text.|
| [InputMethod_ErrorCode OH_TextConfig_SetAbilityName(InputMethod_TextConfig *config, const char16_t *abilityName,size_t length)](#oh_textconfig_setabilityname) | Sets the ability name.|
| [InputMethod_ErrorCode OH_TextConfig_SetConsumeKeyEvents(InputMethod_TextConfig *config, bool consumeKeyEvents)](#oh_textconfig_setconsumekeyevents) | Sets whether the text box has the capability to fully process alphabetic, character, and function key events. |
| [InputMethod_ErrorCode OH_TextConfig_GetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType *inputType)](#oh_textconfig_getinputtype) | Obtains the text box type.|
| [InputMethod_ErrorCode OH_TextConfig_GetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType *enterKeyType)](#oh_textconfig_getenterkeytype) | Obtains the Enter key type.|
| [InputMethod_ErrorCode OH_TextConfig_IsPreviewTextSupported(InputMethod_TextConfig *config, bool *supported)](#oh_textconfig_ispreviewtextsupported) | Obtains whether the text preview feature is supported.|
| [InputMethod_ErrorCode OH_TextConfig_GetCursorInfo(InputMethod_TextConfig *config, InputMethod_CursorInfo **cursorInfo)](#oh_textconfig_getcursorinfo) | Obtains the cursor information.|
| [InputMethod_ErrorCode OH_TextConfig_GetTextAvoidInfo(InputMethod_TextConfig *config, InputMethod_TextAvoidInfo **avoidInfo)](#oh_textconfig_gettextavoidinfo) | Obtains the avoidance information.|
| [InputMethod_ErrorCode OH_TextConfig_GetSelection(InputMethod_TextConfig *config, int32_t *start, int32_t *end)](#oh_textconfig_getselection) | Obtains the selected text area.|
| [InputMethod_ErrorCode OH_TextConfig_GetWindowId(InputMethod_TextConfig *config, int32_t *windowId)](#oh_textconfig_getwindowid) | Obtains the window ID.|
| [InputMethod_ErrorCode OH_TextConfig_GetPlaceholder(InputMethod_TextConfig *config, char16_t *placeholder,size_t *length)](#oh_textconfig_getplaceholder) | Obtains the placeholder text.|
| [InputMethod_ErrorCode OH_TextConfig_GetAbilityName(InputMethod_TextConfig *config, char16_t *abilityName,size_t *length)](#oh_textconfig_getabilityname) | Obtains the ability name.|
| [InputMethod_ErrorCode OH_TextConfig_GetConsumeKeyEvents(InputMethod_TextConfig *config, bool *consumeKeyEvents)](#oh_textconfig_getconsumekeyevents) | Obtains whether the text box has the capability to fully process alphabetic, character, and function key events. |

## Function Description

### OH_TextConfig_Create()

```c
InputMethod_TextConfig *OH_TextConfig_Create(void)
```

**Description**

Creates a new [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance. It is mainly used to set the **config** parameter in the [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) callback.

Usage scenarios: Call this function when you need to create a **TextConfig** object outside the **GetTextConfigFunc** callback in advance to prepare the configuration. Normally, the **config** parameter is provided by the callback framework, so you can set it directly within the callback and do not need to create the instance manually.

Use effect: Upon successful creation, a pointer to the newly created **TextConfig** instance is returned. Configuration properties can then be set via Set* APIs.

Lifecycle management: The returned object must be destroyed through [OH_TextConfig_Destroy](#oh_textconfig_destroy). **Create** and **Destroy** APIs must be used in pairs, and each instance can be destroyed only once. Failure to destroy it results in memory leaks.
> **NOTE**
>
> Memory for the **config** parameter provided by the [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) callback framework is managed by the framework. It is automatically released after the callback returns. Do not call **Destroy** for such objects. Only objects created by **OH_TextConfig_Create** require manual destruction by you.

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) * | If creation succeeds, a pointer to the newly created [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance is returned. If creation fails, **NULL** is returned. A possible failure cause is insufficient memory. The returned pointer must be destroyed via [OH_TextConfig_Destroy](#oh_textconfig_destroy) after use, and the pointer shall be set to **NULL** after destruction to avoid misuse. |

### OH_TextConfig_Destroy()

```c
void OH_TextConfig_Destroy(InputMethod_TextConfig *config)
```

**Description**

Destroys an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance. After destruction, the **config** pointer must no longer be used. It is recommended that you set the pointer to **NULL** to avoid misuse.

Usage scenarios: Call this function to release resources when the app no longer needs the **TextConfig** object.

Use effect: The **config** object is released and its internal resources are reclaimed. After that, no function can be called through the **config** pointer.

Lifecycle management: This function shall be used in pair with [OH_TextConfig_Create](#oh_textconfig_create). Each instance shall be destroyed only once; repeated destruction is prohibited. If **config** is **NULL**, the function performs no operations.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance to be destroyed. If **NULL** is passed, the function performs no operations and does not cause a crash. After destruction, the pointer becomes invalid. It is recommended that you set the pointer to **NULL**. Note: Memory for the **config** parameter provided by the **GetTextConfigFunc** callback framework is managed by the framework. Do not call **Destroy** outside the callback to destroy this object. Its memory is released automatically after the callback returns. |

### OH_TextConfig_SetInputType()

```c
InputMethod_ErrorCode OH_TextConfig_SetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType inputType)
```

**Description**

Sets the input type in the text configuration information. The input method framework adjusts the keyboard layout based on this type.

Usage scenarios: Set the input type of the edit box in the **GetTextConfigFunc** callback, or pre-set the input type after creating **TextConfig**.

Use effect: After the setting succeeds, the input method framework switches to the corresponding keyboard layout (such as a text keyboard or numeric keyboard).

Preconditions: The **config** parameter shall be a valid pointer to an **InputMethod_TextConfig** instance.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be set. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) inputType | Input parameter for the input type of the input box. Value range: [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) enum values, such as **IME_TEXT_INPUT_TYPE_TEXT**, **IME_TEXT_INPUT_TYPE_NUMBER**, and **IME_TEXT_INPUT_TYPE_PHONE**. Use effect: Different types trigger the input method to switch to different keyboard layouts. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>**IME_ERR_OK = 0**: Success.<br>**IME_ERR_NULL_POINTER = 12802000**: Unexpected null pointer. The **config** parameter is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetEnterKeyType()

```c
InputMethod_ErrorCode OH_TextConfig_SetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType enterKeyType)
```

**Description**

Sets the Enter key function type in the text configuration information. The input method framework adjusts the display label and function of the Enter key accordingly.

Usage scenarios: Set the Enter key type of the edit box in the **GetTextConfigFunc** callback.

Use effect: After the setting succeeds, the Enter key on the input method keyboard displays the corresponding label (such as "Search" and "Done") and performs the corresponding function.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be set. It cannot be **NULL**. |
| [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) enterKeyType | Input parameter for the function type of the Enter key. Value range: [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) enum values. Use effect: Different types correspond to different Enter key behaviors and display labels. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **config** parameter is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetPreviewTextSupport()

```c
InputMethod_ErrorCode OH_TextConfig_SetPreviewTextSupport(InputMethod_TextConfig *config, bool supported)
```

**Description**

Sets the preview text support status in the text configuration information. Preview text is the candidate text display feature of the input method. After **supported** is set to **true**, the input method enables the preview text feature.

Usage scenarios: Set whether the edit box supports the preview text feature in the **GetTextConfigFunc** callback.

Use effect: After this API is set to **true**, the input method enables the preview text feature and sends preview text to the edit box through the **SetPreviewTextFunc** callback. After this API is set to **false**, the input method disables the preview text feature.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be set. It cannot be **NULL**. |
| bool supported | Input parameter indicating whether the input box supports preview text. Value range: **true** or **false**. The value **true** indicates that preview text is supported and the input method uses the **SetPreviewTextFunc** callback. The value **false** indicates that preview text is not supported. This parameter is mandatory and must be set. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetSelection()

```c
InputMethod_ErrorCode OH_TextConfig_SetSelection(InputMethod_TextConfig *config, int32_t start, int32_t end)
```

**Description**

Sets the text selection range in the text configuration information. It is used to inform the input method of the text selection status of the current edit box.

Usage scenarios: Set the selection range of the current edit box in the **GetTextConfigFunc** callback.

Use effect: After the setting succeeds, the input method perceives the selection state of the edit box accordingly.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be set. It cannot be **NULL**. |
| int32_t start | Input parameter for the start position of the selected text (unit: character offset, counted from 0). Value rule: **start** must be greater than or equal to 0 and less than or equal to **end**. |
| int32_t end | Input parameter for the end position of the selected text (unit: character offset, counted from 0). Value rule: **end** must be greater than or equal to **start** and less than or equal to the total text length. When no text is selected, **start** equals **end**, which indicates the cursor position. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetWindowId()

```c
InputMethod_ErrorCode OH_TextConfig_SetWindowId(InputMethod_TextConfig *config, int32_t windowId)
```

**Description**

Sets the window ID in the text configuration information. It is used to identify the app window to which the edit box belongs. The input method determines the avoidance area and the positioning of the candidate word window accordingly.

Usage scenarios: Set the ID of the window to which the edit box belongs in the **GetTextConfigFunc** callback.

Use effect: After the setting succeeds, the input method determines the positioning and avoidance strategy of the candidate word window accordingly.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be set. It cannot be **NULL**. |
| int32_t windowId | Input parameter specifying the ID of the app‑attached window for the input method. This parameter is mandatory and must be set. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **config** parameter is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_SetPlaceholder()

```c
InputMethod_ErrorCode OH_TextConfig_SetPlaceholder(InputMethod_TextConfig *config, const char16_t *placeholder, size_t length)
```

**Description**

Sets the placeholder text information in the text configuration. The placeholder text is the hint text displayed in the text box when there is no user input, and the input method uses it to perceive the hint content of the text box.

Usage scenarios: Set the placeholder text of the text box in the **GetTextConfigFunc** callback.

Use effect: After the setting succeeds, the input method uses it to perceive the placeholder content of the text box, which can be used for context analysis.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be set. It cannot be **NULL**. If **NULL** is passed, **IME_ERR_NULL_POINTER** is returned. |
| const char16_t *placeholder | Input pointer to a UTF-16 encoded double-byte string. If a null pointer is passed, the placeholder text information is set to an empty string. The function only reads this data and does not modify or release it. |
| size_t length |  Input parameter indicating the count of UTF‑16 characters referenced by the placeholder pointer (excluding the terminator). Value range: [0, 255]. 1. If the length is **0**, the placeholder text information is set to an empty string. 2. The maximum allowed UTF‑16 character count is **255** (excluding the terminator). Any characters beyond this limit are truncated. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): **IME_ERR_OK = 0**: Success. **IME_ERR_NULL_POINTER = 12802000**: Unexpected null pointer. **config** is **NULL**. |

### OH_TextConfig_SetAbilityName()

```c
InputMethod_ErrorCode OH_TextConfig_SetAbilityName(InputMethod_TextConfig *config, const char16_t *abilityName, size_t length)
```

**Description**

Sets the **abilityName** information in the text configuration. **abilityName** is used to identify the ability to which the text box belongs, and the input method uses it to perceive the service scenario of the text box.

Usage scenarios: Set the name of the ability to which the text box belongs in the **GetTextConfigFunc** callback.

Use effect: After the setting succeeds, the input method uses it to perceive the service scenario of the text box.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be set. It cannot be **NULL**. |
| const char16_t *abilityName | Input pointer to a UTF-16 encoded double-byte string. If a null pointer is passed, **abilityName** is set to an empty string. The function only reads this data. |
| size_t length | Input parameter indicating the count of UTF‑16 characters referenced by the **abilityName** pointer (excluding the terminator). Value range: [0, 127]. 1. If the length is **0**, **abilityName** is set to an empty string. 2. The maximum allowed UTF‑16 character count is **127** (excluding the terminator). Any characters beyond this limit are truncated. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): **IME_ERR_OK = 0**: Success. **IME_ERR_NULL_POINTER = 12802000**: Unexpected null pointer. **config** is **NULL**. |

### OH_TextConfig_SetConsumeKeyEvents()

```c
InputMethod_ErrorCode OH_TextConfig_SetConsumeKeyEvents(InputMethod_TextConfig *config, bool consumeKeyEvents)
```

**Description**

Sets whether the edit box has full capability to process key events like letters, characters, and function keys in the text configuration information. When the value is **true**, the edit box fully handles key events, and the input method framework skips processing these keys. When the value is **false**, the edit box lacks this capability, and the input method framework processes the key events instead.

Usage scenarios: Set whether the edit box can handle key events in the **GetTextConfigFunc** callback. When the edit box has implemented complete key processing logic (for example, processing letter keys, character keys, and function keys by itself), set the value to **true**; otherwise, set it to **false**.

Use effect: When this API is set to **true**, the input method framework skips processing keys such as letters, characters, and function keys, and the edit box consumes these key events by itself. When this API is set to **false**, the input method framework processes these key events by itself, and the edit box no longer consumes them.

Preconditions: **config** must be a valid **InputMethod_TextConfig** instance pointer.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be set. It cannot be **NULL**. If **NULL** is passed, **IME_ERR_NULL_POINTER** is returned. |
| bool consumeKeyEvents | Input parameter indicating the edit box has full capability to process key events such as letters, characters, and function keys. Value range: **true** or **false**. **true**: The edit box has full capability to process key events, and the input method framework skips processing of keys such as letters, characters, and function keys, which are consumed by the edit box itself. **false**: The edit box does not have this capability, and key events are processed by the input method framework. This parameter is mandatory and must be set. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetInputType()

```c
InputMethod_ErrorCode OH_TextConfig_GetInputType(InputMethod_TextConfig *config, InputMethod_TextInputType *inputType)
```

**Description**

Obtains the text box type.

Usage scenarios: Call this function when the configured input box type needs to be read.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be obtained. It cannot be **NULL**. |
| [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) *inputType | Output pointer to an [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) variable. Memory is allocated by you, and the function writes the input type value to this address. It cannot be **NULL**. Value range: [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) enum values. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** or **inputType** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetEnterKeyType()

```c
InputMethod_ErrorCode OH_TextConfig_GetEnterKeyType(InputMethod_TextConfig *config, InputMethod_EnterKeyType *enterKeyType)
```

**Description**

Obtains the Enter key type.

Usage scenarios: Call this function when the configured Enter key type needs to be read.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be obtained. It cannot be **NULL**. |
| [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) *enterKeyType | Output pointer to the [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) variable. Memory is allocated by you. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** or **enterKeyType** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_IsPreviewTextSupported()

```c
InputMethod_ErrorCode OH_TextConfig_IsPreviewTextSupported(InputMethod_TextConfig *config, bool *supported)
```

**Description**

Obtains whether the text preview feature is supported.

Usage scenarios: Call this function when the configured preview text support status needs to be read.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be obtained. It cannot be **NULL**. |
| bool *supported | Output pointer indicating whether preview text is supported. Memory is allocated by you. It cannot be **NULL**. Value range: **true** or **false**. The value **true** indicates that preview text is supported, and the value **false** indicates that preview text is not supported. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** or **supported** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetCursorInfo()

```c
InputMethod_ErrorCode OH_TextConfig_GetCursorInfo(InputMethod_TextConfig *config, InputMethod_CursorInfo **cursorInfo)
```

**Description**

Obtains the cursor information in the text configuration. This API uses a double-pointer parameter and allocates memory internally to return a **CursorInfo** object.

Usage scenarios: Call this function when the configured cursor information needs to be read.

Use effect: After a successful call, **cursorInfo** points to a **CursorInfo** object allocated internally by the function, containing information such as the cursor position and height.

Memory management: **cursorInfo** is a double pointer (output pointer). The function allocates memory internally to create an [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) object and returns it through this parameter. The returned **CursorInfo** object shall be released via a call to [OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy) after use. Otherwise, memory leaks will occur. Do not release it directly via the free API.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be obtained. It cannot be **NULL**. |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) **cursorInfo | Output double pointer used to return the cursor information object. The function allocates memory internally to create the [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance and returns it through this double pointer. It cannot be **NULL**. The returned object must be released via a call to [OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy) after use. Do not release it directly via the free API. Otherwise, memory leaks will occur. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** or **cursorInfo** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetTextAvoidInfo()

```c
InputMethod_ErrorCode OH_TextConfig_GetTextAvoidInfo(InputMethod_TextConfig *config, InputMethod_TextAvoidInfo **avoidInfo)
```

**Description**

Obtains the avoidance information in the text configuration. This API uses a double-pointer parameter and allocates memory internally to return a **TextAvoidInfo** object.

Usage scenarios: Call this function when the configured avoid information needs to be read.

Use effect: After a successful call, **avoidInfo** points to a **TextAvoidInfo** object allocated internally by the function, containing information such as the position and size of the avoidance area.

Memory management: **avoidInfo** is a double pointer (output pointer). The function allocates memory internally to create an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) object and returns it through this parameter. The returned **TextAvoidInfo** object shall be released via a call to [OH_TextAvoidInfo_Destroy](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_destroy) after use. Otherwise, memory leaks will occur. Do not release it directly via the free API.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer, which indicates the text configuration information. It cannot be **NULL**. |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) **avoidInfo | Output double pointer used to return the input box avoidance information object. The function allocates memory internally to create the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance and returns it through this double pointer. It cannot be **NULL**. The returned object must be released via a call to [OH_TextAvoidInfo_Destroy](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_destroy) after use. Do not release it directly via the free API. Otherwise, memory leaks will occur. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** or **avoidInfo** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetSelection()

```c
InputMethod_ErrorCode OH_TextConfig_GetSelection(InputMethod_TextConfig *config, int32_t *start, int32_t *end)
```

**Description**

Obtains the selected text area.

Usage scenarios: Call this function when the configured selection range needs to be read.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be obtained. It cannot be **NULL**. |
| int32_t *start | Output pointer to the start position of the selected text (in character offsets). Memory is allocated by you. It cannot be **NULL**. |
| int32_t *end | Output pointer to the end position of the selected text (in character offsets). Memory is allocated by you. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config**, **start**, or **end** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetWindowId()

```c
InputMethod_ErrorCode OH_TextConfig_GetWindowId(InputMethod_TextConfig *config, int32_t *windowId)
```

**Description**

Obtains the window ID.

Usage scenarios: Call this function when the configured window ID needs to be read.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be obtained. It cannot be **NULL**. |
| int32_t *windowId | Output pointer specifying the ID of the app‑attached window for the input method. Memory is allocated by you. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** or **windowId** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextConfig_GetPlaceholder()

```c
InputMethod_ErrorCode OH_TextConfig_GetPlaceholder(InputMethod_TextConfig *config, char16_t *placeholder, size_t *length)
```

**Description**

Obtains the placeholder text information in the text configuration. This API uses a two-step call pattern. In the first call, pass **NULL** as the **placeholder** parameter, and **length** returns the actual placeholder text length. After sufficient memory is allocated based on the returned length, make a second call to obtain the complete content.

Usage scenario: Call this function when the configured placeholder text needs to be read.

Post-call effect: After a successful call, placeholder contains the complete placeholder text content, and length returns the actual length.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be obtained. It cannot be **NULL**. |
| char16_t *placeholder | Output pointer used to store the placeholder text information. The memory of this pointer is allocated and maintained by you. A two-step call strategy is used: the first call passes **NULL** to obtain the actual length while the second call obtains the complete content with sufficient memory allocated. A maximum of 255 UTF-16 characters (excluding the terminator) is supported. When the memory is allocated, it is recommended that you reserve **length** + 1 elements to include the terminator. |
| size_t *length | Input/Output pointer to the length of the placeholder text information, measured in UTF‑16 characters and excluding the terminator. When used as an input parameter, it indicates the available memory length pointed to by **placeholder** (maximum **255** characters). When used as an output parameter, it indicates the actual placeholder text length. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): **IME_ERR_OK = 0**: Success. **IME_ERR_PARAMCHECK = 401**: Parameter check failed. **placeholder** may be **NULL** or the length is insufficient, in which case **length** will be set to the actual length. **IME_ERR_NULL_POINTER = 12802000**: Unexpected null pointer. **config** or **length** is **NULL**. |

### OH_TextConfig_GetAbilityName()

```c
InputMethod_ErrorCode OH_TextConfig_GetAbilityName(InputMethod_TextConfig *config, char16_t *abilityName, size_t *length)
```

**Description**

Obtains the **abilityName** information in the text configuration. This API uses a two-step call pattern. In the first call, pass **NULL** as the **abilityName** parameter, and **length** returns the actual **abilityName** length. After sufficient memory is allocated based on the returned length, make a second call to obtain the complete content.

Usage scenarios: Call this function when the configured **abilityName** needs to be read.

Use effect: After a successful call, **abilityName** contains the complete **abilityName** content, and **length** returns the actual length.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the **TextConfig** instance whose value is to be obtained. It cannot be **NULL**. |
| char16_t *abilityName | Output pointer used to store **abilityName**. The memory of this pointer is allocated and maintained by you. A two-step call strategy is used: the first call passes **NULL** to obtain the actual length while the second call obtains the complete content with sufficient memory allocated. A maximum of 127 UTF-16 characters (excluding the terminator) is supported. When the memory is allocated, it is recommended that you reserve **length** + 1 elements. |
| size_t *length | Input/Output pointer to the length of **abilityName**, measured in UTF‑16 characters and excluding the terminator. When used as an input parameter, it indicates the available memory length pointed to by **abilityName** (maximum **127** characters). When used as an output parameter, it indicates the actual **abilityName** length. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode):<br>     **IME_ERR_OK = 0**: Success.<br>     **IME_ERR_PARAMCHECK = 401**: Parameter check failed.<br>     **IME_ERR_NULL_POINTER = 12802000**: Unexpected null pointer.|

### OH_TextConfig_GetConsumeKeyEvents()

```c
InputMethod_ErrorCode OH_TextConfig_GetConsumeKeyEvents(InputMethod_TextConfig *config, bool *consumeKeyEvents)
```

**Description**

Obtains whether the edit box has full capability to process key events like letters, characters, and function keys in the text configuration information. This reads the key event consumption capability configuration set through [OH_TextConfig_SetConsumeKeyEvents](#oh_textconfig_setconsumekeyevents).

Usage scenarios: Call this function when you need to read the configured key event processing capability to determine whether the edit box has the full capability to consume key events.

Use effect: After a successful call, **consumeKeyEvents** returns the key event processing capability status of the edit box. **true** indicates that the edit box has the full capability to process key events, and the input method framework skips processing of keys such as letters, characters, and function keys. **false** indicates that the edit box does not have this capability, and key events are processed by the input method framework.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Input pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance whose value is to be obtained. It cannot be **NULL**. If **NULL** is passed, **IME_ERR_NULL_POINTER** is returned. |
| bool *consumeKeyEvents | Output pointer that returns whether the edit box has full capability to process key events such as letters, characters, and function keys. Memory is allocated by you. It cannot be **NULL**. Value range: **true** or **false**. **true**: The edit box has full capability to process key events, and the input method framework skips processing of keys such as letters, characters, and function keys. **false**: The edit box does not have this capability, and key events are processed by the input method framework. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **config** or **consumeKeyEvents** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |