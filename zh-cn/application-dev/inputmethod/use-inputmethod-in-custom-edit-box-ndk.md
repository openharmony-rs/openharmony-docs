# 在自绘编辑框中使用输入法开发指导 (C/C++)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

IME Kit支持开发者在自绘编辑框中使用输入法，与输入法应用交互，包括显示、隐藏输入法，接收来自输入法应用的文本编辑操作通知等，本文档介绍开发者如何使用C/C++完成此功能开发。

## 接口说明

详细接口说明请参考[InputMethod接口文档](../reference/apis-ime-kit/capi-inputmethod.md)。

## 添加动态链接库

CMakeLists.txt中添加以下lib。

```txt
libohinputmethod.so
```

## 引用头文件

```c
#include <inputmethod/inputmethod_controller_capi.h>
```


## 绑定输入法

开发者需要在输入框获焦时，通过调用接口[OH_InputMethodController_Attach](../reference/apis-ime-kit/capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)绑定输入法，绑定成功后用户可以通过输入法输入文字。

1. 创建InputMethod_TextEditorProxy实例，示例代码如下所示：

<!-- @[input_case_input_TextEditorProxy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/cpp/napi_init.cpp) -->

``` C++
    // 创建InputMethod_TextEditorProxy实例
    textEditorProxy = OH_TextEditorProxy_Create();
```

   
3. 创建InputMethod_AttachOptions实例，设置绑定输入法时的选项。示例代码如下所示：

<!-- @[input_case_input_attachOptions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/cpp/napi_init.cpp) -->


4. 调用OH_InputMethodController_Attach发起绑定输入法服务，调用成功后，可以获取到用于和输入法交互的InputMethod_InputMethodProxy。示例代码如下所示：

<!-- @[input_case_input_OH_InputMethodController_Attach](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/cpp/napi_init.cpp) -->


## 显示/隐藏面板功能

绑定成功后，可以使用获取到的[InputMethod_InputMethodProxy](../reference/apis-ime-kit/capi-inputmethod-inputmethod-inputmethodproxy.md)对象向输入法发送消息。示例代码如下所示：

```c
// 显示键盘
if (OH_InputMethodProxy_ShowKeyboard(inputMethodProxy) != InputMethod_ErrorCode::IME_ERR_OK) {
    OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "ShowKeyboard failed!");
}
// 隐藏键盘
if (OH_InputMethodProxy_HideKeyboard(inputMethodProxy) != InputMethod_ErrorCode::IME_ERR_OK) {
    OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "HideKeyboard failed!");
}
// 通知输入框配置信息变化
if (OH_InputMethodProxy_NotifyConfigurationChange(inputMethodProxy, InputMethod_EnterKeyType::IME_ENTER_KEY_GO, InputMethod_TextInputType::IME_TEXT_INPUT_TYPE_TEXT) != InputMethod_ErrorCode::IME_ERR_OK) {
    OH_LOG_Print(LOG_APP, LOG_ERROR, 0, "testTag", "NotifyConfigurationChange failed!");
}
```

## 监听输入法应用的请求/通知

1. 需要先实现对输入法应用发送的请求或通知的响应处理函数，示例代码如下所示：

   ```c
   // 实现InputMethod_TextEditorProxy中的输入法应用事件响应函数
   void GetTextConfig(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_TextConfig *config)
   {
       // 处理输入法发送的获取输入框配置请求
   }
   void InsertText(InputMethod_TextEditorProxy *textEditorProxy, const char16_t *text, size_t length)
   {
       // 处理输入法发送的插入文本请求
   }
   void DeleteForward(InputMethod_TextEditorProxy *textEditorProxy, int32_t length)
   {
       // 处理输入法发送的删除文本请求
   }
   // ......
   ```

2. 将实现后的响应函数，设置到[InputMethod_TextEditorProxy](../reference/apis-ime-kit/capi-inputmethod-inputmethod-texteditorproxy.md)中，再通过绑定输入法时调用的[OH_InputMethodController_Attach](../reference/apis-ime-kit/capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)将其设置到输入法框架中，完成监听注册。示例代码如下所示：

<!-- @[input_case_input_ConstructTextEditorProxy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/cpp/napi_init.cpp) -->

## 解绑输入法

当编辑框失焦，需要结束使用输入法，通过接口[OH_InputMethodController_Detach](../reference/apis-ime-kit/capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_detach)与输入法框架解绑。


<!-- @[input_case_input_OH_InputMethodController_Detach](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/cpp/napi_init.cpp) -->

## 完整示例

示例代码展示了绑定输入法、隐藏输入法、解绑输入法的完整流程。

示例代码总入口为InputMethodNdkDemo函数。

> 说明：
>
> 需要在CMakeList.txt中添加libohinputmethod.so libhilog_ndk.z.so依赖。

<!-- @[input_case_input_CPreview016](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/cpp/napi_init.cpp) -->

<!-- @[input_case_input_CPreview208](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/cpp/napi_init.cpp) -->
