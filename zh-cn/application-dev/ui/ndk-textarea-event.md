# 监听输入框事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @kangshihui-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @HelloCrease-->

输入框包含多种交互行为，开发者可注册事件监听并获取状态。

要实现实时搜索功能，可注册[NODE_TEXT_AREA_ON_CHANGE](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件，输入框文本发生变化时会收到通知，并能获取当前文本内容。

要实现文字过滤功能，可注册[NODE_TEXT_AREA_ON_WILL_INSERT](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件，在文字即将插入前会收到通知，通过返回值控制文字是否插入。

要实现用户编辑文字前后页面布局的不同，可注册[NODE_TEXT_AREA_ON_EDIT_CHANGE](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件，输入框编辑状态切换时会收到通知。

以下示例基于[接入ArkTS页面章节](../ui/ndk-access-the-arkts-page.md)，说明如何监听输入框的事件及数据解析。

- 注册事件
    
    事件注册有统一接口，详情请参见[registerNodeEvent](../../application-dev/reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)。输入框支持的事件类型，请参见[NativeNode组件支持的事件类型定义](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，搜索前缀NODE_TEXT_AREA_。

    <!-- @[obtain_create_textarea](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextAreaEventNDK/entry/src/main/cpp/manager.cpp) -->

- 注册事件回调

    事件回调注册有统一接口，详情请参见[registerNodeEventReceiver](../../application-dev/reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver)。

    <!-- @[obtain_textarea_NodeEventReceiver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextAreaEventNDK/entry/src/main/cpp/manager.cpp) -->

- 完整示例

   本篇示例仅提供核心接口的调用方法，完整的示例工程请参考<!--RP1-->[TextAreaEventNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/TextAreaEventNDK)<!--RP1End-->。
    
    <!-- @[obtain_textarea_all](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextAreaEventNDK/entry/src/main/cpp/manager.cpp) -->


![textarea_getstringevent](figures/textarea_getstringevent.gif)