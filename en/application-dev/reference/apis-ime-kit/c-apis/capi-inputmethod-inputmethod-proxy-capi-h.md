# inputmethod_inputmethod_proxy_capi.h

## Overview

Provides methods for using the input method, allowing requests and notifications to be sent to the input method application.

**Include**: <inputmethod/inputmethod_inputmethod_proxy_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) | InputMethod_InputMethodProxy | A struct that serves as the proxy between an application and the input method. The application can call APIs of the input method through this proxy and receive event callbacks from the input method. |

### Function

| Name | Description |
| -- | -- |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_showkeyboard) | Show keyboard. |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)](#oh_inputmethodproxy_showtextinput) | Displays the text box. |
| [InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_hidekeyboard) | Hide keyboard. |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)](#oh_inputmethodproxy_notifyselectionchange) | Notify selection change.<br> Notify selection change when text or cursor position or selected text changed. |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)](#oh_inputmethodproxy_notifyconfigurationchange) | Notify text editor configuration change. |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)](#oh_inputmethodproxy_notifycursorupdate) | Notify cursor update. |
| [InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)](#oh_inputmethodproxy_sendprivatecommand) | Send private command. |

## Function description

### OH_InputMethodProxy_ShowKeyboard()

```c
InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)
```

**Description**

Show keyboard.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Represents a pointer to an [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The inputMethodProxy is obtained from [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach). |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br>{@link IME_ERR_DETACHED} - input method client detached.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_InputMethodProxy_ShowTextInput()

```c
InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)
```

**Description**

Displays the text box.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy. md) instance obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach). |
| InputMethod_AttachOptions *options | Pointer to the [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance, which is used to obtain the configuration options.<br>In this API, you only need to pay attention to [InputMethod_RequestKeyboardReason](capi-inputmethod-types-capi-h.md#inputmethod_requestkeyboardreason), which indicates the reason for requesting the keyboard. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br>{@link IME_ERR_DETACHED} - input method client detached.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer. If inputMethodProxy is NULL, or options is NULL.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_InputMethodProxy_HideKeyboard()

```c
InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)
```

**Description**

Hide keyboard.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Represents a pointer to an [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The inputMethodProxy is obtained from [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach). |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br>{@link IME_ERR_DETACHED} - input method client detached.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_InputMethodProxy_NotifySelectionChange()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)
```

**Description**

Notify selection change.<br> Notify selection change when text or cursor position or selected text changed.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Represents a pointer to an [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The inputMethodProxy is obtained from [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach). |
| char16_t text[] | The whole input text. |
| size_t length | The length of text. Max length is 8K. |
| int start | The start position of selected text. |
| int end | The end position of selected text. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_PARAMCHECK} - parameter check failed.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br>{@link IME_ERR_DETACHED} - input method client detached.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_InputMethodProxy_NotifyConfigurationChange()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)
```

**Description**

Notify text editor configuration change.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Represents a pointer to an [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The inputMethodProxy is obtained from [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach). |
| InputMethod_EnterKeyType enterKey | The enter key type. |
| InputMethod_TextInputType textType | The text input type. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_PARAMCHECK} - parameter check failed.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br> {@link IME_ERR_DETACHED} - input method client detached.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_InputMethodProxy_NotifyCursorUpdate()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)
```

**Description**

Notify cursor update.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Represents a pointer to an [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The inputMethodProxy is obtained from [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach). |
| InputMethod_CursorInfo *cursorInfo | Represents a pointer to an {@link InputMethod_CursorInfo} instance. The cursor information. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_PARAMCHECK} - parameter check failed.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br>{@link IME_ERR_DETACHED} - input method client detached.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_InputMethodProxy_SendPrivateCommand()

```c
InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)
```

**Description**

Send private command.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Represents a pointer to an [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The inputMethodProxy is obtained from [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach). |
| InputMethod_PrivateCommand *privateCommand[] | The private commands, which is defined in {@link InputMethod_PrivateCommand}. Max size 32KB. |
| size_t size | The size of privateCommand. Max is 5. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_PARAMCHECK} - parameter check failed.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br>{@link IME_ERR_DETACHED} - input method client detached.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |


