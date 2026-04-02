# ArkUI_AccessibilityProviderCallbacksWithInstance
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_AccessibilityProviderCallbacksWithInstance
```

## Overview

Defines a callback function struct of a third-party operation [provider](capi-arkui-accessibility-arkui-accessibilityprovider.md) in the multi-instance scenario. The functions that need to be implemented by the third-party platform are registered with the system through [OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance](capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallbackwithinstance).

**Since**: 15

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Functions

| Name| Description|
| -- | -- |
| [int32_t (\*findAccessibilityNodeInfosById)(const char* instanceId, int64_t elementId,ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbyid) | Finds the information about an accessibility node based on the specified node ID. Multi-instance scenarios are supported. Callback function implemented by the third-party platform and registered with the system.|
| [int32_t (\*findAccessibilityNodeInfosByText)(const char* instanceId, int64_t elementId, const char* text,int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbytext) | Finds the node information matching the specified text content. Multi-instance scenarios are supported. Callback function implemented by the third-party platform and registered with the system.|
| [int32_t (\*findFocusedAccessibilityNode)(const char* instanceId, int64_t elementId,ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findfocusedaccessibilitynode) | Finds the node that currently has focus within a given node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.|
| [int32_t (\*findNextFocusAccessibilityNode)(const char* instanceId, int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findnextfocusaccessibilitynode) | Finds the next node in a specified direction from a given node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.|
| [int32_t (\*executeAccessibilityAction)(const char* instanceId, int64_t elementId,ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)](#executeaccessibilityaction) | Performs a specified action on a specified node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.|
| [int32_t (\*clearFocusedFocusAccessibilityNode)(const char* instanceId)](#clearfocusedfocusaccessibilitynode) | Removes focus from the current node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.|
| [int32_t (\*getAccessibilityNodeCursorPosition)(const char* instanceId, int64_t elementId,int32_t requestId, int32_t* index)](#getaccessibilitynodecursorposition) | Obtains the cursor position within a text component of the current accessibility node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.|

## Member Function Description

### findAccessibilityNodeInfosById()

```c
int32_t (*findAccessibilityNodeInfosById)(const char* instanceId, int64_t elementId,ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Finds the information about an accessibility node based on the specified node ID. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name                                                                           | Description|
|--------------------------------------------------------------------------------| -- |
| const char* instanceId                                                         | Instance ID of the third-party framework.|
| int64_t elementId                                                              | Unique ID of the accessibility element.|
| [ArkUI_AccessibilitySearchMode](capi-native-interface-accessibility-h.md#arkui_accessibilitysearchmode) mode | Search mode for accessibility services.|
| int32_t requestId                                                              | Request ID, which is used to associate the request process. It is recommended that this ID be logged to facilitate fault locating.|
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList                            | List of all accessibility elements found.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>            Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### findAccessibilityNodeInfosByText()

```c
int32_t (*findAccessibilityNodeInfosByText)(const char* instanceId, int64_t elementId, const char* text,int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Finds the node information matching the specified text content. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| const char* instanceId | Instance ID of the third-party framework.|
|  int64_t elementId | Unique ID of the accessibility element.|
|  const char* text | Text content to match in the component.|
| int32_t requestId | Request ID for identifying the request process. It is recommended for logging to aid troubleshooting.|
|  [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList | List of all accessibility elements found.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>            Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### findFocusedAccessibilityNode()

```c
int32_t (*findFocusedAccessibilityNode)(const char* instanceId, int64_t elementId,ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Finds the node that currently has focus within a given node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name                                                                               | Description|
|------------------------------------------------------------------------------------| -- |
| const char* instanceId                                                             | Instance ID of the third-party framework.|
| int64_t elementId                                                                  | Unique ID of the accessibility element.|
| [ArkUI_AccessibilityFocusType](capi-native-interface-accessibility-h.md#arkui_accessibilityfocustype) focusType | Focus type.|
| int32_t requestId                                                                  | Request ID, which is used to associate the request process. It is recommended that this ID be logged to facilitate fault locating.|
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo                                    | List of all accessibility elements found.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>            Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### findNextFocusAccessibilityNode()

```c
int32_t (*findNextFocusAccessibilityNode)(const char* instanceId, int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Finds the next node in a specified direction from a given node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name                                                                                                                              | Description|
|-----------------------------------------------------------------------------------------------------------------------------------| -- |
| const char* instanceId                                                                                                            | Instance ID of the third-party framework.|
| int64_t elementId                                                                                                                 | Unique ID of the accessibility element.|
| [ArkUI_AccessibilityFocusMoveDirection](capi-native-interface-accessibility-h.md#arkui_accessibilityfocusmovedirection) direction | Search direction.|
| int32_t requestId                                                                                                                 | Request ID for identifying the request process. It is recommended for logging to aid troubleshooting.|
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo                         | List of all accessibility elements found.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### executeAccessibilityAction()

```c
int32_t (*executeAccessibilityAction)(const char* instanceId, int64_t elementId,ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)
```

**Description**

Performs a specified action on a specified node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name                                                                                                             | Description|
|------------------------------------------------------------------------------------------------------------------| -- |
| const char* instanceId                                                                                           | Instance ID of the third-party framework.|
| int64_t elementId                                                                                                | Unique ID of the accessibility element.|
| [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) action | Action to perform, such as focus, click, or long press.|
| [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) *actionArguments                                                          | Parameters controlling the action.|
| int32_t requestId                                                                                                | Request ID for identifying the request process. It is recommended for logging to aid troubleshooting.|

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
int32_t (*getAccessibilityNodeCursorPosition)(const char* instanceId, int64_t elementId,int32_t requestId, int32_t* index)
```

**Description**

Obtains the cursor position within a text component of the current accessibility node. Callback function implemented by the third-party platform and registered with the system. Multi-instance scenarios are supported.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| const char* instanceId | Instance ID of the third-party framework.|
|  int64_t elementId | Unique ID of the accessibility element.|
| int32_t requestId | Request ID for identifying the request process. It is recommended for logging to aid troubleshooting.|
|  int32_t* index | Cursor position result.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|
