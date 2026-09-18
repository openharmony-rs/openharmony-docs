# ArkUI_AccessibilityProviderCallbacksWithInstance

```c
typedef struct ArkUI_AccessibilityProviderCallbacksWithInstance {...} ArkUI_AccessibilityProviderCallbacksWithInstance
```

## Overview

Registers callbacks with instance for the accessibility provider.

**Since**: 15

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [int32_t (\*findAccessibilityNodeInfosById)(const char* instanceId, int64_t elementId,ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbyid) | Called to obtain element information based on a specified node. |
| [int32_t (\*findAccessibilityNodeInfosByText)(const char* instanceId, int64_t elementId, const char* text,int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbytext) | Called to obtain element information based on a specified node and text content. |
| [int32_t (\*findFocusedAccessibilityNode)(const char* instanceId, int64_t elementId,ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findfocusedaccessibilitynode) | Called to obtain focused element information based on a specified node. |
| [int32_t (\*findNextFocusAccessibilityNode)(const char* instanceId, int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findnextfocusaccessibilitynode) | Called to find the next focusable node based on the reference node. |
| [int32_t (\*executeAccessibilityAction)(const char* instanceId, int64_t elementId,ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)](#executeaccessibilityaction) | Called to execute a specified action on a specified node. |
| [int32_t (\*clearFocusedFocusAccessibilityNode)(const char* instanceId)](#clearfocusedfocusaccessibilitynode) | Called to clear the focus state of the current focused node. |
| [int32_t (\*getAccessibilityNodeCursorPosition)(const char* instanceId, int64_t elementId,int32_t requestId, int32_t* index)](#getaccessibilitynodecursorposition) | Called to query the current cursor position of the specified node. |

## Member function description

### findAccessibilityNodeInfosById()

```c
int32_t (*findAccessibilityNodeInfosById)(const char* instanceId, int64_t elementId,ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Called to obtain element information based on a specified node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* instanceId | Indicates ID of third-party framework instance. |
|  int64_t elementId | The unique id of the component ID. |
| [ArkUI_AccessibilitySearchMode](capi-native-interface-accessibility-h.md#arkui_accessibilitysearchmode) mode | Indicates accessibility search mode. |
|  int32_t requestId | Matched the request and response. transfer it by callback only. |
|  [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList | The all obtained accessibility elements list information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### findAccessibilityNodeInfosByText()

```c
int32_t (*findAccessibilityNodeInfosByText)(const char* instanceId, int64_t elementId, const char* text,int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Called to obtain element information based on a specified node and text content.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* instanceId | Indicates ID of third-party framework instance. |
|  int64_t elementId | The unique id of the component ID. |
|  const char* text | Filter for the child components to matched with the text. |
| int32_t requestId | Matched the request and response. transfer it by callback only. |
|  [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList | The all obtained accessibility elements list information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### findFocusedAccessibilityNode()

```c
int32_t (*findFocusedAccessibilityNode)(const char* instanceId, int64_t elementId,ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Called to obtain focused element information based on a specified node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* instanceId | Indicates ID of third-party framework instance. |
|  int64_t elementId | The unique id of the component ID. |
| [ArkUI_AccessibilityFocusType](capi-native-interface-accessibility-h.md#arkui_accessibilityfocustype) focusType | Indicates focus type. |
|  int32_t requestId | Matched the request and response. transfer it by callback only. |
|  [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | The all obtained accessibility elements list information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### findNextFocusAccessibilityNode()

```c
int32_t (*findNextFocusAccessibilityNode)(const char* instanceId, int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Called to find the next focusable node based on the reference node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* instanceId | Indicates ID of third-party framework instance. |
|  int64_t elementId | The unique id of the component ID. |
|  [ArkUI_AccessibilityFocusMoveDirection](capi-native-interface-accessibility-h.md#arkui_accessibilityfocusmovedirection) direction | Indicates direction. |
| int32_t requestId | Matched the request and response. transfer it by callback only. |
|  [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | The all obtained accessibility elements list information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### executeAccessibilityAction()

```c
int32_t (*executeAccessibilityAction)(const char* instanceId, int64_t elementId,ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)
```

**Description**

Called to execute a specified action on a specified node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* instanceId | Indicates ID of third-party framework instance. |
|  int64_t elementId | The unique id of the component ID. |
| [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) action | Indicates action. |
|  [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) *actionArguments | Indicates action arguments. |
|  int32_t requestId | Matched the request and response. transfer it by callback only. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### clearFocusedFocusAccessibilityNode()

```c
int32_t (*clearFocusedFocusAccessibilityNode)(const char* instanceId)
```

**Description**

Called to clear the focus state of the current focused node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* instanceId | Indicates ID of third-party framework instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_FAILED](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is failed. |

### getAccessibilityNodeCursorPosition()

```c
int32_t (*getAccessibilityNodeCursorPosition)(const char* instanceId, int64_t elementId,int32_t requestId, int32_t* index)
```

**Description**

Called to query the current cursor position of the specified node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* instanceId | Indicates ID of third-party framework instance. |
|  int64_t elementId | The unique id of the component ID. |
| int32_t requestId | Matched the request and response. transfer it by callback only. |
|  int32_t* index | Indicates index. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |


