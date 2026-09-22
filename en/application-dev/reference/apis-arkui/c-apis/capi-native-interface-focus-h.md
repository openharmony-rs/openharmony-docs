# native_interface_focus.h

## Overview

Declares APIs for focus management, mainly used for actively transferring focus, managing the default focus transfer behavior, and controlling the focus activation state.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_KeyProcessingMode](#arkui_keyprocessingmode) | ArkUI_KeyProcessingMode | Enumerates the key event processing priority modes. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_ErrorCode OH_ArkUI_FocusRequest(ArkUI_NodeHandle node)](#oh_arkui_focusrequest) | Requests focus for a specific node. |
| [void OH_ArkUI_FocusClear(ArkUI_ContextHandle uiContext)](#oh_arkui_focusclear) | Clears the focus to the root container node. |
| [void OH_ArkUI_FocusActivate(ArkUI_ContextHandle uiContext, bool isActive, bool isAutoInactive)](#oh_arkui_focusactivate) | Sets the focus activation state for the current page. When activated, the focused node displays a focus box. |
| [void OH_ArkUI_FocusSetAutoTransfer(ArkUI_ContextHandle uiContext, bool autoTransfer)](#oh_arkui_focussetautotransfer) | Configures the focus transfer behavior when pages are switched. |
| [void OH_ArkUI_FocusSetKeyProcessingMode(ArkUI_ContextHandle uiContext, ArkUI_KeyProcessingMode mode)](#oh_arkui_focussetkeyprocessingmode) | Sets the mode for processing key events. |

## Enum type description

### ArkUI_KeyProcessingMode

```c
enum ArkUI_KeyProcessingMode
```

**Description**

Enumerates the key event processing priority modes.

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

Requests focus for a specific node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Node. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node cannot receive focus.      <br>Returns [ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the ancestor node cannot receive focus.      <br>Returns [ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node does not exist. |

### OH_ArkUI_FocusClear()

```c
void OH_ArkUI_FocusClear(ArkUI_ContextHandle uiContext)
```

**Description**

Clears the focus to the root container node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | UI instance object pointer. |

### OH_ArkUI_FocusActivate()

```c
void OH_ArkUI_FocusActivate(ArkUI_ContextHandle uiContext, bool isActive, bool isAutoInactive)
```

**Description**

Sets the focus activation state for the current page. When activated, the focused node displays a focus box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | UI instance object pointer. |
| bool isActive | Whether to enter or exit the focus activation state. The value **true** means to enter the focus activation state, and **false** means to exit the focus activation state. |
| bool isAutoInactive | Whether to automatically exit the focus active state on touch or mouse down events. **true**: Automatically exit the focus active state. **false**: Maintain the current state until the corresponding setting API is called. |

### OH_ArkUI_FocusSetAutoTransfer()

```c
void OH_ArkUI_FocusSetAutoTransfer(ArkUI_ContextHandle uiContext, bool autoTransfer)
```

**Description**

Configures the focus transfer behavior when pages are switched.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | UI instance object pointer. |
| bool autoTransfer | Whether to automatically transfer focus when pages are switched. The value **true** means to automatically transfer focus when pages are switched, and **false** means the opposite. |

### OH_ArkUI_FocusSetKeyProcessingMode()

```c
void OH_ArkUI_FocusSetKeyProcessingMode(ArkUI_ContextHandle uiContext, ArkUI_KeyProcessingMode mode)
```

**Description**

Sets the mode for processing key events.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | UI instance object pointer. |
| [ArkUI_KeyProcessingMode](capi-native-interface-focus-h.md#arkui_keyprocessingmode) mode | Key event processing priority mode. |


