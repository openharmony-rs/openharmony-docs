# 在NDK中保证多实例场景功能正常
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

API version 20开始，ArkUI开发框架新增了[OH_ArkUI_RunTaskInScope](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_runtaskinscope)接口，解决Native侧多实例场景下的组件操作问题。该功能通过动态切换执行上下文，确保跨实例组件属性设置的合法性，避免实例上下文不匹配导致的接口调用异常。

在NDK多窗口开发时，可能会涉及到组件的跨实例设置属性等场景，使用该能力可确保在调用跨实例组件设置属性时的上下文正确性，避免跨实例接口调用失败。

> **说明：**
> - 适用于NDK多窗口开发中不同UI实例间的交互场景，例如在页面B中修改页面A创建的组件属性或未挂载到UI树的组件逻辑。
>
> - 支持通过userData参数传递自定义数据结构（如组件指针、业务参数等），便于在回调任务中精准定位目标组件。
>
> - 与[OH_ArkUI_NodeUtils_GetAttachedNodeHandleById](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getattachednodehandlebyid)等接口配合使用，有效规避跨实例访问导致的空指针或权限异常问题。


本示例展示OH_ArkUI_RunTaskInScope接口的基础使用方式，OH_ArkUI_NodeUtils_GetAttachedNodeHandleById用于获取前置实例页面内的组件，相关使用请参考[OH_ArkUI_NodeUtils_GetAttachedNodeHandleById](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getattachednodehandlebyid)，此处userData传入的数据类型为最终要设置的组件指针，便于设置对应组件属性。


<!-- @[runtaskinscopeone_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkScopeTask/entry/src/main/cpp/napi_init.cpp) -->

<!-- @[runtaskinscopetwo_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkScopeTask/entry/src/main/cpp/napi_init.cpp) -->
