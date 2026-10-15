# ui_event_injection.h

## Overview

Declares the APIs used by in-app intelligent agents and UI automation to inject relaxed non-precise control actions into the UI.

**Include**: <arkui/ui_event_injection.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](#oh_arkui_nativemodule_uieventinjection_resultcode) | OH_ArkUI_NativeModule_UIEventInjection_ResultCode | Enumerates the result codes of UI event injection.<br> This enumeration is shared by all injection APIs, including relaxed interaction injection (non-precise) and precise component-targeted injection. A nonzero result code indicates an execution failure, and its specific value conveys the failure reason. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)](#oh_arkui_nativemodule_uieventinjectioncallback) | OH_ArkUI_NativeModule_UIEventInjectionCallback | Callback for injection completion.<br> The callback is invoked once when the injected command finishes executing, whether successfully or not. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)](#oh_arkui_nativemodule_uieventinjectcompositecommand) | - | Injects a control command into a target UI node asynchronously.<br> The target node is identified by its unique ID (the same ID used by OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId). The framework resolves the unique ID to the corresponding node within the UI instance specified by uiContext.<br> The command is carried by an OH_ArkUI_NativeModule_UIJsonWrapper object created with OH_ArkUI_NativeModule_UIJsonWrapper_Create. The command payload's top-level structure is: {"schemaVersion": 1, "cmd": {"type": "<command type>", "action_info": { ... }}}<br> Supported command types and their action_info parameters please refernce to developer guide.<br> The uniqueId must correspond to a node that belongs to the same UI instance as uiContext. If the node belongs to a different instance, the framework fails to resolve it within uiContext and returns ARKUI_ERROR_CODE_PARAM_INVALID.<br> This function must be called on the UI thread of the UI instance specified by uiContext. If called on a non-UI thread, the framework triggers a fatal log output and aborts the process. This is a deliberate fail-fast design to prevent undefined behavior from cross-thread UI access. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)( OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData) | Callback for injection completion.<br> The callback is invoked once when the injected command finishes executing, whether successfully or not.<br>**Since**: 26.2.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

## Enum type description

### OH_ArkUI_NativeModule_UIEventInjection_ResultCode

```c
enum OH_ArkUI_NativeModule_UIEventInjection_ResultCode
```

**Description**

Enumerates the result codes of UI event injection.<br> This enumeration is shared by all injection APIs, including relaxed interaction injection (non-precise) and precise component-targeted injection. A nonzero result code indicates an execution failure, and its specific value conveys the failure reason.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS = 0 | The injected command was executed successfully.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND = 1 | No component or target could be found to respond to the injected command.<br> For example, the click coordinates do not hit any component, or the target required by the execution mode cannot be located.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED = 2 | The command cannot be executed in the current UI context.<br> The command is structurally valid, but its type or execution mode is not supported by the current UI state.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER = 3 | The injected command was interrupted by a user operation.<br>**Since**: 26.2.0 |


## Function description

### OH_ArkUI_NativeModule_UIEventInjectionCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)
```

**Description**

Callback for injection completion.<br> The callback is invoked once when the injected command finishes executing, whether successfully or not.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode) result | [in] Result code of the injection execution. For details, see [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode). |
| void *userData | [in] Custom user data pointer passed during injection.It can be NULL if pass NULL when injection. The type, ownership, and lifetime of the pointed-to data are entirely defined by the caller. The framework does not dereference or retain this pointer; it is only passed back to this callback. Must remain valid until the callback is invoked. |

### OH_ArkUI_NativeModule_UIEventInjectCompositeCommand()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)
```

**Description**

Injects a control command into a target UI node asynchronously.<br> The target node is identified by its unique ID (the same ID used by OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId). The framework resolves the unique ID to the corresponding node within the UI instance specified by uiContext.<br> The command is carried by an OH_ArkUI_NativeModule_UIJsonWrapper object created with OH_ArkUI_NativeModule_UIJsonWrapper_Create. The command payload's top-level structure is: {"schemaVersion": 1, "cmd": {"type": "<command type>", "action_info": { ... }}}<br> Supported command types and their action_info parameters please refernce to developer guide.<br> The uniqueId must correspond to a node that belongs to the same UI instance as uiContext. If the node belongs to a different instance, the framework fails to resolve it within uiContext and returns ARKUI_ERROR_CODE_PARAM_INVALID.<br> This function must be called on the UI thread of the UI instance specified by uiContext. If called on a non-UI thread, the framework triggers a fatal log output and aborts the process. This is a deliberate fail-fast design to prevent undefined behavior from cross-thread UI access.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] Pointer to a UI instance. Must not be NULL. The caller must be on the UI thread of this instance; calling from any other thread triggers a fatal abort. The uniqueId must resolve to a node within this instance. |
| uint32_t uniqueId | [in] Unique ID of the target node. This is the same ID used by OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId. The framework resolves this ID to the corresponding node within the uiContext instance. |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *command | [in] Pointer to a configured JSON command object. Must not be NULL. The JSON data is internally copied before the function returns; the caller retains ownership and may destroy the object immediately after return. |
| [OH_ArkUI_NativeModule_UIEventInjectionCallback](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback) callback | [in] Optional completion callback. Can be NULL for fire-and-forget mode. If non-NULL, invoked exactly once on the UI thread. |
| void *userData | [in] Custom user data pointer passed to the callback. Can be NULL. If non-NULL, must remain valid until the callback is invoked. The framework does not dereference or retain this pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the command is queued successfully.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if parameter invalid, including NULL callback, required fields are missing, or the JSON conversion fails </li> <li>ARKUI_ERROR_CODE_NODE_NOT_FOUND if uniqueId does not resolve to a node within the uiContext instance.</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if the UI context is invalid.</li> <li>ARKUI_ERROR_CODE_COMMAND_UNFINISHED if another composite command is still in progress in the current process; the new command is not queued and no callback is invoked.</li> </ul> |


