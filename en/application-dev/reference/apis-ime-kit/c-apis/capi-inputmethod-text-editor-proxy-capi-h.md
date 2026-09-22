# inputmethod_text_editor_proxy_capi.h

## Overview

Provides a set of methods for the custom text box developed by the application to obtain notifications and requests from the input method application.

**Include**: <inputmethod/inputmethod_text_editor_proxy_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) | InputMethod_TextEditorProxy | Define the InputMethod_TextEditorProxy structure type.<br> Provides methods for getting requests and notifications from input method. When input method sends request or notification to editor, the methods will be called. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_TextEditorProxy_GetTextConfigFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_TextConfig *config)](#oh_texteditorproxy_gettextconfigfunc) | OH_TextEditorProxy_GetTextConfigFunc | Defines the function called when input method getting text config.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgettextconfigfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_InsertTextFunc)(InputMethod_TextEditorProxy *textEditorProxy, const char16_t *text, size_t length)](#oh_texteditorproxy_inserttextfunc) | OH_TextEditorProxy_InsertTextFunc | Defines the function called when input method inserting text.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetInsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setinserttextfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_DeleteForwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)](#oh_texteditorproxy_deleteforwardfunc) | OH_TextEditorProxy_DeleteForwardFunc | Defines the function called when input method deleting text forward.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetDeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeleteforwardfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_DeleteBackwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)](#oh_texteditorproxy_deletebackwardfunc) | OH_TextEditorProxy_DeleteBackwardFunc | Defines the function called when input method deleting text backward.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetDeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeletebackwardfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_SendKeyboardStatusFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_KeyboardStatus keyboardStatus)](#oh_texteditorproxy_sendkeyboardstatusfunc) | OH_TextEditorProxy_SendKeyboardStatusFunc | Called when input method notifying keyboard status.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetSendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsendkeyboardstatusfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_SendEnterKeyFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_EnterKeyType enterKeyType)](#oh_texteditorproxy_sendenterkeyfunc) | OH_TextEditorProxy_SendEnterKeyFunc | Called when input method sending enter key.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetSendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsendenterkeyfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_MoveCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_Direction direction)](#oh_texteditorproxy_movecursorfunc) | OH_TextEditorProxy_MoveCursorFunc | Called when input method requesting to move cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetMoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setmovecursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_HandleSetSelectionFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t start, int32_t end)](#oh_texteditorproxy_handlesetselectionfunc) | OH_TextEditorProxy_HandleSetSelectionFunc | Called when input method requesting to set selection.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetHandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sethandlesetselectionfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_HandleExtendActionFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_ExtendAction action)](#oh_texteditorproxy_handleextendactionfunc) | OH_TextEditorProxy_HandleExtendActionFunc | Called when input method sending extend action.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetHandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sethandleextendactionfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_GetLeftTextOfCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length)](#oh_texteditorproxy_getlefttextofcursorfunc) | OH_TextEditorProxy_GetLeftTextOfCursorFunc | Called when input method requesting to get left text of cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgetlefttextofcursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_GetRightTextOfCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length)](#oh_texteditorproxy_getrighttextofcursorfunc) | OH_TextEditorProxy_GetRightTextOfCursorFunc | Called when input method requesting to get right text of cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgetrighttextofcursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef int32_t (\*OH_TextEditorProxy_GetTextIndexAtCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy)](#oh_texteditorproxy_gettextindexatcursorfunc) | OH_TextEditorProxy_GetTextIndexAtCursorFunc | Called when input method requesting to get text index at cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgettextindexatcursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef int32_t (\*OH_TextEditorProxy_ReceivePrivateCommandFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)](#oh_texteditorproxy_receiveprivatecommandfunc) | OH_TextEditorProxy_ReceivePrivateCommandFunc | Called when input method sending private command.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setreceiveprivatecommandfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef int32_t (\*OH_TextEditorProxy_SetPreviewTextFunc)(InputMethod_TextEditorProxy *textEditorProxy, const char16_t text[], size_t length, int32_t start, int32_t end)](#oh_texteditorproxy_setpreviewtextfunc) | OH_TextEditorProxy_SetPreviewTextFunc | Called when input method setting preview text.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetSetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsetpreviewtextfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [typedef void (\*OH_TextEditorProxy_FinishTextPreviewFunc)(InputMethod_TextEditorProxy *textEditorProxy)](#oh_texteditorproxy_finishtextpreviewfunc) | OH_TextEditorProxy_FinishTextPreviewFunc | Called when input method finishing preview text.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetFinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setfinishtextpreviewfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration. |
| [InputMethod_TextEditorProxy *OH_TextEditorProxy_Create(void)](#oh_texteditorproxy_create) | - | Create a new [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance. |
| [void OH_TextEditorProxy_Destroy(InputMethod_TextEditorProxy *proxy)](#oh_texteditorproxy_destroy) | - | Destroy a [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance. |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetGetTextConfigFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextConfigFunc getTextConfigFunc)](#oh_texteditorproxy_setgettextconfigfunc) | - | Set function [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetInsertTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_InsertTextFunc insertTextFunc)](#oh_texteditorproxy_setinserttextfunc) | - | Set function [OH_TextEditorProxy_InsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_inserttextfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetDeleteForwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteForwardFunc deleteForwardFunc)](#oh_texteditorproxy_setdeleteforwardfunc) | - | Set function [OH_TextEditorProxy_SetDeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeleteforwardfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetDeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteBackwardFunc deleteBackwardFunc)](#oh_texteditorproxy_setdeletebackwardfunc) | - | Set function [OH_TextEditorProxy_DeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deletebackwardfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetSendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendKeyboardStatusFunc sendKeyboardStatusFunc)](#oh_texteditorproxy_setsendkeyboardstatusfunc) | - | Set function [OH_TextEditorProxy_SendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendkeyboardstatusfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetSendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendEnterKeyFunc sendEnterKeyFunc)](#oh_texteditorproxy_setsendenterkeyfunc) | - | Set function [OH_TextEditorProxy_SendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendenterkeyfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetMoveCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_MoveCursorFunc moveCursorFunc)](#oh_texteditorproxy_setmovecursorfunc) | - | Set function [OH_TextEditorProxy_MoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_movecursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetHandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleSetSelectionFunc handleSetSelectionFunc)](#oh_texteditorproxy_sethandlesetselectionfunc) | - | Set function [OH_TextEditorProxy_HandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handlesetselectionfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetHandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleExtendActionFunc handleExtendActionFunc)](#oh_texteditorproxy_sethandleextendactionfunc) | - | Set function [OH_TextEditorProxy_HandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handleextendactionfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetGetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetLeftTextOfCursorFunc getLeftTextOfCursorFunc)](#oh_texteditorproxy_setgetlefttextofcursorfunc) | - | Set function [OH_TextEditorProxy_GetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getlefttextofcursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetGetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetRightTextOfCursorFunc getRightTextOfCursorFunc)](#oh_texteditorproxy_setgetrighttextofcursorfunc) | - | Set function [OH_TextEditorProxy_GetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getrighttextofcursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetGetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextIndexAtCursorFunc getTextIndexAtCursorFunc)](#oh_texteditorproxy_setgettextindexatcursorfunc) | - | Set function [OH_TextEditorProxy_GetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextindexatcursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_ReceivePrivateCommandFunc receivePrivateCommandFunc)](#oh_texteditorproxy_setreceiveprivatecommandfunc) | - | Set function [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetSetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SetPreviewTextFunc setPreviewTextFunc)](#oh_texteditorproxy_setsetpreviewtextfunc) | - | Set function [OH_TextEditorProxy_SetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setpreviewtextfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetFinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_FinishTextPreviewFunc finishTextPreviewFunc)](#oh_texteditorproxy_setfinishtextpreviewfunc) | - | Set function [OH_TextEditorProxy_FinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_finishtextpreviewfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetGetTextConfigFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextConfigFunc *getTextConfigFunc)](#oh_texteditorproxy_getgettextconfigfunc) | - | Get function [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetInsertTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_InsertTextFunc *insertTextFunc)](#oh_texteditorproxy_getinserttextfunc) | - | Get function [OH_TextEditorProxy_InsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_inserttextfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetDeleteForwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteForwardFunc *deleteForwardFunc)](#oh_texteditorproxy_getdeleteforwardfunc) | - | Get function [OH_TextEditorProxy_DeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deleteforwardfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetDeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteBackwardFunc *deleteBackwardFunc)](#oh_texteditorproxy_getdeletebackwardfunc) | - | Get function [OH_TextEditorProxy_DeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deletebackwardfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetSendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendKeyboardStatusFunc *sendKeyboardStatusFunc)](#oh_texteditorproxy_getsendkeyboardstatusfunc) | - | Get function [OH_TextEditorProxy_SendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendkeyboardstatusfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetSendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendEnterKeyFunc *sendEnterKeyFunc)](#oh_texteditorproxy_getsendenterkeyfunc) | - | Get function [OH_TextEditorProxy_SendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendenterkeyfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetMoveCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_MoveCursorFunc *moveCursorFunc)](#oh_texteditorproxy_getmovecursorfunc) | - | Get function [OH_TextEditorProxy_MoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_movecursorfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetHandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleSetSelectionFunc *handleSetSelectionFunc)](#oh_texteditorproxy_gethandlesetselectionfunc) | - | Get function [OH_TextEditorProxy_HandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handlesetselectionfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetHandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleExtendActionFunc *handleExtendActionFunc)](#oh_texteditorproxy_gethandleextendactionfunc) | - | Get function [OH_TextEditorProxy_HandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handleextendactionfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetGetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetLeftTextOfCursorFunc *getLeftTextOfCursorFunc)](#oh_texteditorproxy_getgetlefttextofcursorfunc) | - | Get function [OH_TextEditorProxy_GetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getlefttextofcursorfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetGetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetRightTextOfCursorFunc *getRightTextOfCursorFunc)](#oh_texteditorproxy_getgetrighttextofcursorfunc) | - | Get function [OH_TextEditorProxy_GetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getrighttextofcursorfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetGetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextIndexAtCursorFunc *getTextIndexAtCursorFunc)](#oh_texteditorproxy_getgettextindexatcursorfunc) | - | Get function [OH_TextEditorProxy_GetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextindexatcursorfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_ReceivePrivateCommandFunc *receivePrivateCommandFunc)](#oh_texteditorproxy_getreceiveprivatecommandfunc) | - | Get function [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetSetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SetPreviewTextFunc *setPreviewTextFunc)](#oh_texteditorproxy_getsetpreviewtextfunc) | - | Get function [OH_TextEditorProxy_SetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setpreviewtextfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_GetFinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_FinishTextPreviewFunc *finishTextPreviewFunc)](#oh_texteditorproxy_getfinishtextpreviewfunc) | - | Get function [OH_TextEditorProxy_FinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_finishtextpreviewfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). |
| [InputMethod_ErrorCode OH_TextEditorProxy_SetCallbackInMainThread(InputMethod_TextEditorProxy *proxy, bool isCallbackInMainThread)](#oh_texteditorproxy_setcallbackinmainthread) | - | Configure the execution thread (main thread/IPC thread) for the callback functions of [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This interface only controls all callbacks in [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) except [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc). The execution thread of [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) is determined by the thread that calls [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) and is not affected by this interface. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_TextEditorProxy_GetTextConfigFunc)( InputMethod_TextEditorProxy *textEditorProxy, InputMethod_TextConfig *config) | Defines the function called when input method getting text config.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgettextconfigfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_InsertTextFunc)( InputMethod_TextEditorProxy *textEditorProxy, const char16_t *text, size_t length) | Defines the function called when input method inserting text.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetInsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setinserttextfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_DeleteForwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length) | Defines the function called when input method deleting text forward.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetDeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeleteforwardfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_DeleteBackwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length) | Defines the function called when input method deleting text backward.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetDeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeletebackwardfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_SendKeyboardStatusFunc)( InputMethod_TextEditorProxy *textEditorProxy, InputMethod_KeyboardStatus keyboardStatus) | Called when input method notifying keyboard status.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetSendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsendkeyboardstatusfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_SendEnterKeyFunc)( InputMethod_TextEditorProxy *textEditorProxy, InputMethod_EnterKeyType enterKeyType) | Called when input method sending enter key.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetSendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsendenterkeyfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_MoveCursorFunc)( InputMethod_TextEditorProxy *textEditorProxy, InputMethod_Direction direction) | Called when input method requesting to move cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetMoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setmovecursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_HandleSetSelectionFunc)( InputMethod_TextEditorProxy *textEditorProxy, int32_t start, int32_t end) | Called when input method requesting to set selection.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetHandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sethandlesetselectionfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_HandleExtendActionFunc)( InputMethod_TextEditorProxy *textEditorProxy, InputMethod_ExtendAction action) | Called when input method sending extend action.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetHandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sethandleextendactionfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_GetLeftTextOfCursorFunc)( InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length) | Called when input method requesting to get left text of cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgetlefttextofcursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_GetRightTextOfCursorFunc)( InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length) | Called when input method requesting to get right text of cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgetrighttextofcursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| int32_t (*OH_TextEditorProxy_GetTextIndexAtCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy) | Called when input method requesting to get text index at cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgettextindexatcursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| int32_t (*OH_TextEditorProxy_ReceivePrivateCommandFunc)( InputMethod_TextEditorProxy *textEditorProxy, InputMethod_PrivateCommand *privateCommand[], size_t size) | Called when input method sending private command.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setreceiveprivatecommandfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| int32_t (*OH_TextEditorProxy_SetPreviewTextFunc)( InputMethod_TextEditorProxy *textEditorProxy, const char16_t text[], size_t length, int32_t start, int32_t end) | Called when input method setting preview text.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetSetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsetpreviewtextfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |
| void (*OH_TextEditorProxy_FinishTextPreviewFunc)(InputMethod_TextEditorProxy *textEditorProxy) | Called when input method finishing preview text.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetFinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setfinishtextpreviewfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.<br>**Since**: 12 |

## Function description

### OH_TextEditorProxy_GetTextConfigFunc()

```c
typedef void (*OH_TextEditorProxy_GetTextConfigFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_TextConfig *config)
```

**Description**

Defines the function called when input method getting text config.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgettextconfigfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance. |
| InputMethod_TextConfig \*config | Represents a pointer to an [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) instance. You can only access the memory when this callback is called. After this callback returns, the memory will be released and you should not access this memory again. |

### OH_TextEditorProxy_InsertTextFunc()

```c
typedef void (*OH_TextEditorProxy_InsertTextFunc)(InputMethod_TextEditorProxy *textEditorProxy, const char16_t *text, size_t length)
```

**Description**

Defines the function called when input method inserting text.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetInsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setinserttextfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to the [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| const char16_t \*text | Represents a pointer to the text to be inserted. You can only access the memory when this callback is called. After this callback returns, the memory will be released and you should not access this memory again. |
| size_t length | Represents the length of the text to be inserted. |

### OH_TextEditorProxy_DeleteForwardFunc()

```c
typedef void (*OH_TextEditorProxy_DeleteForwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)
```

**Description**

Defines the function called when input method deleting text forward.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetDeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeleteforwardfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to the [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| int32_t length | Represents the length of the text to be deleted. |

### OH_TextEditorProxy_DeleteBackwardFunc()

```c
typedef void (*OH_TextEditorProxy_DeleteBackwardFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)
```

**Description**

Defines the function called when input method deleting text backward.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetDeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeletebackwardfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to the [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| int32_t length | Represents the length of the text to be deleted. |

### OH_TextEditorProxy_SendKeyboardStatusFunc()

```c
typedef void (*OH_TextEditorProxy_SendKeyboardStatusFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_KeyboardStatus keyboardStatus)
```

**Description**

Called when input method notifying keyboard status.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetSendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsendkeyboardstatusfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| InputMethod_KeyboardStatus keyboardStatus | Keyboard status, which is defined in [InputMethod_KeyboardStatus](capi-inputmethod-types-capi-h.md#inputmethod_keyboardstatus). |

### OH_TextEditorProxy_SendEnterKeyFunc()

```c
typedef void (*OH_TextEditorProxy_SendEnterKeyFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_EnterKeyType enterKeyType)
```

**Description**

Called when input method sending enter key.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetSendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsendenterkeyfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| InputMethod_EnterKeyType enterKeyType | Enter key type, which is defined in [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype). |

### OH_TextEditorProxy_MoveCursorFunc()

```c
typedef void (*OH_TextEditorProxy_MoveCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_Direction direction)
```

**Description**

Called when input method requesting to move cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetMoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setmovecursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| InputMethod_Direction direction | Represents the direction of the cursor movement, which is defined in [InputMethod_Direction](capi-inputmethod-types-capi-h.md#inputmethod_direction). |

### OH_TextEditorProxy_HandleSetSelectionFunc()

```c
typedef void (*OH_TextEditorProxy_HandleSetSelectionFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t start, int32_t end)
```

**Description**

Called when input method requesting to set selection.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetHandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sethandlesetselectionfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| int32_t start | Represents the start position of the selection. |
| int32_t end | Represents the end position of the selection. |

### OH_TextEditorProxy_HandleExtendActionFunc()

```c
typedef void (*OH_TextEditorProxy_HandleExtendActionFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_ExtendAction action)
```

**Description**

Called when input method sending extend action.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetHandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sethandleextendactionfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| InputMethod_ExtendAction action | Represents the extend action, which is defined in [InputMethod_ExtendAction](capi-inputmethod-types-capi-h.md#inputmethod_extendaction). |

### OH_TextEditorProxy_GetLeftTextOfCursorFunc()

```c
typedef void (*OH_TextEditorProxy_GetLeftTextOfCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length)
```

**Description**

Called when input method requesting to get left text of cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgetlefttextofcursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| int32_t number | Represents the number of characters to be get. |
| char16_t text[] | Represents the left text of cursor, you need to assign this parameter. You can only access the memory when this callback is called. After this callback returns, the memory will be released and you should not access this memory again. |
| size_t \*length | Represents the length of the left text of cursor, you need to assign this parameter. |

### OH_TextEditorProxy_GetRightTextOfCursorFunc()

```c
typedef void (*OH_TextEditorProxy_GetRightTextOfCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy, int32_t number, char16_t text[], size_t *length)
```

**Description**

Called when input method requesting to get right text of cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgetrighttextofcursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| int32_t number | Represents the number of characters to be get. |
| char16_t text[] | Represents the right text of cursor, you need to assign this parameter. You can only access the memory when this callback is called. After this callback returns, the memory will be released and you should not access this memory again. |
| size_t \*length | Represents the length of the right text of cursor. |

### OH_TextEditorProxy_GetTextIndexAtCursorFunc()

```c
typedef int32_t (*OH_TextEditorProxy_GetTextIndexAtCursorFunc)(InputMethod_TextEditorProxy *textEditorProxy)
```

**Description**

Called when input method requesting to get text index at cursor.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetGetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setgettextindexatcursorfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the index of text at cursor. |

### OH_TextEditorProxy_ReceivePrivateCommandFunc()

```c
typedef int32_t (*OH_TextEditorProxy_ReceivePrivateCommandFunc)(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)
```

**Description**

Called when input method sending private command.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setreceiveprivatecommandfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| InputMethod_PrivateCommand \*privateCommand[] | Private command from input method. You can only access the memory when this callback is called. After this callback returns, the memory will be released and you should not access this memory again. |
| size_t size | Size of private command. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result of handling private command. |

### OH_TextEditorProxy_SetPreviewTextFunc()

```c
typedef int32_t (*OH_TextEditorProxy_SetPreviewTextFunc)(InputMethod_TextEditorProxy *textEditorProxy, const char16_t text[], size_t length, int32_t start, int32_t end)
```

**Description**

Called when input method setting preview text.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetSetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setsetpreviewtextfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |
| const char16_t text[] | Represents text to be previewed. You can only access the memory when this callback is called. After this callback returns, the memory will be released and you should not access this memory again. |
| size_t length | Length of preview text. |
| int32_t start | Start position of preview text. |
| int32_t end | End position of preview text. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result of setting preview text. |

### OH_TextEditorProxy_FinishTextPreviewFunc()

```c
typedef void (*OH_TextEditorProxy_FinishTextPreviewFunc)(InputMethod_TextEditorProxy *textEditorProxy)
```

**Description**

Called when input method finishing preview text.<br> You need to implement this function, set it to [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) through [OH_TextEditorProxy_SetFinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setfinishtextpreviewfunc), and use [OH_InputMethodController_Attach] (capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) to complete the registration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) \*textEditorProxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set in. |

### OH_TextEditorProxy_Create()

```c
InputMethod_TextEditorProxy *OH_TextEditorProxy_Create(void)
```

**Description**

Create a new [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_TextEditorProxy *](capi-inputmethod-inputmethod-texteditorproxy.md) | If the creation succeeds, a pointer to the newly created [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md)  instance is returned. If the creation fails, NULL is returned, possible cause is insufficient memory. |

### OH_TextEditorProxy_Destroy()

```c
void OH_TextEditorProxy_Destroy(InputMethod_TextEditorProxy *proxy)
```

**Description**

Destroy a [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | The [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance to be destroyed. |

### OH_TextEditorProxy_SetGetTextConfigFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetGetTextConfigFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextConfigFunc getTextConfigFunc)
```

**Description**

Set function [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) getTextConfigFunc | Represents function [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetInsertTextFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetInsertTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_InsertTextFunc insertTextFunc)
```

**Description**

Set function [OH_TextEditorProxy_InsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_inserttextfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_InsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_inserttextfunc) insertTextFunc | Represents function [OH_TextEditorProxy_InsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_inserttextfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetDeleteForwardFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetDeleteForwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteForwardFunc deleteForwardFunc)
```

**Description**

Set function [OH_TextEditorProxy_SetDeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setdeleteforwardfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_DeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deleteforwardfunc) deleteForwardFunc | Represents function [OH_TextEditorProxy_DeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deleteforwardfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetDeleteBackwardFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetDeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteBackwardFunc deleteBackwardFunc)
```

**Description**

Set function [OH_TextEditorProxy_DeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deletebackwardfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_DeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deletebackwardfunc) deleteBackwardFunc | Represents function [OH_TextEditorProxy_DeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deletebackwardfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetSendKeyboardStatusFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetSendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendKeyboardStatusFunc sendKeyboardStatusFunc)
```

**Description**

Set function [OH_TextEditorProxy_SendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendkeyboardstatusfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_SendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendkeyboardstatusfunc) sendKeyboardStatusFunc | Represents function [OH_TextEditorProxy_SendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendkeyboardstatusfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetSendEnterKeyFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetSendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendEnterKeyFunc sendEnterKeyFunc)
```

**Description**

Set function [OH_TextEditorProxy_SendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendenterkeyfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_SendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendenterkeyfunc) sendEnterKeyFunc | Represents function [OH_TextEditorProxy_SendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendenterkeyfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetMoveCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetMoveCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_MoveCursorFunc moveCursorFunc)
```

**Description**

Set function [OH_TextEditorProxy_MoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_movecursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_MoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_movecursorfunc) moveCursorFunc | Represents function [OH_TextEditorProxy_MoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_movecursorfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetHandleSetSelectionFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetHandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleSetSelectionFunc handleSetSelectionFunc)
```

**Description**

Set function [OH_TextEditorProxy_HandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handlesetselectionfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_HandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handlesetselectionfunc) handleSetSelectionFunc | Represents function [OH_TextEditorProxy_HandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handlesetselectionfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetHandleExtendActionFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetHandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleExtendActionFunc handleExtendActionFunc)
```

**Description**

Set function [OH_TextEditorProxy_HandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handleextendactionfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_HandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handleextendactionfunc) handleExtendActionFunc | Represents function [OH_TextEditorProxy_HandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handleextendactionfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetGetLeftTextOfCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetGetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetLeftTextOfCursorFunc getLeftTextOfCursorFunc)
```

**Description**

Set function [OH_TextEditorProxy_GetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getlefttextofcursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_GetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getlefttextofcursorfunc) getLeftTextOfCursorFunc | Represents function [OH_TextEditorProxy_GetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getlefttextofcursorfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetGetRightTextOfCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetGetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetRightTextOfCursorFunc getRightTextOfCursorFunc)
```

**Description**

Set function [OH_TextEditorProxy_GetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getrighttextofcursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_GetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getrighttextofcursorfunc) getRightTextOfCursorFunc | Represents function [OH_TextEditorProxy_GetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getrighttextofcursorfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetGetTextIndexAtCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetGetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextIndexAtCursorFunc getTextIndexAtCursorFunc)
```

**Description**

Set function [OH_TextEditorProxy_GetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextindexatcursorfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_GetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextindexatcursorfunc) getTextIndexAtCursorFunc | Represents function [OH_TextEditorProxy_GetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextindexatcursorfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetReceivePrivateCommandFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_ReceivePrivateCommandFunc receivePrivateCommandFunc)
```

**Description**

Set function [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc) receivePrivateCommandFunc | Represents function [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetSetPreviewTextFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetSetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SetPreviewTextFunc setPreviewTextFunc)
```

**Description**

Set function [OH_TextEditorProxy_SetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setpreviewtextfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_SetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setpreviewtextfunc) setPreviewTextFunc | Represents function [OH_TextEditorProxy_SetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setpreviewtextfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetFinishTextPreviewFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetFinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_FinishTextPreviewFunc finishTextPreviewFunc)
```

**Description**

Set function [OH_TextEditorProxy_FinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_finishtextpreviewfunc) into [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be set function in. |
| [OH_TextEditorProxy_FinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_finishtextpreviewfunc) finishTextPreviewFunc | Represents function [OH_TextEditorProxy_FinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_finishtextpreviewfunc) which will be set. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetGetTextConfigFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetGetTextConfigFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextConfigFunc *getTextConfigFunc)
```

**Description**

Get function [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) *getTextConfigFunc | Represents function [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetInsertTextFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetInsertTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_InsertTextFunc *insertTextFunc)
```

**Description**

Get function [OH_TextEditorProxy_InsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_inserttextfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_InsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_inserttextfunc) *insertTextFunc | Represents function [OH_TextEditorProxy_InsertTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_inserttextfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetDeleteForwardFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetDeleteForwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteForwardFunc *deleteForwardFunc)
```

**Description**

Get function [OH_TextEditorProxy_DeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deleteforwardfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_DeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deleteforwardfunc) *deleteForwardFunc | Represents function [OH_TextEditorProxy_DeleteForwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deleteforwardfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetDeleteBackwardFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetDeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_DeleteBackwardFunc *deleteBackwardFunc)
```

**Description**

Get function [OH_TextEditorProxy_DeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deletebackwardfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_DeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deletebackwardfunc) *deleteBackwardFunc | Represents function [OH_TextEditorProxy_DeleteBackwardFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_deletebackwardfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetSendKeyboardStatusFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetSendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendKeyboardStatusFunc *sendKeyboardStatusFunc)
```

**Description**

Get function [OH_TextEditorProxy_SendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendkeyboardstatusfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_SendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendkeyboardstatusfunc) *sendKeyboardStatusFunc | Represents function [OH_TextEditorProxy_SendKeyboardStatusFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendkeyboardstatusfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetSendEnterKeyFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetSendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SendEnterKeyFunc *sendEnterKeyFunc)
```

**Description**

Get function [OH_TextEditorProxy_SendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendenterkeyfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_SendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendenterkeyfunc) *sendEnterKeyFunc | Represents function [OH_TextEditorProxy_SendEnterKeyFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_sendenterkeyfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetMoveCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetMoveCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_MoveCursorFunc *moveCursorFunc)
```

**Description**

Get function [OH_TextEditorProxy_MoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_movecursorfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_MoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_movecursorfunc) *moveCursorFunc | Represents function [OH_TextEditorProxy_MoveCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_movecursorfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetHandleSetSelectionFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetHandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleSetSelectionFunc *handleSetSelectionFunc)
```

**Description**

Get function [OH_TextEditorProxy_HandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handlesetselectionfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_HandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handlesetselectionfunc) *handleSetSelectionFunc | Represents function [OH_TextEditorProxy_HandleSetSelectionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handlesetselectionfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetHandleExtendActionFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetHandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_HandleExtendActionFunc *handleExtendActionFunc)
```

**Description**

Get function [OH_TextEditorProxy_HandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handleextendactionfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_HandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handleextendactionfunc) *handleExtendActionFunc | Represents function [OH_TextEditorProxy_HandleExtendActionFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_handleextendactionfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetGetLeftTextOfCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetGetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetLeftTextOfCursorFunc *getLeftTextOfCursorFunc)
```

**Description**

Get function [OH_TextEditorProxy_GetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getlefttextofcursorfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_GetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getlefttextofcursorfunc) *getLeftTextOfCursorFunc | Represents function [OH_TextEditorProxy_GetLeftTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getlefttextofcursorfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetGetRightTextOfCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetGetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetRightTextOfCursorFunc *getRightTextOfCursorFunc)
```

**Description**

Get function [OH_TextEditorProxy_GetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getrighttextofcursorfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_GetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getrighttextofcursorfunc) *getRightTextOfCursorFunc | Represents function [OH_TextEditorProxy_GetRightTextOfCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_getrighttextofcursorfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetGetTextIndexAtCursorFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetGetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_GetTextIndexAtCursorFunc *getTextIndexAtCursorFunc)
```

**Description**

Get function [OH_TextEditorProxy_GetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextindexatcursorfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_GetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextindexatcursorfunc) *getTextIndexAtCursorFunc | Represents function [OH_TextEditorProxy_GetTextIndexAtCursorFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextindexatcursorfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetReceivePrivateCommandFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_ReceivePrivateCommandFunc *receivePrivateCommandFunc)
```

**Description**

Get function [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc) *receivePrivateCommandFunc | Represents function [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetSetPreviewTextFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetSetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_SetPreviewTextFunc *setPreviewTextFunc)
```

**Description**

Get function [OH_TextEditorProxy_SetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setpreviewtextfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_SetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setpreviewtextfunc) *setPreviewTextFunc | Represents function [OH_TextEditorProxy_SetPreviewTextFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_setpreviewtextfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_GetFinishTextPreviewFunc()

```c
InputMethod_ErrorCode OH_TextEditorProxy_GetFinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy, OH_TextEditorProxy_FinishTextPreviewFunc *finishTextPreviewFunc)
```

**Description**

Get function [OH_TextEditorProxy_FinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_finishtextpreviewfunc) from [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Represents a pointer to an [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance which will be get function from. |
| [OH_TextEditorProxy_FinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_finishtextpreviewfunc) *finishTextPreviewFunc | Represents function [OH_TextEditorProxy_FinishTextPreviewFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_finishtextpreviewfunc) which will be get. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.  Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextEditorProxy_SetCallbackInMainThread()

```c
InputMethod_ErrorCode OH_TextEditorProxy_SetCallbackInMainThread(InputMethod_TextEditorProxy *proxy, bool isCallbackInMainThread)
```

**Description**

Configure the execution thread (main thread/IPC thread) for the callback functions of [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md). This interface only controls all callbacks in [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) except [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc). The execution thread of [OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_gettextconfigfunc) is determined by the thread that calls [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h. md#oh_inputmethodcontroller_attach) and is not affected by this interface.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *proxy | Pointer to the target [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance. |
| bool isCallbackInMainThread | Thread execution policy. - **true**: The callback executes on the main thread to avoid multithreaded concurrency. Do not perform time-consuming operations in the callback, as this may block the main thread. - **false**: The callback executes on an IPC thread (which may result in multithreaded concurrency). |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Execution result.      [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Configuration succeeded.      [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Returned when proxy is NULL. |


