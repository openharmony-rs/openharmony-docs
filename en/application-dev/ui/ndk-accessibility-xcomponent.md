# Integrating Accessibility Through XComponent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

For third-party framework platforms that are accessed through XComponent, the NDK provides functions for interoperability with accessibility services, enabling third-party framework components to support basic accessibility features in ArkUI. These include focus acquisition, accessibility node retrieval, and operation response.

For single-instance scenarios, use [OH_NativeXComponent_GetNativeAccessibilityProvider](../reference/apis-arkui/capi-native-interface-xcomponent-h.md#oh_nativexcomponent_getnativeaccessibilityprovider) to obtain the accessibility provider, and then register the required callback functions [ArkUI_AccessibilityProviderCallbacks](../reference/apis-arkui/capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md) via [OH_ArkUI_AccessibilityProviderRegisterCallback](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallback).

For multi-instance scenarios, register callback functions [ArkUI_AccessibilityProviderCallbacksWithInstance](../reference/apis-arkui/capi-arkui-accessibility-arkui-accessibilityprovidercallbackswithinstance.md) using [OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallbackwithinstance).

In these callbacks, third-party frameworks must handle accessibility [actions](../reference/apis-arkui/capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) from the accessibility system and send appropriate accessibility [events](../reference/apis-arkui/capi-native-interface-accessibility-h.md#arkui_accessibilityeventtype) based on component interactions.

> **NOTE**
>
> - Accessibility capability enables you to create accessible application UIs for users with visual, auditory, motor, and cognitive disabilities.
> - When implementing query APIs ([OH_ArkUI_AccessibilityProviderRegisterCallback](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallback) or [OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallbackwithinstance)), use [OH_ArkUI_AddAndGetAccessibilityElementInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_addandgetaccessibilityelementinfo) to create and manage accessibility node information.
> - When sending events with [OH_ArkUI_SendAccessibilityAsyncEvent](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_sendaccessibilityasyncevent), create event and element info objects using the appropriate creation functions and destroy them after use. Specifically, create an [ArkUI_AccessibilityEventInfo](../reference/apis-arkui/capi-arkui-accessibility-arkui-accessibilityeventinfo.md) object using [OH_ArkUI_CreateAccessibilityEventInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_createaccessibilityeventinfo) and an [ArkUI_AccessibilityElementInfo](../reference/apis-arkui/capi-arkui-accessibility-arkui-accessibilityelementinfo.md) object using [OH_ArkUI_CreateAccessibilityElementInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_createaccessibilityelementinfo), and then destroy the objects after use with [OH_ArkUI_DestoryAccessibilityEventInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_destoryaccessibilityeventinfo) and [OH_ArkUI_DestoryAccessibilityElementInfo](../reference/apis-arkui/capi-native-interface-accessibility-h.md#oh_arkui_destoryaccessibilityelementinfo).
> - When logging within callback functions, include the provided **requestId** parameter to link logs to a specific interaction process. This practice facilitates indexing and querying and aids in troubleshooting and pinpointing issues.


This example demonstrates accessibility integration. For the complete implementation, see [AccessibilityCapiSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/AccessibilityCapi). Once integrated, third-party framework components in **XComponent** will support accessibility interactions when accessibility features are enabled.

1. Create a project based on [OH_ArkUI_SurfaceHolder for surface lifecycle management](napi-xcomponent-guidelines.md#managing-the-surface-lifecycle-with-oh_arkui_surfaceholder) in custom rendering (XComponent).

2. Obtain the accessibility provider and register callbacks (the following uses the multi-instance scenario as an example).

   <!-- @[abilitycap_one_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AccessibilityCapi/entry/src/main/cpp/manager/AccessibilityManager.cpp) -->
   
   ``` C++
   #include <arkui/native_interface_accessibility.h>
   #include <string>
   #include "common/common.h"
   // For details about the complete implementation, see AccessibilityCapiSample.
   #include "fakenode/fake_node.h"
   // For details about the complete implementation, see AccessibilityCapiSample.
   #include "AccessibilityManager.h"
   
   // ···
   AccessibilityManager::AccessibilityManager()
   {
   // Multi-instance scenario
       accessibilityProviderCallbacksWithInstance_.findAccessibilityNodeInfosById = FindAccessibilityNodeInfosById;
       accessibilityProviderCallbacksWithInstance_.findAccessibilityNodeInfosByText = FindAccessibilityNodeInfosByText;
       accessibilityProviderCallbacksWithInstance_.findFocusedAccessibilityNode = FindFocusedAccessibilityNode;
       accessibilityProviderCallbacksWithInstance_.findNextFocusAccessibilityNode = FindNextFocusAccessibilityNode;
       accessibilityProviderCallbacksWithInstance_.executeAccessibilityAction = ExecuteAccessibilityAction;
       accessibilityProviderCallbacksWithInstance_.clearFocusedFocusAccessibilityNode = ClearFocusedFocusAccessibilityNode;
       accessibilityProviderCallbacksWithInstance_.getAccessibilityNodeCursorPosition = GetAccessibilityNodeCursorPosition;
   // Single-instance scenario
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
       // 2. Register callbacks.
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

3. Third-party frameworks must implement the following callbacks:

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
           // Third-party frameworks must implement custom search logic in this method and return accessibility node information to the accessibility service. The following implementation serves as a reference example only.
           // Special constant defined for ArkUI framework compatibility. Root node parent ID must be set to this specific value.
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
       // object.size does not contain the root node.
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
       
       // Screen reader constraint: If it is the root node and navigating backward, return to the last node.
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
       // The ID is 1 greater than the object index.
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
       // Third-party frameworks need to implement the logic for querying accessibility nodes based on text content.
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
       // Third-party frameworks need to implement the logic for obtaining the focus element information based on a specified node.
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
       // 1. Enter the event content.
       FillEvent(eventInfo, elementInfo, eventType, announcedText);
       // 2. Callback
       auto callback = [](int32_t errorCode) {
           OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "result: %{public}d", errorCode);
       };
       // 3. Call the API to send the event to the OpenHarmony side.
       OH_ArkUI_SendAccessibilityAsyncEvent(g_provider, eventInfo, callback);
   }
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
               // Send the specified event to the accessibility service.
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
               // Handle unsupported action types.
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
       // Third-party frameworks need to implement the logic for clearing the currently focused node.
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
       // Third-party frameworks need to implement the logic for obtaining the cursor position within the current text component.
       OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT,
                    "GetAccessibilityNodeCursorPosition, instanceId %{public}s "
                    "elementId: %{public}ld, requestId: %{public}d, index: %{public}d",
                    instanceId, elementId, requestId, index);
       return OH_NATIVEXCOMPONENT_RESULT_SUCCESS;
   }
   ```

4. After successful integration, enable accessibility features in system settings.
