# native_interface_focus.h


## Overview

Declares APIs for focus management, mainly used for actively transferring focus, managing the default focus transfer behavior, and controlling the focus activation state.

**Library**: libace_ndk.z.so

**File to include**: <arkui/native_interface_focus.h>

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Related module**: [ArkUI_NativeModule](_ark_u_i___native_module.md)


## Summary

### Enumeration

| Name| Description| 
| -------- | -------- |
| [ArkUI_KeyProcessingMode](_ark_u_i___native_module.md#arkui_keyprocessingmode) { ARKUI_KEY_PROCESSING_MODE_FOCUS_NAVIGATION = 0, ARKUI_KEY_PROCESSING_MODE_FOCUS_ANCESTOR_EVENT } |Sets the mode for processing key events when a component cannot process them.| 

### Functions

| Name| Description| 
| -------- | -------- |
|[ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode)  [OH_ArkUI_FocusRequest](_ark_u_i___native_module.md#oh_arkui_focusrequest)([ArkUI_NodeHandle](_ark_u_i___native_module.md#arkui_nodehandle) node); | Requests focus for a specific node.<br>**Since**: 15|
| void [OH_ArkUI_FocusClear](_ark_u_i___native_module.md#oh_arkui_focusclear)([ArkUI_ContextHandle](_ark_u_i___native_module.md#arkui_contexthandle-12) uiContext); | Clears the focus to the root container node.<br>**Since**: 15|
| void [OH_ArkUI_FocusActivate](_ark_u_i___native_module.md#oh_arkui_focusactivate)([ArkUI_ContextHandle](_ark_u_i___native_module.md#arkui_contexthandle-12) uiContext, bool isActive, bool isAutoInactive); | Sets the focus activation state for the current page. When activated, the focused node displays a focus box.<br>**Since**: 15|
| void [OH_ArkUI_FocusSetAutoTransfer](_ark_u_i___native_module.md#oh_arkui_focussetautotransfer)([ArkUI_ContextHandle](_ark_u_i___native_module.md#arkui_contexthandle-12) uiContext, bool autoTransfer); | Configures the focus transfer behavior when pages are switched.<br>**Since**: 15| 
| void [OH_ArkUI_FocusSetKeyProcessingMode](_ark_u_i___native_module.md#oh_arkui_focussetkeyprocessingmode)([ArkUI_ContextHandle](_ark_u_i___native_module.md#arkui_contexthandle-12) uiContext, [ArkUI_KeyProcessingMode](_ark_u_i___native_module.md#arkui_keyprocessingmode) mode); | Sets the mode for processing key events.<br>**Since**: 15| 
