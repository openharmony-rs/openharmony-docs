# native_interface_focus.h

## Overview

Declares APIs for focus management, mainly used for actively transferring focus, clearing focus, managing the default focus transfer behavior, controlling the focus activation state, and setting the key event processing mode. It is applicable to scenarios such as page switching and keyboard navigation that require unified management of the focus state and focus transfer behavior, helping improve the predictability of focus control and the interaction experience.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_KeyProcessingMode](#arkui_keyprocessingmode) | ArkUI_KeyProcessingMode | Enumerates the processing modes of key events. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_ErrorCode OH_ArkUI_FocusRequest(ArkUI_NodeHandle node)](#oh_arkui_focusrequest) | Requests focus for a specific node. This is applicable when focus needs to be proactively moved to a specified component, for example, setting the default focus after page initialization or navigating focus through a keyboard or remote control. Before calling this API, ensure that the node exists and is focusable, and that its ancestor nodes are also focusable; otherwise, the corresponding error code is returned. |
| [void OH_ArkUI_FocusClear(ArkUI_ContextHandle uiContext)](#oh_arkui_focusclear) | Clears the current focus, after which the focus returns to the root container node. This is applicable when exiting the current focus interaction or when the page focus state needs to be reset. |
| [void OH_ArkUI_FocusActivate(ArkUI_ContextHandle uiContext, bool isActive, bool isAutoInactive)](#oh_arkui_focusactivate) | Sets the focus activation state of the current page, so that the focused node displays the focus frame. This is applicable when the focus position needs to be displayed in non-touch interactions such as keyboard and remote control. Default configuration: the focus activation state is disabled by default. Note: **OH_ArkUI_FocusActivate** only controls the focus activation state (that is, the display and hiding of the focus frame) and does not affect the logical ownership of the focus. To actually move the focus to the root container node, use **OH_ArkUI_FocusClear**. |
| [void OH_ArkUI_FocusSetAutoTransfer(ArkUI_ContextHandle uiContext, bool autoTransfer)](#oh_arkui_focussetautotransfer) | Sets whether the focus is automatically transferred when the page is switched. |
| [void OH_ArkUI_FocusSetKeyProcessingMode(ArkUI_ContextHandle uiContext, ArkUI_KeyProcessingMode mode)](#oh_arkui_focussetkeyprocessingmode) | Sets the processing mode of key events. This is applicable when a priority policy needs to be selected between focus navigation and key event processing of ancestor components. Default configuration: the default key event processing priority is **ARKUI_KEY_PROCESSING_MODE_FOCUS_NAVIGATION**, that is, key events are used to move the focus. |

## Enum type description

### ArkUI_KeyProcessingMode

```c
enum ArkUI_KeyProcessingMode
```

**Description**

Enumerates the processing modes of key events.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_KEY_PROCESSING_MODE_FOCUS_NAVIGATION = 0 | Key events are used for focus navigation. |
| ARKUI_KEY_PROCESSING_MODE_FOCUS_ANCESTOR_EVENT | Key events are passed up to ancestor components. |


## Function description

### OH_ArkUI_FocusRequest()

```c
ArkUI_ErrorCode OH_ArkUI_FocusRequest(ArkUI_NodeHandle node)
```

**Description**

Requests focus for a specific node. This is applicable when focus needs to be proactively moved to a specified component, for example, setting the default focus after page initialization or navigating focus through a keyboard or remote control. Before calling this API, ensure that the node exists and is focusable, and that its ancestor nodes are also focusable; otherwise, the corresponding error code is returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node for which focus is requested. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the request is successful. <br>Returns ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE if the node cannot gain focus. <br>Returns ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR if the ancestor node cannot gain focus. <br>Returns ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT if the node does not exist. |

### OH_ArkUI_FocusClear()

```c
void OH_ArkUI_FocusClear(ArkUI_ContextHandle uiContext)
```

**Description**

Clears the current focus, after which the focus returns to the root container node. This is applicable when exiting the current focus interaction or when the page focus state needs to be reset.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | Pointer to the UI instance object whose focus needs to be cleared. |

### OH_ArkUI_FocusActivate()

```c
void OH_ArkUI_FocusActivate(ArkUI_ContextHandle uiContext, bool isActive, bool isAutoInactive)
```

**Description**

Sets the focus activation state of the current page, so that the focused node displays the focus frame. This is applicable when the focus position needs to be displayed in non-touch interactions such as keyboard and remote control. Default configuration: the focus activation state is disabled by default. Note: **OH_ArkUI_FocusActivate** only controls the focus activation state (that is, the display and hiding of the focus frame) and does not affect the logical ownership of the focus. To actually move the focus to the root container node, use **OH_ArkUI_FocusClear**.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | Pointer to the UI instance for which the focus active state is to be set. |
| bool isActive | Whether to enter or exit the focus activation state. The value **true** means to enter the focus activation state, and **false** means to exit the focus activation state. |
| bool isAutoInactive | Whether to automatically exit the focus active state on touch or mouse down events. This parameter takes effect only when **isActive** is set to **true**. **true**: Automatically exit the focus active state. **false**: Maintain the current state until the **OH_ArkUI_FocusActivate** API is called. |

### OH_ArkUI_FocusSetAutoTransfer()

```c
void OH_ArkUI_FocusSetAutoTransfer(ArkUI_ContextHandle uiContext, bool autoTransfer)
```

**Description**

Sets whether the focus is automatically transferred when the page is switched.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | UI instance object pointer. |
| bool autoTransfer | Whether to transfer focus when the page is switched. The value **true** means to automatically transfer focus to the new page when the page is switched, and **false** means not to transfer focus. |

### OH_ArkUI_FocusSetKeyProcessingMode()

```c
void OH_ArkUI_FocusSetKeyProcessingMode(ArkUI_ContextHandle uiContext, ArkUI_KeyProcessingMode mode)
```

**Description**

Sets the processing mode of key events. This is applicable when a priority policy needs to be selected between focus navigation and key event processing of ancestor components. Default configuration: the default key event processing priority is **ARKUI_KEY_PROCESSING_MODE_FOCUS_NAVIGATION**, that is, key events are used to move the focus.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | Pointer to the UI instance object for which the key event processing mode is to be set. |
| [ArkUI_KeyProcessingMode](capi-native-interface-focus-h.md#arkui_keyprocessingmode) mode | Key event processing mode. Value selection: **ARKUI_KEY_PROCESSING_MODE_FOCUS_NAVIGATION(0)** is used for focus navigation, and **ARKUI_KEY_PROCESSING_MODE_FOCUS_ANCESTOR_EVENT(1)** is used for passing key events upward to the ancestor component. |


