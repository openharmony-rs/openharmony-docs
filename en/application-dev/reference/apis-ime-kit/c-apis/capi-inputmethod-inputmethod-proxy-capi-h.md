# inputmethod_inputmethod_proxy_capi.h

## Overview

Provides methods for using the input method, allowing requests and notifications to be sent to the input method application.

**File to Include**: <inputmethod/inputmethod_inputmethod_proxy_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) | InputMethod_InputMethodProxy | Provides an interaction proxy object between the app and the input method service. The app can call relevant APIs of the input method service and receive event callbacks from the input method service through this object. This struct is an opaque type. Its internal members shall not be accessed directly. Operations can only be performed through the function interfaces provided by this module. |

### Functions

| Name | Description |
| -- | -- |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_showkeyboard) | Displays the keyboard. After this function is called, the system requests the input method application to display the soft keyboard interface for text input. <br> <br>Application scenario: This function is invoked when an application needs to actively start the keyboard for text input. For example, the keyboard needs to be displayed after the edit box is focused. <br> <br> Effect after use: After the interface is successfully invoked, the soft keyboard interface is displayed. If the interface fails to be invoked, an error code is returned. You need to rectify the fault based on the error code. <br> <br>Prerequisites: You must invoke [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) to obtain the inputMethodProxy instance and the instance is in the Attached state. <br> <br>Life cycle management: The inputMethodProxy is created by the [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) and cannot be manually destroyed. After [OH_InputMethodController_Detach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_detach) is called to unbind the inputMethodProxy, the inputMethodProxy becomes invalid. If this function is called again, the error code IME_ERR_DETAACHE is returned. <br><br>Invoking sequence: OH_InputMethodController_Attach → OH_InputMethodProxy_ShowKeyboard → OH_InputMethodProxy_HideKeyboard → OH_InputMethodController_Detach <br> <br> Thread security: This function is not thread-safe. You are not advised to operate the same inputMethodProxy object at the same time in a multi-thread environment. If multiple threads are required, lock the object. The Controller and InputMethodProxy operations must be performed in serial mode. Concurrent or callback reentrant C interface session operations are rejected before affecting the current session and IME_ERR_IMCLIENT is returned. This protection does not represent a general thread-safe guarantee for native layer, ArkTS, or server-side operations. |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)](#oh_inputmethodproxy_showtextinput) | Displays the text box. |
| [InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_hidekeyboard) | Hides the keyboard. |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)](#oh_inputmethodproxy_notifyselectionchange) | Notifies the input method application of the change in the selected text area, including the change of text content, cursor position, or the selected text. |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)](#oh_inputmethodproxy_notifyconfigurationchange) | Notifies the change of the text box configuration. |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)](#oh_inputmethodproxy_notifycursorupdate) | Notifies the cursor position change. When the cursor position in the edit box changes, this interface is used to notify the input method application of the new cursor information. In this way, the input method can adjust the position of the candidate word window based on the cursor position. <br> <br>Application scenario: This function is invoked when the cursor moves in the edit box, for example, when a user clicks a different position in the edit box or the code actively moves the cursor. <br> <br> Effect after use: After the call is successful, the input method application receives the new cursor information and adjusts the positioning of the candidate word window accordingly. If the interface fails to be invoked, the corresponding error code is returned. <br> <br>Prerequisites: You must invoke [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) to obtain the inputMethodProxy instance. The cursorInfo must be a valid CursorInfo handle created with [OH_CursorInfo_Create](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_create), or a still valid child object borrow view returned by TextConfig, and the relevant properties have been set. <br> <br>Life cycle management: The inputMethodProxy is created and output by the attach process and cannot be manually destroyed. The inputMethodProxy becomes invalid after the detach process. The cursorInfo created independently is managed by the caller. After using the cursorInfo, call [OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy) to destroy the cursorInfo. Sub-object views of TextConfig are borrowed only and cannot be destroyed or used after they expire. <br> <br> Thread-safe: This function is not thread-safe. You are not advised to operate the same inputMethodProxy object in a multi-thread environment. |
| [InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)](#oh_inputmethodproxy_sendprivatecommand) | Send a private data command. An application uses this interface to send customized private command data to an input method application to implement a private communication protocol between the application and the input method. <br> <br>Application scenario: This function is invoked when an application needs to transfer customized private data(such as service-specific instructions and configuration parameters) to an input method application. This function is applicable to the scenario where a private communication protocol is used between the application and the input method. <br> <br> Effect: After the invoking is successful, the input method application receives the private command data through the [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h. md#oh_texteditorproxy_receiveprivatecommandfunc) callback. If the interface fails to be invoked, the corresponding error code is returned. <br> <br>Prerequisites: You must invoke [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) to obtain the inputMethodProxy instance and the instance is in the Attached state. <br> <br>Life cycle management: The inputMethodProxy is created and output by the attach process and cannot be manually destroyed. The inputMethodProxy becomes invalid after the detach process. Self-owned objects in the privateCommand array are managed by the caller. After using the privateCommand array, you need to call [OH_PrivateCommand_Destroy](capi-inputmethod-private-command-capi-h.md#oh_privatecommand_destroy) to destroy them one by one. Borrowed objects provided by the callback cannot be destroyed or retained after the callback ends. <br> <br>Performance suggestion: The privateCommand array contains a maximum of five command objects(the maximum size is 5). If the number of command objects exceeds the limit, IME_ERR_PARAMCHECK is returned. The maximum size of a single command object is 32 KB. If the maximum size is exceeded, data transfer may fail. <br> <br> Thread-safe: This function is not thread-safe. You are not advised to operate the same inputMethodProxy object in a multi-thread environment. |
| [InputMethod_ErrorCode OH_InputMethod_InputMethodProxy_RequestSystemInputCapability(InputMethod_InputMethodProxy *inputMethodProxy, OH_InputMethod_InputCapabilityType type)](#oh_inputmethod_inputmethodproxy_requestsysteminputcapability) | Request system input capability. |

## Function description

### OH_InputMethodProxy_ShowKeyboard()

```c
InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)
```

**Description**

Displays the keyboard. After this function is called, the system requests the input method application to display the soft keyboard interface for text input. <br> <br>Application scenario: This function is invoked when an application needs to actively start the keyboard for text input. For example, the keyboard needs to be displayed after the edit box is focused. <br> <br> Effect after use: After the interface is successfully invoked, the soft keyboard interface is displayed. If the interface fails to be invoked, an error code is returned. You need to rectify the fault based on the error code. <br> <br>Prerequisites: You must invoke [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) to obtain the inputMethodProxy instance and the instance is in the Attached state. <br> <br>Life cycle management: The inputMethodProxy is created by the [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) and cannot be manually destroyed. After [OH_InputMethodController_Detach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_detach) is called to unbind the inputMethodProxy, the inputMethodProxy becomes invalid. If this function is called again, the error code IME_ERR_DETAACHE is returned. <br><br>Invoking sequence: OH_InputMethodController_Attach → OH_InputMethodProxy_ShowKeyboard → OH_InputMethodProxy_HideKeyboard → OH_InputMethodController_Detach <br> <br> Thread security: This function is not thread-safe. You are not advised to operate the same inputMethodProxy object at the same time in a multi-thread environment. If multiple threads are required, lock the object. The Controller and InputMethodProxy operations must be performed in serial mode. Concurrent or callback reentrant C interface session operations are rejected before affecting the current session and IME_ERR_IMCLIENT is returned. This protection does not represent a general thread-safe guarantee for native layer, ArkTS, or server-side operations.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | [in] Input pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The value of inputMethodProxy is obtained by invoking [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). The pointer cannot be null. If the pointer is null, the error code IME_ERR_NULL_POINTER is returned. After Detach, the pointer becomes invalid and cannot be used to invoke any functions related to InputMethodProxy. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success and the keyboard has requested display. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - inputMethodProxy does not match the current proxy. </li> <li>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method client error, which may be an internal exception of the client. </li> <li>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. The possible cause is that the input method management service is unavailable. </li> <li>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unbound input method, indicating that Detach has been invoked and can be used only after re-attaching. </li> <li>IME_ERR_EDITABLE: The text box is in the non-editing state. The binding relationship may still be valid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The inputMethodProxy is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

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
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | [in] Input pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The value of inputMethodProxy is obtained by invoking [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). The pointer cannot be null. If the pointer is null, the error code IME_ERR_NULL_POINTER is returned. The pointer becomes invalid after the Detach operation. |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | [in] Input pointer to the [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance, which is used to obtain configuration options. The pointer cannot be null. If the pointer is null, the error code IME_ERR_NULL_POINTER is returned. In this interface, you only need to pay attention to the [InputMethod_RequestKeyboardReason](capi-inputmethod-types-capi-h.md#inputmethod_requestkeyboardreason) attribute, which indicates the reason for requesting keyboard input. The ShowKeyboard attribute in AttachOptions is always true in this interface. options must be a valid AttachOptions handle; An unregistered or invalid value object handle returns IME_ERR_PARAMCHECK. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - inputMethodProxy does not match the current proxy, or the options handle is not registered or invalid. </li> <li>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method client error. </li> <li>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. </li> <li>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): The input method is not bound. The detached input method needs to be re-attached. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The value of inputMethodProxy or options is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

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
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | [in] Input pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The value of inputMethodProxy is obtained by invoking [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). The pointer cannot be null. If the pointer is null, the error code IME_ERR_NULL_POINTER is returned. The pointer becomes invalid after the Detach operation. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. The keyboard has requested to be hidden. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - inputMethodProxy does not match the current proxy. </li> <li>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method client error. </li> <li>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. </li> <li>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): The input method is not bound. The detached input method needs to be re-attached. </li> <li>IME_ERR_EDITABLE: The text box is in the non-editing state. The binding relationship may still be valid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

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
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | [in] Input pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The value of inputMethodProxy is obtained by invoking [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). The pointer cannot be null. If the pointer is null, the error code IME_ERR_NULL_POINTER is returned. The pointer becomes invalid after the Detach operation. |
| char16_t text[] | [in] Pointer to the input text, which is encoded using UTF-16. Memory is allocated by the caller, and the function reads only this data. The pointer cannot be NULL. The maximum length is 8 KB.(8192 char16_t characters, corresponding to 16384 bytes) If this limit is exceeded, IME_ERR_PARAMCHECK is returned. |
| size_t length | [in] Input parameter, number of characters in the text parameter(unit: char16_t). Value range: 0 to 8192. If the number exceeds 8192, the IME_ERR_PARAMCHECK error code is returned. |
| int start | [in] Input parameter, which indicates the start position of the selected text.(Unit: character offset, counting from 0) Value range: greater than or equal to 0 and less than or equal to end. Rule: The value of start must be smaller than or equal to that of end, and the length of text cannot exceed the actual length. |
| int end | [in] Input parameter, which indicates the end position of the selected text.(Unit: character offset, counting from 0) Value range: greater than or equal to the actual length of start and less than or equal to the actual length of text. Rule: When no text is selected, start is the same as end, indicating the cursor position. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. The possible cause is that the length exceeds 8 KB or the start/end range is invalid. Check whether the parameter value is within the valid range. </li> <li>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method client error. </li> <li>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. </li> <li>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): The input method is not bound. The detached input method needs to be re-attached. </li> <li>IME_ERR_EDITABLE: The text box is in the non-editing state. The binding relationship may still be valid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer, inputMethodProxy is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

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
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | [in] Input pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The value of inputMethodProxy is obtained by invoking [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). The pointer cannot be null. If the pointer is null, the error code IME_ERR_NULL_POINTER is returned. The pointer becomes invalid after the Detach operation. |
| [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) enterKey | [in] Enter the input parameter. Value range: [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) Enumerated value, such as IME_ENTER_KEY_UNSPECIFIED, IME_ENTER_KEY_GO, and IME_ENTER_KEY_SEARCH. Effect after use: The input method will adjust the display label and function of the Enter key accordingly. |
| [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) textType | [in] Input parameter, text box type. Value range: [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) Enumerated value, such as IME_TEXT_INPUT_TYPE_UNSPECIFIED, IME_TEXT_INPUT_TYPE_TEXT, and IME_TEXT_INPUT_TYPE_NUMBER. Effect after use: The input method will switch the keyboard layout(such as the numeric keypad, text keyboard, etc.) accordingly. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. The possible cause is that the value of enterKey or textType is invalid. Check whether the enumerated value is within the valid range. </li> <li>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method client error. </li> <li>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. </li> <li>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): The input method is not bound. The detached input method needs to be re-attached. </li> <li>IME_ERR_EDITABLE: The text box is in the non-editing state. The binding relationship may still be valid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_InputMethodProxy_NotifyCursorUpdate()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)
```

**Description**

Notifies the cursor position change. When the cursor position in the edit box changes, this interface is used to notify the input method application of the new cursor information. In this way, the input method can adjust the position of the candidate word window based on the cursor position. <br> <br>Application scenario: This function is invoked when the cursor moves in the edit box, for example, when a user clicks a different position in the edit box or the code actively moves the cursor. <br> <br> Effect after use: After the call is successful, the input method application receives the new cursor information and adjusts the positioning of the candidate word window accordingly. If the interface fails to be invoked, the corresponding error code is returned. <br> <br>Prerequisites: You must invoke [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) to obtain the inputMethodProxy instance. The cursorInfo must be a valid CursorInfo handle created with [OH_CursorInfo_Create](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_create), or a still valid child object borrow view returned by TextConfig, and the relevant properties have been set. <br> <br>Life cycle management: The inputMethodProxy is created and output by the attach process and cannot be manually destroyed. The inputMethodProxy becomes invalid after the detach process. The cursorInfo created independently is managed by the caller. After using the cursorInfo, call [OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy) to destroy the cursorInfo. Sub-object views of TextConfig are borrowed only and cannot be destroyed or used after they expire. <br> <br> Thread-safe: This function is not thread-safe. You are not advised to operate the same inputMethodProxy object in a multi-thread environment.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | [in] Input pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. inputMethodProxy is obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). The pointer cannot be null. If the pointer is null, the error code IME_ERR_NULL_POINTER is returned. The pointer becomes invalid after the Detach operation. |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) *cursorInfo | [in] Input pointer to the [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) instance, indicating cursor information. The pointer cannot be null. If the pointer is null, the error code IME_ERR_NULL_POINTER is returned. cursorInfo must be a valid CursorInfo handle or a TextConfig sub-object borrowing view; An unregistered or invalid value object handle returns IME_ERR_PARAMCHECK. The function reads only its internal data and does not modify or release it. The object created independently through [OH_CursorInfo_Create](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_create) is released by the caller through [OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy) after using it. The borrowed view cannot be destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. The possible cause is that the internal data of cursorInfo is invalid, or the handle is not registered or invalid. Check the cursor information parameter. </li> <li>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method client error. </li> <li>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. </li> <li>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): The input method is not bound. The detached input method needs to be re-attached. </li> <li>IME_ERR_EDITABLE: The text box is in the non-editing state. The binding relationship may still be valid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. inputMethodProxy or cursorInfo is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_InputMethodProxy_SendPrivateCommand()

```c
InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)
```

**Description**

Send a private data command. An application uses this interface to send customized private command data to an input method application to implement a private communication protocol between the application and the input method. <br> <br>Application scenario: This function is invoked when an application needs to transfer customized private data(such as service-specific instructions and configuration parameters) to an input method application. This function is applicable to the scenario where a private communication protocol is used between the application and the input method. <br> <br> Effect: After the invoking is successful, the input method application receives the private command data through the [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h. md#oh_texteditorproxy_receiveprivatecommandfunc) callback. If the interface fails to be invoked, the corresponding error code is returned. <br> <br>Prerequisites: You must invoke [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) to obtain the inputMethodProxy instance and the instance is in the Attached state. <br> <br>Life cycle management: The inputMethodProxy is created and output by the attach process and cannot be manually destroyed. The inputMethodProxy becomes invalid after the detach process. Self-owned objects in the privateCommand array are managed by the caller. After using the privateCommand array, you need to call [OH_PrivateCommand_Destroy](capi-inputmethod-private-command-capi-h.md#oh_privatecommand_destroy) to destroy them one by one. Borrowed objects provided by the callback cannot be destroyed or retained after the callback ends. <br> <br>Performance suggestion: The privateCommand array contains a maximum of five command objects(the maximum size is 5). If the number of command objects exceeds the limit, IME_ERR_PARAMCHECK is returned. The maximum size of a single command object is 32 KB. If the maximum size is exceeded, data transfer may fail. <br> <br> Thread-safe: This function is not thread-safe. You are not advised to operate the same inputMethodProxy object in a multi-thread environment.

<!--Device-InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)--><!--Device-InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | [in] Input pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The value of inputMethodProxy is obtained by invoking [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). The pointer cannot be null. If the pointer is null, the error code IME_ERR_NULL_POINTER is returned. The pointer becomes invalid after the Detach operation. |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *privateCommand[] | [in] Input pointer, private command array. Each element must be a valid self-owned command object or a borrowed command object provided by the callback, pointing to the InputMethod_PrivateCommand instance. An unregistered or invalid value object handle returns IME_ERR_PARAMCHECK. Own objects are created and memory is allocated by the caller, and functions only read data. The pointer cannot be NULL. The maximum size of a single command object is 32 KB(including the total size of the key and value). If the size exceeds 32 KB, the transmission may fail. The maximum length of the array is 5(that is, the maximum length of the size parameter is 5). |
| size_t size | [in] Input parameter, indicating the number of elements in the private command array. Value range: 0 to 5. If the value exceeds 5, the IME_ERR_PARAMCHECK error code is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success and the private command has been sent. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. The possible causes are as follows: size exceeds 5, privateCommand is NULL, or a single command exceeds 32 KB, or the object handle in the array is not registered or invalid. Check the parameter value. </li> <li>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method client error. </li> <li>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. </li> <li>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): The input method is not bound. The detached input method needs to be re-attached. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer, inputMethodProxy or privateCommand is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

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


