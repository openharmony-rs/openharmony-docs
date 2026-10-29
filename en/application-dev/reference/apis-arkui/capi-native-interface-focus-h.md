# native_interface_focus.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=177cf08b41b42ef2a0a1e73e96f1ea583ec5a150 translatedAt=2026-09-23T09:38:06.877Z pushedAt=2026-10-09T08:29:09.184Z -->

## Overview

Declares APIs for focus management, mainly used for actively transferring focus, managing and controlling the default focus transfer behavior, and controlling the focus active state. It is applicable to scenarios such as page switching and keyboard navigation that require unified management of the focus state and focus transfer behavior, helping improve the predictability of focus control and the interaction experience.

**File to include**: <arkui/native_interface_focus.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[NdkFocus](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NdkFocus)<!--RP1End-->

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_KeyProcessingMode](#arkui_keyprocessingmode) | ArkUI_KeyProcessingMode | Enumerates the processing mode of key events. |

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_ErrorCode OH_ArkUI_FocusRequest(ArkUI_NodeHandle node)](#oh_arkui_focusrequest) | Requests focus for a specific node.|
| [void OH_ArkUI_FocusClear(ArkUI_ContextHandle uiContext)](#oh_arkui_focusclear) | Clears the focus to the root container node.|
| [void OH_ArkUI_FocusActivate(ArkUI_ContextHandle uiContext, bool isActive, bool isAutoInactive)](#oh_arkui_focusactivate) | Sets the focus active state for the current page. When activated, the focused node displays a focus box.|
| [void OH_ArkUI_FocusSetAutoTransfer(ArkUI_ContextHandle uiContext, bool autoTransfer)](#oh_arkui_focussetautotransfer) | Sets whether focus is automatically transferred when the page is switched. |
| [void OH_ArkUI_FocusSetKeyProcessingMode(ArkUI_ContextHandle uiContext, ArkUI_KeyProcessingMode mode)](#oh_arkui_focussetkeyprocessingmode) | Sets the mode for processing key events.|

## Enum Description

### ArkUI_KeyProcessingMode

```c
enum ArkUI_KeyProcessingMode
```

**Description**


Enumerates the processing mode of key events.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_KEY_PROCESSING_MODE_FOCUS_NAVIGATION = 0 | Key events are used for focus navigation.|
| ARKUI_KEY_PROCESSING_MODE_FOCUS_ANCESTOR_EVENT = 1 | Key events are passed up to ancestor components.|


## Function Description

### OH_ArkUI_FocusRequest()

```c
ArkUI_ErrorCode OH_ArkUI_FocusRequest(ArkUI_NodeHandle node)
```

**Description**


Requests focus for a specific node. This is applicable when focus needs to be proactively moved to a specified component, for example, setting the default focus after page initialization or navigating focus through a keyboard or remote control.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node for which focus is requested. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the request is successful.<br>         Returns [ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the node cannot gain focus.<br>         Returns [ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the ancestor node cannot gain focus.<br>         Returns [ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the node does not exist. |

### OH_ArkUI_FocusClear()

```c
void OH_ArkUI_FocusClear(ArkUI_ContextHandle uiContext)
```

**Description**


Clears the current focus, after which the focus returns to the root container node. This is applicable when exiting the current focus interaction or when the page focus state needs to be reset.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | Pointer to the UI context instance object whose focus is to be cleared. |

### OH_ArkUI_FocusActivate()

```c
void OH_ArkUI_FocusActivate(ArkUI_ContextHandle uiContext, bool isActive, bool isAutoInactive)
```

**Description**


Sets the focus active state of the current page, so that the focused node displays the focus frame. This is applicable when the focus position needs to be displayed in non-touch interactions such as keyboard and remote control.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | UI instance object pointer.|
| bool isActive | Whether to enter or exit the focus active state. The value **true** means to enter the focus active state, and **false** means to exit the focus active state.|
| bool isAutoInactive | Whether to automatically exit the focus active state on touch or mouse down events. **true**: Automatically exit the focus active state. **false**: Maintain the current state until the **OH_ArkUI_FocusActivate** API is called. |

### OH_ArkUI_FocusSetAutoTransfer()

```c
void OH_ArkUI_FocusSetAutoTransfer(ArkUI_ContextHandle uiContext, bool autoTransfer)
```

**Description**


Sets whether focus is automatically transferred when the page is switched.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | UI instance object pointer.|
| bool autoTransfer | Whether to transfer focus when the page is switched. The value **true** means to automatically transfer focus to the new page when the page is switched, and **false** means not to transfer focus. |

### OH_ArkUI_FocusSetKeyProcessingMode()

```c
void OH_ArkUI_FocusSetKeyProcessingMode(ArkUI_ContextHandle uiContext, ArkUI_KeyProcessingMode mode)
```

**Description**


Sets the processing mode of key events. This is applicable when a priority policy needs to be selected between focus navigation and key event processing of ancestor components.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | UI instance object pointer.|
| [ArkUI_KeyProcessingMode](#arkui_keyprocessingmode) mode | Key event processing mode. |


