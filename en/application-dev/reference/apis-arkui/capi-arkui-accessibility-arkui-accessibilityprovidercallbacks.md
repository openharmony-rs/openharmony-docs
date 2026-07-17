# ArkUI_AccessibilityProviderCallbacks

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-16T10:44:37.567Z pushedAt=2026-07-17T07:45:39.332Z -->

```c
typedef struct {...} ArkUI_AccessibilityProviderCallbacks
```

## Overview

Defines callback functions of a third-party [provider](capi-arkui-accessibility-arkui-accessibilityprovider.md). The functions that need to be implemented by the third-party platform are registered with the system through [OH_ArkUI_AccessibilityProviderRegisterCallback](capi-native-interface-accessibility-h.md#oh_arkui_accessibilityproviderregistercallback). This struct is applicable to accessibility scenarios such as screen readers, voice control, and switch control. The third-party platform responds to the system's accessibility query and action requests by implementing these callbacks.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Functions

| Name| Description|
| -- | -- |
| [int32_t (\*findAccessibilityNodeInfosById)(int64_t elementId, ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbyid) | Finds node information for the specified node. Callback function implemented by the third-party platform and registered with the system.|
| [int32_t (\*findAccessibilityNodeInfosByText)(int64_t elementId, const char* text, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbytext) | Finds the node information matching the specified text content based on the specified node. Callback function implemented by the third-party platform and registered with the system. |
| [int32_t (\*findFocusedAccessibilityNode)(int64_t elementId, ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findfocusedaccessibilitynode) | Finds the node that has obtained the focus based on the focus type and returns the element information of the node. Callback function implemented by the third-party platform and registered with the system.|
| [int32_t (\*findNextFocusAccessibilityNode)(int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findnextfocusaccessibilitynode) | Finds the next node that can be focused based on the reference node and focus movement direction. Callback function implemented by the third-party platform and registered with the system.|
| [int32_t (\*executeAccessibilityAction)(int64_t elementId, ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)](#executeaccessibilityaction) | Executes an action on the specified node. Callback function implemented by the third-party platform and registered with the system. |
| [int32_t (\*clearFocusedFocusAccessibilityNode)()](#clearfocusedfocusaccessibilitynode) | Clears the focus state of the current focused node. Callback function implemented by the third-party platform and registered with the system. For example, it is triggered when the accessibility service needs to reset focus highlighting or when the user switches to another interaction area. |
| [int32_t (\*getAccessibilityNodeCursorPosition)(int64_t elementId, int32_t requestId, int32_t* index)](#getaccessibilitynodecursorposition) | Obtains the current cursor position of the specified node. Callback function implemented by the third-party platform and registered with the system. For example, it is triggered when a screen reader needs to announce the cursor position or when a voice input method locates the text insertion point. |

## Member Function Description

### findAccessibilityNodeInfosById()

```c
int32_t (*findAccessibilityNodeInfosById)(int64_t elementId, ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Finds node information for the specified node. Callback function implemented by the third-party platform and registered with the system.

**Since**: 13

**Parameters**

| Name                                                                           | Description|
|--------------------------------------------------------------------------------| -- |
| int64_t elementId                                                              | Unique ID of the accessibility element.|
| [ArkUI_AccessibilitySearchMode](capi-native-interface-accessibility-h.md#arkui_accessibilitysearchmode) mode | Accessibility search mode. For details about the values and meanings, see [ArkUI_AccessibilitySearchMode](capi-native-interface-accessibility-h.md#arkui_accessibilitysearchmode). |
| int32_t requestId                                                              | Request ID.|
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList                            | Pointer to the accessibility element information list.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs. The possible cause is that the passed **elementId** is invalid or **elementList** is a null pointer. To solve this error, check the validity of the **elementId**, **mode**, and **elementList** parameters. |

### findAccessibilityNodeInfosByText()

```c
int32_t (*findAccessibilityNodeInfosByText)(int64_t elementId, const char* text, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Finds the node information matching the specified text content based on the specified node. Callback function implemented by the third-party platform and registered with the system.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| int64_t elementId | Unique ID of the accessibility element.|
|  const char* text | Text content used to find the node. |
|  int32_t requestId | Request ID.|
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList | Pointer to the accessibility element information list.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### findFocusedAccessibilityNode()

```c
int32_t (*findFocusedAccessibilityNode)(int64_t elementId, ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Finds the node that has obtained the focus based on the focus type and returns the element information of the node. Callback function implemented by the third-party platform and registered with the system.

**Since**: 13

**Parameters**

| Name                                                                                                            | Description|
|-----------------------------------------------------------------------------------------------------------------| -- |
| int64_t elementId                                                                                               | Unique ID of the accessibility element.|
| [ArkUI_AccessibilityFocusType](capi-native-interface-accessibility-h.md#arkui_accessibilityfocustype) focusType | Focus type. For details about the values and their meanings, see [ArkUI_AccessibilityFocusType](capi-native-interface-accessibility-h.md#arkui_accessibilityfocustype). |
| int32_t requestId                                                                                               | Request ID.|
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo                                                                 | Pointer to the accessibility element information.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### findNextFocusAccessibilityNode()

```c
int32_t (*findNextFocusAccessibilityNode)(int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Finds the next node that can be focused based on the reference node and focus movement direction. Callback function implemented by the third-party platform and registered with the system.

**Since**: 13

**Parameters**

| Name                                                                                                                              | Description|
|-----------------------------------------------------------------------------------------------------------------------------------| -- |
| int64_t elementId                                                                                                                 | Unique ID of the accessibility element.|
| [ArkUI_AccessibilityFocusMoveDirection](capi-native-interface-accessibility-h.md#arkui_accessibilityfocusmovedirection) direction | Focus movement direction. For details about the values and their meanings, see [ArkUI_AccessibilityFocusMoveDirection](capi-native-interface-accessibility-h.md#arkui_accessibilityfocusmovedirection). |
| int32_t requestId                                                                                                                 | Request ID.|
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Pointer to the accessibility element information. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### executeAccessibilityAction()

```c
int32_t (*executeAccessibilityAction)(int64_t elementId, ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)
```

**Description**

Executes an accessibility action on a specified accessibility node. For example, when a user triggers actions such as tap, scrolling, or selection through voice commands or switch control in a screen reader, the system notifies the third-party platform to execute the corresponding action through this callback. This callback function is implemented by the third-party platform and registered with the system.

**Since**: 13

**Parameters**

| Name                                                                                                             | Description|
|------------------------------------------------------------------------------------------------------------------| -- |
| int64_t elementId                                                                                                | Unique ID of the accessibility element.|
| [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) action | Action to be executed. For details about the values and meanings, see [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype). |
| [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) *actionArguments                                                          | Pointer to the action argument array.|
| int32_t requestId                                                                                                | Request ID.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### clearFocusedFocusAccessibilityNode()

```c
int32_t (*clearFocusedFocusAccessibilityNode)()
```

**Description**

Clears the focus state of the current focused node. Callback function implemented by the third-party platform and registered with the system.

**Since**: 13

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|

### getAccessibilityNodeCursorPosition()

```c
int32_t (*getAccessibilityNodeCursorPosition)(int64_t elementId, int32_t requestId, int32_t* index)
```

**Description**

Obtains the current cursor position of the specified node. Callback function implemented by the third-party platform and registered with the system.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| int64_t elementId | Unique ID of the accessibility element.|
|  int32_t requestId | Request ID.|
|  int32_t* index | Pointer to the index of the cursor position. The value is a non-negative integer, indicating the character position of the cursor in the text. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.<br>Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter error occurs.|