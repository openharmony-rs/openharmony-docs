# 在自绘编辑框中使用输入法开发指导 (C/C++)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

IME Kit支持开发者在自绘编辑框中使用输入法，与输入法应用交互，包括显示、隐藏输入法，接收来自输入法应用的文本编辑操作通知等，本文档介绍开发者如何使用C/C++完成此功能开发。

## 接口说明

详细接口说明请参考[InputMethod接口文档](../reference/apis-ime-kit/capi-inputmethod.md)。

## 添加动态链接库

CMakeLists.txt中添加以下lib。

```txt
libace_napi.z.so
libohinputmethod.so
libhilog_ndk.z.so
```

## 引用头文件

本示例使用的头文件如下：

<!-- @[preview_style_c_headers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include <algorithm>
#include <mutex>
#include <string>

#include "PreviewDisplayState.h"

#include "hilog/log.h"
#include "inputmethod/inputmethod_text_editor_proxy_capi.h"
#include "inputmethod/inputmethod_preview_text_style_capi.h"
#include "inputmethod/inputmethod_controller_capi.h"
#include "napi/native_api.h"
```

## 绑定输入法

开发者需要在输入框获焦时，通过调用接口[OH_InputMethodController_Attach](../reference/apis-ime-kit/capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)绑定输入法，绑定成功后用户可以通过输入法输入文字。

1. 创建InputMethod_TextEditorProxy实例，示例代码如下所示：

   <!-- @[input_case_input_TextEditorProxy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

   ```cpp
   textEditorProxy = OH_TextEditorProxy_Create();
   ```


2. 创建InputMethod_AttachOptions实例，设置绑定输入法时的选项。示例代码如下所示：

   <!-- @[input_case_input_attachOptions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

   ```cpp
   attachOptions = OH_AttachOptions_Create(true);
   ```


3. 调用OH_InputMethodController_Attach发起绑定输入法服务，调用成功后，可以获取到用于和输入法交互的InputMethod_InputMethodProxy。示例代码如下所示：

   <!-- @[input_case_input_OH_InputMethodController_Attach](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

   ```cpp
   result = OH_InputMethodController_Attach(textEditorProxy, attachOptions, &inputMethodProxy);
   if (result != IME_ERR_OK) {
       inputMethodProxy = nullptr;
       ReleaseCEditor();
   }
   return result;
   ```


## 显示/隐藏面板功能

绑定成功后，调用OH_InputMethodProxy_ShowKeyboard显示键盘。本示例在ShowInputMethodKeyboard中检查代理是否存在，再调用显示接口：

<!-- @[preview_style_c_show_keyboard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

``` C++
const auto code = inputMethodProxy == nullptr ? IME_ERR_NULL_POINTER :
    OH_InputMethodProxy_ShowKeyboard(inputMethodProxy);
```

解绑前，调用OH_InputMethodProxy_HideKeyboard隐藏键盘。本示例在ReleaseCEditor中调用：

<!-- @[preview_style_c_hide_keyboard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

``` C++
OH_InputMethodProxy_HideKeyboard(inputMethodProxy);
```

## 监听输入法应用的请求/通知

1. 在[napi_init.cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp)中，实现GetTextConfigFunc、InsertTextFunc、DeleteForwardFunc等回调。输入法框架请求输入框配置、插入或删除文本时，会调用对应回调，由自绘编辑框处理请求并更新文本状态。对应回调实现如下。

   本示例收到键盘状态通知时，不在`SendKeyboardStatusFunc`中更新编辑框。编辑框的显示状态由文本编辑回调更新。

   <!-- @[preview_style_c_edit_callbacks](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   void GetTextConfigFunc(InputMethod_TextEditorProxy *proxy, InputMethod_TextConfig *config)
   {
       // 处理获取输入框配置请求
       auto ret = OH_TextConfig_SetEnterKeyType(config, InputMethod_EnterKeyType::IME_ENTER_KEY_SEND);
       if (ret != IME_ERR_OK) {
           OH_LOG_Print(LOG_APP, LOG_ERROR, 0xF811, "PreviewTextStyleC", "SetEnterKeyType failed, ret=%{public}d", ret);
           return;
       }
   
       ret = OH_TextConfig_SetInputType(config, InputMethod_TextInputType::IME_TEXT_INPUT_TYPE_TEXT);
       if (ret != IME_ERR_OK) {
           OH_LOG_Print(LOG_APP, LOG_ERROR, 0xF811, "PreviewTextStyleC", "SetInputType failed, ret=%{public}d", ret);
           return;
       }
   
       ret = OH_TextConfig_SetPreviewTextSupport(config, true);
       if (ret != IME_ERR_OK) {
           OH_LOG_Print(LOG_APP, LOG_ERROR, 0xF811, "PreviewTextStyleC",
               "SetPreviewTextSupport failed, ret=%{public}d", ret);
       }
   }
   
   void InsertTextFunc(InputMethod_TextEditorProxy *proxy, const char16_t *text, size_t length)
   {
       if (text == nullptr) {
           return;
       }
       std::lock_guard<std::mutex> lock(g_textMutex);
       g_display.text.append(text, length);
       g_display.active = false;
   }
   
   // 框架为兼容性反转输入方向；C编辑框的向后删除表示退格。
   void DeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, int32_t length)
   {
       std::lock_guard<std::mutex> lock(g_textMutex);
       if (length <= 0) {
           return;
       }
       size_t count = std::min(static_cast<size_t>(length), g_display.text.size());
       size_t start = g_display.text.size() - count;
       if (start > 0 && start < g_display.text.size() && g_display.text[start] >= 0xDC00 &&
           g_display.text[start] <= 0xDFFF && g_display.text[start - 1] >= 0xD800 &&
           g_display.text[start - 1] <= 0xDBFF) {
           --start;
       }
       g_display.text.erase(start);
       g_display.active = false;
   }
   
   void DeleteForwardFunc(InputMethod_TextEditorProxy *proxy, int32_t length)
   {
       std::lock_guard<std::mutex> lock(g_textMutex);
       // 本示例将光标保持在文本末尾，光标右侧没有文本。
   }
   
   void SendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, InputMethod_KeyboardStatus status)
   {
       // 无需处理：本示例通过编辑回调更新显示状态。
   }
   
   void SendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, InputMethod_EnterKeyType type)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC", "C enter action=%{public}d", type);
   }
   
   void MoveCursorFunc(InputMethod_TextEditorProxy *proxy, InputMethod_Direction direction)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC", "C cursor request=%{public}d", direction);
   }
   
   void HandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, int32_t start, int32_t end)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC",
           "C selection request=%{public}d,%{public}d", start, end);
   }
   
   void HandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, InputMethod_ExtendAction action)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC", "C edit action=%{public}d", action);
   }
   
   void GetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, int32_t number, char16_t text[], size_t *length)
   {
       if (length == nullptr) {
           return;
       }
       if (text == nullptr || number <= 0) {
           *length = 0;
           return;
       }
       std::lock_guard<std::mutex> lock(g_textMutex);
       const size_t count = std::min(static_cast<size_t>(number), g_display.text.size());
       std::copy(g_display.text.end() - count, g_display.text.end(), text);
       *length = count;
   }
   
   void GetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, int32_t number, char16_t text[], size_t *length)
   {
       if (length != nullptr) {
           *length = 0;
       }
   }
   
   int32_t GetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy)
   {
       std::lock_guard<std::mutex> lock(g_textMutex);
       return static_cast<int32_t>(g_display.text.size());
   }
   
   int32_t ReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, InputMethod_PrivateCommand *privateCommand[],
       size_t size)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC", "C private command received");
       return 0;
   }
   
   // OH_InputMethodController_Attach要求注册SetPreviewText回调；样式由带样式的回调处理。
   int32_t SetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, const char16_t *text, size_t length,
       int32_t start, int32_t end)
   {
       return text == nullptr ? IME_ERR_NULL_POINTER : IME_ERR_OK;
   }
   ```

2. 在ConstructTextEditorProxy中，调用OH_TextEditorProxy_SetGetTextConfigFunc、OH_TextEditorProxy_SetInsertTextFunc等Set接口，将上述回调注册到[InputMethod_TextEditorProxy](../reference/apis-ime-kit/capi-inputmethod-inputmethod-texteditorproxy.md)。随后，AttachEditor调用[OH_InputMethodController_Attach](../reference/apis-ime-kit/capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)绑定输入法，框架通过已注册的回调传递请求或通知。回调注册代码如下；AttachEditor的调用顺序见[完整示例](#完整示例)的第二段代码。

   这些设置函数将输入配置、文本插入与删除、光标查询等处理函数保存到textEditorProxy。预上屏相关设置检查返回值；样式回调设置后还会读取并核对函数指针。注册完成后再调用OH_InputMethodController_Attach绑定输入法。

   <!-- @[input_case_input_ConstructTextEditorProxy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   OH_TextEditorProxy_SetGetTextConfigFunc(textEditorProxy, GetTextConfigFunc);
   OH_TextEditorProxy_SetInsertTextFunc(textEditorProxy, InsertTextFunc);
   OH_TextEditorProxy_SetDeleteForwardFunc(textEditorProxy, DeleteForwardFunc);
   OH_TextEditorProxy_SetDeleteBackwardFunc(textEditorProxy, DeleteBackwardFunc);
   OH_TextEditorProxy_SetSendKeyboardStatusFunc(textEditorProxy, SendKeyboardStatusFunc);
   OH_TextEditorProxy_SetSendEnterKeyFunc(textEditorProxy, SendEnterKeyFunc);
   OH_TextEditorProxy_SetMoveCursorFunc(textEditorProxy, MoveCursorFunc);
   OH_TextEditorProxy_SetHandleSetSelectionFunc(textEditorProxy, HandleSetSelectionFunc);
   OH_TextEditorProxy_SetHandleExtendActionFunc(textEditorProxy, HandleExtendActionFunc);
   OH_TextEditorProxy_SetGetLeftTextOfCursorFunc(textEditorProxy, GetLeftTextOfCursorFunc);
   OH_TextEditorProxy_SetGetRightTextOfCursorFunc(textEditorProxy, GetRightTextOfCursorFunc);
   OH_TextEditorProxy_SetGetTextIndexAtCursorFunc(textEditorProxy, GetTextIndexAtCursorFunc);
   OH_TextEditorProxy_SetReceivePrivateCommandFunc(textEditorProxy, ReceivePrivateCommandFunc);
   auto result = OH_TextEditorProxy_SetSetPreviewTextFunc(textEditorProxy, SetPreviewTextFunc);
   if (result != IME_ERR_OK) {
       return result;
   }
   result = OH_InputMethod_TextEditorProxy_SetSetPreviewTextWithStyleFunc(
       textEditorProxy, SetPreviewTextWithStyleFunc);
   if (result != IME_ERR_OK) {
       return result;
   }
   OH_InputMethod_TextEditorProxy_SetPreviewTextWithStyleFunc registered = nullptr;
   result = OH_InputMethod_TextEditorProxy_GetSetPreviewTextWithStyleFunc(textEditorProxy, &registered);
   if (result != IME_ERR_OK) {
       return result;
   }
   if (registered != SetPreviewTextWithStyleFunc) {
       return IME_ERR_UNDEFINED;
   }
   return OH_TextEditorProxy_SetFinishTextPreviewFunc(textEditorProxy, FinishTextPreviewFunc);
   ```


带样式预上屏需要在`GetTextConfigFunc`中启用预上屏支持，并注册`SetPreviewTextWithStyleFunc`。旧预上屏回调仍需注册以满足绑定要求，显示状态由带样式回调更新。回调中的样式对象由框架管理，应用读取并复制所需值，不销毁该对象。

## 解绑输入法

当编辑框失焦，需要结束使用输入法，通过接口[OH_InputMethodController_Detach](../reference/apis-ime-kit/capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_detach)与输入法框架解绑。


   <!-- @[input_case_input_OH_InputMethodController_Detach](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   static int ReleaseCEditor()
   {
       {
           std::lock_guard<std::mutex> lock(g_textMutex);
           g_display.active = false;
       }
       if (g_releaseError != IME_ERR_OK) {
           return g_releaseError;
       }
       if (inputMethodProxy != nullptr) {
           OH_InputMethodProxy_HideKeyboard(inputMethodProxy);
           const int ret = OH_InputMethodController_Detach(inputMethodProxy);
           inputMethodProxy = nullptr;
           if (ret != IME_ERR_OK) {
               g_releaseError = ret;
               return ret;
           }
       }
       if (textEditorProxy != nullptr) {
           OH_TextEditorProxy_Destroy(textEditorProxy);
           textEditorProxy = nullptr;
       }
       if (attachOptions != nullptr) {
           OH_AttachOptions_Destroy(attachOptions);
           attachOptions = nullptr;
       }
       return IME_ERR_OK;
   }
   ```


## 完整示例

示例代码展示了绑定输入法、接收带样式的预上屏回调、结束预上屏和解绑输入法的流程。页面只保留一个自绘编辑框、绑定/解绑按钮和状态提示。

示例代码入口为`AttachEditor`函数，由页面的绑定操作调用。`PreviewTextStyleObjectExample`演示样式对象的创建、设置、读取和销毁；编辑框显示的内容与样式仅来自真实回调。该工程包含JS、C两个编辑器页面。从JS页面点击“打开C编辑器”进入C页面，点击“返回JS”返回JS页面。

> **说明：**
>
> 需要在CMakeLists.txt中添加libace_napi.z.so、libohinputmethod.so和libhilog_ndk.z.so依赖。SDK与设备运行库需提供相应公开接口，应用原生库架构需与设备一致。

   <!-- @[input_case_input_CPreview016](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   #include <algorithm>
   #include <mutex>
   #include <string>

   #include "PreviewDisplayState.h"

   #include "hilog/log.h"
   #include "inputmethod/inputmethod_text_editor_proxy_capi.h"
   #include "inputmethod/inputmethod_preview_text_style_capi.h"
   #include "inputmethod/inputmethod_controller_capi.h"
   #include "napi/native_api.h"

   static PreviewDisplayState g_display;
   static std::mutex g_textMutex;
   static InputMethod_TextEditorProxy *textEditorProxy = nullptr;
   static InputMethod_AttachOptions *attachOptions = nullptr;
   static InputMethod_InputMethodProxy *inputMethodProxy = nullptr;

   void GetTextConfigFunc(InputMethod_TextEditorProxy *proxy, InputMethod_TextConfig *config)
   {
       // 处理获取输入框配置请求
       auto ret = OH_TextConfig_SetEnterKeyType(config, InputMethod_EnterKeyType::IME_ENTER_KEY_SEND);
       if (ret != IME_ERR_OK) {
           OH_LOG_Print(LOG_APP, LOG_ERROR, 0xF811, "PreviewTextStyleC", "SetEnterKeyType failed, ret=%{public}d", ret);
           return;
       }

       ret = OH_TextConfig_SetInputType(config, InputMethod_TextInputType::IME_TEXT_INPUT_TYPE_TEXT);
       if (ret != IME_ERR_OK) {
           OH_LOG_Print(LOG_APP, LOG_ERROR, 0xF811, "PreviewTextStyleC", "SetInputType failed, ret=%{public}d", ret);
           return;
       }

       ret = OH_TextConfig_SetPreviewTextSupport(config, true);
       if (ret != IME_ERR_OK) {
           OH_LOG_Print(LOG_APP, LOG_ERROR, 0xF811, "PreviewTextStyleC",
               "SetPreviewTextSupport failed, ret=%{public}d", ret);
       }
   }

   void InsertTextFunc(InputMethod_TextEditorProxy *proxy, const char16_t *text, size_t length)
   {
       if (text == nullptr) {
           return;
       }
       std::lock_guard<std::mutex> lock(g_textMutex);
       g_display.text.append(text, length);
       g_display.active = false;
   }

   // 框架为兼容性反转输入方向；C编辑框的向后删除表示退格。
   void DeleteBackwardFunc(InputMethod_TextEditorProxy *proxy, int32_t length)
   {
       std::lock_guard<std::mutex> lock(g_textMutex);
       if (length <= 0) {
           return;
       }
       size_t count = std::min(static_cast<size_t>(length), g_display.text.size());
       size_t start = g_display.text.size() - count;
       if (start > 0 && start < g_display.text.size() && g_display.text[start] >= 0xDC00 &&
           g_display.text[start] <= 0xDFFF && g_display.text[start - 1] >= 0xD800 &&
           g_display.text[start - 1] <= 0xDBFF) {
           --start;
       }
       g_display.text.erase(start);
       g_display.active = false;
   }

   void DeleteForwardFunc(InputMethod_TextEditorProxy *proxy, int32_t length)
   {
       std::lock_guard<std::mutex> lock(g_textMutex);
       // 本示例将光标保持在文本末尾，光标右侧没有文本。
   }

   void SendKeyboardStatusFunc(InputMethod_TextEditorProxy *proxy, InputMethod_KeyboardStatus status)
   {
       // 无需处理：本示例通过编辑回调更新显示状态。
   }

   void SendEnterKeyFunc(InputMethod_TextEditorProxy *proxy, InputMethod_EnterKeyType type)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC", "C enter action=%{public}d", type);
   }

   void MoveCursorFunc(InputMethod_TextEditorProxy *proxy, InputMethod_Direction direction)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC", "C cursor request=%{public}d", direction);
   }

   void HandleSetSelectionFunc(InputMethod_TextEditorProxy *proxy, int32_t start, int32_t end)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC",
           "C selection request=%{public}d,%{public}d", start, end);
   }

   void HandleExtendActionFunc(InputMethod_TextEditorProxy *proxy, InputMethod_ExtendAction action)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC", "C edit action=%{public}d", action);
   }

   void GetLeftTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, int32_t number, char16_t text[], size_t *length)
   {
       if (length == nullptr) {
           return;
       }
       if (text == nullptr || number <= 0) {
           *length = 0;
           return;
       }
       std::lock_guard<std::mutex> lock(g_textMutex);
       const size_t count = std::min(static_cast<size_t>(number), g_display.text.size());
       std::copy(g_display.text.end() - count, g_display.text.end(), text);
       *length = count;
   }

   void GetRightTextOfCursorFunc(InputMethod_TextEditorProxy *proxy, int32_t number, char16_t text[], size_t *length)
   {
       if (length != nullptr) {
           *length = 0;
       }
   }

   int32_t GetTextIndexAtCursorFunc(InputMethod_TextEditorProxy *proxy)
   {
       std::lock_guard<std::mutex> lock(g_textMutex);
       return static_cast<int32_t>(g_display.text.size());
   }

   int32_t ReceivePrivateCommandFunc(InputMethod_TextEditorProxy *proxy, InputMethod_PrivateCommand *privateCommand[],
       size_t size)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xF811, "PreviewTextStyleC", "C private command received");
       return 0;
   }

   // OH_InputMethodController_Attach要求注册SetPreviewText回调；样式由带样式的回调处理。
   int32_t SetPreviewTextFunc(InputMethod_TextEditorProxy *proxy, const char16_t *text, size_t length,
       int32_t start, int32_t end)
   {
       return text == nullptr ? IME_ERR_NULL_POINTER : IME_ERR_OK;
   }


   int32_t SetPreviewTextWithStyleFunc(InputMethod_TextEditorProxy *proxy, const char16_t *text, uint32_t length,
       int32_t start, int32_t end, const OH_InputMethod_PreviewTextStyle *style)
   {
       if (text == nullptr || style == nullptr) {
           return IME_ERR_NULL_POINTER;
       }
       OH_InputMethod_UnderlineStyle kind = OH_INPUTMETHOD_UNDERLINE_STYLE_NONE;
       uint32_t color = 0;
       bool hasColor = false;
       // 读取框架传入的样式对象，其生命周期由输入法框架管理。
       // C接口接收非const指针，但此处仅读取框架持有的对象。
       auto *readStyle = const_cast<OH_InputMethod_PreviewTextStyle *>(style);
       auto result = OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(readStyle, &kind);
       if (result != IME_ERR_OK) {
           return result;
       }
       result = OH_InputMethod_PreviewTextStyle_GetUnderlineColor(readStyle, &color);
       if (result != IME_ERR_OK) {
           return result;
       }
       result = OH_InputMethod_PreviewTextStyle_HasUnderlineColor(readStyle, &hasColor);
       if (result != IME_ERR_OK) {
           return result;
       }
       std::lock_guard<std::mutex> lock(g_textMutex);
       g_display.ApplyStyled(text, length, static_cast<int32_t>(kind), color, hasColor);
       return IME_ERR_OK;
   }


   void FinishTextPreviewFunc(InputMethod_TextEditorProxy *proxy)
   {
       std::lock_guard<std::mutex> lock(g_textMutex);
       g_display.active = false;
   }

   int32_t ConstructTextEditorProxy(InputMethod_TextEditorProxy *textEditorProxy)
   {
       OH_TextEditorProxy_SetGetTextConfigFunc(textEditorProxy, GetTextConfigFunc);
       OH_TextEditorProxy_SetInsertTextFunc(textEditorProxy, InsertTextFunc);
       OH_TextEditorProxy_SetDeleteForwardFunc(textEditorProxy, DeleteForwardFunc);
       OH_TextEditorProxy_SetDeleteBackwardFunc(textEditorProxy, DeleteBackwardFunc);
       OH_TextEditorProxy_SetSendKeyboardStatusFunc(textEditorProxy, SendKeyboardStatusFunc);
       OH_TextEditorProxy_SetSendEnterKeyFunc(textEditorProxy, SendEnterKeyFunc);
       OH_TextEditorProxy_SetMoveCursorFunc(textEditorProxy, MoveCursorFunc);
       OH_TextEditorProxy_SetHandleSetSelectionFunc(textEditorProxy, HandleSetSelectionFunc);
       OH_TextEditorProxy_SetHandleExtendActionFunc(textEditorProxy, HandleExtendActionFunc);
       OH_TextEditorProxy_SetGetLeftTextOfCursorFunc(textEditorProxy, GetLeftTextOfCursorFunc);
       OH_TextEditorProxy_SetGetRightTextOfCursorFunc(textEditorProxy, GetRightTextOfCursorFunc);
       OH_TextEditorProxy_SetGetTextIndexAtCursorFunc(textEditorProxy, GetTextIndexAtCursorFunc);
       OH_TextEditorProxy_SetReceivePrivateCommandFunc(textEditorProxy, ReceivePrivateCommandFunc);
       auto result = OH_TextEditorProxy_SetSetPreviewTextFunc(textEditorProxy, SetPreviewTextFunc);
       if (result != IME_ERR_OK) {
           return result;
       }
       result = OH_InputMethod_TextEditorProxy_SetSetPreviewTextWithStyleFunc(
           textEditorProxy, SetPreviewTextWithStyleFunc);
       if (result != IME_ERR_OK) {
           return result;
       }
       OH_InputMethod_TextEditorProxy_SetPreviewTextWithStyleFunc registered = nullptr;
       result = OH_InputMethod_TextEditorProxy_GetSetPreviewTextWithStyleFunc(textEditorProxy, &registered);
       if (result != IME_ERR_OK) {
           return result;
       }
       if (registered != SetPreviewTextWithStyleFunc) {
           return IME_ERR_UNDEFINED;
       }
       return OH_TextEditorProxy_SetFinishTextPreviewFunc(textEditorProxy, FinishTextPreviewFunc);
   }
   ```


   <!-- @[input_case_input_CPreview208](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/cpp/napi_init.cpp) -->

   ```cpp
   // 解绑失败时原生代理可能已被删除，重新启动前停止复用。
   static int g_releaseError = IME_ERR_OK;
   static int ReleaseCEditor()
   {
       {
           std::lock_guard<std::mutex> lock(g_textMutex);
           g_display.active = false;
       }
       if (g_releaseError != IME_ERR_OK) {
           return g_releaseError;
       }
       if (inputMethodProxy != nullptr) {
           OH_InputMethodProxy_HideKeyboard(inputMethodProxy);
           const int ret = OH_InputMethodController_Detach(inputMethodProxy);
           inputMethodProxy = nullptr;
           if (ret != IME_ERR_OK) {
               g_releaseError = ret;
               return ret;
           }
       }
       if (textEditorProxy != nullptr) {
           OH_TextEditorProxy_Destroy(textEditorProxy);
           textEditorProxy = nullptr;
       }
       if (attachOptions != nullptr) {
           OH_AttachOptions_Destroy(attachOptions);
           attachOptions = nullptr;
       }
       return IME_ERR_OK;
   }


   // 样式对象的创建与销毁示例，不依赖接收到的预上屏内容。
   static int32_t PreviewTextStyleObjectExample()
   {
       auto *style = OH_InputMethod_PreviewTextStyle_Create();
       if (style == nullptr) {
           return IME_ERR_NULL_POINTER;
       }
       auto result = OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(style, OH_INPUTMETHOD_UNDERLINE_STYLE_WAVY);
       if (result == IME_ERR_OK) {
           result = OH_InputMethod_PreviewTextStyle_SetUnderlineColor(style, 0x00FF0000);
       }
       OH_InputMethod_UnderlineStyle kind = OH_INPUTMETHOD_UNDERLINE_STYLE_NONE;
       uint32_t color = 0;
       bool hasColor = false;
       if (result == IME_ERR_OK) {
           result = OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(style, &kind);
       }
       if (result == IME_ERR_OK) {
           result = OH_InputMethod_PreviewTextStyle_GetUnderlineColor(style, &color);
       }
       if (result == IME_ERR_OK) {
           result = OH_InputMethod_PreviewTextStyle_HasUnderlineColor(style, &hasColor);
       }
       OH_InputMethod_PreviewTextStyle_Destroy(style);
       return result;
   }


   static int32_t AttachEditor()
   {
       auto result = ReleaseCEditor();
       if (result != IME_ERR_OK) {
           return result;
       }
       result = PreviewTextStyleObjectExample();
       if (result != IME_ERR_OK) {
           return result;
       }
       textEditorProxy = OH_TextEditorProxy_Create();
       if (textEditorProxy == nullptr) {
           return IME_ERR_NULL_POINTER;
       }
       {
           std::lock_guard<std::mutex> lock(g_textMutex);
           g_display = PreviewDisplayState{};
       }
       result = ConstructTextEditorProxy(textEditorProxy);
       if (result != IME_ERR_OK) {
           ReleaseCEditor();
           return result;
       }
       attachOptions = OH_AttachOptions_Create(true);
       if (attachOptions == nullptr) {
           ReleaseCEditor();
           return IME_ERR_NULL_POINTER;
       }
       result = OH_InputMethodController_Attach(textEditorProxy, attachOptions, &inputMethodProxy);
       if (result != IME_ERR_OK) {
           inputMethodProxy = nullptr;
           ReleaseCEditor();
       }
       return result;
   }

   static napi_value AttachInputMethod(napi_env env, napi_callback_info info)
   {
       napi_value result;
       napi_create_int32(env, AttachEditor(), &result);
       return result;
   }

   static napi_value InputMethodDestroy(napi_env env, napi_callback_info info)
   {
       napi_value result;
       napi_create_int32(env, ReleaseCEditor(), &result);
       return result;
   }

   static napi_value IsInputMethodAttached(napi_env env, napi_callback_info info)
   {
       napi_value result;
       napi_get_boolean(env, inputMethodProxy != nullptr, &result);
       return result;
   }

   static napi_value ShowInputMethodKeyboard(napi_env env, napi_callback_info info)
   {
       const auto code = inputMethodProxy == nullptr ? IME_ERR_NULL_POINTER :
           OH_InputMethodProxy_ShowKeyboard(inputMethodProxy);
       napi_value result;
       napi_create_int32(env, code, &result);
       return result;
   }

   static napi_value GetCEditorDisplay(napi_env env, napi_callback_info info)
   {
       std::lock_guard<std::mutex> lock(g_textMutex);
       napi_value result;
       napi_value value;
       napi_create_object(env, &result);
       napi_create_string_utf16(env, g_display.text.data(), g_display.text.size(), &value);
       napi_set_named_property(env, result, "text", value);
       napi_get_boolean(env, g_display.active, &value);
       napi_set_named_property(env, result, "active", value);
       napi_create_int32(env, g_display.underlineStyle, &value);
       napi_set_named_property(env, result, "underlineStyle", value);
       napi_create_uint32(env, g_display.underlineColor, &value);
       napi_set_named_property(env, result, "underlineColor", value);
       napi_get_boolean(env, g_display.hasUnderlineColor, &value);
       napi_set_named_property(env, result, "hasUnderlineColor", value);
       return result;
   }

   EXTERN_C_START
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           { "attachInputMethod", nullptr, AttachInputMethod, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "isInputMethodAttached", nullptr, IsInputMethodAttached, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "showInputMethodKeyboard", nullptr, ShowInputMethodKeyboard, nullptr, nullptr,
               nullptr, napi_default, nullptr },
           { "getCEditorDisplay", nullptr, GetCEditorDisplay, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "inputMethodDestroy", nullptr, InputMethodDestroy, nullptr, nullptr, nullptr, napi_default, nullptr },
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   EXTERN_C_END

   static napi_module sampleModule = {
       .nm_version = 1,
       .nm_flags = 0,
       .nm_filename = nullptr,
       .nm_register_func = Init,
       .nm_modname = "entry",
       .nm_priv = nullptr,
       .reserved = { 0 },
   };

   extern "C" __attribute__((constructor)) void RegisterEntryModule(void)
   {
       napi_module_register(&sampleModule);
   }
   ```
