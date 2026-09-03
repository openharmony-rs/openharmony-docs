# InputMethod_TextEditorProxy
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c9f68a28229d3fb5da602baa0bfb8e542d407a50 translatedAt=2026-09-02T02:25:48.982Z pushedAt=2026-09-02T07:01:30.714Z -->

```c
typedef struct InputMethod_TextEditorProxy InputMethod_TextEditorProxy
```

## Overview

Represents the proxy class for the input method text editor. It handles the interaction between the input method app and the text editor, provides methods for receiving input method requests and notifications, and is suitable for scenarios requiring bidirectional communication between the input method and the editor. This struct is an opaque type. You cannot directly access its internal members and can only operate on it through the functions provided by this module.

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

**Header file**: [inputmethod_text_editor_proxy_capi.h](capi-inputmethod-text-editor-proxy-capi-h.md)

## Struct Purpose

Represents a proxy object for the interaction between the text editor and the input method app. It uses a callback mechanism to implement bidirectional communication, allowing the input method app to send requests and notifications to the editor. When the input method app sends a request to the editor (such as inserting text, deleting text, or moving the cursor) or a notification (such as a keyboard state change or an Enter key event), the request or notification is processed through the callback functions registered in this proxy object. You need to implement each callback function, register it with **TextEditorProxy** through the **Set*Func** APIs, and then complete the registration through the attach API.

## Lifecycle Management

- Creation: Create a new **InputMethod_TextEditorProxy** instance pointer by calling the [OH_TextEditorProxy_Create](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_create) function. If creation fails, **NULL** is returned, possibly due to insufficient memory.
- Destruction: Destroy an instance by calling the [OH_TextEditorProxy_Destroy](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_destroy) function with the pointer to the instance to be destroyed. After destruction, the pointer cannot be used again. It is recommended that you set the pointer to **NULL** to avoid misuse.
- Paired calls: **OH_TextEditorProxy_Create** and **OH_TextEditorProxy_Destroy** must be used in pairs. Objects created shall eventually be released via the destroy function; otherwise, memory leaks will occur. The same **TextEditorProxy** instance can be destroyed only once and cannot be destroyed repeatedly.
- Usage timing: After creating a **TextEditorProxy**, register callback functions using **Set*Func** APIs first, and then complete attachment registration via [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). Modifying callback function settings after attachment is not recommended.

## Callback Mechanism

**TextEditorProxy** uses a callback function mechanism to implement bidirectional communication between the input method app and the editor:

- Callback registration process: Create **TextEditorProxy** → Register each callback function via **Set*Func** APIs → Complete registration via the attach function.
- Callback trigger timing: When the input method app sends a request or notification to the editor, the system automatically calls the corresponding callback function registered in **TextEditorProxy**.
- Temporary pointers in callback functions: The pointer parameters (such as **text** and **privateCommand**) received in a callback function are valid only during callback execution. After the callback returns, the memory is released and must not be accessed again. You should complete the necessary data copying or processing inside the callback and must not continue to use these pointers outside the callback.
- **GetTextConfigFunc** is not affected by **SetCallbackInMainThread**: The execution thread of [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) is determined by the thread from which [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) is called, and is not affected by [OH_TextEditorProxy_SetCallbackInMainThread](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setcallbackinmainthread). If **GetTextConfigFunc** needs to run on the main thread, ensure that the attach function is called on the main thread.

## Usage Notes

- All **Set*Func** APIs must be called before the attach function is called. Callback functions set after attachment will not be called by the input method.
- Pointer parameters in callback functions are temporary. They cannot be accessed after the callback returns, and data processing must be completed within the callback.
- It is recommended that you register at least the two core callbacks, **GetTextConfigFunc** and **InsertTextFunc**. Otherwise, the input method may not work properly.
- This object is not thread-safe. It is not recommended that you operate the same **TextEditorProxy** object concurrently in a multi-threaded environment. You can switch callbacks to the main thread via [OH_TextEditorProxy_SetCallbackInMainThread](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setcallbackinmainthread) to avoid multi-thread concurrency issues.
- This object is an opaque type. You cannot access its internal members or perform memory operations on it.

Related functions:

- Create/Destroy functions

| Function | Description |
| -- | -- |
| [OH_TextEditorProxy_Create](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_create) | Creates a new **InputMethod_TextEditorProxy** instance. |
| [OH_TextEditorProxy_Destroy](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_destroy) | Destroys an **InputMethod_TextEditorProxy** instance. |

- Callback setting functions (**Set*Func**, must be called before the attach function)

| Function | Description |
| -- | -- |
| [OH_TextEditorProxy_SetGetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgettextconfigfunc) | Sets the **GetTextConfigFunc** callback. |
| [OH_TextEditorProxy_SetInsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setinserttextfunc) | Sets the **InsertTextFunc** callback. |
| [OH_TextEditorProxy_SetDeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeleteforwardfunc) | Sets the **DeleteForwardFunc** callback. |
| [OH_TextEditorProxy_SetDeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeletebackwardfunc) | Sets the **DeleteBackwardFunc** callback. |
| [OH_TextEditorProxy_SetSendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsendkeyboardstatusfunc) | Sets the **SendKeyboardStatusFunc** callback. |
| [OH_TextEditorProxy_SetSendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsendenterkeyfunc) | Sets the **SendEnterKeyFunc** callback. |
| [OH_TextEditorProxy_SetMoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setmovecursorfunc) | Sets the **MoveCursorFunc** callback. |
| [OH_TextEditorProxy_SetHandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sethandlesetselectionfunc) | Sets the **HandleSetSelectionFunc** callback. |
| [OH_TextEditorProxy_SetHandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sethandleextendactionfunc) | Sets the **HandleExtendActionFunc** callback. |
| [OH_TextEditorProxy_SetGetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgetlefttextofcursorfunc) | Sets the **GetLeftTextOfCursorFunc** callback. |
| [OH_TextEditorProxy_SetGetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgetrighttextofcursorfunc) | Sets the **GetRightTextOfCursorFunc** callback. |
| [OH_TextEditorProxy_SetGetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgettextindexatcursorfunc) | Sets the **GetTextIndexAtCursorFunc** callback. |
| [OH_TextEditorProxy_SetReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setreceiveprivatecommandfunc) | Sets the **ReceivePrivateCommandFunc** callback. |
| [OH_TextEditorProxy_SetSetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsetpreviewtextfunc) | Sets the **SetPreviewTextFunc** callback. |
| [OH_TextEditorProxy_SetFinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setfinishtextpreviewfunc) | Sets the **FinishTextPreviewFunc** callback. |

- Callback getting functions (**Get*Func**)

| Function | Description |
| -- | -- |
| [OH_TextEditorProxy_GetGetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getgettextconfigfunc) | Obtains the registered **GetTextConfigFunc** callback. |
| [OH_TextEditorProxy_GetInsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getinserttextfunc) | Obtains the registered **InsertTextFunc** callback. |
| [OH_TextEditorProxy_GetDeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getdeleteforwardfunc) | Obtains the registered **DeleteForwardFunc** callback. |
| [OH_TextEditorProxy_GetDeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getdeletebackwardfunc) | Obtains the registered **DeleteBackwardFunc** callback. |
| [OH_TextEditorProxy_GetSendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getsendkeyboardstatusfunc) | Obtains the registered **SendKeyboardStatusFunc** callback. |
| [OH_TextEditorProxy_GetSendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getsendenterkeyfunc) | Obtains the registered **SendEnterKeyFunc** callback. |
| [OH_TextEditorProxy_GetMoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getmovecursorfunc) | Obtains the registered **MoveCursorFunc** callback. |
| [OH_TextEditorProxy_GetHandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gethandlesetselectionfunc) | Obtains the registered **HandleSetSelectionFunc** callback. |
| [OH_TextEditorProxy_GetHandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gethandleextendactionfunc) | Obtains the registered **HandleExtendActionFunc** callback. |
| [OH_TextEditorProxy_GetGetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getgetlefttextofcursorfunc) | Obtains the registered **GetLeftTextOfCursorFunc** callback. |
| [OH_TextEditorProxy_GetGetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getgetrighttextofcursorfunc) | Obtains the registered **GetRightTextOfCursorFunc** callback. |
| [OH_TextEditorProxy_GetGetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getgettextindexatcursorfunc) | Obtains the registered **GetTextIndexAtCursorFunc** callback. |
| [OH_TextEditorProxy_GetReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getreceiveprivatecommandfunc) | Obtains the registered **ReceivePrivateCommandFunc** callback. |
| [OH_TextEditorProxy_GetSetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getsetpreviewtextfunc) | Obtains the registered **SetPreviewTextFunc** callback. |
| [OH_TextEditorProxy_GetFinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getfinishtextpreviewfunc) | Obtains the registered **FinishTextPreviewFunc** callback. |

Thread configuration functions

| Function | Description |
| -- | -- |
| [OH_TextEditorProxy_SetCallbackInMainThread](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setcallbackinmainthread) | Configures the thread policy for executing callback functions. |

Association relationships:

- Relationship with **InputMethodProxy**: [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) is responsible for sending requests and notifications to the input method service, while **InputMethod_TextEditorProxy** is responsible for receiving requests and notifications from the input method app. The two are associated at the same time when the attach API is called, forming a bidirectional communication channel.
- Relationship with **TextConfig**: [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) is used in the **GetTextConfigFunc** callback to pass the configuration information of the edit box to the input method. When the **GetTextConfigFunc** callback is triggered, you need to assign a value to the **config** parameter within the callback to fill in the configuration information.
