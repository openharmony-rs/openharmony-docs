# 通过XComponent接入无障碍
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

通过XComponent接入的第三方框架平台，NDK提供了对接无障碍服务的接口函数，使三方框架组件能够支持ArkUI中的基本无障碍功能，包括焦点获取、获取无障碍节点和操作响应。

如果需要支持单实例，使用XComponent的[OH_NativeXComponent_GetNativeAccessibilityProvider](../reference/apis-arkui/capi-native-interface-xcomponent-h.md#oh_nativexcomponent_getnativeaccessibilityprovider)获得无障碍接入provider。然后，通过[OH_ArkUI_AccessibilityProviderRegisterCallback](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallback)注册接入无障碍所需的回调函数[ArkUI_AccessibilityProviderCallbacks](../reference/apis-arkui/capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md)。

如果需要支持多实例，则通过[OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallbackwithinstance)注册接入无障碍所需的回调函数[ArkUI_AccessibilityProviderCallbacksWithInstance](../reference/apis-arkui/capi-arkui-accessibility-arkui-accessibilityprovidercallbackswithinstance.md)。

在上述回调中，三方框架需要适配无障碍系统发出的操作[Action](../reference/apis-arkui/capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype)，并针对组件交互行为发送无障碍事件[Event](../reference/apis-arkui/capi-native-interface-accessibility-h.md#arkui_accessibilityeventtype)到无障碍子系统，实现无障碍辅助应用的交互体验。

> **说明：**
>
> - 无障碍能力：指开发者能够创建可访问的应用界面，满足视觉、听觉、运动和认知障碍等用户需求的能力。
> - 实现[OH_ArkUI_AccessibilityProviderRegisterCallback](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallback)或者[OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallbackwithinstance)回调查询接口时，查询到的每个无障碍节点信息通过[OH_ArkUI_AddAndGetAccessibilityElementInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_addandgetaccessibilityelementinfo)创建分配element内存，并将其加入到指定的elementList中。
> - 使用[OH_ArkUI_SendAccessibilityAsyncEvent](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_sendaccessibilityasyncevent)发送事件时，需要使用[OH_ArkUI_CreateAccessibilityEventInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_createaccessibilityeventinfo)创建[ArkUI_AccessibilityEventInfo](../reference/apis-arkui/capi-arkui-accessibility-arkui-accessibilityeventinfo.md)，使用[OH_ArkUI_CreateAccessibilityElementInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_createaccessibilityelementinfo)创建[ArkUI_AccessibilityElementInfo](../reference/apis-arkui/capi-arkui-accessibility-arkui-accessibilityelementinfo.md)，使用结束后，需要调用[OH_ArkUI_DestoryAccessibilityEventInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_destoryaccessibilityeventinfo)以及[OH_ArkUI_DestoryAccessibilityElementInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_destoryaccessibilityelementinfo)销毁函数释放内存。
> - 回调函数打印日志时，携带输入的requestId，用于关联一次交互过程相关的日志，便于索引查询整个流程，协助问题定位。


以下示例提供了对接无障碍能力的实现方法，仅包含主要步骤，完整示例请参考[AccessibilityCapiSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/AccessibilityCapi)。对接完成后，在开启无障碍功能时，可使XComponent中的三方框架绘制组件接入，实现无障碍交互。

1. 按照自定义渲染（XComponent）的[使用OH_ArkUI_SurfaceHolder管理Surface生命周期](napi-xcomponent-guidelines.md#使用oh_arkui_surfaceholder管理surface生命周期)场景创建前置工程。

2. 获得无障碍接入provider并注册回调函数（以多实例场景为例）。

   <!-- @[abilitycap_one_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->
   
   ``` C++
   #include <arkui/native_interface_accessibility.h>
   #include <string>
   #include "common/common.h"
   // 完整实现请参考AccessibilityCapiSample。
   #include "fakenode/fake_node.h"
   // 完整实现请参考AccessibilityCapiSample。
   #include "AccessibilityManager.h"
   
   // ···
   // [StartExclude abilitycap_six_start]
   AccessibilityManager::AccessibilityManager()
   {
   //    多实例场景
       accessibilityProviderCallbacksWithInstance_.findAccessibilityNodeInfosById = FindAccessibilityNodeInfosById;
       accessibilityProviderCallbacksWithInstance_.findAccessibilityNodeInfosByText = FindAccessibilityNodeInfosByText;
       accessibilityProviderCallbacksWithInstance_.findFocusedAccessibilityNode = FindFocusedAccessibilityNode;
       accessibilityProviderCallbacksWithInstance_.findNextFocusAccessibilityNode = FindNextFocusAccessibilityNode;
       accessibilityProviderCallbacksWithInstance_.executeAccessibilityAction = ExecuteAccessibilityAction;
       accessibilityProviderCallbacksWithInstance_.clearFocusedFocusAccessibilityNode = ClearFocusedFocusAccessibilityNode;
       accessibilityProviderCallbacksWithInstance_.getAccessibilityNodeCursorPosition = GetAccessibilityNodeCursorPosition;
   //    单实例场景
       accessibilityProviderCallbacks_.findAccessibilityNodeInfosById = FindAccessibilityNodeInfosById;
       accessibilityProviderCallbacks_.findAccessibilityNodeInfosByText = FindAccessibilityNodeInfosByText;
       accessibilityProviderCallbacks_.findFocusedAccessibilityNode = FindFocusedAccessibilityNode;
       accessibilityProviderCallbacks_.findNextFocusAccessibilityNode = FindNextFocusAccessibilityNode;
       accessibilityProviderCallbacks_.executeAccessibilityAction = ExecuteAccessibilityAction;
       accessibilityProviderCallbacks_.clearFocusedFocusAccessibilityNode = ClearFocusedFocusAccessibilityNode;
       accessibilityProviderCallbacks_.getAccessibilityNodeCursorPosition = GetAccessibilityNodeCursorPosition;
   }
   
   void AccessibilityManager::Initialize(const std::string &id, OH_NativeXComponent *nativeXComponent)
   {
       int32_t ret = OH_NativeXComponent_GetNativeAccessibilityProvider(nativeXComponent, &provider);
       if (provider == nullptr) {
           OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "get provider is null");
           return;
       }
       // 2.注册回调函数
       ret = OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance(id.c_str(), provider,
           &accessibilityProviderCallbacksWithInstance_);
       if (ret != 0) {
           OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                        "InterfaceDesignTest OH_ArkUI_AccessibilityProviderRegisterCallback failed");
           return;
       }
       g_provider = provider;
   }
   
   // ···
   ```

3. 三方框架需要实现如下回调函数。

   <!-- @[abilitycap_two_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->



   <!-- @[abilitycap_three_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->



   <!-- @[abilitycap_four_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->



   <!-- @[abilitycap_five_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->



   <!-- @[abilitycap_six_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->



   <!-- @[abilitycap_seven_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->



   <!-- @[abilitycap_eight_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->

4. 对接成功后，可开启无障碍功能。
