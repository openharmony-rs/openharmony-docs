# inputmethod_text_editor_proxy_capi.h

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=87ecd313da7eaf9820ea21ed983e70c5f013ee1a translatedAt=2026-08-26T12:20:53.550Z pushedAt=2026-08-29T09:14:46.439Z -->

## Overview

Provides a set of methods that enable self‑drawn input boxes implemented by an app to receive notifications and requests from the input method app. This module uses a callback mechanism to implement bidirectional communication between the input method app and self‑drawn input box.

**File to include**: <inputmethod/inputmethod_text_editor_proxy_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) | InputMethod_TextEditorProxy | Input method text editor proxy class. Provides methods for obtaining notifications and requests from the input method app. |

### Function

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (*OH_TextEditorProxy_GetTextConfigFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_TextConfig *config)](#oh_texteditorproxy_gettextconfigfunc) | OH_TextEditorProxy_GetTextConfigFunc | Function triggered when the input method obtains the input box configuration. |
| [typedef void (*OH_TextEditorProxy_InsertTextFunc)(InputMethod_TextEditorProxy *textEditorProxy, const char16_t *text, size_t length)](#oh_texteditorproxy_inserttextfunc) | OH_TextEditorProxy_InsertTextFunc | Function triggered when the input method app inserts text. |
| [typedef void (*OH_TextEditorProxy_DeleteForwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)](#oh_texteditorproxy_deleteforwardfunc) | OH_TextEditorProxy_DeleteForwardFunc | Function triggered when the input method deletes text to the right of the cursor. |
| [typedef void (*OH_TextEditorProxy_DeleteBackwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)](#oh_texteditorproxy_deletebackwardfunc) | OH_TextEditorProxy_DeleteBackwardFunc | Function triggered when the input method deletes text to the left of the cursor. |
| [typedef void (*OH_TextEditorProxy_SendKeyboardStatusFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_KeyboardStatus keyboardStatus)](#oh_texteditorproxy_sendkeyboardstatusfunc) | OH_TextEditorProxy_SendKeyboardStatusFunc | Function triggered when the input method reports the keyboard status. |
| [typedef void (*OH_TextEditorProxy_SendEnterKeyFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_EnterKeyType enterKeyType)](#oh_texteditorproxy_sendenterkeyfunc) | OH_TextEditorProxy_SendEnterKeyFunc | Function triggered when the input method sends the Enter key. |
| [typedef void (*OH_TextEditorProxy_MoveCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_Direction direction)](#oh_texteditorproxy_movecursorfunc) | OH_TextEditorProxy_MoveCursorFunc | Function triggered when cursor movement is initiated via the input method. |
| [typedef void (*OH_TextEditorProxy_HandleSetSelectionFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t start, int32_t end)](#oh_texteditorproxy_handlesetselectionfunc) | OH_TextEditorProxy_HandleSetSelectionFunc | Function triggered when the input method requests text selection. |
| [typedef void (*OH_TextEditorProxy_HandleExtendActionFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_ExtendAction action)](#oh_texteditorproxy_handleextendactionfunc) | OH_TextEditorProxy_HandleExtendActionFunc | Function triggered when the input method sends an extended editing action. |
| [typedef void (*OH_TextEditorProxy_GetLeftTextOfCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length)](#oh_texteditorproxy_getlefttextofcursorfunc) | OH_TextEditorProxy_GetLeftTextOfCursorFunc | Function triggered when the input method obtains text to the left of the cursor. |
| [typedef void (*OH_TextEditorProxy_GetRightTextOfCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length)](#oh_texteditorproxy_getrighttextofcursorfunc) | OH_TextEditorProxy_GetRightTextOfCursorFunc | Function triggered when the input method obtains text to the right of the cursor. |
| [typedef int32_t (*OH_TextEditorProxy_GetTextIndexAtCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy)](#oh_texteditorproxy_gettextindexatcursorfunc) | OH_TextEditorProxy_GetTextIndexAtCursorFunc | Function triggered when the input method obtains the text index at the cursor position in the input box. |
| [typedef int32_t (*OH_TextEditorProxy_ReceivePrivateCommandFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)](#oh_texteditorproxy_receiveprivatecommandfunc) | OH_TextEditorProxy_ReceivePrivateCommandFunc | Function triggered when the input method app sends a private data command. |
| [typedef int32_t (*OH_TextEditorProxy_SetPreviewTextFunc)(InputMethod_TextEditorProxy *textEditorProxy, const char16_t text[], size_t length, int32_t start, int32_t end)](#oh_texteditorproxy_setpreviewtextfunc) | OH_TextEditorProxy_SetPreviewTextFunc | Function triggered when the input method sets preview text. |
| [typedef void (*OH_TextEditorProxy_FinishTextPreviewFunc)(InputMethod_TextEditorProxy *textEditorProxy)](#oh_texteditorproxy_finishtextpreviewfunc) | OH_TextEditorProxy_FinishTextPreviewFunc | Function triggered when the input method terminates text preview. |
| [InputMethod_TextEditorProxy *OH_TextEditorProxy_Create(void)](#oh_texteditorproxy_create) | - | Creates a new **InputMethod_TextEditorProxy** instance. |
| [void OH_TextEditorProxy_Destroy(InputMethod_TextEditorProxy *proxy)](#oh_texteditorproxy_destroy) | - | Destroys an **InputMethod_TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetGetTextConfigFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextConfigFunc getTextConfigFunc)](#oh_texteditorproxy_setgettextconfigfunc) | - | Registers the **GetTextConfigFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetInsertTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_InsertTextFunc insertTextFunc)](#oh_texteditorproxy_setinserttextfunc) | - | Registers the **InsertTextFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetDeleteForwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteForwardFunc deleteForwardFunc)](#oh_texteditorproxy_setdeleteforwardfunc) | - | Registers the **DeleteForwardFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetDeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteBackwardFunc deleteBackwardFunc)](#oh_texteditorproxy_setdeletebackwardfunc) | - | Registers the **DeleteBackwardFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetSendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendKeyboardStatusFunc sendKeyboardStatusFunc)](#oh_texteditorproxy_setsendkeyboardstatusfunc) | - | Registers the **SendKeyboardStatusFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetSendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendEnterKeyFunc sendEnterKeyFunc)](#oh_texteditorproxy_setsendenterkeyfunc) | - | Registers the **SendEnterKeyFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetMoveCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_MoveCursorFunc moveCursorFunc)](#oh_texteditorproxy_setmovecursorfunc) | - | Registers the **MoveCursorFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetHandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleSetSelectionFunc handleSetSelectionFunc)](#oh_texteditorproxy_sethandlesetselectionfunc) | - | Registers the **HandleSetSelectionFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetHandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleExtendActionFunc handleExtendActionFunc)](#oh_texteditorproxy_sethandleextendactionfunc) | - | Registers the **HandleExtendActionFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetGetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetLeftTextOfCursorFunc getLeftTextOfCursorFunc)](#oh_texteditorproxy_setgetlefttextofcursorfunc) | - | Registers the **GetLeftTextOfCursorFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetGetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetRightTextOfCursorFunc getRightTextOfCursorFunc)](#oh_texteditorproxy_setgetrighttextofcursorfunc) | - | Registers the **GetRightTextOfCursorFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetGetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextIndexAtCursorFunc getTextIndexAtCursorFunc)](#oh_texteditorproxy_setgettextindexatcursorfunc) | - | Registers the **GetTextIndexAtCursorFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_ReceivePrivateCommandFunc receivePrivateCommandFunc)](#oh_texteditorproxy_setreceiveprivatecommandfunc) | - | Registers the **ReceivePrivateCommandFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetSetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SetPreviewTextFunc setPreviewTextFunc)](#oh_texteditorproxy_setsetpreviewtextfunc) | - | Registers the **SetPreviewTextFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetFinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_FinishTextPreviewFunc finishTextPreviewFunc)](#oh_texteditorproxy_setfinishtextpreviewfunc) | - | Registers the **FinishTextPreviewFunc** callback for the **TextEditorProxy** instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetGetTextConfigFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextConfigFunc *getTextConfigFunc)](#oh_texteditorproxy_getgettextconfigfunc) | - | Obtains the **GetTextConfigFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetInsertTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_InsertTextFunc *insertTextFunc)](#oh_texteditorproxy_getinserttextfunc) | - | Obtains the **InsertTextFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetDeleteForwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteForwardFunc *deleteForwardFunc)](#oh_texteditorproxy_getdeleteforwardfunc) | - | Obtains the **DeleteForwardFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetDeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteBackwardFunc *deleteBackwardFunc)](#oh_texteditorproxy_getdeletebackwardfunc) | - | Obtains the **DeleteBackwardFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetSendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendKeyboardStatusFunc *sendKeyboardStatusFunc)](#oh_texteditorproxy_getsendkeyboardstatusfunc) | - | Obtains the **SendKeyboardStatusFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetSendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendEnterKeyFunc *sendEnterKeyFunc)](#oh_texteditorproxy_getsendenterkeyfunc) | - | Obtains the **SendEnterKeyFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetMoveCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_MoveCursorFunc *moveCursorFunc)](#oh_texteditorproxy_getmovecursorfunc) | - | Obtains the **MoveCursorFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetHandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleSetSelectionFunc *handleSetSelectionFunc)](#oh_texteditorproxy_gethandlesetselectionfunc) | - | Obtains the **HandleSetSelectionFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetHandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleExtendActionFunc *handleExtendActionFunc)](#oh_texteditorproxy_gethandleextendactionfunc) | - | Obtains the **HandleExtendActionFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetGetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetLeftTextOfCursorFunc *getLeftTextOfCursorFunc)](#oh_texteditorproxy_getgetlefttextofcursorfunc) | - | Obtains the **GetLeftTextOfCursorFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetGetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetRightTextOfCursorFunc *getRightTextOfCursorFunc)](#oh_texteditorproxy_getgetrighttextofcursorfunc) | - | Obtains the **GetRightTextOfCursorFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetGetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextIndexAtCursorFunc *getTextIndexAtCursorFunc)](#oh_texteditorproxy_getgettextindexatcursorfunc) | - | Obtains the **GetTextIndexAtCursorFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_ReceivePrivateCommandFunc *receivePrivateCommandFunc)](#oh_texteditorproxy_getreceiveprivatecommandfunc) | - | Obtains the **ReceivePrivateCommandFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetSetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SetPreviewTextFunc *setPreviewTextFunc)](#oh_texteditorproxy_getsetpreviewtextfunc) | - | Obtains the **SetPreviewTextFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetFinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_FinishTextPreviewFunc *finishTextPreviewFunc)](#oh_texteditorproxy_getfinishtextpreviewfunc) | - | Obtains the **FinishTextPreviewFunc** function from **TextEditorProxy**. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetCallbackInMainThread(InputMethod_TextEditorProxy *proxy, bool isCallbackInMainThread)](#oh_texteditorproxy_setcallbackinmainthread) | - | Configures the execution thread policy for callback functions. |

## Function Description

### OH_TextEditorProxy_GetTextConfigFunc()

```c
typedef void (*OH_TextEditorProxy_GetTextConfigFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_TextConfig *config)
```

**Description**

Callback triggered when the input method obtains the input box configuration. You need to implement this function and set the configuration information of the edit box (input type, Enter key type, cursor information, etc.) for the **config** parameter in the function. The input method framework adjusts the keyboard layout and input behavior accordingly.

Usage scenarios: When the input method app needs to obtain the configuration information of the edit box, the system automatically invokes this callback. This callback is one of the core callbacks for interaction between the input method and the editor, and must be implemented.

Use effect: After the callback returns, the input method framework reads the configuration information in **config** and adjusts the keyboard behavior accordingly. The memory of the **config** parameter is released after the callback returns and cannot be accessed again.

Preconditions: This callback must be set to **TextEditorProxy** through [OH_TextEditorProxy_SetGetTextConfigFunc](#oh_texteditorproxy_setgettextconfigfunc), and registration must be completed through [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). The execution thread of this callback is determined by the thread that calls **Attach**, and is not affected by [OH_TextEditorProxy_SetCallbackInMainThread](#oh_texteditorproxy_setcallbackinmainthread).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance for the current callback. It identifies the proxy object that triggers the callback. |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) *config | Output pointer to the [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance. In the function implementation, set its configuration properties (input type, Enter key type, cursor information, etc.) for the input box configuration. This pointer is valid only during callback execution. After the callback returns, the memory will be released and must not be accessed again. You must complete all configuration operations inside the callback and must not continue to use this pointer outside the callback. |

### OH_TextEditorProxy_InsertTextFunc()

```c
typedef void (*OH_TextEditorProxy_InsertTextFunc)(InputMethod_TextEditorProxy *textEditorProxy, const char16_t *text, size_t length)
```

**Description**

Callback triggered when the input method app inserts text. You need to implement this function to insert the text content specified by the **text** parameter at the cursor position of the edit box.

Usage scenarios: When the input method app inserts text into the edit box (for example, when the user selects a candidate word or enters a character), the system automatically invokes this callback. This callback is one of the core callbacks for interaction between the input method and the editor, and must be implemented.

Use effect: After the callback is executed, the edit box should insert the specified text at the cursor position and update the text content and cursor position.

Preconditions: This callback must be set to **TextEditorProxy** through [OH_TextEditorProxy_SetInsertTextFunc](#oh_texteditorproxy_setinserttextfunc), and registration must be completed through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| const char16_t *text | Input pointer to the text content to be inserted, encoded in UTF-16. This pointer is valid only during callback execution. After the callback returns, the memory is released and must not be accessed again. You should complete the necessary data copy or processing inside the callback. |
| size_t length | Input parameter, indicating the number of characters to insert (unit: number of char16_t characters). Value range: greater than 0. |

### OH_TextEditorProxy_DeleteForwardFunc()

```c
typedef void (*OH_TextEditorProxy_DeleteForwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)
```

**Description**

Callback triggered when the input method deletes the text to the right of the cursor. You need to implement this function to delete the specified number of characters to the right from the cursor position.

Usage scenarios: This callback is automatically invoked when the input method app requests to delete the text to the right of the cursor (for example, when the user performs a forward delete operation in the input method).

Use effect: After the callback execution, the edit box should delete the specified number of characters to the right from the cursor position and update the text content and cursor position.

Preconditions: This callback must be set for **TextEditorProxy** through [OH_TextEditorProxy_SetDeleteForwardFunc](#oh_texteditorproxy_setdeleteforwardfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| int32_t length | Input parameter, indicating the number of characters to delete (unit: character count). Value range: greater than 0. Value principle: if **length** exceeds the length of the existing text to the right of the cursor, delete runs to the end of the text; otherwise, the specified number of characters are deleted. |

### OH_TextEditorProxy_DeleteBackwardFunc()

```c
typedef void (*OH_TextEditorProxy_DeleteBackwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)
```

**Description**

Callback triggered when the input method deletes the text to the left of the cursor. You need to implement this function to delete the specified number of characters to the left from the cursor position.

Usage scenarios: When the input method app requests to delete text to the left of the cursor (for example, when the user performs a backspace deletion in the input method), the system automatically invokes this callback.

Use effect: After the callback is executed, the edit box should delete the specified number of characters to the left of the cursor position and update the text content and cursor position.

Preconditions: This callback must be set to **TextEditorProxy** via [OH_TextEditorProxy_SetDeleteBackwardFunc](#oh_texteditorproxy_setdeletebackwardfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| int32_t length | Input parameter, indicating the number of characters to delete (unit: number of characters). Value range: greater than 0. Value principle: if **length** exceeds the length of the existing text to the left of the cursor, delete runs to the beginning of the text; otherwise, the specified number of characters are deleted. |

### OH_TextEditorProxy_SendKeyboardStatusFunc()

```c
typedef void (*OH_TextEditorProxy_SendKeyboardStatusFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_KeyboardStatus keyboardStatus)
```

**Description**

Callback triggered when the input method reports the keyboard status. You need to implement this function to update the edit box's awareness of the keyboard status based on the **keyboardStatus** parameter.

Usage scenarios: When the keyboard status of the input method app changes (shown or hidden), the system automatically invokes this callback to notify the edit box of the current keyboard status.

Use effect: After the callback is executed, the edit box should update its awareness of keyboard visibility accordingly, for example, adjusting the avoidance strategy or UI layout.

Preconditions: This callback must be set to **TextEditorProxy** via [OH_TextEditorProxy_SetSendKeyboardStatusFunc](#oh_texteditorproxy_setsendkeyboardstatusfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| [InputMethod_KeyboardStatus](capi-inputmethod-types-capi-h.md#inputmethod_keyboardstatus) keyboardStatus | Input parameter, indicating the keyboard status. Value range: [InputMethod_KeyboardStatus](capi-inputmethod-types-capi-h.md#inputmethod_keyboardstatus) enum values (**IME_KEYBOARD_STATUS_NONE=0**, **IME_KEYBOARD_STATUS_HIDE=1**, and **IME_KEYBOARD_STATUS_SHOW=2**). Use effect: when set to **IME_KEYBOARD_STATUS_SHOW**, it indicates that the keyboard is shown; when set to **IME_KEYBOARD_STATUS_HIDE**, it indicates that the keyboard is hidden. |

### OH_TextEditorProxy_SendEnterKeyFunc()

```c
typedef void (*OH_TextEditorProxy_SendEnterKeyFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_EnterKeyType enterKeyType)
```

**Description**

Callback triggered when the input method sends the Enter key. You need to implement this function to perform the corresponding Enter key action based on the **enterKeyType** parameter.

Usage scenarios: When the input method app notifies the edit box of an Enter key event, the system automatically invokes this callback.

Use effect: After the callback is executed, the edit box should perform the corresponding Enter key behavior (such as Search, Send, Done, etc.).

Preconditions: This callback must be set to the **TextEditorProxy** through [OH_TextEditorProxy_SetSendEnterKeyFunc](#oh_texteditorproxy_setsendenterkeyfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) enterKeyType | Input parameter, indicating the Enter key type. Value range: [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) enum values. Use effect: different types correspond to different Enter key behaviors, for example, **IME_ENTER_KEY_GO** indicates **"Go"** and **IME_ENTER_KEY_SEARCH** indicates **"Search"**. |

### OH_TextEditorProxy_MoveCursorFunc()

```c
typedef void (*OH_TextEditorProxy_MoveCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_Direction direction)
```

**Description**

Callback triggered when the input method moves the cursor. You need to implement this function to move the cursor position in the edit box based on the **direction** parameter.

Usage scenarios: When the input method app requests to move the cursor, the system automatically invokes this callback.

Use effect: After the callback is executed, the edit box should move the cursor position accordingly and update the cursor display.

Preconditions: This callback must be set to the **TextEditorProxy** through [OH_TextEditorProxy_SetMoveCursorFunc](#oh_texteditorproxy_setmovecursorfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| [InputMethod_Direction](capi-inputmethod-types-capi-h.md#inputmethod_direction) direction | Input parameter, indicating the cursor movement direction. Value range: [InputMethod_Direction](capi-inputmethod-types-capi-h.md#inputmethod_direction) enum values. Use effect: different directions correspond to different cursor movement behaviors, for example, **IME_DIRECTION_UP** indicates moving up, **IME_DIRECTION_DOWN** indicates moving down, **IME_DIRECTION_LEFT** indicates moving left, and **IME_DIRECTION_RIGHT** indicates moving right. |

### OH_TextEditorProxy_HandleSetSelectionFunc()

```c
typedef void (*OH_TextEditorProxy_HandleSetSelectionFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t start, int32_t end)
```

**Description**

Callback triggered when the input method requests text selection. You need to implement this function to select the specified range of text in the text box based on the **start** and **end** parameters.

Usage scenarios: When the input method app requests to select a range of text in the text box, the system automatically invokes this callback.

Use effect: After the callback is executed, the text box should select the text from **start** to **end** and update the selection state and UI display.

Preconditions: This callback must be set to **TextEditorProxy** through [OH_TextEditorProxy_SetHandleSetSelectionFunc](#oh_texteditorproxy_sethandlesetselectionfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| int32_t start | Input parameter, indicating the start position of the selected text (unit: character offset, counted from 0). Value rule: **start** must be greater than or equal to 0 and less than or equal to **end**. |
| int32_t end | Input parameter, indicating the end position of the selected text (unit: character offset, counted from 0). Value rule: **end** must be greater than or equal to **start** and less than the total text length. |

### OH_TextEditorProxy_HandleExtendActionFunc()

```c
typedef void (*OH_TextEditorProxy_HandleExtendActionFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_ExtendAction action)
```

**Description**

Callback triggered when the input method sends an extended editing operation. You need to implement this function to perform the corresponding extended editing operation based on the action parameter.

Usage scenarios: When the input method app requests an extended editing operation (such as cut, copy, or select all), the system automatically invokes this callback.

Use effect: After the callback is executed, the editor should perform the corresponding extended editing action accordingly.

Preconditions: This callback must be set to the **TextEditorProxy** through [OH_TextEditorProxy_SetHandleExtendActionFunc](#oh_texteditorproxy_sethandleextendactionfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| [InputMethod_ExtendAction](capi-inputmethod-types-capi-h.md#inputmethod_extendaction) action | Input parameter, extended editing action. Value range: [InputMethod_ExtendAction](capi-inputmethod-types-capi-h.md#inputmethod_extendaction) enum values. Use effect: Different actions correspond to different editing behaviors. For example, **IME_EXTEND_ACTION_SELECT_ALL** indicates select all, **IME_EXTEND_ACTION_CUT** indicates cut, and **IME_EXTEND_ACTION_COPY** indicates copy. |

### OH_TextEditorProxy_GetLeftTextOfCursorFunc()

```c
typedef void (*OH_TextEditorProxy_GetLeftTextOfCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length)
```

**Description**

Callback triggered when the input method obtains the text to the left of the cursor. You must implement this function to write the specified number of characters to the left of the cursor into the **text** parameter and write the actual number of characters into the **length** parameter.

Usage scenarios: When the input method app needs to obtain the text to the left of the cursor (for example, for predictive input or context analysis), the system automatically invokes this callback.

Use effect: After the callback returns, the input method app reads the data in **text** and **length** for context analysis.

Preconditions: This callback must be set to **TextEditorProxy** through [OH_TextEditorProxy_SetGetLeftTextOfCursorFunc](#oh_texteditorproxy_setgetlefttextofcursorfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| int32_t number | Input parameter, number of characters to obtain (unit: character count). Value range: greater than 0. Value principle: if **number** exceeds the length of existing text to the left of the cursor, all text to the left should be returned. |
| char16_t text[] | Output pointer, text content of the specified length to the left of the cursor, which needs to be assigned in the function implementation. UTF-16 encoding is used. This pointer is valid only during callback execution. After the callback returns, the memory is released and must not be accessed again. You must complete the assignment inside the callback. |
| size_t *length | Output pointer, used to return the actual number of characters obtained (unit: number of char16_t characters). The memory is allocated by the caller (input method framework), and you must assign a value to *length inside the callback. |

### OH_TextEditorProxy_GetRightTextOfCursorFunc()

```c
typedef void (*OH_TextEditorProxy_GetRightTextOfCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length)
```

**Description**

Callback triggered when the input method obtains the text to the right of the cursor. The developer must implement this function to write the specified number of characters to the right of the cursor into the text parameter and write the actual number of characters into the length parameter.

Usage scenarios: When the input method app needs to obtain the text to the right of the cursor, the system automatically invokes this callback.

Use effect: After the callback returns, the input method app reads the data in **text** and **length** for context analysis.

Preconditions: This callback must be set to **TextEditorProxy** via [OH_TextEditorProxy_SetGetRightTextOfCursorFunc](#oh_texteditorproxy_setgetrighttextofcursorfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| int32_t number | Input parameter, number of characters to obtain (unit: number of characters). Value range: greater than 0. Value principle: if number exceeds the length of the remaining text to the right of the cursor, all text on the right should be returned. |
| char16_t text[] | Output pointer, text content of the specified length to the right of the cursor, which needs to be assigned in the function implementation. UTF-16 encoding is used. This pointer is valid only during callback execution. After the callback returns, the memory will be released and must not be accessed again. |
| size_t *length | Output pointer, used to return the number of characters actually obtained (unit: number of char16_t characters). The memory is allocated by the caller, and you need to assign a value to *length inside the callback. |

### OH_TextEditorProxy_GetTextIndexAtCursorFunc()

```c
typedef int32_t (*OH_TextEditorProxy_GetTextIndexAtCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy)
```

**Description**

Callback triggered when the input method obtains the text index of the input box where the cursor is located. You need to implement this function and return the character index position of the cursor in the text of the edit box.

Usage scenarios: When the input method app needs to obtain the precise position of the cursor in the text, the system automatically calls this callback.

Use effect: After the callback returns, the input method app reads the returned index value to locate the context.

Preconditions: This callback must be set to **TextEditorProxy** via [OH_TextEditorProxy_SetGetTextIndexAtCursorFunc](#oh_texteditorproxy_setgettextindexatcursorfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the character index position of the cursor in the text content, with the index starting from 0 (unit: character offset). Value range: greater than or equal to 0 and less than the total text length. |

### OH_TextEditorProxy_ReceivePrivateCommandFunc()

```c
typedef int32_t (*OH_TextEditorProxy_ReceivePrivateCommandFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)
```

**Description**

Callback triggered when the input method app sends private data commands. You must implement this function to process the private command data sent by the input method app.

Usage scenarios: When the input method app sends a private command to the editor through [OH_InputMethodProxy_SendPrivateCommand](capi-inputmethod-inputmethod-proxy-capi-h.md#oh_inputmethodproxy_sendprivatecommand), the system automatically invokes this callback.

Use effect: After the callback returns, the input method app determines whether the command was processed successfully based on the return value.

Preconditions: This callback must be set to **TextEditorProxy** through [OH_TextEditorProxy_SetReceivePrivateCommandFunc](#oh_texteditorproxy_setreceiveprivatecommandfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *privateCommand[] | Input pointer, array of private data commands. This pointer is valid only during callback execution. After the callback returns, the memory will be released and must not be accessed again. You should complete the necessary data copy or processing inside the callback and must not continue using this pointer outside the callback. |
| size_t size | input parameter, number of elements in the private data command array. Value range: greater than 0 and no more than 5. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the processing result of the private data command. **0** indicates success, and a non-zero value indicates failure. |

### OH_TextEditorProxy_SetPreviewTextFunc()

```c
typedef int32_t (*OH_TextEditorProxy_SetPreviewTextFunc)(InputMethod_TextEditorProxy *textEditorProxy, const char16_t text[], size_t length, int32_t start, int32_t end)
```

**Description**

Callback triggered when the input method sets preview text. Preview text is the candidate text display feature of the input method, typically shown when the user enters pinyin or input codes before the Chinese characters are determined. This function is responsible for setting the preview text and its cursor position. It is used together with [OH_TextEditorProxy_FinishTextPreviewFunc](#oh_texteditorproxy_finishtextpreviewfunc): first call **SetPreviewTextFunc** to set the preview text content, and when the user selects a candidate word or cancels the input, call **FinishTextPreviewFunc** to end the preview.

Usage scenarios: When the input method app needs to display candidate text (such as preview text during Pinyin input), the system automatically invokes this callback.

Use effect: After the callback is executed, the edit box should display the text content in preview text style within the range from **start** to **end**, and return the result to the input method.

Preconditions: This callback must be set to **TextEditorProxy** through [OH_TextEditorProxy_SetSetPreviewTextFunc](#oh_texteditorproxy_setsetpreviewtextfunc) and registered through **Attach**. The edit box must enable preview text support in **TextConfig** (**supported**=**true**).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |
| const char16_t text[] | Input pointer, the text content requested to be set as the preview text style, encoded in UTF-16. This pointer is valid only during callback execution. After the callback returns, the memory will be released and must not be accessed again. You should complete the necessary data copy within the callback. |
| size_t length | Input parameter, the number of characters in the preview text (unit: number of char16_t characters). |
| int32_t start | Input parameter, the starting cursor position of the preview text (unit: character offset, relative to the beginning of the text). Value rule: **start** should be greater than or equal to 0 and less than or equal to **end**. |
| int32_t end | Input parameter, the ending cursor position of the preview text (unit: character offset, relative to the beginning of the text). Value rule: **end** should be greater than or equal to **start** and less than the total text length. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the processing result. The value **0** indicates success, and a non-zero value indicates failure. |

### OH_TextEditorProxy_FinishTextPreviewFunc()

```c
typedef void (*OH_TextEditorProxy_FinishTextPreviewFunc)(InputMethod_TextEditorProxy *textEditorProxy)
```

**Description**

Callback triggered when the input method finishes preview text. This function is used to clear the preview text state, and is typically invoked when the user selects a candidate word (confirms input) or cancels input. It is used together with [OH_TextEditorProxy_SetPreviewTextFunc](#oh_texteditorproxy_setpreviewtextfunc).

Usage scenarios: When the input method app needs to end the preview text state, the system automatically invokes this callback.

Use effect: After callback execution, the edit box should clear the preview text display state and restore normal text display.

Preconditions: This callback must be set to **TextEditorProxy** through [OH_TextEditorProxy_SetFinishTextPreviewFunc](#oh_texteditorproxy_setfinishtextpreviewfunc) and registered through **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Input pointer to the **TextEditorProxy** instance for the current callback. |

### OH_TextEditorProxy_Create()

```c
InputMethod_TextEditorProxy *OH_TextEditorProxy_Create(void)
```

**Description**

Creates a new [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance. After creation, register callback functions through the **Set*Func** APIs, and then complete attachment and registration through [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach).

Usage scenarios: Call this function when an app needs to create a text editor proxy object to receive input method requests and notifications.

Use effect: If the creation succeeds, a new **TextEditorProxy** instance pointer is returned, and callback functions can be registered through the **Set*Func** APIs afterward.

Lifecycle management: The returned object must be destroyed through [OH_TextEditorProxy_Destroy](#oh_texteditorproxy_destroy). **Create** and **Destroy** must be used in pairs. Failure to destroy it will cause memory leaks. The same instance can be destroyed only once.

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) * | If the creation is successful, returns a pointer to the newly created [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance. If the creation fails, returns **NULL**. A possible cause of failure is insufficient memory. When **NULL** is returned, check the system memory status. After use, the returned pointer must be destroyed by [OH_TextEditorProxy_Destroy](#oh_texteditorproxy_destroy), and the pointer should be set to **NULL** after destruction to avoid misuse. |

### OH_TextEditorProxy_Destroy()

```c
void OH_TextEditorProxy_Destroy(InputMethod_TextEditorProxy *proxy)
```

**Description**

Destroys an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance. After destruction, the proxy pointer can no longer be used. It is recommended that you set the pointer to **NULL** to avoid misuse.

Usage scenarios: Call this function to release resources when the app no longer needs the **TextEditorProxy** object (for example, after **Detach** is called or when the app exits).

Use effect: The proxy object is released and its internal resources are reclaimed. After that, no function can be called through the proxy pointer.

Lifecycle management: Used in pairs with [OH_TextEditorProxy_Create](#oh_texteditorproxy_create). The object returned by **Create** must eventually be released through **Destroy**. The same instance can be destroyed only once and cannot be destroyed repeatedly. If proxy is null, the function does nothing.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance to be destroyed. If **NULL** is passed in, the function does nothing and does not cause a crash. After destruction, this pointer becomes invalid. It is recommended that you set it to **NULL**. |

### OH_TextEditorProxy_SetGetTextConfigFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetGetTextConfigFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextConfigFunc getTextConfigFunc)
```

**Description**

Sets the [OH_TextEditorProxy_GetTextConfigFunc](#oh_texteditorproxy_gettextconfigfunc) function to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach** is called. Callbacks set after **Attach** will not be invoked by the input method.

Usage scenarios: Call this function when the app needs to register the **GetTextConfigFunc** callback to respond to the input method's request for configuration.

Use effect: After the setting succeeds, the **GetTextConfigFunc** callback is registered to **TextEditorProxy**. After **Attach** is called, this callback is automatically triggered when the input method requests configuration.

Preconditions: **proxy** must be created through [OH_TextEditorProxy_Create](#oh_texteditorproxy_create) first.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance to be set. It cannot be **NULL**. If **NULL** is passed in, **IME_ERR_NULL_POINTER** is returned. |
| [OH_TextEditorProxy_GetTextConfigFunc](#oh_texteditorproxy_gettextconfigfunc) getTextConfigFunc | Input parameter, indicating the callback function [OH_TextEditorProxy_GetTextConfigFunc](#oh_texteditorproxy_gettextconfigfunc) to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **proxy** or **getTextConfigFunc** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetInsertTextFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetInsertTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_InsertTextFunc insertTextFunc)
```

**Description**

Sets the [OH_TextEditorProxy_InsertTextFunc](#oh_texteditorproxy_inserttextfunc) function to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

Usage scenarios: Call this function when the app needs to register the **InsertTextFunc** callback to respond to the input method's request to insert text.

Use effect: After the setting succeeds, the **InsertTextFunc** callback is registered to **TextEditorProxy**. After **Attach** is called, this callback is automatically triggered when the input method requests to insert text.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_InsertTextFunc](#oh_texteditorproxy_inserttextfunc) insertTextFunc | Input parameter, indicating the callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetDeleteForwardFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetDeleteForwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteForwardFunc deleteForwardFunc)
```

**Description**

Sets the [OH_TextEditorProxy_DeleteForwardFunc](#oh_texteditorproxy_deleteforwardfunc) function to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

Usage scenarios: Call this function when the app needs to register the **DeleteForwardFunc** callback to respond to the input method's request to delete text to the right of the cursor.

Use effect: After the setting succeeds, the **DeleteForwardFunc** callback is registered to **TextEditorProxy**. After **Attach** is called, this callback is automatically triggered when the input method requests to delete text to the right of the cursor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_DeleteForwardFunc](#oh_texteditorproxy_deleteforwardfunc) deleteForwardFunc | Input parameter, indicating the callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetDeleteBackwardFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetDeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteBackwardFunc deleteBackwardFunc)
```

**Description**

Sets the [OH_TextEditorProxy_DeleteBackwardFunc](#oh_texteditorproxy_deletebackwardfunc) function into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

Usage scenarios: Call this function when the app needs to register the **DeleteBackwardFunc** callback to respond to the input method's request to delete text to the left of the cursor.

Use effect: After the setting succeeds, the **DeleteBackwardFunc** callback is registered in **TextEditorProxy**. After **Attach** is called, this callback is automatically triggered when the input method requests deletion of text to the left of the cursor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_DeleteBackwardFunc](#oh_texteditorproxy_deletebackwardfunc) deleteBackwardFunc | Input parameter, indicating the callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetSendKeyboardStatusFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetSendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendKeyboardStatusFunc sendKeyboardStatusFunc)
```

**Description**

Sets the [OH_TextEditorProxy_SendKeyboardStatusFunc](#oh_texteditorproxy_sendkeyboardstatusfunc) function into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_SendKeyboardStatusFunc](#oh_texteditorproxy_sendkeyboardstatusfunc) sendKeyboardStatusFunc | Input parameter, indicating the callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetSendEnterKeyFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetSendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendEnterKeyFunc sendEnterKeyFunc)
```

**Description**

Sets the [OH_TextEditorProxy_SendEnterKeyFunc](#oh_texteditorproxy_sendenterkeyfunc) function into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_SendEnterKeyFunc](#oh_texteditorproxy_sendenterkeyfunc) sendEnterKeyFunc | Input parameter, indicating the callback function to be set to proxy. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetMoveCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetMoveCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_MoveCursorFunc moveCursorFunc)
```

**Description**

Sets the function [OH_TextEditorProxy_MoveCursorFunc](#oh_texteditorproxy_movecursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_MoveCursorFunc](#oh_texteditorproxy_movecursorfunc) moveCursorFunc | Input parameter, the callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetHandleSetSelectionFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetHandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleSetSelectionFunc handleSetSelectionFunc)
```

**Description**

Sets the function [OH_TextEditorProxy_HandleSetSelectionFunc](#oh_texteditorproxy_handlesetselectionfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_HandleSetSelectionFunc](#oh_texteditorproxy_handlesetselectionfunc) handleSetSelectionFunc | Input parameter, indicating the callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetHandleExtendActionFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetHandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleExtendActionFunc handleExtendActionFunc)
```

**Description**

Sets the function [OH_TextEditorProxy_HandleExtendActionFunc](#oh_texteditorproxy_handleextendactionfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_HandleExtendActionFunc](#oh_texteditorproxy_handleextendactionfunc) handleExtendActionFunc | Input parameter, indicating the callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetGetLeftTextOfCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetGetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetLeftTextOfCursorFunc getLeftTextOfCursorFunc)
```

**Description**

Sets the function [OH_TextEditorProxy_GetLeftTextOfCursorFunc](#oh_texteditorproxy_getlefttextofcursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_GetLeftTextOfCursorFunc](#oh_texteditorproxy_getlefttextofcursorfunc) getLeftTextOfCursorFunc | Input parameter, indicating the callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetGetRightTextOfCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetGetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetRightTextOfCursorFunc getRightTextOfCursorFunc)
```

**Description**

Sets the function [OH_TextEditorProxy_GetRightTextOfCursorFunc](#oh_texteditorproxy_getrighttextofcursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_GetRightTextOfCursorFunc](#oh_texteditorproxy_getrighttextofcursorfunc) getRightTextOfCursorFunc | Input parameter, callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetGetTextIndexAtCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetGetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextIndexAtCursorFunc getTextIndexAtCursorFunc)
```

**Description**

Sets the [OH_TextEditorProxy_GetTextIndexAtCursorFunc](#oh_texteditorproxy_gettextindexatcursorfunc) function into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_GetTextIndexAtCursorFunc](#oh_texteditorproxy_gettextindexatcursorfunc) getTextIndexAtCursorFunc | Input parameter, callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetReceivePrivateCommandFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_ReceivePrivateCommandFunc receivePrivateCommandFunc)
```

**Description**

Sets the [OH_TextEditorProxy_ReceivePrivateCommandFunc](#oh_texteditorproxy_receiveprivatecommandfunc) function into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_ReceivePrivateCommandFunc](#oh_texteditorproxy_receiveprivatecommandfunc) receivePrivateCommandFunc | Input parameter, callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetSetPreviewTextFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetSetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SetPreviewTextFunc setPreviewTextFunc)
```

**Description**

Sets the [OH_TextEditorProxy_SetPreviewTextFunc](#oh_texteditorproxy_setpreviewtextfunc) function into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_SetPreviewTextFunc](#oh_texteditorproxy_setpreviewtextfunc) setPreviewTextFunc | Input parameter, callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetFinishTextPreviewFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetFinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_FinishTextPreviewFunc finishTextPreviewFunc)
```

**Description**

Sets the [OH_TextEditorProxy_FinishTextPreviewFunc](#oh_texteditorproxy_finishtextpreviewfunc) function into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This setting must be completed before **Attach**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be set. It cannot be **NULL**. |
| [OH_TextEditorProxy_FinishTextPreviewFunc](#oh_texteditorproxy_finishtextpreviewfunc) finishTextPreviewFunc | Input parameter, callback function to be set to the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetGetTextConfigFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetGetTextConfigFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextConfigFunc *getTextConfigFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_GetTextConfigFunc](#oh_texteditorproxy_gettextconfigfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_GetTextConfigFunc](#oh_texteditorproxy_gettextconfigfunc) *getTextConfigFunc | Output pointer, indicating the function pointer obtained from the **proxy**. The memory is allocated by the caller. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetInsertTextFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetInsertTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_InsertTextFunc *insertTextFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_InsertTextFunc](#oh_texteditorproxy_inserttextfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_InsertTextFunc](#oh_texteditorproxy_inserttextfunc) *insertTextFunc | Output pointer, indicating the function pointer obtained from the **proxy**. The memory is allocated by the caller. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetDeleteForwardFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetDeleteForwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteForwardFunc *deleteForwardFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_DeleteForwardFunc](#oh_texteditorproxy_deleteforwardfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_DeleteForwardFunc](#oh_texteditorproxy_deleteforwardfunc) *deleteForwardFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetDeleteBackwardFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetDeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteBackwardFunc *deleteBackwardFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_DeleteBackwardFunc](#oh_texteditorproxy_deletebackwardfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_DeleteBackwardFunc](#oh_texteditorproxy_deletebackwardfunc) *deleteBackwardFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetSendKeyboardStatusFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetSendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendKeyboardStatusFunc *sendKeyboardStatusFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_SendKeyboardStatusFunc](#oh_texteditorproxy_sendkeyboardstatusfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_SendKeyboardStatusFunc](#oh_texteditorproxy_sendkeyboardstatusfunc) *sendKeyboardStatusFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetSendEnterKeyFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetSendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendEnterKeyFunc *sendEnterKeyFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_SendEnterKeyFunc](#oh_texteditorproxy_sendenterkeyfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_SendEnterKeyFunc](#oh_texteditorproxy_sendenterkeyfunc) *sendEnterKeyFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetMoveCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetMoveCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_MoveCursorFunc *moveCursorFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_MoveCursorFunc](#oh_texteditorproxy_movecursorfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_MoveCursorFunc](#oh_texteditorproxy_movecursorfunc) *moveCursorFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetHandleSetSelectionFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetHandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleSetSelectionFunc *handleSetSelectionFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_HandleSetSelectionFunc](#oh_texteditorproxy_handlesetselectionfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_HandleSetSelectionFunc](#oh_texteditorproxy_handlesetselectionfunc) *handleSetSelectionFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetHandleExtendActionFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetHandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleExtendActionFunc *handleExtendActionFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_HandleExtendActionFunc](#oh_texteditorproxy_handleextendactionfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_HandleExtendActionFunc](#oh_texteditorproxy_handleextendactionfunc) *handleExtendActionFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetGetLeftTextOfCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetGetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetLeftTextOfCursorFunc *getLeftTextOfCursorFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_GetLeftTextOfCursorFunc](#oh_texteditorproxy_getlefttextofcursorfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_GetLeftTextOfCursorFunc](#oh_texteditorproxy_getlefttextofcursorfunc) *getLeftTextOfCursorFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetGetRightTextOfCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetGetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetRightTextOfCursorFunc *getRightTextOfCursorFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_GetRightTextOfCursorFunc](#oh_texteditorproxy_getrighttextofcursorfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_GetRightTextOfCursorFunc](#oh_texteditorproxy_getrighttextofcursorfunc) *getRightTextOfCursorFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetGetTextIndexAtCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetGetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextIndexAtCursorFunc *getTextIndexAtCursorFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_GetTextIndexAtCursorFunc](#oh_texteditorproxy_gettextindexatcursorfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_GetTextIndexAtCursorFunc](#oh_texteditorproxy_gettextindexatcursorfunc) *getTextIndexAtCursorFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetReceivePrivateCommandFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_ReceivePrivateCommandFunc *receivePrivateCommandFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_ReceivePrivateCommandFunc](#oh_texteditorproxy_receiveprivatecommandfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_ReceivePrivateCommandFunc](#oh_texteditorproxy_receiveprivatecommandfunc) *receivePrivateCommandFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetSetPreviewTextFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetSetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SetPreviewTextFunc *setPreviewTextFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_SetPreviewTextFunc](#oh_texteditorproxy_setpreviewtextfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_SetPreviewTextFunc](#oh_texteditorproxy_setpreviewtextfunc) *setPreviewTextFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetFinishTextPreviewFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetFinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_FinishTextPreviewFunc *finishTextPreviewFunc)
```

**Description**

Obtains the [OH_TextEditorProxy_FinishTextPreviewFunc](#oh_texteditorproxy_finishtextpreviewfunc) function from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **TextEditorProxy** instance to be read. It cannot be **NULL**. |
| [OH_TextEditorProxy_FinishTextPreviewFunc](#oh_texteditorproxy_finishtextpreviewfunc) *finishTextPreviewFunc | Output pointer, indicating the function pointer obtained from the **proxy**. It cannot be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetCallbackInMainThread()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetCallbackInMainThread(InputMethod_TextEditorProxy *proxy, bool isCallbackInMainThread)
```

**Description**

Configures the execution thread (main thread/IPC thread) for the callback functions of **InputMethod_TextEditorProxy**. This API only controls all callback functions in **InputMethod_TextEditorProxy** except [OH_TextEditorProxy_GetTextConfigFunc](#oh_texteditorproxy_gettextconfigfunc). The execution thread of [OH_TextEditorProxy_GetTextConfigFunc](#oh_texteditorproxy_gettextconfigfunc) is determined by the thread that calls [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach), and is not affected by this API. To ensure that **GetTextConfigFunc** also executes on the main thread, make sure that **Attach** is called on the main thread.

Usage scenarios: When an app needs to avoid multi-thread concurrency issues, it can switch callbacks to the main thread for execution. When an app requires faster callback response, it can keep callbacks executing on the IPC thread.

Use effect: When this API is set to **true**, all callbacks except **GetTextConfigFunc** will be executed on the main thread, avoiding multi-thread concurrency, but time-consuming operations should be avoided inside callbacks. When this API is set to **false**, callbacks are executed on the IPC thread, providing faster response but potentially introducing concurrency issues.

Preconditions: The **proxy** must be created through [OH_TextEditorProxy_Create](#oh_texteditorproxy_create) first. It is recommended that you call this API to configure the thread policy before **Attach** is called.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Input pointer to the **InputMethod_TextEditorProxy** instance to be read. It cannot be **NULL**. If **NULL** is passed in, **IME_ERR_NULL_POINTER** is returned. |
| bool isCallbackInMainThread | Input parameter, thread execution policy. Value range: **true** or **false**. Value principle: When the value is **true**, the callback function is switched to the main thread for execution (used to avoid multi-thread concurrency issues). Avoid performing time-consuming operations in the callback to prevent main thread blocking. When the value is **false**, the callback function is executed on the IPC thread (multi-thread concurrency may occur), with faster response. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Returned when **proxy** is **NULL**.<br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |