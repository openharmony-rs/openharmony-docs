# ArkUI_AccessibilityProviderCallbacksWithInstance

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-16T10:45:16.827Z pushedAt=2026-07-17T02:16:20.639Z -->

```c
typedef struct {...} ArkUI_AccessibilityProviderCallbacksWithInstance
```

## Overview

Defines callback functions of a third-party action [provider](capi-arkui-accessibility-arkui-accessibilityprovider.md) in multi-instance scenarios, including node information query, focus search and clearing, action execution, and cursor position obtaining. The functions that need to be implemented by the third-party platform are registered with the system through [OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance](capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallbackwithinstance) to support the third-party platform in integrating with the system accessibility service.

**Since**: 15

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Functions

| Name| Description|
| -- | -- |
| [int32_t (\*findAccessibilityNodeInfosById)(const char* instanceId, int64_t elementId,ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbyid) | Finds the information about the specified node based on a search mode. Multi-instance scenarios are supported. Callback function implemented by the third-party platform and registered with the system. |
| [int32_t (\*findAccessibilityNodeInfosByText)(const char* instanceId, int64_t elementId, const char* text,int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbytext) | Finds the node information matching the specified text content. Multi-instance scenarios are supported. Callback function implemented by the third-party platform and registered with the system. |
| [int32_t (\*findFocusedAccessibilityNode)(const char* instanceId, int64_t elementId,ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findfocusedaccessibilitynode) | Finds the node that currently has focus within a given node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported. **Use scenario**: When the accessibility service needs to determine the currently focused element (for example, when a screen reader reads the content of the currently focused element), it can use this callback to query the element from the third-party platform. |
| [int32_t (\*findNextFocusAccessibilityNode)(const char* instanceId, int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findnextfocusaccessibilitynode) | Finds the next focusable node in a specified direction from a given node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.|
| [int32_t (\*executeAccessibilityAction)(const char* instanceId, int64_t elementId,ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)](#executeaccessibilityaction) | Executes a specified action on a specified node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported. **Use scenario**: When the accessibility service executes an action on behalf of a user on a UI element (such as automatic tap, focusing, and scrolling), it instructs the third-party platform to execute the corresponding action through this callback. |
| [int32_t (\*clearFocusedFocusAccessibilityNode)(const char* instanceId)](#clearfocusedfocusaccessibilitynode) | Removes focus from the current node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.|
| [int32_t (\*getAccessibilityNodeCursorPosition)(const char* instanceId, int64_t elementId,int32_t requestId, int32_t* index)](#getaccessibilitynodecursorposition) | Obtains the cursor position within a text component of the current accessibility node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported. |

## Member Function Description

### findAccessibilityNodeInfosById()

```c
int32_t (*findAccessibilityNodeInfosById)(const char* instanceId, int64_t elementId, ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Finds the information about the specified node based on a search mode. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name                                                                           | Description|
|--------------------------------------------------------------------------------| -- |
| const char* instanceId                                                         | Pointer to the instance ID of the third-party framework.|
| int64_t elementId                                                              | Unique ID of the accessibility element.|
| [ArkUI_AccessibilitySearchMode](capi-native-interface-accessibility-h.md#arkui_accessibilitysearchmode) mode | Search mode of the accessibility service, which determines how to query the information about a specified node, for example, query by subtree, by preorder traversal, or by postorder traversal. For details about the values and their meanings, see the description of **ArkUI_AccessibilitySearchMode**. |
| int32_t requestId                                                              | Request ID, which is used to associate the request process. It is recommended that this ID be logged to facilitate fault locating.|
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList                            | List of all accessibility elements found.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs. |

### findAccessibilityNodeInfosByText()

```c
int32_t (*findAccessibilityNodeInfosByText)(const char* instanceId, int64_t elementId, const char* text, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Finds the node information matching the specified text content. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported. **Use scenario:** When the accessibility service performs a text search (for example, when a user searches for an element containing specific text through a screen reader), it can use this callback to query the matched node information from the third-party platform.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| const char* instanceId | Pointer to the instance ID of the third-party framework.|
| int64_t elementId | Unique ID of the accessibility element, which must point to a text component. |
|  const char* text | Pointer to the text content to match in the component.|
| int32_t requestId | Request ID, which is used to associate the request process. It is recommended that this ID be logged to facilitate fault locating. |
|  [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList | Pointer to the list of all accessibility elements found.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs. |

### findFocusedAccessibilityNode()

```c
int32_t (*findFocusedAccessibilityNode)(const char* instanceId, int64_t elementId, ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Finds the node that currently has focus within a given node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name                                                                               | Description|
|------------------------------------------------------------------------------------| -- |
| const char* instanceId                                                             | Pointer to the instance ID of the third-party framework.|
| int64_t elementId                                                                  | Unique ID of the accessibility element.|
| [ArkUI_AccessibilityFocusType](capi-native-interface-accessibility-h.md#arkui_accessibilityfocustype) focusType | Focus type, used to distinguish between input focus and accessibility focus. |
| int32_t requestId                                                                  | Request ID, which is used to associate the request process. It is recommended that this ID be logged to facilitate fault locating.|
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo                                    | Pointer to the list of all accessibility elements found.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs. |

### findNextFocusAccessibilityNode()

```c
int32_t (*findNextFocusAccessibilityNode)(const char* instanceId, int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Finds the next focusable node in a specified direction from a given node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name                                                                                                                              | Description|
|-----------------------------------------------------------------------------------------------------------------------------------| -- |
| const char* instanceId                                                                                                            | Pointer to the instance ID of the third-party framework.|
| int64_t elementId                                                                                                                 | Unique ID of the accessibility element.|
| [ArkUI_AccessibilityFocusMoveDirection](capi-native-interface-accessibility-h.md#arkui_accessibilityfocusmovedirection) direction | Focus movement direction, which specifies the direction for finding the next focus node. |
| int32_t requestId                                                                                                                 | Request ID, which is used to associate the request process. It is recommended that this ID be logged to facilitate fault locating. |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo                         | Pointer to the list of all accessibility elements found.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### executeAccessibilityAction()

```c
int32_t (*executeAccessibilityAction)(const char* instanceId, int64_t elementId, ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments* actionArguments, int32_t requestId)
```

**Description**

Performs a specified action on a specified node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name                                                                                                             | Description|
|------------------------------------------------------------------------------------------------------------------| -- |
| const char* instanceId                                                                                           | Pointer to the instance ID of the third-party framework.|
| int64_t elementId                                                                                                | Unique ID of the accessibility element.|
| [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) action | Action to perform, such as focus, click, or long press.|
| [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) *actionArguments | Pointer to the collection of arguments required for executing an action. The specific parameter content depends on the action type specified by **action**. |
| int32_t requestId                                                                                                | Request ID, which is used to associate the request process. It is recommended that this ID be logged to facilitate fault locating. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### clearFocusedFocusAccessibilityNode()

```c
int32_t (*clearFocusedFocusAccessibilityNode)(const char* instanceId)
```

**Description**

Removes focus from the current node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| const char* instanceId | Instance ID of the third-party framework.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### getAccessibilityNodeCursorPosition()

```c
int32_t (*getAccessibilityNodeCursorPosition)(const char* instanceId, int64_t elementId, int32_t requestId, int32_t* index)
```

**Description**

Obtains the cursor position within a text component of the current accessibility node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| const char* instanceId | Pointer to the instance ID of the third-party framework.|
|  int64_t elementId | Unique ID of the accessibility element.|
| int32_t requestId | Request ID, which is used to associate the request process. It is recommended that this ID be logged to facilitate fault locating. |
| int32_t* index | Pointer to the cursor position result, indicating the character index of the cursor from the start position in the text, starting from 0. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|