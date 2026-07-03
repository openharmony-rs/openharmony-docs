# native_interface_accessibility.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Declares the APIs for accessing Native Accessibility features.

**File to include**: <arkui/native_interface_accessibility.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Sample**: <!--RP1-->[AccessibilityCapi](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/AccessibilityCapi)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_AccessibleAction](capi-arkui-accessibility-arkui-accessibleaction.md) | ArkUI_AccessibleAction | Defines a struct for accessibility actions.|
| [ArkUI_AccessibleRect](capi-arkui-accessibility-arkui-accessiblerect.md) | ArkUI_AccessibleRect | Provides the bounding rectangle coordinates of the node.|
| [ArkUI_AccessibleRangeInfo](capi-arkui-accessibility-arkui-accessiblerangeinfo.md) | ArkUI_AccessibleRangeInfo | Sets the current value, maximum value, and minimum value for a specific component, such as [Slider](arkui-ts/ts-basic-components-slider.md), [Rating](arkui-ts/ts-basic-components-rating.md), and [Progress](arkui-ts/ts-basic-components-progress.md).|
| [ArkUI_AccessibleGridInfo](capi-arkui-accessibility-arkui-accessiblegridinfo.md) | ArkUI_AccessibleGridInfo | Sets the number of rows, number of columns, and selection mode for a specific component, such as [List](arkui-ts/ts-container-list.md), [Flex](arkui-ts/ts-container-flex.md), [Select](arkui-ts/ts-basic-components-select.md), and [Swiper](arkui-ts/ts-container-swiper.md).|
| [ArkUI_AccessibleGridItemInfo](capi-arkui-accessibility-arkui-accessiblegriditeminfo.md) | ArkUI_AccessibleGridItemInfo | Sets attributes for a specific component, such as [List](arkui-ts/ts-container-list.md), [Flex](arkui-ts/ts-container-flex.md), [Select](arkui-ts/ts-basic-components-select.md), and [Swiper](arkui-ts/ts-container-swiper.md).|
| [ArkUI_AccessibilityProviderCallbacks](capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md) | ArkUI_AccessibilityProviderCallbacks | Defines callback functions of a third-party operation provider, which need to be implemented by third-party platforms and registered with the system using [OH_ArkUI_AccessibilityProviderRegisterCallback](#oh_arkui_accessibilityproviderregistercallback).|
| [ArkUI_AccessibilityProviderCallbacksWithInstance](capi-arkui-accessibility-arkui-accessibilityprovidercallbackswithinstance.md) | ArkUI_AccessibilityProviderCallbacksWithInstance | Defines callback functions of a third-party operation provider in multi-instance scenarios. These functions should be implemented by third-party platforms and registered with the system using [OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance](#oh_arkui_accessibilityproviderregistercallbackwithinstance).|
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) | [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) | Defines accessibility node information, which is used to transfer node information to accessibility services and applications.|
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) | [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) | Describes the accessibility event information. After a component completes an action requested by an accessibility service or application, it needs to send a success event to confirm the operation. Similarly, if the component needs to synchronize its state change with the accessibility service or application due to its own interactive behavior, it should actively trigger an event to communicate the change.|
| [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) | [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) |  Defines a provider for third-party accessibility operations, which is used to implement callback functions.|
| [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) | [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) | Sets the parameters of accessibility actions.|
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md) | [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md) | Provides a **List** instance of encapsulated [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [ArkUI_Node*](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle | Defines the pointer to an ArkUI native component object.<br>**Since**: 23 |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_Accessibility_ActionType](#arkui_accessibility_actiontype) | ArkUI_Accessibility_ActionType | Enumerates accessibility action types.|
| [ArkUI_AccessibilityEventType](#arkui_accessibilityeventtype) | ArkUI_AccessibilityEventType | Enumerates accessibility event types.|
| [ArkUI_AcessbilityErrorCode](#arkui_acessbilityerrorcode) | ArkUI_AcessbilityErrorCode | Enumerates accessibility error codes.|
| [ArkUI_AccessibilitySearchMode](#arkui_accessibilitysearchmode) | ArkUI_AccessibilitySearchMode | Enumerates accessibility search modes.|
| [ArkUI_AccessibilityFocusType](#arkui_accessibilityfocustype) | ArkUI_AccessibilityFocusType | Enumerates accessibility focus types.|
| [ArkUI_AccessibilityFocusMoveDirection](#arkui_accessibilityfocusmovedirection) | ArkUI_AccessibilityFocusMoveDirection | Enumerates accessibility focus movement directions.|

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_ArkUI_AccessibilityProviderRegisterCallback(ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityProviderCallbacks* callbacks)](#oh_arkui_accessibilityproviderregistercallback) | Defines a struct for third-party accessibility provider callback functions, which third-party platforms need to implement. These functions are registered with the system side through **OH_ArkUI_AccessibilityProviderRegisterCallback**.|
| [int32_t OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance(const char* instanceId,ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityProviderCallbacksWithInstance* callbacks)](#oh_arkui_accessibilityproviderregistercallbackwithinstance) | Registers callback functions with the system for third-party platforms in accessibility multi-instance scenarios.|
| [void OH_ArkUI_SendAccessibilityAsyncEvent(ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityEventInfo* eventInfo,void (\*callback)(int32_t errorCode))](#oh_arkui_sendaccessibilityasyncevent) | Proactively sends an event to notify the accessibility service.|
| [ArkUI_AccessibilityElementInfo* OH_ArkUI_AddAndGetAccessibilityElementInfo(ArkUI_AccessibilityElementInfoList* list)](#oh_arkui_addandgetaccessibilityelementinfo) | Adds an **ArkUI_AccessibilityElementInfo** member to the specified list and returns the **ArkUI_AccessibilityElementInfo** struct.|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetElementId(ArkUI_AccessibilityElementInfo* elementInfo, int32_t elementId)](#oh_arkui_accessibilityelementinfosetelementid) | Sets the unique ID (**elementId**) of an accessibility element for **ArkUI_AccessibilityElementInfo**.|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetParentId(ArkUI_AccessibilityElementInfo* elementInfo, int32_t parentId)](#oh_arkui_accessibilityelementinfosetparentid) | Sets the accessibility ID (**parentId**) of the parent element for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetComponentType(ArkUI_AccessibilityElementInfo* elementInfo, const char* componentType)](#oh_arkui_accessibilityelementinfosetcomponenttype) | Sets the component type for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetContents(ArkUI_AccessibilityElementInfo* elementInfo, const char* contents)](#oh_arkui_accessibilityelementinfosetcontents) | Sets the component text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetHintText(ArkUI_AccessibilityElementInfo* elementInfo, const char* hintText)](#oh_arkui_accessibilityelementinfosethinttext) | Sets the hint text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityText(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityText)](#oh_arkui_accessibilityelementinfosetaccessibilitytext) | Sets the accessibility-specific alternative text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityDescription(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityDescription)](#oh_arkui_accessibilityelementinfosetaccessibilitydescription) | Sets the accessibility description for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetChildNodeIds(ArkUI_AccessibilityElementInfo* elementInfo, int32_t childCount, int64_t* childNodeIds)](#oh_arkui_accessibilityelementinfosetchildnodeids) | Sets the number of child nodes and the child node ID array for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetOperationActions(ArkUI_AccessibilityElementInfo* elementInfo,int32_t operationCount, ArkUI_AccessibleAction* operationActions)](#oh_arkui_accessibilityelementinfosetoperationactions) | Sets the list of accessibility actions supported by the component for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetScreenRect(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleRect* screenRect)](#oh_arkui_accessibilityelementinfosetscreenrect) | Sets the rectangle area of the component on the screen for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetCheckable(ArkUI_AccessibilityElementInfo* elementInfo, bool checkable)](#oh_arkui_accessibilityelementinfosetcheckable) | Sets whether the component is checkable for **ArkUI_AccessibilityElementInfo**.|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetChecked(ArkUI_AccessibilityElementInfo* elementInfo, bool checked)](#oh_arkui_accessibilityelementinfosetchecked) | Sets the current checked state of the component for **ArkUI_AccessibilityElementInfo**.|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetFocusable(ArkUI_AccessibilityElementInfo* elementInfo, bool focusable)](#oh_arkui_accessibilityelementinfosetfocusable) | Sets whether the component is focusable for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetFocused(ArkUI_AccessibilityElementInfo* elementInfo, bool isFocused)](#oh_arkui_accessibilityelementinfosetfocused) | Sets whether the component has been focused for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetVisible(ArkUI_AccessibilityElementInfo* elementInfo, bool isVisible)](#oh_arkui_accessibilityelementinfosetvisible) | Sets whether the component is visible on the screen for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityFocused(ArkUI_AccessibilityElementInfo* elementInfo, bool accessibilityFocused)](#oh_arkui_accessibilityelementinfosetaccessibilityfocused) | Sets the current accessibility focus status for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetSelected(ArkUI_AccessibilityElementInfo* elementInfo, bool selected)](#oh_arkui_accessibilityelementinfosetselected) | Sets whether the component is selected for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetClickable(ArkUI_AccessibilityElementInfo* elementInfo, bool clickable)](#oh_arkui_accessibilityelementinfosetclickable) | Sets whether the component is clickable for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetLongClickable(ArkUI_AccessibilityElementInfo* elementInfo, bool longClickable)](#oh_arkui_accessibilityelementinfosetlongclickable) | Sets whether the component can be long-pressed for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetEnabled(ArkUI_AccessibilityElementInfo* elementInfo, bool isEnabled)](#oh_arkui_accessibilityelementinfosetenabled) | Sets whether the component is in the enabled state for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetIsPassword(ArkUI_AccessibilityElementInfo* elementInfo, bool isPassword)](#oh_arkui_accessibilityelementinfosetispassword) | Sets whether the component is a password text box for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetScrollable(ArkUI_AccessibilityElementInfo* elementInfo, bool scrollable)](#oh_arkui_accessibilityelementinfosetscrollable) | Sets whether the component is scrollable for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetEditable(ArkUI_AccessibilityElementInfo* elementInfo, bool editable)](#oh_arkui_accessibilityelementinfoseteditable) | Sets whether the text content is editable for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetIsHint(ArkUI_AccessibilityElementInfo* elementInfo, bool isHint)](#oh_arkui_accessibilityelementinfosetishint) | Sets whether the component is in the hint text state for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetRangeInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleRangeInfo* rangeInfo)](#oh_arkui_accessibilityelementinfosetrangeinfo) | Sets the range information for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetGridInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleGridInfo* gridInfo)](#oh_arkui_accessibilityelementinfosetgridinfo) | Sets the grid information for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetGridItemInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleGridItemInfo* gridItem)](#oh_arkui_accessibilityelementinfosetgriditeminfo) | Sets the attribute information of subitems in the grid container for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetSelectedTextStart(ArkUI_AccessibilityElementInfo* elementInfo, int32_t selectedTextStart)](#oh_arkui_accessibilityelementinfosetselectedtextstart) | Sets the start position of the selected text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetSelectedTextEnd(ArkUI_AccessibilityElementInfo* elementInfo, int32_t selectedTextEnd)](#oh_arkui_accessibilityelementinfosetselectedtextend) | Sets the end position of the selected text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetCurrentItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t currentItemIndex)](#oh_arkui_accessibilityelementinfosetcurrentitemindex) | Sets the position index of the currently focused or highlighted subitem for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetStartItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t startItemIndex)](#oh_arkui_accessibilityelementinfosetstartitemindex) | Sets the position index of the first element in the visible area of the current screen for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetEndItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t endItemIndex)](#oh_arkui_accessibilityelementinfosetenditemindex) | Sets the position index of the last element in the visible area of the current screen for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetItemCount(ArkUI_AccessibilityElementInfo* elementInfo, int32_t itemCount)](#oh_arkui_accessibilityelementinfosetitemcount) | Sets the total number of subitems in the container for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityOffset(ArkUI_AccessibilityElementInfo* elementInfo, int32_t offset)](#oh_arkui_accessibilityelementinfosetaccessibilityoffset) | Sets the scroll offset for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityGroup(ArkUI_AccessibilityElementInfo* elementInfo, bool accessibilityGroup)](#oh_arkui_accessibilityelementinfosetaccessibilitygroup) | Sets the accessibility group for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityLevel(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityLevel)](#oh_arkui_accessibilityelementinfosetaccessibilitylevel) | Sets the accessibility importance level for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetZIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t zIndex)](#oh_arkui_accessibilityelementinfosetzindex) | Sets the component Z-index for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityOpacity(ArkUI_AccessibilityElementInfo* elementInfo, float opacity)](#oh_arkui_accessibilityelementinfosetaccessibilityopacity) | Sets the opacity for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetBackgroundColor(ArkUI_AccessibilityElementInfo* elementInfo, const char* backgroundColor)](#oh_arkui_accessibilityelementinfosetbackgroundcolor) | Sets the background color for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetBackgroundImage(ArkUI_AccessibilityElementInfo* elementInfo, const char* backgroundImage)](#oh_arkui_accessibilityelementinfosetbackgroundimage) | Sets the background image for **ArkUI_AccessibilityElementInfo**.|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetBlur(ArkUI_AccessibilityElementInfo* elementInfo, const char* blur)](#oh_arkui_accessibilityelementinfosetblur) | Sets the blur effect for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetHitTestBehavior(ArkUI_AccessibilityElementInfo* elementInfo, const char* hitTestBehavior)](#oh_arkui_accessibilityelementinfosethittestbehavior) | Sets the response logic and node blocking rule for the hit test for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [int32_t OH_ArkUI_AccessibilityElementInfoSetComponentIdentifier(ArkUI_AccessibilityElementInfo* elementInfo, const char* identifier)](#oh_arkui_accessibilityelementinfosetcomponentidentifier) | Sets the component identifier for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md), which can be used to identify a specific component during automated testing.|
| [ArkUI_AccessibilityElementInfo* OH_ArkUI_CreateAccessibilityElementInfo(void)](#oh_arkui_createaccessibilityelementinfo) | Creates an [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) object. After the object is created, call [OH_ArkUI_DestoryAccessibilityElementInfo](#oh_arkui_destoryaccessibilityelementinfo) to destroy it.|
| [void OH_ArkUI_DestoryAccessibilityElementInfo(ArkUI_AccessibilityElementInfo* elementInfo)](#oh_arkui_destoryaccessibilityelementinfo) | Destroys an [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) object.|
| [ArkUI_AccessibilityEventInfo* OH_ArkUI_CreateAccessibilityEventInfo(void)](#oh_arkui_createaccessibilityeventinfo) | Creates an [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) object. After the object is created, call [OH_ArkUI_DestoryAccessibilityEventInfo](#oh_arkui_destoryaccessibilityeventinfo) to destroy it.|
| [void OH_ArkUI_DestoryAccessibilityEventInfo(ArkUI_AccessibilityEventInfo* eventInfo)](#oh_arkui_destoryaccessibilityeventinfo) | Destroys an [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) object.|
| [int32_t OH_ArkUI_AccessibilityEventSetEventType(ArkUI_AccessibilityEventInfo* eventInfo,  ArkUI_AccessibilityEventType eventType)](#oh_arkui_accessibilityeventseteventtype) | Sets the event type for [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md).|
| [int32_t OH_ArkUI_AccessibilityEventSetTextAnnouncedForAccessibility(ArkUI_AccessibilityEventInfo* eventInfo,  const char* textAnnouncedForAccessibility)](#oh_arkui_accessibilityeventsettextannouncedforaccessibility) | Sets the content to be proactively announced for [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md).|
| [int32_t OH_ArkUI_AccessibilityEventSetRequestFocusId(ArkUI_AccessibilityEventInfo* eventInfo,  int32_t requestFocusId)](#oh_arkui_accessibilityeventsetrequestfocusid) | Sets the focus request ID for [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md).|
| [int32_t OH_ArkUI_AccessibilityEventSetElementInfo(ArkUI_AccessibilityEventInfo* eventInfo,  ArkUI_AccessibilityElementInfo* elementInfo)](#oh_arkui_accessibilityeventsetelementinfo) | Sets **elementInfo** for [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md).|
| [int32_t OH_ArkUI_FindAccessibilityActionArgumentByKey(ArkUI_AccessibilityActionArguments* arguments, const char* key, char** value)](#oh_arkui_findaccessibilityactionargumentbykey) | Obtains the value of a specified key in [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md).|
| [int32_t OH_ArkUI_NativeModule_GetNativeAccessibilityProvider(ArkUI_NodeHandle* node, ArkUI_AccessibilityProvider** provider)](#oh_arkui_nativemodule_getnativeaccessibilityprovider) |Obtains the level-2 pointer variable of the pointer to the [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) object.<br>The [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) object corresponds to the [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) instance passed.<br>A third-party framework maps its UI components as [RenderNode](js-apis-arkui-renderNode.md) of the [ARKUI_NODE_CUSTOM](capi-native-node-h.md#arkui_nodetype) type to obtain [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).<br>Then, it calls **OH_ArkUI_NativeModule_GetNativeAccessibilityProvider** to obtain the [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) pointer and register an accessibility callback.<br>Finally, the ArkUI accessibility service can identify the UI of the third-party framework and trigger events.<br>This API takes effect only when the third-party framework maps its UI components as [RenderNode](js-apis-arkui-renderNode.md) of the [ARKUI_NODE_CUSTOM](capi-native-node-h.md#arkui_nodetype) type. Otherwise, an error code will be reported.<br>This API uses [RenderNode](js-apis-arkui-renderNode.md) to implement the access of the third-party framework. Only [ARKUI_NODE_CUSTOM](capi-native-node-h.md#arkui_nodetype) can access the accessibility service to obtain the accessibility control tree.<br>Multi-thread concurrency is not supported. The third-party framework ensures thread security during the API calling.|

## Enum Description

### ArkUI_Accessibility_ActionType

```c
enum ArkUI_Accessibility_ActionType
```

**Description**


Enumerates accessibility action types.

**Since**: 13

| Value| Description                                                                                                                               |
| -- |-----------------------------------------------------------------------------------------------------------------------------------|
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_INVALID = 0 | Invalid value.                                                                                                                              |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CLICK = 0x00000010 | Triggers the component's click event handling.                                                                                                               |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_LONG_CLICK = 0x00000020 | Triggers the component's long-press event handling.                                                                                                              |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_GAIN_ACCESSIBILITY_FOCUS = 0x00000040 | Requests accessibility focus for the component.                                                                                                           |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CLEAR_ACCESSIBILITY_FOCUS = 0x00000080 | Clears accessibility focus from the component.                                                                                                                   |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_FORWARD = 0x00000100 | Initiates forward scrolling in scrollable containers.                                                                                                                    |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_BACKWARD = 0x00000200 | Initiates backward scrolling in scrollable containers.                                                                                                                    |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_COPY = 0x00000400 | Copies the current text selection.                                                                                                                     |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_PASTE = 0x00000800 | Pastes content to the text component.                                                                                                                     |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CUT = 0x00001000 | Cuts the current text selection to the pasteboard.                                                                                                                     |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SELECT_TEXT = 0x00002000 | Selects a range of text within an editable area in a text component. Selects a range of text within an editable area by using **ArkUI_AccessibilityActionArguments** and setting **selectTextBegin** (indicates the start position of the selection), **selectTextEnd** (indicates the end position of the selection), and **selectTextInForward** (**true** indicates to select text forward, and **false** indicates to select text backward).                                                                   |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SET_TEXT = 0x00004000 | Sets the text content of the text component.                                                                                                                     |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SET_CURSOR_POSITION = 0x00100000 | Sets the cursor position where the text can be entered for the text component. This enumerated value is used together with [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md).|
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_NEXT_HTML_ITEM = 0x02000000 | Moves focus to the next focusable component. Note: "HTML" indicates the web-like navigation capability, not actual web elements. This attribute is available only when the [findNextFocusAccessibilityNode](./capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md#findnextfocusaccessibilitynode) capability is implemented.<br>**Since**: 15|
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_PREVIOUS_HTML_ITEM = 0x04000000 | Moves focus to the previous focusable component. Note: "HTML" indicates the web-like navigation capability, not actual web elements. This attribute is available only when the [findNextFocusAccessibilityNode](./capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md#findnextfocusaccessibilitynode) capability is implemented.<br>**Since**: 15    |

### ArkUI_AccessibilityEventType

```c
enum ArkUI_AccessibilityEventType
```

**Description**


Enumerates accessibility event types.

**Since**: 13

| Value| Description|
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_INVALID = 0 | Invalid value.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_CLICKED = 0x00000001 | Click event, sent after the UI component responds.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_LONG_CLICKED = 0x00000002 | Long-pressing event, sent after the UI component responds.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_SELECTED = 0x00000004 | Selection event, sent after the UI component responds.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_TEXT_UPDATE = 0x00000010 | Text update event, sent when text is updated.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_PAGE_STATE_UPDATE = 0x00000020 | Page state update event, sent on page navigation, switching, resizing, or movement.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_PAGE_CONTENT_UPDATE = 0x00000800 | Page content update event, sent when the page content changes.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_SCROLLED = 0x000001000 | Scroll event, sent when scrolling occurs on scrollable components.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ACCESSIBILITY_FOCUSED = 0x00008000 | Accessibility focus event, sent after the UI component receives focus.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ACCESSIBILITY_FOCUS_CLEARED = 0x00010000 | Accessibility focus cleared event, sent after the UI component loses focus.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_REQUEST_ACCESSIBILITY_FOCUS = 0x02000000 | Event to actively requests focus for the specified node.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_PAGE_OPEN = 0x20000000 | Page open event reported by the UI component.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_PAGE_CLOSE = 0x08000000 | Page close event reported by the UI component.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ANNOUNCE_FOR_ACCESSIBILITY = 0x10000000 | Announcement event, indicating a request to proactively announce specified content.|
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_FOCUS_NODE_UPDATE = 0x10000001 | Focus update event, used in the focus update scenarios.|

### ArkUI_AcessbilityErrorCode

```c
enum ArkUI_AcessbilityErrorCode
```

**Description**


Enumerates accessibility error codes.

**Since**: 13

| Value| Description|
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL = 0 | The operation is successful.|
| ARKUI_ACCESSIBILITY_NATIVE_RESULT_FAILED = -1 | The operation failed.|
| ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER = -2 | Invalid parameter.|
| ARKUI_ACCESSIBILITY_NATIVE_RESULT_OUT_OF_MEMORY = -3 | Insufficient memory.|

### ArkUI_AccessibilitySearchMode

```c
enum ArkUI_AccessibilitySearchMode
```

**Description**


Enumerates accessibility search modes.

**Since**: 13

| Value| Description|
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_CURRENT = 0 | Searches the current node.|
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_PREDECESSORS = 1 << 0 | Searches parent nodes.|
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_SIBLINGS = 1 << 1 | Searches sibling nodes.|
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_CHILDREN = 1 << 2 | Searches immediate child nodes.|
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_RECURSIVE_CHILDREN = 1 << 3 | Searches all child nodes.|

### ArkUI_AccessibilityFocusType

```c
enum ArkUI_AccessibilityFocusType
```

**Description**


Enumerates accessibility focus types.

**Since**: 13

| Value| Description|
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_FOCUS_TYPE_INVALID = -1 | Invalid value.|
| ARKUI_ACCESSIBILITY_NATIVE_FOCUS_TYPE_INPUT = 1 << 0 | Input focus type.|
| ARKUI_ACCESSIBILITY_NATIVE_FOCUS_TYPE_ACCESSIBILITY = 1 << 1 | Accessibility focus type.|

### ArkUI_AccessibilityFocusMoveDirection

```c
enum ArkUI_AccessibilityFocusMoveDirection
```

**Description**


Enumerates accessibility focus movement directions.

**Since**: 13

| Value| Description|
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_INVALID = 0 | Invalid value.|
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_UP = 0x00000001 | Moves focus up.|
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_DOWN = 0x00000002 | Moves focus down.|
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_LEFT = 0x00000004 | Moves focus left.|
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_RIGHT = 0x00000008 | Moves focus right.|
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_FORWARD = 0x00000010 | Moves focus to the next focusable node (relative to the reference node in query).|
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_BACKWARD = 0x00000020 | Moves focus to the previous focusable node (relative to the reference node in query).|


## Function Description

### OH_ArkUI_AccessibilityProviderRegisterCallback()

```c
int32_t OH_ArkUI_AccessibilityProviderRegisterCallback(ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityProviderCallbacks* callbacks)
```

**Description**


Defines a struct for third-party accessibility provider callback functions, which third-party platforms need to implement. These functions are registered with the system side through **OH_ArkUI_AccessibilityProviderRegisterCallback**.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md)* provider | Pointer to an [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) instance.|
| [ArkUI_AccessibilityProviderCallbacks](capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md)* callbacks | Pointer to an [ArkUI_AccessibilityProviderCallbacks](capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md) instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance()

```c
int32_t OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance(const char* instanceId, ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityProviderCallbacksWithInstance* callbacks)
```

**Description**


Registers callback functions with the system for third-party platforms in accessibility multi-instance scenarios.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| const char* instanceId | Pointer to the instance ID for third-party platform integration, used to distinguish between different instances in multi-instance scenarios. The ID is assigned and maintained by the third-party platform.|
| [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md)* provider | Handle to the third-party platform provider.|
| [ArkUI_AccessibilityProviderCallbacksWithInstance](capi-arkui-accessibility-arkui-accessibilityprovidercallbackswithinstance.md)* callbacks | Pointer to an [ArkUI_AccessibilityProviderCallbacksWithInstance](capi-arkui-accessibility-arkui-accessibilityprovidercallbackswithinstance.md) instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_SendAccessibilityAsyncEvent()

```c
void OH_ArkUI_SendAccessibilityAsyncEvent(ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityEventInfo* eventInfo, void (*callback)(int32_t errorCode))
```

**Description**


Proactively sends an event to notify the accessibility service.

**Since**: 13


**Parameters**

| Name                                                                                             | Description|
|--------------------------------------------------------------------------------------------------| -- |
| [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md)* provider | Handle to the third-party platform provider.|
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo                                                      | Pointer to the accessibility event information.|
| void (*callback)(int32_t errorCode)                                                                                         | Pointer to the **SendAccessibilityAsyncEvent** callback.|

### OH_ArkUI_AddAndGetAccessibilityElementInfo()

```c
ArkUI_AccessibilityElementInfo* OH_ArkUI_AddAndGetAccessibilityElementInfo(ArkUI_AccessibilityElementInfoList* list)
```

**Description**


Adds an **ArkUI_AccessibilityElementInfo** member to the specified list and returns the **ArkUI_AccessibilityElementInfo** struct.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* list | Pointer to the [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md) struct. After the newly created **ElementInfo** member is added to the list, the list is returned to the function caller.|

**Returns**

| Type                                 | Description|
|-------------------------------------| -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* | Pointer to the created [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) struct. If the creation fails, **NULL** is returned.|

### OH_ArkUI_AccessibilityElementInfoSetElementId()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetElementId(ArkUI_AccessibilityElementInfo* elementInfo, int32_t elementId)
```

**Description**

Sets the unique ID (**elementId**) of an accessibility element for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **elementId** indicates the unique identifier of a node in the accessibility component tree, which is used by the accessibility service to locate and reference the specific node. The accessibility service relies on this identifier when searching for node information, performing operations, and moving focus.
> - A third-party framework must ensure that **elementId** of each node in the same component tree is globally unique. Otherwise, the accessibility service may fail to find the node.
> - The value of **elementId** is allocated and maintained by the third-party framework. You are advised to use an incremental integer or a stable component ID.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t elementId | ID of an accessibility element, which must be unique in the current component tree.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetParentId()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetParentId(ArkUI_AccessibilityElementInfo* elementInfo, int32_t parentId)
```

**Description**

Sets the accessibility ID (**parentId**) of the parent element for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **parentId** is used to build a hierarchical relationship for an accessibility component tree and identify the parent node of the current node. The accessibility service depends on the parent-child relationship when traversing the node tree and searching for sibling nodes.
> - If the current node is the root node, you are advised to set **parentId** to **-1** or **0** (different from **elementId** of the root node).
> - The parent node's **elementId** pointed to by **parentId** must exist in the component tree. Otherwise, an exception may occur when the accessibility service performs upward traversal.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t parentId | Accessibility ID of the element's parent component. The value must point to the existing **elementId** of the parent node.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetComponentType()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetComponentType(ArkUI_AccessibilityElementInfo* elementInfo, const char* componentType)
```

**Description**

Sets the component type for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **componentType** is used to identify the component type of an accessibility node, such as **Button**, **Text**, **Image**, and **List**.
> - The accessibility service (such as an accessibility application) determines how to describe and interact with the node for users based on the component type. For example, the **Button** type is read as a button, and the **Text** type is read as text. A third-party framework can use its own component type name. You are advised to use the character string that is the same as the ArkUI component name to achieve the best reading effect.
> - The recommended component type names include: [Button](arkui-ts/ts-basic-components-button.md), [Text](arkui-ts/ts-basic-components-text.md), [Image](arkui-ts/ts-basic-components-image.md), [List](arkui-ts/ts-container-list.md), [TextInput](arkui-ts/ts-basic-components-textinput.md), [Slider](arkui-ts/ts-basic-components-slider.md), [Rating](arkui-ts/ts-basic-components-rating.md), [Progress](arkui-ts/ts-basic-components-progress.md), [CheckBox](arkui-ts/ts-basic-components-checkbox.md), [Toggle](arkui-ts/ts-basic-components-toggle.md), [Grid](arkui-ts/ts-container-grid.md), [Swiper](arkui-ts/ts-container-swiper.md), [Select](arkui-ts/ts-basic-components-select.md), and [Tab](arkui-ts/ts-container-tabs.md).

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* componentType | Pointer to the component type string of the element. This parameter cannot be a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetContents()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetContents(ArkUI_AccessibilityElementInfo* elementInfo, const char* contents)
```

**Description**

Sets the component text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **contents** specifies the main text content of a component, which will be read by accessibility applications to users.
> - For text components (such as [Text](arkui-ts/ts-basic-components-text.md) and [TextInput](arkui-ts/ts-basic-components-textinput.md)), **contents** is usually set to the text displayed on the component.
> - For non-text components (such as [Button](arkui-ts/ts-basic-components-button.md) and [Image](arkui-ts/ts-basic-components-image.md)), if **accessibilityText** is set, the accessibility applications preferentially use it.
> - Call [OH_ArkUI_AccessibilityElementInfoSetAccessibilityText](#oh_arkui_accessibilityelementinfosetaccessibilitytext) to set **accessibilityText**. Otherwise, **contents** is used as the content to be read.
> - If both **contents** and **accessibilityText** are set for the component, the accessibility application preferentially uses **accessibilityText**.
> - A null pointer cannot be passed to **contents**. If a null pointer is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* contents | Pointer to the text content recognized by the accessibility service for the element. This parameter cannot be a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetHintText()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetHintText(ArkUI_AccessibilityElementInfo* elementInfo, const char* hintText)
```

**Description**


Sets the hint text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **hintText** is used as the placeholder hint text for editable components (for example, the text box) to provide auxiliary description for the components. When a component is in the hint state (**isHint** is set to **true**), accessibility applications read the value of **hintText** instead of **contents**. For example, the placeholder text "Please enter username" displayed when the text box is empty should be passed through **hintText**.
> - **hintText** is used together with **isHint**: When **isHint** is set to **true**, accessibility applications read the value of **hintText**. When **isHint** is set to **false**, accessibility applications read the value of **contents**. You can set **isHint** by calling [OH_ArkUI_AccessibilityElementInfoSetIsHint](#oh_arkui_accessibilityelementinfosetishint) and set **contents** by calling [OH_ArkUI_AccessibilityElementInfoSetContents](#oh_arkui_accessibilityelementinfosetcontents).
> - A null pointer cannot be passed to **hintText**. If a null pointer is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* hintText | Pointer to the hint text. The value cannot be a null pointer. The default value is **""**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityText()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityText(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityText)
```

**Description**


Sets the accessibility-specific alternative text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **accessibilityText** indicates accessibility-specific alternative text, which is used to overwrite the content specified by **contents** for accessibility applications.
> - If **accessibilityText** is set for a component and is not empty, accessibility applications preferentially announce the content specified by **accessibilityText** instead of **contents**. This attribute is applicable to scenarios where additional description is required for visual content. For example, **accessibilityText** can be set to "a sea photo" for the image component. In this case, even if the image does not have text content, accessibility applications can describe the meaning of the image to users.
> - If **accessibilityText** is an empty string, accessibility applications use **contents**.
> - A null pointer cannot be passed to **accessibilityText**. If a null pointer is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* accessibilityText | Pointer to the accessibility text. The value cannot be a null pointer. The default value is **""**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityDescription()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityDescription(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityDescription)
```

**Description**

Sets the accessibility description for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **accessibilityDescription** provides additional accessibility description for a component.
> - After announcing the main content (specified by **accessibilityText** or **contents**) of a component, accessibility applications continues to announce the content specified by **accessibilityDescription**. For example, if **contents** of a button is set to "Submit", you can set **accessibilityDescription** to "Tap to submit form data". In this case, accessibility applications will read "Submit. Tap to submit form data." This attribute is applicable to scenarios where additional operation prompts or status description need to be provided for users.
> - A null pointer cannot be passed to **accessibilityDescription**. If a null pointer is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* accessibilityDescription | Pointer to the accessibility description. The value cannot be a null pointer. The default value is **""**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetChildNodeIds()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetChildNodeIds(ArkUI_AccessibilityElementInfo* elementInfo, int32_t childCount, int64_t* childNodeIds)
```

**Description**

Sets the number of child nodes and the child node ID array for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **childNodeIds** is used to build a parent-child relationship for an accessibility component tree and identify all direct child nodes of the current node. The accessibility service traverses child nodes through **childNodeIds** to obtain a complete accessibility tree structure.
> - Each time this API is called, all previously configured child node information is cleared and replaced with the child node array passed this time (update in overwriting instead of appending mode). Each value in **childNodeIds** corresponds to an existing **elementId** of a child node.
> - The value of **childCount** must be greater than 0, and the **childNodeIds** array must contain at least **childCount** valid elements.
> - A null pointer cannot be passed to **childNodeIds** and **elementInfo**, and the value of **childCount** cannot be less than or equal to 0. Otherwise, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t childCount | Number of child nodes, which must be greater than 0.|
| int64_t* childNodeIds | Pointer to the child node ID array. Each ID must point to an existing **elementId** of a child node. The value cannot be a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetOperationActions()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetOperationActions(ArkUI_AccessibilityElementInfo* elementInfo,int32_t operationCount, ArkUI_AccessibleAction* operationActions)
```

**Description**


Sets the list of accessibility actions supported by the component for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t operationCount | Number of actions supported by the component. The value must be greater than 0.|
| [ArkUI_AccessibleAction](capi-arkui-accessibility-arkui-accessibleaction.md)* operationActions | Pointer to the array of actions supported by the component. The value cannot be a null pointer. For details about the supported action types, see [ArkUI_Accessibility_ActionType](#arkui_accessibility_actiontype).|


**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetScreenRect()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetScreenRect(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleRect* screenRect)
```

**Description**

Sets the rectangle area of the component on the screen for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **screenRect** defines the position and size of the component on the screen, in pixels. The accessibility service uses **screenRect** to highlight the focus, locate the touch target, and determine the element visibility.
> - Auxiliary applications, such as accessibility applications, leverage **screenRect** to determine the display position of the focus box, helping users understand the position of the current focused element on the screen.
> - If the area specified by **screenRect** is 0 or is not within the visible range of the screen, the node may not be focused by auxiliary applications.
> - A null pointer cannot be passed to **screenRect** and **elementInfo**. Otherwise, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [ArkUI_AccessibleRect](capi-arkui-accessibility-arkui-accessiblerect.md)* screenRect | Screen area, including the coordinates of the upper left corner and lower right corner. The value cannot be a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetCheckable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetCheckable(ArkUI_AccessibilityElementInfo* elementInfo, bool checkable)
```

**Description**


Sets whether the component is checkable for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - This API applies to components that have checkable semantics, such as [CheckBox](arkui-ts/ts-basic-components-checkbox.md), [Toggle](arkui-ts/ts-basic-components-toggle.md), and [Radio](arkui-ts/ts-basic-components-radio.md) in ArkUI.
> - Accessibility applications will announce the "checkable" prompt to users based on the checkable state and inform the users that they can perform an operation to change the checkable state.
> - When setting **checkable** to **true**, you need to use [OH_ArkUI_AccessibilityElementInfoSetChecked](#oh_arkui_accessibilityelementinfosetchecked) to set **checked** to indicate the current checked state.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool checkable | Whether the component is checkable. The value **true** indicates that the component is checkable, and **false** indicates the opposite. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetChecked()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetChecked(ArkUI_AccessibilityElementInfo* elementInfo, bool checked)
```

**Description**


Sets the current checked state for the component for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - Accessibility applications will announce "checked" or "unchecked" based on the checked state. This API only sets the checked state and does not automatically set the **checkable** attribute.
> - If the component needs to be identified as checkable, call [OH_ArkUI_AccessibilityElementInfoSetCheckable](#oh_arkui_accessibilityelementinfosetcheckable) to set the **checkable** attribute to **true**.
> - If only **checked** is set and the **checkable** attribute is not set to **true**, the checked state will not be displayed in accessibility applications.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool checked | Whether the component is checked. The value **true** indicates that the component is checked, and **false** indicates the opposite. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetFocusable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetFocusable(ArkUI_AccessibilityElementInfo* elementInfo, bool focusable)
```

**Description**


Sets whether the component is focusable for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - This API applies to focusable interactive components, such as [TextInput](arkui-ts/ts-basic-components-textinput.md) and [Button](arkui-ts/ts-basic-components-button.md) in ArkUI.
> - When traversing focusable nodes, auxiliary applications such as accessibility applications will skip nodes whose **focusable** is set to **false**.
> - For components whose **focusable** is set to **true**, you also need to set **clickable** to **true** using [OH_ArkUI_AccessibilityElementInfoSetClickable](#oh_arkui_accessibilityelementinfosetclickable) and register the corresponding action.
> - The difference between **focusable** and **accessibilityFocused** lies in: **focusable** indicates the input focus capability, and **accessibilityFocused** indicates the current status of the accessibility focus.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool focusable | Whether the object is focusable. **true**: focusable; **false**: not focusable. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetFocused()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetFocused(ArkUI_AccessibilityElementInfo* elementInfo, bool isFocused)
```

**Description**


Sets whether the component has been focused for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - When gaining focus, accessibility applications will announce the information about the focused element.
> - When setting **isFocused** to **true**, you need to set **focusable** to **true** using [OH_ArkUI_AccessibilityElementInfoSetFocusable](#oh_arkui_accessibilityelementinfosetfocusable). Otherwise, the meaning of the focus state is incomplete.
> - The difference between **isFocused** and **accessibilityFocused** lies in: **isFocused** indicates the input focus state, while **accessibilityFocused** (set by [OH_ArkUI_AccessibilityElementInfoSetAccessibilityFocused](#oh_arkui_accessibilityelementinfosetaccessibilityfocused)) indicates the accessibility focus state.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool isFocused | Whether the object is focused. **true**: focused; **false**: not focused. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetVisible()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetVisible(ArkUI_AccessibilityElementInfo* elementInfo, bool isVisible)
```

**Description**

Sets whether the component is visible on the screen for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - When auxiliary applications, such as accessibility applications, traverse nodes, they will skip nodes whose **isVisible** is set to **false** by default and do not focus on or announce these nodes. For components that are not in the visible area due to scrolling, you are advised to set **isVisible** to **false**.
> - If an interactive component is incorrectly set to be **invisible**, users will not be able to access it through an auxiliary application.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool isVisible | Whether the element is visible. **true**: visible; **false**: not visible. The default value is **false**. **isVisible** must be explicitly set to **true** for all components that need to be identified by auxiliary applications.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityFocused()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityFocused(ArkUI_AccessibilityElementInfo* elementInfo, bool accessibilityFocused)
```

**Description**

Sets the current accessibility focus status for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - When users browse UIs by focus movement of accessibility applications, the value of **accessibilityFocused** for the focused nodes should be **true**.
> - Accessibility applications announce the content of the nodes whose **accessibilityFocused** is set to **true** and draw focus highlight boxes on the screen.
> - When the accessibility service performs the [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_GAIN_ACCESSIBILITY_FOCUS](#arkui_accessibility_actiontype) and [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CLEAR_ACCESSIBILITY_FOCUS](#arkui_accessibility_actiontype) actions, a third-party framework should update the status accordingly and notify the system by sending the [ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ACCESSIBILITY_FOCUSED](#arkui_accessibilityeventtype) or [ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ACCESSIBILITY_FOCUS_CLEARED](#arkui_accessibilityeventtype) event.
> - The difference between **accessibilityFocused** and **isFocused** lies in: **accessibilityFocused** indicates the accessibility focus state, and **isFocused** indicates the input focus (keyboard focus) state.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool accessibilityFocused | Accessibility focus state. **true**: Accessibility focus is set. **false**: Accessibility focus is not set. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetSelected()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetSelected(ArkUI_AccessibilityElementInfo* elementInfo, bool selected)
```

**Description**


Sets whether the component is selected for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - This API applies to components that have the selected semantics, such as [Tab](arkui-ts/ts-container-tabs.md) and [ListItem](arkui-ts/ts-container-listitem.md) in ArkUI.
> - Accessibility applications will announce "selected" or "deselected" based on the selected state. For [Tab](arkui-ts/ts-container-tabs.md), the tab whose **selected** is set to **true** will be announced as the current active tab.
> - In list scenarios, **selected** can be used together with **accessibilityGroup** (set by [OH_ArkUI_AccessibilityElementInfoSetAccessibilityGroup](#oh_arkui_accessibilityelementinfosetaccessibilitygroup)) to mark the currently activated list item.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool selected | Whether the object is selected. **true**: selected; **false**: not selected. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetClickable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetClickable(ArkUI_AccessibilityElementInfo* elementInfo, bool clickable)
```

**Description**


Sets whether the component is clickable for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - Accessibility applications will notify users that the component is clickable. When the users perform click actions through the accessibility applications, the system will use the **executeAccessibilityAction** callback in [ArkUI_AccessibilityProviderCallbacks](capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md) to notify third-party frameworks.
> - When setting **clickable** to **true**, you need to add [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CLICK](#arkui_accessibility_actiontype) to **operationActions** through [OH_ArkUI_AccessibilityElementInfoSetOperationActions](#oh_arkui_accessibilityelementinfosetoperationactions). Otherwise, users cannot click the component through accessibility applications.
> - **clickable** must be used together with **enabled** (set by [OH_ArkUI_AccessibilityElementInfoSetEnabled](#oh_arkui_accessibilityelementinfosetenabled)). When **clickable** is set to **true** but **enabled** is set to **false**, accessibility applications will announce "disabled", indicating that the component is clickable but currently unavailable.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool clickable | Whether the object is clickable. **true**: supported; **false**: not supported. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetLongClickable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetLongClickable(ArkUI_AccessibilityElementInfo* elementInfo, bool longClickable)
```

**Description**


Sets whether the component can be long-pressed for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - Accessibility applications will notify users that the component can be long-pressed. When the users perform long-pressing actions through the accessibility applications, the system will use the **executeAccessibilityAction** callback in [ArkUI_AccessibilityProviderCallbacks](capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md) to notify third-party frameworks.
> - When setting **longClickable** to **true**, you need to add [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_LONG_CLICK](#arkui_accessibility_actiontype) to **operationActions** through [OH_ArkUI_AccessibilityElementInfoSetOperationActions](#oh_arkui_accessibilityelementinfosetoperationactions).
> - Otherwise, users cannot long-press the component through accessibility applications.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool longClickable | Whether long-press gestures are supported. **true**: supported; **false**: not supported. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetEnabled()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetEnabled(ArkUI_AccessibilityElementInfo* elementInfo, bool isEnabled)
```

**Description**


Sets whether the component is in the enabled state for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - When **isEnabled** is set to **false**, accessibility applications will announce "disabled" or "unavailable," indicating that the component is not currently interactive.
> - For disabled component (such as a dimmed button), you need to set **isEnabled** to **false** and set **clickable** to **true** through [OH_ArkUI_AccessibilityElementInfoSetClickable](#oh_arkui_accessibilityelementinfosetclickable). In this way, accessibility applications will prompt users that the component exists but is currently unavailable.
> - If both **isEnabled** and **clickable** are set to **false**, accessibility applications may skip the component completely.
> - **isEnabled** must be explicitly set to **true** for all components with which users need to interact.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool isEnabled | Whether the object is enabled. **true**: enabled; **false**: not enabled. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetIsPassword()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetIsPassword(ArkUI_AccessibilityElementInfo* elementInfo, bool isPassword)
```

**Description**


Sets whether the component is a password text box for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - When **isPassword** is set to **true**, accessibility applications will not read the specific password characters. Instead, they announce alternative prompts such as "password text box" or "password entered" to prevent password disclosure.
> - If text components such as [TextInput](arkui-ts/ts-basic-components-textinput.md) are used for password input, **isPassword** must be set to **true**.
> - If this attribute is not set or is set to **false**, accessibility applications may directly read the password content, posing a security risk.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool isPassword | Whether the object is a password. **true**: The object is a password. **false**: The object is not a password. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetScrollable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetScrollable(ArkUI_AccessibilityElementInfo* elementInfo, bool scrollable)
```

**Description**


Sets whether the component is scrollable for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - This API applies to container components that support content scrolling, such as [List](arkui-ts/ts-container-list.md), [Grid](arkui-ts/ts-container-grid.md), [Scroll](arkui-ts/ts-container-scroll.md), and [Swiper](arkui-ts/ts-container-swiper.md) in ArkUI.
> - Auxiliary applications, such as accessibility applications, provide scrolling action prompts to users based on the scrollable state. Users can use auxiliary applications to perform forward scrolling ([ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_FORWARD](#arkui_accessibility_actiontype)) or backward scrolling ([ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_BACKWARD](#arkui_accessibility_actiontype)).
> - When setting **scrollable** to **true**, you need to add scrolling actions to **operationActions** through [OH_ArkUI_AccessibilityElementInfoSetOperationActions](#oh_arkui_accessibilityelementinfosetoperationactions), including [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_FORWARD](#arkui_accessibility_actiontype) and [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_BACKWARD](#arkui_accessibility_actiontype). Otherwise, users cannot scroll the content of the component through the auxiliary applications.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool scrollable | Whether scrolling is supported. **true**: supported; **false**: not supported. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetEditable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetEditable(ArkUI_AccessibilityElementInfo* elementInfo, bool editable)
```

**Description**


Sets whether the text content is editable for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **editable** indicates whether the text content of the component can be edited by users. This attribute applies to editable text components such as [TextInput](arkui-ts/ts-basic-components-textinput.md) and [TextArea](arkui-ts/ts-basic-components-textarea.md).
> - Accessibility applications will announce the "editable" prompt to users based on the editable state and allow users to enter or modify the text through the accessibility applications.
> - For components with **editable** set to **true**, you need to register corresponding accessibility actions, such as [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SET_TEXT](#arkui_accessibility_actiontype), [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_COPY](#arkui_accessibility_actiontype), [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_PASTE](#arkui_accessibility_actiontype), and [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CUT](#arkui_accessibility_actiontype), through [OH_ArkUI_AccessibilityElementInfoSetOperationActions](#oh_arkui_accessibilityelementinfosetoperationactions) to allow users to perform editing actions through accessibility applications.
> - If both **editable** and **isPassword** (set by [OH_ArkUI_AccessibilityElementInfoSetIsPassword](#oh_arkui_accessibilityelementinfosetispassword)) are set to **true**, accessibility applications will announce "password edit box". The default value is **false**.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool editable | Whether editing is supported. **true**: supported; **false**: not supported. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetIsHint()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetIsHint(ArkUI_AccessibilityElementInfo* elementInfo, bool isHint)
```

**Description**


Sets whether the component is in the hint text state for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - When **isHint** is set to **true**, accessibility applications will read the content specified by **hintText** (set by [OH_ArkUI_AccessibilityElementInfoSetHintText](#oh_arkui_accessibilityelementinfosethinttext)) instead of **contents** (set by [OH_ArkUI_AccessibilityElementInfoSetContents](#oh_arkui_accessibilityelementinfosetcontents)).
> - This attribute is mainly used to display placeholder hint text for editable text components (such as [TextInput](arkui-ts/ts-basic-components-textinput.md)) when users have not entered any content.
> - For example, when a text box displays "Enter your username", set **isHint** to **true** and **hintText** to "Enter your username". After a user enters content, set **isHint** to **false** and **contents** to the text entered by the user.
> - If **isHint** is set to **true** but **hintText** is not set, accessibility applications may announce empty content.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool isHint | Whether the object represents a hint. **true** if the object represents a hint, **false** otherwise. In the hint text state, accessibility applications announce the content specified by **hintText**. Otherwise, they announce the content specified by **contents**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetRangeInfo()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetRangeInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleRangeInfo* rangeInfo)
```

**Description**


Sets the range information for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **rangeInfo** is used to set the current value, minimum value, and maximum value for a component that has a continuous range of values, such as [Slider](arkui-ts/ts-basic-components-slider.md), [Rating](arkui-ts/ts-basic-components-rating.md), [Progress](arkui-ts/ts-basic-components-progress.md), and **SeekBar**.
> - Accessibility applications will announce the current value and range based on **rangeInfo**, for example, "50% progress, range 0 to 100".
> - In **rangeInfo**, **current** indicates the current value, **min** indicates the minimum value, and **max** indicates the maximum value.
> - When setting **rangeInfo**, ensure that the value of **min** is less than or equal to that of **max** and the value of **current** is from **min** to **max**.
> - A null pointer cannot be passed to **rangeInfo** and **elementInfo**. Otherwise, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [ArkUI_AccessibleRangeInfo](capi-arkui-accessibility-arkui-accessiblerangeinfo.md)* rangeInfo | Pointer to the current value, maximum value, and minimum value of the specific component. The value cannot be a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetGridInfo()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetGridInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleGridInfo* gridInfo)
```

**Description**


Sets the grid information for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **gridInfo** is used to set the number of rows, number of columns, and selection mode for a grid container, such as [Grid](arkui-ts/ts-container-grid.md), [List](arkui-ts/ts-container-list.md), [Flex](arkui-ts/ts-container-flex.md), [Select](arkui-ts/ts-basic-components-select.md), and [Swiper](arkui-ts/ts-container-swiper.md).
> - Accessibility applications will announce the grid structure based on **gridInfo**, for example, "row 2, 5 rows and 3 columns in total".
> - **rowCount** indicates the number of rows, **columnCount** indicates the number of columns, and **selectionMode** indicates the selection mode (the value **0** indicates that a single row is selected, and other values indicate that multiple rows are selected).
> - A null pointer cannot be passed to **gridInfo** and **elementInfo**. Otherwise, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [ArkUI_AccessibleGridInfo](capi-arkui-accessibility-arkui-accessiblegridinfo.md)* gridInfo | Pointer to the number of rows, number of columns, and selection mode of the specific component. The value cannot be a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetGridItemInfo()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetGridItemInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleGridItemInfo* gridItem)
```

**Description**


Sets the attribute information of subitems in the grid container for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **gridItem** is used to set the attributes of each subitem in [Grid](arkui-ts/ts-container-grid.md), including whether the subitem is a title, whether it is selected, and its row and column subscript and span information. This attribute applies to subitems of grid or list containers, such as [Grid](arkui-ts/ts-container-grid.md), [List](arkui-ts/ts-container-list.md), [Flex](arkui-ts/ts-container-flex.md), [Select](arkui-ts/ts-basic-components-select.md), and [Swiper](arkui-ts/ts-container-swiper.md) in ArkUI.
> - Accessibility applications will announce the position of the subitem based on **rowIndex** and **columnIndex** in **gridItem**, for example, "row 2, column 3".
> - If **heading** in [ArkUI_AccessibleGridItemInfo](capi-arkui-accessibility-arkui-accessiblegriditeminfo.md) is set to **true**, accessibility applications will announce "title".
> - A null pointer cannot be passed to **gridItem** and **elementInfo**. Otherwise, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| [ArkUI_AccessibleGridItemInfo](capi-arkui-accessibility-arkui-accessiblegriditeminfo.md)* gridItem | Pointer to the attribute value of the grid subitem. The value cannot be a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetSelectedTextStart()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetSelectedTextStart(ArkUI_AccessibilityElementInfo* elementInfo, int32_t selectedTextStart)
```

**Description**


Sets the start position of the selected text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
>
> - **selectedTextStart** is used for editable text components to mark the start character index position (counting from 0) of the currently selected text.
> - Auxiliary applications, such as accessibility applications, announce the currently selected text range based on **selectedTextStart** and **selectedTextEnd**.
> - When a user performs an [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SELECT_TEXT](#arkui_accessibility_actiontype) action through an accessibility application, a third-party framework should obtain the start position.
> - You can obtain the start position through **selectTextBegin** in [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md).
> - **selectedTextStart** must be used together with **selectedTextEnd** (set by [OH_ArkUI_AccessibilityElementInfoSetSelectedTextEnd](#oh_arkui_accessibilityelementinfosetselectedtextend)), and the value of **selectedTextStart** must not be greater than that of **selectedTextEnd**.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t selectedTextStart | Start position index of the selected text (starting from 0), which is applicable to text components. This parameter must be used together with **selectedTextEnd**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetSelectedTextEnd()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetSelectedTextEnd(ArkUI_AccessibilityElementInfo* elementInfo, int32_t selectedTextEnd)
```

**Description**


Sets the end position of the selected text for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
>
> - **selectedTextEnd** is used for editable text components to mark the end character index position (counting from 0) of the currently selected text.
> - Auxiliary applications, such as accessibility applications, calculate and announce the selected text content based on **selectedTextStart** and **selectedTextEnd**.
> - **selectedTextEnd** must be used together with **selectedTextStart**, and the value of **selectedTextEnd** must be greater than or equal to that of **selectedTextStart**. You can set **selectedTextStart** by [OH_ArkUI_AccessibilityElementInfoSetSelectedTextStart](#oh_arkui_accessibilityelementinfosetselectedtextstart).
> - When no text is selected, **selectedTextStart** and **selectedTextEnd** can be set to the same value (that is, the cursor position).

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t selectedTextEnd | End position index of the selected text (starting from 0), which is applicable to text components. This parameter must be used together with **selectedTextStart**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetCurrentItemIndex()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetCurrentItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t currentItemIndex)
```

**Description**


Sets the position index of the currently focused or highlighted subitem for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **currentItemIndex** is used for container components, such as [List](arkui-ts/ts-container-list.md), [Select](arkui-ts/ts-basic-components-select.md), [Swiper](arkui-ts/ts-container-swiper.md), and [Tab](arkui-ts/ts-container-tabs.md), and it indicates the position index (starting from 0) of the currently focused or active subitem in the container.
> - Accessibility applications will announce the position of the current item, for example, "item 3 of 10".
> - **currentItemIndex** must be used together with **itemCount** (set by [OH_ArkUI_AccessibilityElementInfoSetItemCount](#oh_arkui_accessibilityelementinfosetitemcount)) so that accessibility applications can announce the complete information, that is, "item X of Y".
> - The value of **currentItemIndex** must be within the range of 0 to **itemCount** – 1.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t currentItemIndex | Position index (starting from 0) of the currently focused component, which must be used together with **itemCount**. This parameter applies to container components such as [List](arkui-ts/ts-container-list.md), [Select](arkui-ts/ts-basic-components-select.md), [Swiper](arkui-ts/ts-container-swiper.md), and [Tab](arkui-ts/ts-container-tabs.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetStartItemIndex()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetStartItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t startItemIndex)
```

**Description**


Sets the position index of the first element in the visible area of the current screen for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **startItemIndex** is used for scrollable container components, such as [List](arkui-ts/ts-container-list.md), [Select](arkui-ts/ts-basic-components-select.md), [Swiper](arkui-ts/ts-container-swiper.md), and [Tab](arkui-ts/ts-container-tabs.md), and it indicates the position index (starting from 0) of the first subitem in the visible area of the current screen.
> - Auxiliary applications, such as accessibility applications, determine the visible area based on **startItemIndex** and **endItemIndex** (set by [OH_ArkUI_AccessibilityElementInfoSetEndItemIndex](#oh_arkui_accessibilityelementinfosetenditemindex)) to optimize focus movement and announcement.
> - The value of **startItemIndex** must be less than or equal to that of **endItemIndex**, and both values must be within the range of 0 to **itemCount** – 1.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t startItemIndex | Position index of the first element in the visible area of the current screen (starting from 0). This parameter is used for container components such as **List**, **Select**, **Swiper**, and **Tab_Bar**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetEndItemIndex()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetEndItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t endItemIndex)
```

**Description**


Sets the position index of the last element in the visible area of the current screen for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **endItemIndex** is used for scrollable container components, such as [List](arkui-ts/ts-container-list.md), [Select](arkui-ts/ts-basic-components-select.md), [Swiper](arkui-ts/ts-container-swiper.md), and [Tab](arkui-ts/ts-container-tabs.md), and it indicates the position index (starting from 0) of the last subitem in the visible area of the current screen.
> - Auxiliary applications, such as accessibility applications, determine the visible area based on **startItemIndex** (set by [OH_ArkUI_AccessibilityElementInfoSetStartItemIndex](#oh_arkui_accessibilityelementinfosetstartitemindex)) and **endItemIndex**, so that the applications can announce scrolling progress based on these values when users perform scrolling actions.
> - The value of **endItemIndex** must be greater than or equal to that of **startItemIndex**, and both values must be within the range of 0 to **itemCount** – 1.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t endItemIndex | Position index of the last element in the visible area of the current screen (starting from 0). This parameter is used for container components such as **List**, **Select**, **Swiper**, and **Tab_Bar**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetItemCount()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetItemCount(ArkUI_AccessibilityElementInfo* elementInfo, int32_t itemCount)
```

**Description**


Sets the total number of subitems in the container for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **itemCount** is used for container components, such as [List](arkui-ts/ts-container-list.md), [Select](arkui-ts/ts-basic-components-select.md), [Swiper](arkui-ts/ts-container-swiper.md), and [Tab](arkui-ts/ts-container-tabs.md), and it indicates the total number of subitems in the container.
> - Auxiliary applications, such as accessibility applications, will announce the position of the current item based on **currentItemIndex** (set by [OH_ArkUI_AccessibilityElementInfoSetCurrentItemIndex](#oh_arkui_accessibilityelementinfosetcurrentitemindex)) and **itemCount**, for example, "item 3 of 10".
> - The value of **itemCount** should be the total number of subitems in the container (including both visible and invisible items), not just the number of subitems currently visible on the screen.
> - The value of **itemCount** must be a non-negative integer. The value **0** indicates that the container is empty.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t itemCount | Total number of subitems (including visible and invisible items) in the container, which is used by auxiliary applications to announce "item X of Y". This parameter is used for container components such as [List](arkui-ts/ts-container-list.md), [Select](arkui-ts/ts-basic-components-select.md), [Swiper](arkui-ts/ts-container-swiper.md), and [Tab](arkui-ts/ts-container-tabs.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityOffset()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityOffset(ArkUI_AccessibilityElementInfo* elementInfo, int32_t offset)
```

**Description**


Sets the scroll offset for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **offset** is used for scrollable container components, such as [List](arkui-ts/ts-container-list.md), [Grid](arkui-ts/ts-container-grid.md), and [Scroll](arkui-ts/ts-container-scroll.md, and it indicates the scrolling pixel offset of the content area relative to the top coordinates of the element.
> - The accessibility service uses **offset** to determine the scrolling position, and auxiliary applications use it to announce the scrolling progress.
> - After a user performs an [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_FORWARD](#arkui_accessibility_actiontype) or [ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_BACKWARD](#arkui_accessibility_actiontype) action, a third-party framework should update the **offset** value in the updated node information.
> - If the value of **offset** is **0**, the content area is not scrolled (at the initial position). A positive value indicates the pixel distance for scrolling down or right.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t offset | Scrolling pixel offset of the content area relative to the top coordinates of the element for scrollable controls, such as [List](arkui-ts/ts-container-list.md) and [Grid](arkui-ts/ts-container-grid.md). The unit is pixel. The value **0** indicates that the content area is not scrolled. A positive value indicates the scrolled distance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityGroup()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityGroup(ArkUI_AccessibilityElementInfo* elementInfo, bool accessibilityGroup)
```

**Description**


Sets the accessibility group for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **accessibilityGroup** indicates whether to treat the component and all its child components as a whole.
> - When **accessibilityGroup** is set to **true**, accessibility applications consider the node as a whole and fo not focus on or announce the information about its child nodes separately, but combine the text content of its child nodes and announce the content together.
> - This attribute is applicable to scenarios where a group of related content (for example, a list item containing an icon and text) is treated as an accessibility unit. For example, a list item contains a product image and name. After **accessibilityGroup** is set to **true**, accessibility applications will treat the entire list item as a node to announce instead of announcing the image and text separately.
> - If **accessibilityGroup** is set to **false**, accessibility applications traverse child nodes one by one.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| bool accessibilityGroup | Whether to enable accessibility group behavior for the object. The value **true** indicates that the component and its child components are announced as a whole. The value **false** indicates that child nodes are traversed one by one.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityLevel()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityLevel(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityLevel)
```

**Description**


Sets the accessibility importance level for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **accessibilityLevel** is used to control whether a component can be identified by the accessibility service, which affects the visibility of the node in the accessibility node tree.
> - Auxiliary applications, such as accessibility applications, determine whether to display the node to users based on **accessibilityLevel**.
> - The values and their meanings are as follows:
> - **auto**: The system automatically determines whether the component is important based on its attributes and whether to allow the accessibility service to identify the component. Generally, components with interactive attributes (such as **clickable**) or text content are automatically identified as important.
> - **yes**: The component is important and can be identified by the accessibility service. The accessibility service identifies the component regardless of the component attributes.
> - **no**: The component is not important and cannot be identified by the accessibility service. The accessibility service skips this node, but its child nodes can still be identified.
> - **no-hide-descendants**: The component and all its descendant components are not important and cannot be identified by the accessibility service. This value is applicable to containers that are only used for decoration, to prevent the accessibility service from announcing meaningless content.
> - A null pointer cannot be passed to **accessibilityLevel**. If a null pointer is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* accessibilityLevel | Pointer to the accessibility importance level of the component. The value can be **auto**, **yes**, **no**, or **no-hide-descendants**, but cannot be a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetZIndex()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetZIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t zIndex)
```

**Description**


Sets the component Z-index for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **zIndex** is used to control the position of an element along the z-axis perpendicular to the screen. When multiple components overlap on the screen, the component with a larger **zIndex** value will cover the component with a smaller **zIndex** value.
> - This attribute is mainly used by the **UiTest** automation framework to identify the stacking order of components.
> - The accessibility service may also use **zIndex** to determine the focus movement direction.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| int32_t zIndex | Z-order of the component, used to control the position of the component along the z-axis perpendicular to the screen. This parameter is required for [UiTest](../apis-test-kit/js-apis-uitest.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityOpacity()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityOpacity(ArkUI_AccessibilityElementInfo* elementInfo, float opacity)
```

**Description**


Sets the opacity for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **opacity** indicates the opacity of a component. This attribute is mainly used by the **UiTest** automation framework to identify the visual opacity status of a component. The value ranges from 0 to 1, where **1** indicates opaque and **0** indicates completely transparent.
> - Note: If **NaN** is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned. However, values outside the range of 0 to 1 (such as a negative number or a value greater than 1) will not be automatically corrected. It is recommended that you always pass a valid value from 0 to 1.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| float opacity | Opacity. The value ranges from 0 to 1, where **1** indicates opaque and **0** indicates completely transparent. This parameter is required for [UiTest](../apis-test-kit/js-apis-uitest.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetBackgroundColor()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetBackgroundColor(ArkUI_AccessibilityElementInfo* elementInfo, const char* backgroundColor)
```

**Description**


Sets the background color for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **backgroundColor** indicates the background color of a component. This attribute is mainly used by the **UiTest** automation framework to identify the visual background color of a component.
> - This attribute is in the format of **#ARGB**. For example, **#FFFFFFFF** indicates non-transparent white and **#80FF0000** indicates semi-transparent red.
> - A null pointer cannot be passed to **backgroundColor**. If a null pointer is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* backgroundColor | Pointer to the background color. The value is in the **#ARGB** format. For example, the value for non-transparent white is **#FFFFFFFF**. The value cannot be a null pointer. This parameter is required for [UiTest](../apis-test-kit/js-apis-uitest.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetBackgroundImage()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetBackgroundImage(ArkUI_AccessibilityElementInfo* elementInfo, const char* backgroundImage)
```

**Description**


Sets the background image for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **backgroundImage** indicates the background image resource of a component. This attribute is mainly used by the **UiTest** automation framework to identify the visual background image of a component.
> - A null pointer cannot be passed to **backgroundImage**. If a null pointer is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* backgroundImage | Pointer to the path or description of the background image resource. The value cannot be a null pointer. This parameter is required for [UiTest](../apis-test-kit/js-apis-uitest.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetBlur()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetBlur(ArkUI_AccessibilityElementInfo* elementInfo, const char* blur)
```

**Description**


Sets the blur effect for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **blur** indicates the blur effect parameter of a component. This attribute is mainly used by the **UiTest** automation framework to identify the visual blur status of a component.
> - A null pointer cannot be passed to **blur**. If a null pointer is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* blur | Pointer to the blur value. The value cannot be a null pointer. This parameter is required for [UiTest](../apis-test-kit/js-apis-uitest.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetHitTestBehavior()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetHitTestBehavior(ArkUI_AccessibilityElementInfo* elementInfo, const char* hitTestBehavior)
```

**Description**


Sets the response logic and node blocking rule for the hit test for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).

> **NOTE**
> 
> - **hitTestBehavior** is used to control the response behavior of a component during the hit test and determine whether the touch event can pass through the component.
> - This attribute is mainly used by the **UiTest** automation framework. For details about the value range, see **HitTestMode**. The options are as follows:
> - **Default**: The default behavior is used, which does not block the touch event.
> - **Block**: The touch event of the component and its child components is blocked.
> - **Transparent**: The component does not respond to the touch event, but its child components can respond.
> - **None**: Neither the component nor its child components respond to the touch event.
> - A null pointer cannot be passed to **hitTestBehavior**. If a null pointer is passed, [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) is returned.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|
| const char* hitTestBehavior | Pointer to the hit test mode. The value cannot be a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityElementInfoSetComponentIdentifier()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetComponentIdentifier(ArkUI_AccessibilityElementInfo* elementInfo, const char* identifier)
```

**Description**


Sets the component identifier for [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md), which can be used to identify a specific component during automated testing.

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to the element information of an accessibility node.|
| const char* identifier | Pointer to the unique identifier of a component.<br>Ensure that the component identifier in the reported component tree is unique and the character string contains a maximum of 1024 characters. If the character string exceeds 1024 characters, it will be truncated.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_CreateAccessibilityElementInfo()

```c
ArkUI_AccessibilityElementInfo* OH_ArkUI_CreateAccessibilityElementInfo(void)
```

**Description**


Creates an [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) object. After the object is created, call [OH_ArkUI_DestoryAccessibilityElementInfo](#oh_arkui_destoryaccessibilityelementinfo) to destroy it.

**Since**: 13

**Returns**

| Type                                 | Description|
|-------------------------------------| -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* | Pointer to the [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) object.|

### OH_ArkUI_DestoryAccessibilityElementInfo()

```c
void OH_ArkUI_DestoryAccessibilityElementInfo(ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**


Destroys an [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) object.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md).|

### OH_ArkUI_CreateAccessibilityEventInfo()

```c
ArkUI_AccessibilityEventInfo* OH_ArkUI_CreateAccessibilityEventInfo(void)
```

**Description**


Creates an [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) object. After the object is created, call [OH_ArkUI_DestoryAccessibilityEventInfo](#oh_arkui_destoryaccessibilityeventinfo) to destroy it.

**Since**: 13

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* | Pointer to the [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) object.|

### OH_ArkUI_DestoryAccessibilityEventInfo()

```c
void OH_ArkUI_DestoryAccessibilityEventInfo(ArkUI_AccessibilityEventInfo* eventInfo)
```

**Description**


Destroys an [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) object.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Pointer to the [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) object to be destroyed.|

### OH_ArkUI_AccessibilityEventSetEventType()

```c
int32_t OH_ArkUI_AccessibilityEventSetEventType(ArkUI_AccessibilityEventInfo* eventInfo,  ArkUI_AccessibilityEventType eventType)
```

**Description**


Sets the event type for [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md).

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Pointer to an **ArkUI_AccessibilityEventInfo** object.|
| [ArkUI_AccessibilityEventType](capi-native-interface-accessibility-h.md#arkui_accessibilityeventtype) eventType | Event type.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityEventSetTextAnnouncedForAccessibility()

```c
int32_t OH_ArkUI_AccessibilityEventSetTextAnnouncedForAccessibility(ArkUI_AccessibilityEventInfo* eventInfo,  const char* textAnnouncedForAccessibility)
```

**Description**


Sets the content to be proactively announced for [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md).

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Pointer to an **ArkUI_AccessibilityEventInfo** object.|
| const char* textAnnouncedForAccessibility | Pointer to the content for auto-announcing.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityEventSetRequestFocusId()

```c
int32_t OH_ArkUI_AccessibilityEventSetRequestFocusId(ArkUI_AccessibilityEventInfo* eventInfo,  int32_t requestFocusId)
```

**Description**


Sets the focus request ID for [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md).

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Pointer to an **ArkUI_AccessibilityEventInfo** object.|
| int32_t requestFocusId | Focus request ID.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_AccessibilityEventSetElementInfo()

```c
int32_t OH_ArkUI_AccessibilityEventSetElementInfo(ArkUI_AccessibilityEventInfo* eventInfo,  ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**


Sets **elementInfo** for [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md).

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Pointer to an **ArkUI_AccessibilityEventInfo** object.|
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to the [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) element information.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_FindAccessibilityActionArgumentByKey()

```c
int32_t OH_ArkUI_FindAccessibilityActionArgumentByKey(ArkUI_AccessibilityActionArguments* arguments, const char* key, char** value)
```

**Description**


Obtains the value of a specified key in [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md).

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md)* arguments | Pointer to the [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) object information.|
| const char* key | Pointer to the key.|
| char** value | Pointer to the value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### OH_ArkUI_NativeModule_GetNativeAccessibilityProvider()

```c
int32_t OH_ArkUI_NativeModule_GetNativeAccessibilityProvider(ArkUI_NodeHandle* node, ArkUI_AccessibilityProvider** provider)
```

**Description**

Obtains the level-2 pointer variable of the pointer to the [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) object.

The [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) object corresponds to the [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) instance passed.

A third-party framework maps its UI components as [RenderNode](js-apis-arkui-renderNode.md) of the [ARKUI_NODE_CUSTOM](capi-native-node-h.md#arkui_nodetype) type to obtain [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).

Then, it calls **OH_ArkUI_NativeModule_GetNativeAccessibilityProvider** to obtain the [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) pointer and register an accessibility callback.

Finally, the ArkUI accessibility service can identify the UI of the third-party framework and trigger events.

This API takes effect only when the third-party framework maps its UI components as [RenderNode](js-apis-arkui-renderNode.md) of the [ARKUI_NODE_CUSTOM](capi-native-node-h.md#arkui_nodetype) type. Otherwise, an error code will be reported.

This API uses [RenderNode](js-apis-arkui-renderNode.md) to implement the access of the third-party framework. Only [ARKUI_NODE_CUSTOM](capi-native-node-h.md#arkui_nodetype) can access the accessibility service to obtain the accessibility control tree.

Multi-thread concurrency is not supported. The third-party framework ensures thread security during the API calling.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | Pointer to an [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) object.|
| [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md)** provider | Double pointer to an [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) object. **provider** is used to register an accessibility callback function.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Status code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>Parameter error: 1. The input parameter **node** or **provider** is a null pointer.<br>2. The **ArkUI_NodeHandle** type corresponding to **node** is not **ARKUI_NODE_CUSTOM**.|
