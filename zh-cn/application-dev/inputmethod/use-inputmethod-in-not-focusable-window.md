# 不可获焦窗口中输入框与输入法交互指南

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

应用获得焦点是使用输入法的必要条件，开发者需要正确处理焦点以确保输入法的正常工作。

例如，在应用开发中，开发者可以通过[setWindowFocusable](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9)，将创建的窗口的可获焦属性设置为false（如悬浮窗、辅助交互窗口等），并希望在该窗口中绘制输入框（如[TextInput](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md)、[TextArea](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md)或[自绘输入框](use-inputmethod-in-custom-edit-box.md)）以支持用户输入，即拉起系统键盘进行输入操作。

## 系统限制

当通过[setWindowFocusable](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9)将窗口设置为不可获焦时，系统侧会对该窗口施加限制。由于窗口无焦点，输入事件（如按键信息）无法被窗口正确接收和处理，输入内容无法同步到该窗口中的输入框，导致输入框与键盘交互异常。

## 推荐方案

若需要在不可获焦窗口中绘制输入框，并希望能够与键盘正常交互，建议按照以下方式开发（以[TextInput](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md)为例）：

1. 在主窗中创建一个子窗，设置其初始为不可获焦窗口。

   实现效果：点击主窗输入组件，弹出子窗，焦点仍然在主窗的输入框上。

   ArkTS-Dyn示例：

   <!-- @[input_case_input_create_not_focusable_subwindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/KikaInputMethod/entry/src/main/ets/pages/NotFocusableWindowDemo.ets) -->

   ArkTS-Sta示例：

   <!-- @[input_case_input_create_not_focusable_subwindow](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/InputMethod/SimpleKeyboard/entry/src/main/ets/pages/NotFocusableWindowDemo.ets) -->
   

2. 当用户点击子窗中的输入框组件时，可以先通过[setWindowFocusable](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9)将子窗设置为可获焦，然后通过[shiftAppWindowFocus](../reference/apis-arkui/arkts-apis-window-f.md#windowshiftappwindowfocus11)将焦点窗口从主窗切换为子窗，即可在子窗的输入框中正常使用输入法。
   ArkTS-Dyn示例：

   <!-- @[input_case_input_shift_focus_in_not_focusable_window](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/KikaInputMethod/entry/src/main/ets/pages/SubWindowIndex.ets) -->

   ArkTS-Sta示例：

   <!-- @[input_case_input_shift_focus_in_not_focusable_window](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/InputMethod/SimpleKeyboard/entry/src/main/ets/pages/SubWindowIndex.ets) -->


3. 当用户重新点击子窗中的非输入框组件时，可以通过[setWindowFocusable](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9)将子窗重新设置为不可获焦，焦点窗口即可恢复至主窗。
   ArkTS-Dyn示例：

   <!-- @[input_case_input_shift_focus_to_main_window](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/KikaInputMethod/entry/src/main/ets/pages/SubWindowIndex.ets) -->

ArkTS-Sta示例：

   <!-- @[input_case_input_shift_focus_to_main_window](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/InputMethod/SimpleKeyboard/entry/src/main/ets/pages/SubWindowIndex.ets) -->
