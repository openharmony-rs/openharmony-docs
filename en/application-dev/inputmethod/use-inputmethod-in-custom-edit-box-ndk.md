# Using the Input Method in a Custom Edit Box (C/C++)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

## When to Use

IME Kit allows you to use input method in the custom edit box to interact with input method applications, including displaying and hiding input methods and receiving text editing notifications from input method applications. This document describes how to use C/C++ to develop this function.

## APIs

For details about the APIs, see [API Reference](../reference/apis-ime-kit/capi-inputmethod.md).

## Adding Dynamic Link Libraries

Add the following library to **CMakeLists.txt**.

```txt
libohinputmethod.so
```

## Including Header Files

```c
#include <inputmethod/inputmethod_controller_capi.h>
```


## Binding an Input Method

When the text box is focused, you can call the [OH_InputMethodController_Attach](../reference/apis-ime-kit/capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) API to bind the input method. After the binding is successful, you can use the input method to enter text.

1. Create an **InputMethod_TextEditorProxy** instance. The sample code is as follows:

   ```c
   // Create an InputMethod_TextEditorProxy instance.
   InputMethod_TextEditorProxy *textEditorProxy = OH_TextEditorProxy_Create();
   ```
   
2. Create an **InputMethod_AttachOptions** instance and set the options for binding the input method. The sample code is as follows:

   ```c
   // Create an InputMethod_AttachOptions instance. showKeyboard specifies whether to display the keyboard after the binding is successful. The following uses displaying the target keyboard as an example.
   bool showKeyboard = true;
   InputMethod_AttachOptions *options = OH_AttachOptions_Create(showKeyboard);
   ```

3. Call **OH_InputMethodController_Attach** to bind the input method service. After the call is successful, you can obtain **InputMethod_InputMethodProxy** used to interact with the input method. The sample code is as follows:

   ```c
   InputMethod_InputMethodProxy *inputMethodProxy = nullptr;
   // Send a binding request.
   if (OH_InputMethodController_Attach(textEditorProxy, options, &inputMethodProxy) != InputMethod_ErrorCode::IME_ERR_OK) {
       OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "Attach failed!");
   }
   ```

## Displaying or Hiding the Panel

After the binding is successful, you can use the obtained [InputMethod_InputMethodProxy](../reference/apis-ime-kit/capi-inputmethod-inputmethod-inputmethodproxy.md) object to send a message to the input method. The sample code is as follows:

```c
// Display the keyboard.
if (OH_InputMethodProxy_ShowKeyboard(inputMethodProxy) != InputMethod_ErrorCode::IME_ERR_OK) {
    OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "ShowKeyboard failed!");
}
// Hide the keyboard.
if (OH_InputMethodProxy_HideKeyboard(inputMethodProxy) != InputMethod_ErrorCode::IME_ERR_OK) {
    OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "HideKeyboard failed!");
}
// Notify the change of the input box configuration.
if (OH_InputMethodProxy_NotifyConfigurationChange(inputMethodProxy, InputMethod_EnterKeyType::IME_ENTER_KEY_GO, InputMethod_TextInputType::IME_TEXT_INPUT_TYPE_TEXT) != InputMethod_ErrorCode::IME_ERR_OK) {
    OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "NotifyConfigurationChange failed!");
}
```

## Listening to Requests/Notifications from the Input Method Application

1. Implement the response processing function for the request or notification sent by the input method application. The sample code is as follows:

   ```c
   // Implement the input method application event response function in InputMethod_TextEditorProxy.
   void GetTextConfig(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_TextConfig *config)
   {
       // Process the request sent by the input method for obtaining the input box configuration.
   }
   void InsertText(InputMethod_TextEditorProxy *textEditorProxy, const char16_t *text, size_t length)
   {
       // Process the text insertion request sent by the input method.
   }
   void DeleteForward(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)
   {
       // Process the text deletion request sent by the input method.
   }
   // ......
   ```

2. Set the implemented response function to [InputMethod_TextEditorProxy](../reference/apis-ime-kit/capi-inputmethod-inputmethod-texteditorproxy.md), and then set the response function to the input method framework using [OH_InputMethodController_Attach](../reference/apis-ime-kit/capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach) called when the input method is bound to complete listener registration. The sample code is as follows:

   ```c
   // Set the implemented response processing function to InputMethod_TextEditorProxy.
   OH_TextEditorProxy_SetGetTextConfigFunc(textEditorProxy, GetTextConfig);
   OH_TextEditorProxy_SetInsertTextFunc(textEditorProxy, InsertText);
   OH_TextEditorProxy_SetDeleteForwardFunc(textEditorProxy, DeleteForward);
   ```

## Unbinding an Input Method

When the edit box is out of focus, you need to stop using the input method and unbind the input method framework by calling [OH_InputMethodController_Detach](../reference/apis-ime-kit/capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_detach).

```c
// Send an unbinding request.
if (OH_InputMethodController_Detach(inputMethodProxy) != InputMethod_ErrorCode::IME_ERR_OK) {
    OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "Detach failed!");
}
inputMethodProxy = nullptr;
OH_TextEditorProxy_Destroy(textEditorProxy);
textEditorProxy = nullptr;
OH_AttachOptions_Destroy(options);
options = nullptr;
```

## Sample Code

The sample code shows how to bind, hide, and unbind an input method.

The entry is the **InputMethodNdkDemo** function.

> **NOTE**
>
> Dependencies of **libohinputmethod.so** and **libhilog_ndk.z.so** should be added to the **CMakeList.txt** file.
```c++
#include <codecvt>
#include <locale>
#include <string>

#include "hilog/log.h"
#include "inputmethod/inputmethod_controller_capi.h"

void GetTextConfigFunc(InputMethod_TextEditorProxy *proxy, InputMethod_TextConfig *config) { // Process the request sent by the input method for obtaining the text box configuration.
    auto ret = OH_TextConfig_SetEnterKeyType(config, InputMethod_EnterKeyType::IME_ENTER_KEY_SEND);
    if (ret != IME_ERR_OK) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "SetEnterKeyType failed, ret=%{public}d", ret);
        return;
    }

    ret = OH_TextConfig_SetInputType(config, InputMethod_TextInputType::IME_TEXT_INPUT_TYPE_PHONE);
    if (ret != IME_ERR_OK) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "SetInputType failed, ret=%{public}d", ret);
        return;
    }
}
void InsertTextFunc(InputMethod_TextEditorProxy *proxy, const char16_t *text, size_t length) {
    // Process the text insertion request.
    // Convert the string of the char16_t type to u16string.
    std::u16string u16Str(text);

    // Convert the string to the UTF-8 encoding format.
    std::wstring_convert<std::codecvt_utf8_utf16<char16_t>, char16_t> converter;
    std::string utf8Str = converter.to_bytes(u16Str);

    OH_LOG_Print(LOG_APP, LOG_INFO, 0, "testTag", "insertText=%{public}s", utf8Str.c_str());
}
void DeleteForwardFunc(InputMethod_TextEditorProxy *proxy, int32_t length) {
    // Handle the request for deleting the text on the right of the cursor.
}
void DeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, int32_t length) {
    // Handle the request for deleting the text on the left of the cursor.
}
void SendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, InputMethod_KeyboardStatus status) {
    // Handle the request for keyboard status changes.
}
void SendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, InputMethod_EnterKeyType type) {
    // Handle the request for changes in the Enter key function.
}
void MoveCursorFunc(InputMethod_TextEditorProxy *proxy, InputMethod_Direction direction) {
    // Handle the cursor movement request.
}
void HandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, int32_t start, int32_t end) {
    // Handle the text selection request
}
void HandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, InputMethod_ExtendAction action) {
    // Handle the extended editing request
}
void GetleftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, int32_t number, char16_t text[], size_t *length) {
    // Handle the request for obtaining the text on the left of the cursor.
}
void GetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, int32_t number, char16_t text[], size_t *length) {
    // Handle the request for obtaining the text on the right of the cursor.
}
int32_t GetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy) {
// Handle the request for obtaining the text index of the text box where the cursor is located.
    return 0;
}
int32_t ReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, InputMethod_PrivateCommand *privateCommand[],
                                  size_t size) {
    // Handle the request for private data commands.
    return 0;
}
int32_t SetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, const char16_t *text, size_t length, int32_t start,
                           int32_t end) {
    // Handle the request for text preview.
    return 0;
}
void FinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy) {
    // Handle the request for ending text preview.
}

void ConstructTextEditorProxy(InputMethod_TextEditorProxy *textEditorProxy) {
    OH_TextEditorProxy_SetGetTextConfigFunc(textEditorProxy, GetTextConfigFunc);
    OH_TextEditorProxy_SetInsertTextFunc(textEditorProxy, InsertTextFunc);
    OH_TextEditorProxy_SetDeleteForwardFunc(textEditorProxy, DeleteForwardFunc);
    OH_TextEditorProxy_SetDeleteBackwardFunc(textEditorProxy, DeleteBackwardFunc);
    OH_TextEditorProxy_SetSendKeyboardStatusFunc(textEditorProxy, SendKeyboardStatusFunc);
    OH_TextEditorProxy_SetSendEnterKeyFunc(textEditorProxy, SendEnterKeyFunc);
    OH_TextEditorProxy_SetMoveCursorFunc(textEditorProxy, MoveCursorFunc);
    OH_TextEditorProxy_SetHandleSetSelectionFunc(textEditorProxy, HandleSetSelectionFunc);
    OH_TextEditorProxy_SetHandleExtendActionFunc(textEditorProxy, HandleExtendActionFunc);
    OH_TextEditorProxy_SetGetLeftTextOfCursorFunc(textEditorProxy, GetleftTextOfCursorFunc);
    OH_TextEditorProxy_SetGetRightTextOfCursorFunc(textEditorProxy, GetRightTextOfCursorFunc);
    OH_TextEditorProxy_SetGetTextIndexAtCursorFunc(textEditorProxy, GetTextIndexAtCursorFunc);
    OH_TextEditorProxy_SetReceivePrivateCommandFunc(textEditorProxy, ReceivePrivateCommandFunc);
    OH_TextEditorProxy_SetSetPreviewTextFunc(textEditorProxy, SetPreviewTextFunc);
    OH_TextEditorProxy_SetFinishTextPreviewFunc(textEditorProxy, FinishTextPreviewFunc);
}

void InputMethodNdkDemo() {
    // Create an InputMethod_TextEditorProxy instance.
    InputMethod_TextEditorProxy *textEditorProxy = OH_TextEditorProxy_Create();
    if (textEditorProxy == nullptr) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "Create TextEditorProxy failed.");
        return;
    }

    // Set the implemented response processing function to InputMethod_TextEditorProxy.
    ConstructTextEditorProxy(textEditorProxy);

    // Create an InputMethod_AttachOptions instance. showKeyboard specifies whether to display the keyboard after the binding is successful. The following uses displaying the target keyboard as an example.
    bool showKeyboard = true;
    InputMethod_AttachOptions *attachOptions = OH_AttachOptions_Create(showKeyboard);
    if (attachOptions == nullptr) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "Create AttachOptions failed.");
        OH_TextEditorProxy_Destroy(textEditorProxy);
        return;
    }

    InputMethod_InputMethodProxy *inputMethodProxy = nullptr;
    // Send a binding request.
    auto ret = OH_InputMethodController_Attach(textEditorProxy, attachOptions, &inputMethodProxy);
    if (ret != IME_ERR_OK) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "Attach failed, ret=%{public}d.", ret);
        OH_TextEditorProxy_Destroy(textEditorProxy);
        OH_AttachOptions_Destroy(attachOptions);
        return;
    }

    // Display the keyboard for 3 seconds.
    std::this_thread::sleep_for(std::chrono::seconds(3));

    // Hide the keyboard.
    ret = OH_InputMethodProxy_HideKeyboard(inputMethodProxy);
    if (ret != IME_ERR_OK) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "HideKeyboard failed, ret=%{public}d.", ret);
        OH_TextEditorProxy_Destroy(textEditorProxy);
        OH_AttachOptions_Destroy(attachOptions);
        return;
    }

    // Send an unbinding request.
    OH_InputMethodController_Detach(inputMethodProxy);
    OH_TextEditorProxy_Destroy(textEditorProxy);
    OH_AttachOptions_Destroy(attachOptions);
    OH_LOG_Print(LOG_APP, LOG_INFO, 0, "testTag", "Finished.");
}
```
