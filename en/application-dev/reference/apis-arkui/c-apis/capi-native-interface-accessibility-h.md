# native_interface_accessibility.h

## Overview

Declares the APIs used to access the native Accessibility.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_AccessibleAction](capi-arkui-accessibility-arkui-accessibleaction.md) | ArkUI_AccessibleAction | Defines a struct for the accessible action. |
| [ArkUI_AccessibleRect](capi-arkui-accessibility-arkui-accessiblerect.md) | ArkUI_AccessibleRect | Defines a struct for the accessible rectangle. |
| [ArkUI_AccessibleRangeInfo](capi-arkui-accessibility-arkui-accessiblerangeinfo.md) | ArkUI_AccessibleRangeInfo | Define a struct for the accessible range information. |
| [ArkUI_AccessibleGridInfo](capi-arkui-accessibility-arkui-accessiblegridinfo.md) | ArkUI_AccessibleGridInfo | Defines a struct for the accessible grid information. |
| [ArkUI_AccessibleGridItemInfo](capi-arkui-accessibility-arkui-accessiblegriditeminfo.md) | ArkUI_AccessibleGridItemInfo | Defines a struct for the accessible grid item information. |
| [ArkUI_AccessibilityProviderCallbacks](capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md) | ArkUI_AccessibilityProviderCallbacks | Registers callbacks for the accessibility provider. |
| [ArkUI_AccessibilityProviderCallbacksWithInstance](capi-arkui-accessibility-arkui-accessibilityprovidercallbackswithinstance.md) | ArkUI_AccessibilityProviderCallbacksWithInstance | Registers callbacks with instance for the accessibility provider. |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) | ArkUI_AccessibilityElementInfo | Defines a struct for accessibility element information. |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) | ArkUI_AccessibilityEventInfo | Defines a struct for accessibility event information. |
| [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md) | ArkUI_AccessibilityProvider | Defines a struct for the local provider of accessibility. |
| [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) | ArkUI_AccessibilityActionArguments | Defines a struct for accessibility action arguments. |
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md) | ArkUI_AccessibilityElementInfoList | Defines a struct for the accessibility element information list. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_Accessibility_ActionType](#arkui_accessibility_actiontype) | ArkUI_Accessibility_ActionType | Defines an enum for accessibility action types. |
| [ArkUI_AccessibilityEventType](#arkui_accessibilityeventtype) | ArkUI_AccessibilityEventType | Defines an enum for accessibility event types. |
| [ArkUI_AcessbilityErrorCode](#arkui_acessbilityerrorcode) | ArkUI_AcessbilityErrorCode | Enumerates the accessibility error codes. |
| [ArkUI_AccessibilitySearchMode](#arkui_accessibilitysearchmode) | ArkUI_AccessibilitySearchMode | Defines an enum for the accessibility search modes. |
| [ArkUI_AccessibilityFocusType](#arkui_accessibilityfocustype) | ArkUI_AccessibilityFocusType | Defines an enum for the accessibility focus types. |
| [ArkUI_AccessibilityFocusMoveDirection](#arkui_accessibilityfocusmovedirection) | ArkUI_AccessibilityFocusMoveDirection | Enumerates the directions for moving the accessibility focus. |

### Macro

| Name | Description |
| -- | -- |
| _NATIVE_INTERFACE_ACCESSIBILITY_H | Declares the APIs used to access the native Accessibility.<br>**Since**: 13<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_ArkUI_AccessibilityProviderRegisterCallback(ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityProviderCallbacks* callbacks)](#oh_arkui_accessibilityproviderregistercallback) | Registers a callback for this <b>ArkUI_AccessibilityProvider</b> instance. |
| [int32_t OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance(const char* instanceId, ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityProviderCallbacksWithInstance* callbacks)](#oh_arkui_accessibilityproviderregistercallbackwithinstance) | Registers a callback with instance for this <b>ArkUI_AccessibilityProvider</b> instance. |
| [void OH_ArkUI_SendAccessibilityAsyncEvent(ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityEventInfo* eventInfo, void (\*callback)(int32_t errorCode))](#oh_arkui_sendaccessibilityasyncevent) | Sends accessibility event information. |
| [ArkUI_AccessibilityElementInfo* OH_ArkUI_AddAndGetAccessibilityElementInfo(ArkUI_AccessibilityElementInfoList* list)](#oh_arkui_addandgetaccessibilityelementinfo) | Adds and obtains the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetElementId(ArkUI_AccessibilityElementInfo* elementInfo, int32_t elementId)](#oh_arkui_accessibilityelementinfosetelementid) | Sets the element ID for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetParentId(ArkUI_AccessibilityElementInfo* elementInfo, int32_t parentId)](#oh_arkui_accessibilityelementinfosetparentid) | Sets the parent ID for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetComponentType(ArkUI_AccessibilityElementInfo* elementInfo, const char* componentType)](#oh_arkui_accessibilityelementinfosetcomponenttype) | Sets the component type for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetContents(ArkUI_AccessibilityElementInfo* elementInfo, const char* contents)](#oh_arkui_accessibilityelementinfosetcontents) | Sets the component content for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetHintText(ArkUI_AccessibilityElementInfo* elementInfo, const char* hintText)](#oh_arkui_accessibilityelementinfosethinttext) | Sets the hint text for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityText(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityText)](#oh_arkui_accessibilityelementinfosetaccessibilitytext) | Sets the accessibility text for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityDescription(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityDescription)](#oh_arkui_accessibilityelementinfosetaccessibilitydescription) | Sets the accessibility description for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetChildNodeIds(ArkUI_AccessibilityElementInfo* elementInfo, int32_t childCount, int64_t* childNodeIds)](#oh_arkui_accessibilityelementinfosetchildnodeids) | Set the number of child nodes and child node IDs for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetOperationActions(ArkUI_AccessibilityElementInfo* elementInfo, int32_t operationCount, ArkUI_AccessibleAction* operationActions)](#oh_arkui_accessibilityelementinfosetoperationactions) | Sets the operation actions for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetScreenRect(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleRect* screenRect)](#oh_arkui_accessibilityelementinfosetscreenrect) | Sets the screen area for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetCheckable(ArkUI_AccessibilityElementInfo* elementInfo, bool checkable)](#oh_arkui_accessibilityelementinfosetcheckable) | Sets whether the element is checkable for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetChecked(ArkUI_AccessibilityElementInfo* elementInfo, bool checked)](#oh_arkui_accessibilityelementinfosetchecked) | Sets whether the element is checked for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetFocusable(ArkUI_AccessibilityElementInfo* elementInfo, bool focusable)](#oh_arkui_accessibilityelementinfosetfocusable) | Sets whether the element is focusable for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetFocused(ArkUI_AccessibilityElementInfo* elementInfo, bool isFocused)](#oh_arkui_accessibilityelementinfosetfocused) | Sets whether the element is focused for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetVisible(ArkUI_AccessibilityElementInfo* elementInfo, bool isVisible)](#oh_arkui_accessibilityelementinfosetvisible) | Sets whether the element is visible for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityFocused(ArkUI_AccessibilityElementInfo* elementInfo, bool accessibilityFocused)](#oh_arkui_accessibilityelementinfosetaccessibilityfocused) | Sets the accessibility focus state for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetSelected(ArkUI_AccessibilityElementInfo* elementInfo, bool selected)](#oh_arkui_accessibilityelementinfosetselected) | Sets whether the element is selected for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetClickable(ArkUI_AccessibilityElementInfo* elementInfo, bool clickable)](#oh_arkui_accessibilityelementinfosetclickable) | Sets whether the element is clickable for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetLongClickable(ArkUI_AccessibilityElementInfo* elementInfo, bool longClickable)](#oh_arkui_accessibilityelementinfosetlongclickable) | Sets whether the element is long clickable for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetEnabled(ArkUI_AccessibilityElementInfo* elementInfo, bool isEnabled)](#oh_arkui_accessibilityelementinfosetenabled) | Sets whether the element is enabled for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetIsPassword(ArkUI_AccessibilityElementInfo* elementInfo, bool isPassword)](#oh_arkui_accessibilityelementinfosetispassword) | Sets whether the element is a password for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetScrollable(ArkUI_AccessibilityElementInfo* elementInfo, bool scrollable)](#oh_arkui_accessibilityelementinfosetscrollable) | Sets whether the element is scrollable for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetEditable(ArkUI_AccessibilityElementInfo* elementInfo, bool editable)](#oh_arkui_accessibilityelementinfoseteditable) | Sets whether the element is editable for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetIsHint(ArkUI_AccessibilityElementInfo* elementInfo, bool isHint)](#oh_arkui_accessibilityelementinfosetishint) | Sets whether the element is a hint for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetRangeInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleRangeInfo* rangeInfo)](#oh_arkui_accessibilityelementinfosetrangeinfo) | Sets the range information for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetGridInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleGridInfo* gridInfo)](#oh_arkui_accessibilityelementinfosetgridinfo) | Sets the grid information for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetGridItemInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleGridItemInfo* gridItem)](#oh_arkui_accessibilityelementinfosetgriditeminfo) | Sets the grid item for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetSelectedTextStart(ArkUI_AccessibilityElementInfo* elementInfo, int32_t selectedTextStart)](#oh_arkui_accessibilityelementinfosetselectedtextstart) | Sets the starting index of the selected text for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetSelectedTextEnd(ArkUI_AccessibilityElementInfo* elementInfo, int32_t selectedTextEnd)](#oh_arkui_accessibilityelementinfosetselectedtextend) | Sets the end index of the selected text for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetCurrentItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t currentItemIndex)](#oh_arkui_accessibilityelementinfosetcurrentitemindex) | Sets the index of the currently selected item for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetStartItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t startItemIndex)](#oh_arkui_accessibilityelementinfosetstartitemindex) | Sets the index of the first item for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetEndItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t endItemIndex)](#oh_arkui_accessibilityelementinfosetenditemindex) | Sets the index of the last item for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetItemCount(ArkUI_AccessibilityElementInfo* elementInfo, int32_t itemCount)](#oh_arkui_accessibilityelementinfosetitemcount) | Sets the number of items for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityOffset(ArkUI_AccessibilityElementInfo* elementInfo, int32_t offset)](#oh_arkui_accessibilityelementinfosetaccessibilityoffset) | Sets the offset for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityGroup(ArkUI_AccessibilityElementInfo* elementInfo, bool accessibilityGroup)](#oh_arkui_accessibilityelementinfosetaccessibilitygroup) | Sets the accessibility group for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityLevel(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityLevel)](#oh_arkui_accessibilityelementinfosetaccessibilitylevel) | Sets the accessibility level for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetZIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t zIndex)](#oh_arkui_accessibilityelementinfosetzindex) | Sets the z-index for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityOpacity(ArkUI_AccessibilityElementInfo* elementInfo, float opacity)](#oh_arkui_accessibilityelementinfosetaccessibilityopacity) | Sets the opacity for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetBackgroundColor(ArkUI_AccessibilityElementInfo* elementInfo, const char* backgroundColor)](#oh_arkui_accessibilityelementinfosetbackgroundcolor) | Sets the background color for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetBackgroundImage(ArkUI_AccessibilityElementInfo* elementInfo, const char* backgroundImage)](#oh_arkui_accessibilityelementinfosetbackgroundimage) | Sets the background image for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetBlur(ArkUI_AccessibilityElementInfo* elementInfo, const char* blur)](#oh_arkui_accessibilityelementinfosetblur) | Sets the blur effect for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetHitTestBehavior(ArkUI_AccessibilityElementInfo* elementInfo, const char* hitTestBehavior)](#oh_arkui_accessibilityelementinfosethittestbehavior) | Sets the hit test behavior for an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [ArkUI_AccessibilityElementInfo* OH_ArkUI_CreateAccessibilityElementInfo(void)](#oh_arkui_createaccessibilityelementinfo) | Creates an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [void OH_ArkUI_DestoryAccessibilityElementInfo(ArkUI_AccessibilityElementInfo* elementInfo)](#oh_arkui_destoryaccessibilityelementinfo) | Destroys an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [ArkUI_AccessibilityEventInfo* OH_ArkUI_CreateAccessibilityEventInfo(void)](#oh_arkui_createaccessibilityeventinfo) | Creates an <b>ArkUI_AccessibilityEventInfo</b> object. |
| [void OH_ArkUI_DestoryAccessibilityEventInfo(ArkUI_AccessibilityEventInfo* eventInfo)](#oh_arkui_destoryaccessibilityeventinfo) | Destroys an <b>ArkUI_AccessibilityEventInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityEventSetEventType(ArkUI_AccessibilityEventInfo* eventInfo, ArkUI_AccessibilityEventType eventType)](#oh_arkui_accessibilityeventseteventtype) | Sets the event type for an <b>ArkUI_AccessibilityEventInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityEventSetTextAnnouncedForAccessibility(ArkUI_AccessibilityEventInfo* eventInfo, const char* textAnnouncedForAccessibility)](#oh_arkui_accessibilityeventsettextannouncedforaccessibility) | Sets the text announced for accessibility for an <b>ArkUI_AccessibilityEventInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityEventSetRequestFocusId(ArkUI_AccessibilityEventInfo* eventInfo, int32_t requestFocusId)](#oh_arkui_accessibilityeventsetrequestfocusid) | Sets the request focus ID for an <b>ArkUI_AccessibilityEventInfo</b> object. |
| [int32_t OH_ArkUI_AccessibilityEventSetElementInfo(ArkUI_AccessibilityEventInfo* eventInfo, ArkUI_AccessibilityElementInfo* elementInfo)](#oh_arkui_accessibilityeventsetelementinfo) | Sets the element information for an <b>ArkUI_AccessibilityEventInfo</b> object. |
| [int32_t OH_ArkUI_FindAccessibilityActionArgumentByKey(ArkUI_AccessibilityActionArguments* arguments, const char* key, char** value)](#oh_arkui_findaccessibilityactionargumentbykey) | Obtains the value of a key from an <b>ArkUI_AccessibilityActionArguments</b> object. |
| [int32_t OH_ArkUI_NativeModule_GetNativeAccessibilityProvider(ArkUI_NodeHandle* node, ArkUI_AccessibilityProvider** provider)](#oh_arkui_nativemodule_getnativeaccessibilityprovider) | Obtains the pointer to the <b> ArkUI_AccessibilityProvider</b> instance of this <b>ArkUI_NodeHandle</b> instance. |
| [int32_t OH_ArkUI_AccessibilityElementInfoSetComponentIdentifier(ArkUI_AccessibilityElementInfo* elementInfo, const char* identifier)](#oh_arkui_accessibilityelementinfosetcomponentidentifier) | Sets the component identifier for an <b>ArkUI_AccessibilityElementInfo</b> object. |

## Enum type description

### ArkUI_Accessibility_ActionType

```c
enum ArkUI_Accessibility_ActionType
```

**Description**

Defines an enum for accessibility action types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

| Enum item | Description |
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_INVALID = 0 | Invalid action. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CLICK = 0x00000010 | Response to a click. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_LONG_CLICK = 0x00000020 | Response to a long click. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_GAIN_ACCESSIBILITY_FOCUS = 0x00000040 | Accessibility focus acquisition. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CLEAR_ACCESSIBILITY_FOCUS = 0x00000080 | Accessibility focus clearance. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_FORWARD = 0x00000100 | Forward scroll action. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SCROLL_BACKWARD = 0x00000200 | Backward scroll action. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_COPY = 0x00000400 | Copy action for text content. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_PASTE = 0x00000800 | Paste action for text content. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_CUT = 0x00001000 | Cut action for text content. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SELECT_TEXT = 0x00002000 | Text selection action, requiring the setting of <b>selectTextBegin</b>, <b>TextEnd</b>, and <b>TextInForward</b> |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SET_TEXT = 0x00004000 | Text content setting action. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_SET_CURSOR_POSITION = 0x00100000 | Cursor position setting action. |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_NEXT_HTML_ITEM = 0x02000000 | Support action for find next item in focus move operation @since 15 |
| ARKUI_ACCESSIBILITY_NATIVE_ACTION_TYPE_PREVIOUS_HTML_ITEM = 0x04000000 | Support action for find previous item in focus move operation @since 15 |

### ArkUI_AccessibilityEventType

```c
enum ArkUI_AccessibilityEventType
```

**Description**

Defines an enum for accessibility event types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

| Enum item | Description |
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_INVALID = 0 | Invalid event. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_CLICKED = 0x00000001 | Click event, sent after the UI component responds. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_LONG_CLICKED = 0x00000002 | Long click event, sent after the UI component responds. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_SELECTED = 0x00000004 | Selection event, sent after the UI component responds. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_TEXT_UPDATE = 0x00000010 | Text update event, sent when text is updated. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_PAGE_STATE_UPDATE = 0x00000020 | Page state update event, sent when the page transitions, switches, resizes, or moves. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_PAGE_CONTENT_UPDATE = 0x00000800 | Page content update event, sent when the page content changes. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_SCROLLED = 0x000001000 | Scrolled event, sent when a scrollable component experiences a scroll event. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ACCESSIBILITY_FOCUSED = 0x00008000 | Accessibility focus event, sent after the UI component responds. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ACCESSIBILITY_FOCUS_CLEARED = 0x00010000 | Accessibility focus cleared event, sent after the UI component responds. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_REQUEST_ACCESSIBILITY_FOCUS = 0x02000000 | FOcus request for a specific node. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_PAGE_OPEN = 0x20000000 | Page open event reported by the UI component. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_PAGE_CLOSE = 0x08000000 | Page close event reported by the UI component. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_ANNOUNCE_FOR_ACCESSIBILITY = 0x10000000 | Announcement event, indicating a request to proactively announce specified content. |
| ARKUI_ACCESSIBILITY_NATIVE_EVENT_TYPE_FOCUS_NODE_UPDATE = 0x10000001 | Focus update event, used for focus update scenarios. |

### ArkUI_AcessbilityErrorCode

```c
enum ArkUI_AcessbilityErrorCode
```

**Description**

Enumerates the accessibility error codes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

| Enum item | Description |
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL = 0 | Success. |
| ARKUI_ACCESSIBILITY_NATIVE_RESULT_FAILED = -1 | Failure. |
| ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER = -2 | Invalid parameter. |
| ARKUI_ACCESSIBILITY_NATIVE_RESULT_OUT_OF_MEMORY = -3 | Out of memory. |

### ArkUI_AccessibilitySearchMode

```c
enum ArkUI_AccessibilitySearchMode
```

**Description**

Defines an enum for the accessibility search modes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

| Enum item | Description |
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_CURRENT = 0 | Search for current nodes. |
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_PREDECESSORS = 1 << 0 | Search for parent nodes. |
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_SIBLINGS = 1 << 1 | Search for sibling nodes. |
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_CHILDREN = 1 << 2 | Search for child nodes at the next level. |
| ARKUI_ACCESSIBILITY_NATIVE_SEARCH_MODE_PREFETCH_RECURSIVE_CHILDREN = 1 << 3 | Search for all child nodes. |

### ArkUI_AccessibilityFocusType

```c
enum ArkUI_AccessibilityFocusType
```

**Description**

Defines an enum for the accessibility focus types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

| Enum item | Description |
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_FOCUS_TYPE_INVALID = -1 | Invalid type. |
| ARKUI_ACCESSIBILITY_NATIVE_FOCUS_TYPE_INPUT = 1 << 0 | Input focus type. |
| ARKUI_ACCESSIBILITY_NATIVE_FOCUS_TYPE_ACCESSIBILITY = 1 << 1 | Accessibility focus type. |

### ArkUI_AccessibilityFocusMoveDirection

```c
enum ArkUI_AccessibilityFocusMoveDirection
```

**Description**

Enumerates the directions for moving the accessibility focus.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

| Enum item | Description |
| -- | -- |
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_INVALID = 0 | Invalid direction. |
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_UP = 0x00000001 | Up. |
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_DOWN = 0x00000002 | Down. |
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_LEFT = 0x00000004 | Left. |
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_RIGHT = 0x00000008 | Right. |
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_FORWARD = 0x00000010 | Forward. |
| ARKUI_ACCESSIBILITY_NATIVE_DIRECTION_BACKWARD = 0x00000020 | Backward. |


## Function description

### OH_ArkUI_AccessibilityProviderRegisterCallback()

```c
int32_t OH_ArkUI_AccessibilityProviderRegisterCallback(ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityProviderCallbacks* callbacks)
```

**Description**

Registers a callback for this <b>ArkUI_AccessibilityProvider</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md)* provider | Indicates the pointer to the <b>ArkUI_AccessibilityProvider</b> instance. |
| [ArkUI_AccessibilityProviderCallbacks](capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md)* callbacks | Indicates the pointer to the <b>GetAccessibilityNodeCursorPosition</b> callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.          Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance()

```c
int32_t OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance(const char* instanceId, ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityProviderCallbacksWithInstance* callbacks)
```

**Description**

Registers a callback with instance for this <b>ArkUI_AccessibilityProvider</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* instanceId | Indicates ID of third-party framework instance. |
| [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md)* provider | Indicates the pointer to the <b>ArkUI_AccessibilityProvider</b> instance. |
| [ArkUI_AccessibilityProviderCallbacksWithInstance](capi-arkui-accessibility-arkui-accessibilityprovidercallbackswithinstance.md)* callbacks | Indicates the pointer to the <b>ArkUI_AccessibilityProviderCallbacksWithInstance</b> callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.          Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_SendAccessibilityAsyncEvent()

```c
void OH_ArkUI_SendAccessibilityAsyncEvent(ArkUI_AccessibilityProvider* provider, ArkUI_AccessibilityEventInfo* eventInfo, void (*callback)(int32_t errorCode))
```

**Description**

Sends accessibility event information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_AccessibilityProvider\* provider | Indicates the pointer to the <b>ArkUI_AccessibilityProvider</b> instance. |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)\* eventInfo | Indicates the pointer to the accessibility event information. |
| void (\*callback)(int32_t errorCode) | Indicates the pointer to the callback that is called after the event is sent. |

### OH_ArkUI_AddAndGetAccessibilityElementInfo()

```c
ArkUI_AccessibilityElementInfo* OH_ArkUI_AddAndGetAccessibilityElementInfo(ArkUI_AccessibilityElementInfoList* list)
```

**Description**

Adds and obtains the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* list | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfoList</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo*](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) | Returns the pointer to the <b>ArkUI_AccessibilityElementInfo</b> object. |

### OH_ArkUI_AccessibilityElementInfoSetElementId()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetElementId(ArkUI_AccessibilityElementInfo* elementInfo, int32_t elementId)
```

**Description**

Sets the element ID for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t elementId | Indicates the element ID. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetParentId()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetParentId(ArkUI_AccessibilityElementInfo* elementInfo, int32_t parentId)
```

**Description**

Sets the parent ID for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t parentId | Indicates the parent ID. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetComponentType()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetComponentType(ArkUI_AccessibilityElementInfo* elementInfo, const char* componentType)
```

**Description**

Sets the component type for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* componentType | Indicates the component type. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetContents()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetContents(ArkUI_AccessibilityElementInfo* elementInfo, const char* contents)
```

**Description**

Sets the component content for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* contents | Indicates the component content. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetHintText()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetHintText(ArkUI_AccessibilityElementInfo* elementInfo, const char* hintText)
```

**Description**

Sets the hint text for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* hintText | Indicates the hint text. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityText()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityText(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityText)
```

**Description**

Sets the accessibility text for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* accessibilityText | Indicates the accessibility text. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityDescription()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityDescription(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityDescription)
```

**Description**

Sets the accessibility description for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* accessibilityDescription | Indicates the accessibility description. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetChildNodeIds()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetChildNodeIds(ArkUI_AccessibilityElementInfo* elementInfo, int32_t childCount, int64_t* childNodeIds)
```

**Description**

Set the number of child nodes and child node IDs for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t childCount | Indicates the number of child nodes. |
| int64_t* childNodeIds | Indicates an array of child node IDs. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetOperationActions()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetOperationActions(ArkUI_AccessibilityElementInfo* elementInfo, int32_t operationCount, ArkUI_AccessibleAction* operationActions)
```

**Description**

Sets the operation actions for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t operationCount | Indicates the operation count. |
| [ArkUI_AccessibleAction](capi-arkui-accessibility-arkui-accessibleaction.md)* operationActions | Indicates the operation actions. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetScreenRect()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetScreenRect(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleRect* screenRect)
```

**Description**

Sets the screen area for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [ArkUI_AccessibleRect](capi-arkui-accessibility-arkui-accessiblerect.md)* screenRect | Indicates the screen area. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetCheckable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetCheckable(ArkUI_AccessibilityElementInfo* elementInfo, bool checkable)
```

**Description**

Sets whether the element is checkable for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool checkable | Indicates whether the element is checkable. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetChecked()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetChecked(ArkUI_AccessibilityElementInfo* elementInfo, bool checked)
```

**Description**

Sets whether the element is checked for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool checked | Indicates whether the element is checked. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetFocusable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetFocusable(ArkUI_AccessibilityElementInfo* elementInfo, bool focusable)
```

**Description**

Sets whether the element is focusable for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool focusable | Indicates whether the element is focusable. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetFocused()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetFocused(ArkUI_AccessibilityElementInfo* elementInfo, bool isFocused)
```

**Description**

Sets whether the element is focused for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool isFocused | Indicates whether the element is focused. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetVisible()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetVisible(ArkUI_AccessibilityElementInfo* elementInfo, bool isVisible)
```

**Description**

Sets whether the element is visible for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool isVisible | Indicates whether the element is visible. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityFocused()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityFocused(ArkUI_AccessibilityElementInfo* elementInfo, bool accessibilityFocused)
```

**Description**

Sets the accessibility focus state for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool accessibilityFocused | Indicates whether the element has accessibility focus. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetSelected()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetSelected(ArkUI_AccessibilityElementInfo* elementInfo, bool selected)
```

**Description**

Sets whether the element is selected for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool selected | Indicates whether the element is selected. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetClickable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetClickable(ArkUI_AccessibilityElementInfo* elementInfo, bool clickable)
```

**Description**

Sets whether the element is clickable for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool clickable | Indicates whether the element is clickable. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetLongClickable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetLongClickable(ArkUI_AccessibilityElementInfo* elementInfo, bool longClickable)
```

**Description**

Sets whether the element is long clickable for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool longClickable | Indicates whether the element is long clickable. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetEnabled()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetEnabled(ArkUI_AccessibilityElementInfo* elementInfo, bool isEnabled)
```

**Description**

Sets whether the element is enabled for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool isEnabled | Indicates whether the element is enabled. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetIsPassword()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetIsPassword(ArkUI_AccessibilityElementInfo* elementInfo, bool isPassword)
```

**Description**

Sets whether the element is a password for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool isPassword | Indicates whether the element is a password. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetScrollable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetScrollable(ArkUI_AccessibilityElementInfo* elementInfo, bool scrollable)
```

**Description**

Sets whether the element is scrollable for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool scrollable | Indicates whether the element is scrollable. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetEditable()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetEditable(ArkUI_AccessibilityElementInfo* elementInfo, bool editable)
```

**Description**

Sets whether the element is editable for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool editable | Indicates whether the element is editable. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetIsHint()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetIsHint(ArkUI_AccessibilityElementInfo* elementInfo, bool isHint)
```

**Description**

Sets whether the element is a hint for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool isHint | Indicates whether the element is a hint. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetRangeInfo()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetRangeInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleRangeInfo* rangeInfo)
```

**Description**

Sets the range information for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [ArkUI_AccessibleRangeInfo](capi-arkui-accessibility-arkui-accessiblerangeinfo.md)* rangeInfo | Indicates the range information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetGridInfo()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetGridInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleGridInfo* gridInfo)
```

**Description**

Sets the grid information for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [ArkUI_AccessibleGridInfo](capi-arkui-accessibility-arkui-accessiblegridinfo.md)* gridInfo | Indicates the grid information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetGridItemInfo()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetGridItemInfo(ArkUI_AccessibilityElementInfo* elementInfo, ArkUI_AccessibleGridItemInfo* gridItem)
```

**Description**

Sets the grid item for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| [ArkUI_AccessibleGridItemInfo](capi-arkui-accessibility-arkui-accessiblegriditeminfo.md)* gridItem | Indicates the grid item. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetSelectedTextStart()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetSelectedTextStart(ArkUI_AccessibilityElementInfo* elementInfo, int32_t selectedTextStart)
```

**Description**

Sets the starting index of the selected text for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t selectedTextStart | Indicates the starting index of the selected text |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetSelectedTextEnd()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetSelectedTextEnd(ArkUI_AccessibilityElementInfo* elementInfo, int32_t selectedTextEnd)
```

**Description**

Sets the end index of the selected text for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t selectedTextEnd | Indicates the end index of the selected text |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetCurrentItemIndex()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetCurrentItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t currentItemIndex)
```

**Description**

Sets the index of the currently selected item for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t currentItemIndex | Indicates the index of the currently selected item. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetStartItemIndex()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetStartItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t startItemIndex)
```

**Description**

Sets the index of the first item for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t startItemIndex | Indicates the index of the first item. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetEndItemIndex()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetEndItemIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t endItemIndex)
```

**Description**

Sets the index of the last item for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t endItemIndex | Indicates the index of the last item. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetItemCount()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetItemCount(ArkUI_AccessibilityElementInfo* elementInfo, int32_t itemCount)
```

**Description**

Sets the number of items for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t itemCount | Indicates the number of items. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityOffset()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityOffset(ArkUI_AccessibilityElementInfo* elementInfo, int32_t offset)
```

**Description**

Sets the offset for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t offset | Indicates the scroll pixel offset relative to the top of the element. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityGroup()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityGroup(ArkUI_AccessibilityElementInfo* elementInfo, bool accessibilityGroup)
```

**Description**

Sets the accessibility group for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| bool accessibilityGroup | Indicates the accessibility group. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityLevel()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityLevel(ArkUI_AccessibilityElementInfo* elementInfo, const char* accessibilityLevel)
```

**Description**

Sets the accessibility level for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* accessibilityLevel | Indicates the accessibility level. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetZIndex()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetZIndex(ArkUI_AccessibilityElementInfo* elementInfo, int32_t zIndex)
```

**Description**

Sets the z-index for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| int32_t zIndex | Indicates the z-index value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetAccessibilityOpacity()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetAccessibilityOpacity(ArkUI_AccessibilityElementInfo* elementInfo, float opacity)
```

**Description**

Sets the opacity for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| float opacity | Indicates the opacity. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetBackgroundColor()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetBackgroundColor(ArkUI_AccessibilityElementInfo* elementInfo, const char* backgroundColor)
```

**Description**

Sets the background color for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* backgroundColor | Indicates the background color. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetBackgroundImage()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetBackgroundImage(ArkUI_AccessibilityElementInfo* elementInfo, const char* backgroundImage)
```

**Description**

Sets the background image for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* backgroundImage | Indicates the backgroundImage. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetBlur()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetBlur(ArkUI_AccessibilityElementInfo* elementInfo, const char* blur)
```

**Description**

Sets the blur effect for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* blur | Indicates the blur effect. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityElementInfoSetHitTestBehavior()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetHitTestBehavior(ArkUI_AccessibilityElementInfo* elementInfo, const char* hitTestBehavior)
```

**Description**

Sets the hit test behavior for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* hitTestBehavior | Indicates the hit test behavior. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_CreateAccessibilityElementInfo()

```c
ArkUI_AccessibilityElementInfo* OH_ArkUI_CreateAccessibilityElementInfo(void)
```

**Description**

Creates an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo*](capi-arkui-accessibility-arkui-accessibilityelementinfo.md) | Returns the <b>ArkUI_AccessibilityElementInfo</b> object, or NULL if it fails to create.          The possible reason for failure is that the memory error occurred during object creation. |

### OH_ArkUI_DestoryAccessibilityElementInfo()

```c
void OH_ArkUI_DestoryAccessibilityElementInfo(ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Destroys an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to the <b>ArkUI_AccessibilityElementInfo</b> object to destroy. |

### OH_ArkUI_CreateAccessibilityEventInfo()

```c
ArkUI_AccessibilityEventInfo* OH_ArkUI_CreateAccessibilityEventInfo(void)
```

**Description**

Creates an <b>ArkUI_AccessibilityEventInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_AccessibilityEventInfo*](capi-arkui-accessibility-arkui-accessibilityeventinfo.md) | Returns the <b>ArkUI_AccessibilityEventInfo</b> object, or NULL if it fails to create.          The possible reason for failure is that the memory error occurred during object creation. |

### OH_ArkUI_DestoryAccessibilityEventInfo()

```c
void OH_ArkUI_DestoryAccessibilityEventInfo(ArkUI_AccessibilityEventInfo* eventInfo)
```

**Description**

Destroys an <b>ArkUI_AccessibilityEventInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Indicates the pointer to the <b>ArkUI_AccessibilityEventInfo</b> object to destroy. |

### OH_ArkUI_AccessibilityEventSetEventType()

```c
int32_t OH_ArkUI_AccessibilityEventSetEventType(ArkUI_AccessibilityEventInfo* eventInfo, ArkUI_AccessibilityEventType eventType)
```

**Description**

Sets the event type for an <b>ArkUI_AccessibilityEventInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Indicates the pointer to an <b>ArkUI_AccessibilityEventInfo</b> object. |
| [ArkUI_AccessibilityEventType](capi-native-interface-accessibility-h.md#arkui_accessibilityeventtype) eventType | Indicates the event type. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityEventSetTextAnnouncedForAccessibility()

```c
int32_t OH_ArkUI_AccessibilityEventSetTextAnnouncedForAccessibility(ArkUI_AccessibilityEventInfo* eventInfo, const char* textAnnouncedForAccessibility)
```

**Description**

Sets the text announced for accessibility for an <b>ArkUI_AccessibilityEventInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Indicates the pointer to an <b>ArkUI_AccessibilityEventInfo</b> object. |
| const char* textAnnouncedForAccessibility | Indicates the text announced for accessibility. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityEventSetRequestFocusId()

```c
int32_t OH_ArkUI_AccessibilityEventSetRequestFocusId(ArkUI_AccessibilityEventInfo* eventInfo, int32_t requestFocusId)
```

**Description**

Sets the request focus ID for an <b>ArkUI_AccessibilityEventInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Indicates the pointer to an <b>ArkUI_AccessibilityEventInfo</b> object. |
| int32_t requestFocusId | Indicates the request focus ID. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_AccessibilityEventSetElementInfo()

```c
int32_t OH_ArkUI_AccessibilityEventSetElementInfo(ArkUI_AccessibilityEventInfo* eventInfo, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Sets the element information for an <b>ArkUI_AccessibilityEventInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityEventInfo](capi-arkui-accessibility-arkui-accessibilityeventinfo.md)* eventInfo | Indicates the pointer to an <b>ArkUI_AccessibilityEventInfo</b> object. |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_FindAccessibilityActionArgumentByKey()

```c
int32_t OH_ArkUI_FindAccessibilityActionArgumentByKey(ArkUI_AccessibilityActionArguments* arguments, const char* key, char** value)
```

**Description**

Obtains the value of a key from an <b>ArkUI_AccessibilityActionArguments</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md)* arguments | Indicates the pointer to an <b>ArkUI_AccessibilityActionArguments</b> object. |
| const char* key | Indicates the key. |
| char** value | Indicates the value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.         Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### OH_ArkUI_NativeModule_GetNativeAccessibilityProvider()

```c
int32_t OH_ArkUI_NativeModule_GetNativeAccessibilityProvider(ArkUI_NodeHandle* node, ArkUI_AccessibilityProvider** provider)
```

**Description**

Obtains the pointer to the <b> ArkUI_AccessibilityProvider</b> instance of this <b>ArkUI_NodeHandle</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle* node | Indicates the pointer to the <b>ArkUI_NodeHandle</b> instance. |
| [ArkUI_AccessibilityProvider](capi-arkui-accessibility-arkui-accessibilityprovider.md)** provider | Indicates the pointer to the <b>ArkUI_AccessibilityProvider</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code. |

### OH_ArkUI_AccessibilityElementInfoSetComponentIdentifier()

```c
int32_t OH_ArkUI_AccessibilityElementInfoSetComponentIdentifier(ArkUI_AccessibilityElementInfo* elementInfo, const char* identifier)
```

**Description**

Sets the component identifier for an <b>ArkUI_AccessibilityElementInfo</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates the pointer to an <b>ArkUI_AccessibilityElementInfo</b> object. |
| const char* identifier | Indicates the component identifier. A string up to 1024 bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.          Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |


