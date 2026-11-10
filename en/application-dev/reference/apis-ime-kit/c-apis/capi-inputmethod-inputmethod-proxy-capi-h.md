# inputmethod_inputmethod_proxy_capi.h

## Overview

Provides methods for using the input method, allowing requests and notifications to be sent to the input method application.

**File to Include**: <inputmethod/inputmethod_inputmethod_proxy_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) | InputMethod_InputMethodProxy | Provides an interaction proxy object between the app and the input method service. The app can call relevant APIs of the input method service and receive event callbacks from the input method service through this object. This struct is an opaque type. Its internal members shall not be accessed directly. Operations can only be performed through the function interfaces provided by this module. |

### Function

| Name | Description |
| -- | -- |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_showkeyboard) | Displays the keyboard. |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)](#oh_inputmethodproxy_showtextinput) | Displays the text box. |
| [InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_hidekeyboard) | Hides the keyboard. |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)](#oh_inputmethodproxy_notifyselectionchange) | Notifies the input method application of the change in the selected text area, including the change of text content, cursor position, or the selected text. |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)](#oh_inputmethodproxy_notifyconfigurationchange) | Notifies the change of the text box configuration. |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)](#oh_inputmethodproxy_notifycursorupdate) | Notifies the cursor position change. |
| [InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)](#oh_inputmethodproxy_sendprivatecommand) | Sends a private data command. |
| [InputMethod_ErrorCode OH_InputMethod_InputMethodProxy_RequestSystemInputCapability(InputMethod_InputMethodProxy *inputMethodProxy, OH_InputMethod_InputCapabilityType type)](#oh_inputmethod_inputmethodproxy_requestsysteminputcapability) | Request system input capability. |

## Function description

### OH_InputMethodProxy_ShowKeyboard()

```c
InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)
```

**Description**

Displays the keyboard.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method not bound. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethodProxy_ShowTextInput()

```c
InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)
```

**Description**

Displays the text box.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | Pointer to the [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance, which is used to obtain the configuration options. <br>In this API, you only need to pay attention to [InputMethod_RequestKeyboardReason](capi-inputmethod-types-capi-h.md#inputmethod_requestkeyboardreason), which indicates the reason for requesting the keyboard. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method not bound. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethodProxy_HideKeyboard()

```c
InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)
```

**Description**

Hides the keyboard.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method not bound. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethodProxy_NotifySelectionChange()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)
```

**Description**

Notifies the input method application of the change in the selected text area, including the change of text content, cursor position, or the selected text.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |
| char16_t text[] | Entire input text. |
| size_t length | Length of the **text** parameter. Maximum length: 8 KB. |
| int start | Start position of the selected text. |
| int end | End position of the selected text. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method not bound. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethodProxy_NotifyConfigurationChange()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)
```

**Description**

Notifies the change of the text box configuration.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |
| [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) enterKey | Enter key type. |
| [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) textType | Text box type. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method not bound. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethodProxy_NotifyCursorUpdate()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)
```

**Description**

Notifies the cursor position change.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) *cursorInfo | Pointer to the [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance, indicating the cursor information. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method not bound. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethodProxy_SendPrivateCommand()

```c
InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)
```

**Description**

Sends a private data command.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *privateCommand[] | Private command that is defined in [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). The maximum size is 32 KB. |
| size_t size | Size of the private command array. The maximum size is 5. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method not bound. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethod_InputMethodProxy_RequestSystemInputCapability()

```c
InputMethod_ErrorCode OH_InputMethod_InputMethodProxy_RequestSystemInputCapability(InputMethod_InputMethodProxy *inputMethodProxy, OH_InputMethod_InputCapabilityType type)
```

**Description**

Request system input capability.

<!--Device-InputMethod_ErrorCode OH_InputMethod_InputMethodProxy_RequestSystemInputCapability(InputMethod_InputMethodProxy *inputMethodProxy, OH_InputMethod_InputCapabilityType type)--><!--Device-InputMethod_ErrorCode OH_InputMethod_InputMethodProxy_RequestSystemInputCapability(InputMethod_InputMethodProxy *inputMethodProxy, OH_InputMethod_InputCapabilityType type)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | [in] indicates the pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The value of inputMethodProxy is obtained from [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |
| [OH_InputMethod_InputCapabilityType](capi-inputmethod-types-capi-h.md#oh_inputmethod_inputcapabilitytype) type | [out] indicates the input capability type. [OH_InputMethod_InputCapabilityType](capi-inputmethod-types-capi-h.md#oh_inputmethod_inputcapabilitytype) |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success.</li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter verification failed.</li> <li>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method management service error.</li> <li>IME_ERR_DETAACHE - The input method client is disconnected.</li> <li>OH_INPUT METHOD_ERR_NOT_DEFAULT_IME - The current input method is not the default input method configured in the system.</li> <li>OH_INPUT METHOD_ERR_INPUT_CAPABLE_TYPE_NOT_SUPPORTED - The input capability type is not supported.</li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer.</li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode).</li> <ul> |


