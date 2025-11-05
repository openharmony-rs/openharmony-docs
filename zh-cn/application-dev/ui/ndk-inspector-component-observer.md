# 监听组件布局和绘制送显事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

从API version 16开始，NDK接口针对UI组件的布局或绘制送显完成，提供了注册与取消监听函数的方式。开发者可使用如下接口监听指定节点布局完成或者绘制送显完成的时机，并注册相应的回调函数。可使用[OH_ArkUI_RegisterLayoutCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerlayoutcallbackonnodehandle)注册组件布局完成的回调方法。可使用[OH_ArkUI_RegisterDrawCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerdrawcallbackonnodehandle)注册绘制送显完成的回调方法。可使用[OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_unregisterlayoutcallbackonnodehandle)取消组件布局完成的回调方法注册。可使用[OH_ArkUI_UnregisterDrawCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_unregisterdrawcallbackonnodehandle)取消绘制送显完成的回调方法注册。


> **说明：**
> [OH_ArkUI_RegisterLayoutCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerlayoutcallbackonnodehandle)和[OH_ArkUI_RegisterDrawCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerdrawcallbackonnodehandle)能够监听组件的布局完成或者绘制送显完成事件触发，但只能传递一个函数指针，多次调用使用最后一次的函数指针进行回调。


以下示例基于[接入ArkTS页面](ndk-access-the-arkts-page.md)章节，补充相关事件监听。
在ArkUITextNode对象中实现布局或者绘制送显完成事件注册逻辑。
<!-- @[arkUITestNode_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NativeNodeUtilsSample/entry/src/main/cpp/ArkUITextNode.h) -->

<!-- @[normalTextListExample_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NativeNodeUtilsSample/entry/src/main/cpp/NormalTextListExample.h) -->