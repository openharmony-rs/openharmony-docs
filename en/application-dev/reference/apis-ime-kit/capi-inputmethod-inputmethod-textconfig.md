# InputMethod_TextConfig

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4c244f2ed12456a4c6059eccff764e442d7872b9 translatedAt=2026-08-19T01:22:27.843Z pushedAt=2026-08-24T07:06:19.340Z -->

```c
typedef struct InputMethod_TextConfig InputMethod_TextConfig
```

## Overview

Represents a configuration struct for text input behavior in text input boxes. The input box uses it to pass core input rules to the input method framework, which then performs the corresponding input behavior based on the configuration. By configuring input attributes (such as input type and text format), it can meet input requirements in various scenarios and improve user input experience. It is suitable for text input scenarios that require fine-grained control over input behavior. This struct is an opaque type, and you cannot directly access its internal members. You can only operate on it through the function interfaces provided by this module.

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

**Header file**: [inputmethod_text_config_capi.h](capi-inputmethod-text-config-capi-h.md)

## Struct Purpose

Carries the configuration information of the edit box, including the input type, enter key type, preview text support, selection range, cursor information, avoidance information, window ID, placeholder text, and **abilityName**. This configuration information is used in the [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) callback. In the callback, you need to set each configuration item in the **config** parameter, and the input method framework adjusts the keyboard layout and input behavior based on the settings.

## Composition

InputMethod_TextConfig internally contains the following substructure information:

- [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md): Cursor information, including the cursor position and height. It can be obtained through [OH_TextConfig_GetCursorInfo](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getcursorinfo) which returns a double pointer (memory is allocated inside the function).

- [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md): Avoidance information, including the position and size of the avoidance area. It can be obtained through [OH_TextConfig_GetTextAvoidInfo](capi-inputmethod-text-config-capi-h.md#oh_textconfig_gettextavoidinfo) which returns a double pointer (memory is allocated inside the function).

Related functions:

- Create/Destroy functions

| Function | Description |
| -- | -- |
| [OH_TextConfig_Create](capi-inputmethod-text-config-capi-h.md#oh_textconfig_create) | Creates a new **InputMethod_TextConfig** instance. |
| [OH_TextConfig_Destroy](capi-inputmethod-text-config-capi-h.md#oh_textconfig_destroy) | Destroys an **InputMethod_TextConfig** instance. |

- Set functions (Set*)

| Function | Description |
| -- | -- |
| [OH_TextConfig_SetInputType](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setinputtype) | Sets the input box type in the text configuration information. |
| [OH_TextConfig_SetEnterKeyType](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setenterkeytype) | Sets the enter key function type in the text configuration information. |
| [OH_TextConfig_SetPreviewTextSupport](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setpreviewtextsupport) | Sets whether preview text is supported. |
| [OH_TextConfig_SetSelection](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setselection) | Sets the selected text range. |
| [OH_TextConfig_SetWindowId](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setwindowid) | Sets the ID of the window to which the input box belongs. |
| [OH_TextConfig_SetPlaceholder](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setplaceholder) | Sets the placeholder text information. |
| [OH_TextConfig_SetAbilityName](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setabilityname) | Sets the **abilityName** information. |
| [OH_TextConfig_SetConsumeKeyEvents](capi-inputmethod-text-config-capi-h.md#oh_textconfig_setconsumekeyevents) | Sets whether the edit box can fully process keys such as letters, characters, and function keys in the text configuration information.<br/>**Since:** 26.0.0 |

- Get functions (Get*)

| Function | Description |
| -- | -- |
| [OH_TextConfig_GetInputType](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getinputtype) | Obtains the input box type. |
| [OH_TextConfig_GetEnterKeyType](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getenterkeytype) | Obtains the enter key function type. |
| [OH_TextConfig_IsPreviewTextSupported](capi-inputmethod-text-config-capi-h.md#oh_textconfig_ispreviewtextsupported) | Obtains whether preview text is supported. |
| [OH_TextConfig_GetCursorInfo](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getcursorinfo) | Obtains the cursor information (double pointer, memory allocated inside the function). |
| [OH_TextConfig_GetTextAvoidInfo](capi-inputmethod-text-config-capi-h.md#oh_textconfig_gettextavoidinfo) | Obtains the avoidance information (double pointer, memory allocated inside the function). |
| [OH_TextConfig_GetSelection](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getselection) | Obtains the selection range information. |
| [OH_TextConfig_GetWindowId](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getwindowid) | Obtains the window ID of the owning window. |
| [OH_TextConfig_GetPlaceholder](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getplaceholder) | Obtains the placeholder text information. |
| [OH_TextConfig_GetAbilityName](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getabilityname) | Obtains the **abilityName** information. |
| [OH_TextConfig_GetConsumeKeyEvents](capi-inputmethod-text-config-capi-h.md#oh_textconfig_getconsumekeyevents) | Obtains whether the edit box can fully process keys such as letters, characters, and function keys in the text configuration information.<br/>**Since:** 26.0.0 |