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
   
   ``` C++
   int32_t AccessibilityManager::FindAccessibilityNodeInfosById(const char* instanceId, int64_t elementId,
       ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList *elementList)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                    "FindAccessibilityNodeInfosById start,instanceId %{public}s elementId: %{public}ld, "
                    "requestId: %{public}d, mode: %{public}d", instanceId,
                    elementId, requestId, static_cast<int32_t>(mode));
       if (elementList == nullptr) {
           OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                        "FindAccessibilityNodeInfosById elementList is null");
           return OH_NATIVEXCOMPONENT_RESULT_FAILED;
       }
       int ret = 0;
       const int parentOfRoot = -2100000;
       if (elementId == -1) {
           elementId = 0;
       }
       
       if (mode == ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_RECURSIVE_CHILDREN) {
           // 三方框架需要在该方法中实现自己的查找策略，返回无障碍节点信息给无障碍服务，以下逻辑仅为示意过程。
           // ArkUI框架设计的特殊值，根节点必须设置parentId为这个值。
           auto rootNode = OH_ArkUI_AddAndGetAccessibilityElementInfo(elementList);
           if (!rootNode) {
               return OH_NATIVEXCOMPONENT_RESULT_FAILED;
           }
           OH_ArkUI_AccessibilityElementInfoSetElementId(rootNode, 0);
           OH_ArkUI_AccessibilityElementInfoSetParentId(rootNode, parentOfRoot);
           FakeWidget::Instance().fillAccessibilityElement(rootNode);
   
           ArkUI_AccessibleRect rect;
           rect.leftTopX = NUMBER_ZERO;
           rect.leftTopY = NUMBER_ZERO;
           rect.rightBottomX = NUMBER_THIRD;
           rect.rightBottomY = NUMBER_THIRD;
           ret = OH_ArkUI_AccessibilityElementInfoSetScreenRect(rootNode, &rect);
           OH_ArkUI_AccessibilityElementInfoSetAccessibilityLevel(rootNode, "no");
           auto objects = FakeWidget::Instance().GetAllObjects(instanceId);
           int64_t childNodes[1024];
           for (int i = 0; i < objects.size(); i++) {
               int elementId = i + 1;
   
               childNodes[i] = elementId;
           }
           for (int i = 0; i < objects.size(); i++) {
               int elementId = i + 1;
               childNodes[i] = elementId;
               auto child = OH_ArkUI_AddAndGetAccessibilityElementInfo(elementList);
               OH_ArkUI_AccessibilityElementInfoSetElementId(child, elementId);
               OH_ArkUI_AccessibilityElementInfoSetParentId(child, 0);
               OH_ArkUI_AccessibilityElementInfoSetAccessibilityLevel(child, "yes");
               objects[i]->fillAccessibilityElement(child);
   
               ArkUI_AccessibleRect rect;
               rect.leftTopX = i * NUMBER_FIRST;
               rect.leftTopY = NUMBER_FIRST;
               rect.rightBottomX = i * NUMBER_FIRST + NUMBER_FIRST;
               rect.rightBottomY = NUMBER_SECOND;
               OH_ArkUI_AccessibilityElementInfoSetScreenRect(child, &rect);
               if (objects[i]->ObjectType() == "FakeSlider") {
                   auto rangeInfo = objects[i]->GetRangeInfo();
                   OH_ArkUI_AccessibilityElementInfoSetRangeInfo(child, &rangeInfo);
               }
               if (objects[i]->ObjectType() == "FakeList") {
                   auto gridInfo = objects[i]->GetGridInfo();
                   OH_ArkUI_AccessibilityElementInfoSetGridInfo(child, &gridInfo);
               }
               if (objects[i]->ObjectType() == "FakeSwiper") {
                   auto gridItemInfo = objects[i]->GetGridItemInfo();
                   OH_ArkUI_AccessibilityElementInfoSetGridItemInfo(child, &gridItemInfo);
               }
           }
   
           ret = OH_ArkUI_AccessibilityElementInfoSetChildNodeIds(rootNode, objects.size(), childNodes);
           OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                        "FindAccessibilityNodeInfosById child count: %{public}ld %{public}d",
                        objects.size(), ret);
       } else if (mode == ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_CURRENT) {
           auto &widget = FakeWidget::Instance();
           AccessibleObject *obj = nullptr;
           if (elementId == 0) {
               obj = &widget;
           } else {
               obj = widget.GetChild(elementId);
           }
           if (!obj) {
               return OH_NATIVEXCOMPONENT_RESULT_FAILED;
           }
           auto node = OH_ArkUI_AddAndGetAccessibilityElementInfo(elementList);
           OH_ArkUI_AccessibilityElementInfoSetElementId(node, elementId);
           OH_ArkUI_AccessibilityElementInfoSetParentId(node, elementId == 0 ? parentOfRoot : 0);
           OH_ArkUI_AccessibilityElementInfoSetAccessibilityLevel(node, elementId == 0 ?  "no" : "yes");
           obj->fillAccessibilityElement(node);
           ArkUI_AccessibleRect rect;
           if (elementId == 0) {
               rect.leftTopX = NUMBER_ZERO;
               rect.leftTopY = NUMBER_ZERO;
               rect.rightBottomX = NUMBER_THIRD;
               rect.rightBottomY = NUMBER_THIRD;
           } else {
               int i = elementId - 1;
               rect.leftTopX = i * NUMBER_FIRST;
               rect.leftTopY = NUMBER_FIRST;
               rect.rightBottomX = i * NUMBER_FIRST + NUMBER_FIRST;
               rect.rightBottomY = NUMBER_SECOND;
           }
   
           OH_ArkUI_AccessibilityElementInfoSetScreenRect(node, &rect);
           if (elementId == 0) {
               auto objects = FakeWidget::Instance().GetAllObjects(instanceId);
               int64_t childNodes[1024];
   
               for (int i = 0; i < objects.size(); i++) {
                   int elementId = i + 1;
   
                   childNodes[i] = elementId;
                   auto child = OH_ArkUI_AddAndGetAccessibilityElementInfo(elementList);
                   OH_ArkUI_AccessibilityElementInfoSetElementId(child, elementId);
                   OH_ArkUI_AccessibilityElementInfoSetParentId(child, 0);
   
                   objects[i]->fillAccessibilityElement(child);
   
                   ArkUI_AccessibleRect rect;
                   rect.leftTopX = i * NUMBER_FIRST;
                   rect.leftTopY = NUMBER_ZERO;
                   rect.rightBottomX = i * NUMBER_FIRST + NUMBER_FIRST;
                   rect.rightBottomY = NUMBER_SECOND;
                   OH_ArkUI_AccessibilityElementInfoSetScreenRect(child, &rect);
               }
               ret = OH_ArkUI_AccessibilityElementInfoSetChildNodeIds(node, objects.size(), childNodes);
               OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                            "FindAccessibilityNodeInfosById child2 count: %{public}ld", objects.size());
           }
       }
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "FindAccessibilityNodeInfosById end");
       return OH_NATIVEXCOMPONENT_RESULT_SUCCESS;
   }
   ```



   <!-- @[abilitycap_three_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->
   
   ``` C++
   int32_t AccessibilityManager::FindNextFocusAccessibilityNode(const char* instanceId, int64_t elementId,
       ArkUI_AccessibilityFocusMoveDirection direction, int32_t requestId,
       ArkUI_AccessibilityElementInfo *elementInfo)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                    "FindNextFocusAccessibilityNode instanceId %{public}s "
                    "elementId: %{public}ld, requestId: %{public}d, direction: %{public}d",
                    instanceId, elementId, requestId, static_cast<int32_t>(direction));
       auto objects = FakeWidget::Instance().GetAllObjects(instanceId);
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "objects.size() %{public}d", objects.size());
       // object.size 不包含 root节点
       if ((elementId < 0) || (elementId > objects.size())) {
           OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "elementId invalid");
           return OH_NATIVEXCOMPONENT_RESULT_FAILED;
       }
       int64_t nextElementId = -1;
       if (direction == ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_FORWARD) {
           nextElementId = elementId + 1;
       } else {
           nextElementId = elementId - 1;
       }
       
       // 屏幕朗读约束 如果是根节点 然后backward的话需要回到最后一个节点
       if ((nextElementId == -1) && (direction == ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_BACKWARD)) {
           nextElementId = objects.size();
       }
       
       if (nextElementId >  objects.size()) {
           OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "nextElementId invalid");
           return OH_NATIVEXCOMPONENT_RESULT_FAILED;
       }
       
       if (nextElementId <=  0) {
           OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "nextElementId less than zero");
           return OH_NATIVEXCOMPONENT_RESULT_FAILED;
       }
       OH_ArkUI_AccessibilityElementInfoSetElementId(elementInfo, nextElementId);
       OH_ArkUI_AccessibilityElementInfoSetParentId(elementInfo, 0);
       // id 比object索引大1
       objects[nextElementId - 1]->fillAccessibilityElement(elementInfo);
       ArkUI_AccessibleRect rect;
       rect.leftTopX = nextElementId * NUMBER_FIRST;
       rect.leftTopY = NUMBER_ZERO;
       rect.rightBottomX = nextElementId * NUMBER_FIRST + NUMBER_FIRST;
       rect.rightBottomY = NUMBER_SECOND;
       OH_ArkUI_AccessibilityElementInfoSetScreenRect(elementInfo, &rect);
       auto eventInfo = OH_ArkUI_CreateAccessibilityEventInfo();
       OH_ArkUI_AccessibilityEventSetRequestFocusId(eventInfo, requestId);
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "%{public}ld", nextElementId);
       return OH_NATIVEXCOMPONENT_RESULT_SUCCESS;
   }
   ```



   <!-- @[abilitycap_four_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->
   
   ``` C++
   int32_t AccessibilityManager::FindAccessibilityNodeInfosByText(const char* instanceId, int64_t elementId,
       const char *text, int32_t requestId, ArkUI_AccessibilityElementInfoList *elementList)
   {
       // 三方框架需实现根据文本内容查询无障碍节点的逻辑。
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                    "FindAccessibilityNodeInfosByText start,instanceId %{public}s elementId: %{public}ld, "
                    "requestId: %{public}d, text: %{public}s.", instanceId,
                    elementId, requestId, text);
       return OH_NATIVEXCOMPONENT_RESULT_SUCCESS;
   }
   ```



   <!-- @[abilitycap_five_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->
   
   ``` C++
   int32_t AccessibilityManager::FindFocusedAccessibilityNode(const char* instanceId, int64_t elementId,
       ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo *elementInfo)
   {
       // 三方框架需实现基于指定节点获取焦点元素信息的逻辑。
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                    "FindFocusedAccessibilityNode start instanceId %{public}s, "
                    "elementId: %{public}ld, requestId: %{public}d, focusType: %{public}d",
                    instanceId, elementId, requestId, static_cast<int32_t>(focusType));
       return OH_NATIVEXCOMPONENT_RESULT_SUCCESS;
   }
   ```



   <!-- @[abilitycap_six_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->
   
   ``` C++
   void FillEvent(ArkUI_AccessibilityEventInfo *eventInfo, ArkUI_AccessibilityElementInfo *elementInfo,
                  ArkUI_AccessibilityEventType eventType, std::string announcedText)
   {
       if (eventInfo == nullptr) {
           return;
       }
       if (elementInfo == nullptr) {
           return;
       }
       OH_ArkUI_AccessibilityEventSetEventType(eventInfo, eventType);
   
       OH_ArkUI_AccessibilityEventSetElementInfo(eventInfo, elementInfo);
       
       if (eventType == ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ANNOUNCE_FOR_ACCESSIBILITY && announcedText.size() > 0) {
           OH_ArkUI_AccessibilityEventSetTextAnnouncedForAccessibility(eventInfo, announcedText.data());
       }
   }
   
   // ···
   
   void AccessibilityManager::SendAccessibilityAsyncEvent(ArkUI_AccessibilityElementInfo *elementInfo,
                                                          ArkUI_AccessibilityEventType eventType,
                                                          std::string announcedText)
   {
       auto eventInfo = OH_ArkUI_CreateAccessibilityEventInfo();
       // 1.填写event内容
       FillEvent(eventInfo, elementInfo, eventType, announcedText);
       // 2.callback
       auto callback = [](int32_t errorCode) {
           OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "result: %{public}d", errorCode);
       };
       // 3. 调用接口发送事件给OH侧
       OH_ArkUI_SendAccessibilityAsyncEvent(g_provider, eventInfo, callback);
   }
   // [EndExclude abilitycap_one_start]
   // ···
   
   int32_t AccessibilityManager::ExecuteAccessibilityAction(const char* instanceId, int64_t elementId,
       ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)
   {
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                    "ExecuteAccessibilityAction instanceId %{public}s elementId: %{public}ld, "
                    "action: %{public}d, requestId: %{public}d",
                    instanceId, elementId, action, requestId);
       auto object = FakeWidget::Instance().GetChild(elementId);
       if (!object) {
           return 0;
       }
       auto announcedText = object->GetAnnouncedForAccessibility();
       auto element = OH_ArkUI_CreateAccessibilityElementInfo();
       OH_ArkUI_AccessibilityElementInfoSetElementId(element, elementId);
       const char *actionKey = "some_key";
       char *actionValue = nullptr;
       OH_ArkUI_FindAccessibilityActionArgumentByKey(actionArguments, actionKey, &actionValue);
       switch (action) {
           case ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CLICK:
               if (object) {
                   object->OnClick();
                   object->fillAccessibilityElement(element);
               }
               AccessibilityManager::SendAccessibilityAsyncEvent(element,
                   ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_CLICKED, announcedText);
               break;
           case ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_GAIN_ACCESSIBILITY_FOCUS:
               if (object) {
                   object->SetFocus(true);
   
                   object->fillAccessibilityElement(element);
               }
               // 向无障碍服务发送指定事件。
               AccessibilityManager::SendAccessibilityAsyncEvent(element,
                   ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ACCESSIBILITY_FOCUSED,
                   announcedText);
               break;
           case ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CLEAR_ACCESSIBILITY_FOCUS:
               if (object) {
                   object->SetFocus(false);
                   object->fillAccessibilityElement(element);
               }
               AccessibilityManager::SendAccessibilityAsyncEvent(
                   element, ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ACCESSIBILITY_FOCUS_CLEARED,
                   announcedText);
               break;
           default:
               // 处理不支持的action行为。
               break;
       }
       OH_ArkUI_DestoryAccessibilityElementInfo(element);
       return OH_NATIVEXCOMPONENT_RESULT_SUCCESS;
   }
   ```



   <!-- @[abilitycap_seven_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->
   
   ``` C++
   int32_t AccessibilityManager::ClearFocusedFocusAccessibilityNode(const char* instanceId)
   {
       // 三方框架需要实现清除当前获焦的节点的行为。
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                    "ClearFocusedFocusAccessibilityNode, instanceId %{public}s", instanceId);
       return OH_NATIVEXCOMPONENT_RESULT_SUCCESS;
   }
   ```



   <!-- @[abilitycap_eight_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->
   
   ``` C++
   int32_t AccessibilityManager::GetAccessibilityNodeCursorPosition(const char* instanceId, int64_t elementId,
       int32_t requestId, int32_t *index)
   {
       // 三方框架需要实现获取当前组件中（文本组件）光标位置。
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                    "GetAccessibilityNodeCursorPosition, instanceId %{public}s "
                    "elementId: %{public}ld, requestId: %{public}d, index: %{public}d",
                    instanceId, elementId, requestId, index);
       return OH_NATIVEXCOMPONENT_RESULT_SUCCESS;
   }
   ```

4. 对接成功后，可开启无障碍功能。
