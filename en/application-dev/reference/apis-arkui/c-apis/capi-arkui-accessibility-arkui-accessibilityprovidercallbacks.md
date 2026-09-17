# ArkUI_AccessibilityProviderCallbacks

```c
typedef struct ArkUI_AccessibilityProviderCallbacks {...} ArkUI_AccessibilityProviderCallbacks
```

## Overview

Registers callbacks for the accessibility provider.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [int32_t (\*findAccessibilityNodeInfosById)(int64_t elementId, ArkUI_AccessibilitySearchMode mode,int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbyid) | Called to obtain element information based on a specified node. |
| [int32_t (\*findAccessibilityNodeInfosByText)(int64_t elementId, const char* text, int32_t requestId,ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbytext) | Called to obtain element information based on a specified node and text content. |
| [int32_t (\*findFocusedAccessibilityNode)(int64_t elementId, ArkUI_AccessibilityFocusType focusType,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findfocusedaccessibilitynode) | Called to obtain focused element information based on a specified node. |
| [int32_t (\*findNextFocusAccessibilityNode)(int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findnextfocusaccessibilitynode) | Called to find the next focusable node based on the reference node. |
| [int32_t (\*executeAccessibilityAction)(int64_t elementId, ArkUI_Accessibility_ActionType action,ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)](#executeaccessibilityaction) | Called to execute a specified action on a specified node. |
| [int32_t (\*clearFocusedFocusAccessibilityNode)()](#clearfocusedfocusaccessibilitynode) | Called to clear the focus state of the current focused node. |
| [int32_t (\*getAccessibilityNodeCursorPosition)(int64_t elementId, int32_t requestId, int32_t* index)](#getaccessibilitynodecursorposition) | Called to query the current cursor position of the specified node. |

## Member function description

### findAccessibilityNodeInfosById()

```c
int32_t (*findAccessibilityNodeInfosById)(int64_t elementId, ArkUI_AccessibilitySearchMode mode,int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Called to obtain element information based on a specified node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t elementId | Indicates the element ID. |
|  [ArkUI_AccessibilitySearchMode](capi-native-interface-accessibility-h.md#arkui_accessibilitysearchmode) mode | Indicates accessibility search mode. |
| int32_t requestId | Indicates the request ID. |
|  [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList | Indicates accessibility elementInfo list. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### findAccessibilityNodeInfosByText()

```c
int32_t (*findAccessibilityNodeInfosByText)(int64_t elementId, const char* text, int32_t requestId,ArkUI_AccessibilityElementInfoList* elementList)
```

**Description**

Called to obtain element information based on a specified node and text content.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t elementId | Indicates the element ID. |
|  const char* text | Indicates accessibility text. |
|  int32_t requestId | Indicates the request ID. |
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList | Indicates accessibility elementInfo list. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### findFocusedAccessibilityNode()

```c
int32_t (*findFocusedAccessibilityNode)(int64_t elementId, ArkUI_AccessibilityFocusType focusType,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Called to obtain focused element information based on a specified node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t elementId | Indicates the element ID. |
|  [ArkUI_AccessibilityFocusType](capi-native-interface-accessibility-h.md#arkui_accessibilityfocustype) focusType | Indicates focus type. |
| int32_t requestId | Indicates the request ID. |
|  [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates accessibility elementInfo. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### findNextFocusAccessibilityNode()

```c
int32_t (*findNextFocusAccessibilityNode)(int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**Description**

Called to find the next focusable node based on the reference node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t elementId | Indicates the element ID. |
|  [ArkUI_AccessibilityFocusMoveDirection](capi-native-interface-accessibility-h.md#arkui_accessibilityfocusmovedirection) direction | Indicates direction. |
| int32_t requestId | Indicates the request ID. |
|  [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo | Indicates accessibility elementInfo. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### executeAccessibilityAction()

```c
int32_t (*executeAccessibilityAction)(int64_t elementId, ArkUI_Accessibility_ActionType action,ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)
```

**Description**

Called to execute a specified action on a specified node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t elementId | Indicates the element ID. |
|  [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) action | Indicates action. |
| [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) *actionArguments | Indicates action arguments. |
|  int32_t requestId | Indicates the request ID. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |

### clearFocusedFocusAccessibilityNode()

```c
int32_t (*clearFocusedFocusAccessibilityNode)()
```

**Description**

Called to clear the focus state of the current focused node.

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_FAILED](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is failed. |

### getAccessibilityNodeCursorPosition()

```c
int32_t (*getAccessibilityNodeCursorPosition)(int64_t elementId, int32_t requestId, int32_t* index)
```

**Description**

Called to query the current cursor position of the specified node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t elementId | Indicates the element ID. |
|  int32_t requestId | Indicates the request ID. |
|  int32_t* index | Indicates index. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if the operation is successful.             Returns [ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode) if a parameter is incorrect. |


