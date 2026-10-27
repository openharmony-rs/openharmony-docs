# ui_event_injection.h

## Overview

Declares the APIs used by in-app intelligent agents and UI automation to inject control commands into specified UI nodes.

**Include**: <arkui/ui_event_injection.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](#oh_arkui_nativemodule_uieventinjection_resultcode) | OH_ArkUI_NativeModule_UIEventInjection_ResultCode | Enumerates the result codes of UI event injection.<br> This enumeration is shared by all injection APIs, including relaxed interaction injection (non-precise) and precise component-targeted injection. A nonzero result code indicates an execution failure, and its specific value conveys the failure reason. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)](#oh_arkui_nativemodule_uieventinjectioncallback) | OH_ArkUI_NativeModule_UIEventInjectionCallback | Callback for injection completion.<br> Reports the results of command dispatch and immediate component handling, without waiting for deferred effects or rendering. Each accepted request receives exactly one callback on the originating UI thread after the injection function returns. Callbacks on different UI threads are not globally serialized. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)](#oh_arkui_nativemodule_uieventinjectcompositecommand) | - | Injects a control command into a target UI node asynchronously.<br> This API provides no cancellation operation or fixed completion timeout. Completion depends on UI-thread task processing. A caller-side wait timeout does not cancel an accepted request. Instance destruction does not cancel completion callbacks for accepted requests. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)( OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData) | Callback for injection completion.<br> Reports the results of command dispatch and immediate component handling, without waiting for deferred effects or rendering. Each accepted request receives exactly one callback on the originating UI thread after the injection function returns. Callbacks on different UI threads are not globally serialized.<br>**Since**: 26.1.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

## Enum type description

### OH_ArkUI_NativeModule_UIEventInjection_ResultCode

```c
enum OH_ArkUI_NativeModule_UIEventInjection_ResultCode
```

**Description**

Enumerates the result codes of UI event injection.<br> This enumeration is shared by all injection APIs, including relaxed interaction injection (non-precise) and precise component-targeted injection. A nonzero result code indicates an execution failure, and its specific value conveys the failure reason.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS = 0 | The injected command was executed successfully.<br>**Since**: 26.1.0 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND = 1 | No component or target could be found to respond to the injected command.<br> For example, the click coordinates do not hit any component, or the target required by the execution mode cannot be located.<br>**Since**: 26.1.0 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED = 2 | The command cannot be executed in the current UI context.<br> The command is structurally valid, but its type or execution mode is not supported by the current UI state.<br>**Since**: 26.1.0 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER = 3 | The injected command was interrupted by a user operation.<br>**Since**: 26.1.0 |


## Function description

### OH_ArkUI_NativeModule_UIEventInjectionCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)
```

**Description**

Callback for injection completion.<br> Reports the results of command dispatch and immediate component handling, without waiting for deferred effects or rendering. Each accepted request receives exactly one callback on the originating UI thread after the injection function returns. Callbacks on different UI threads are not globally serialized.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode) result | [in] Result code of the injection execution. For details, see [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode). |
| void *userData | [in] Custom user data pointer supplied during injection. NULL if NULL was supplied. The framework stores only the pointer value for delivery to this callback. It does not access the pointed-to data, copy or free that data, or take ownership of it. After the request is accepted, the caller must keep non-NULL data valid until the callback returns. |

### OH_ArkUI_NativeModule_UIEventInjectCompositeCommand()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)
```

**Description**

Injects a control command into a target UI node asynchronously.<br> This API provides no cancellation operation or fixed completion timeout. Completion depends on UI-thread task processing. A caller-side wait timeout does not cancel an accepted request. Instance destruction does not cancel completion callbacks for accepted requests.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] Pointer to a UI instance. Must not be NULL. The caller must be on the UI thread of this instance; a detected thread violation triggers a fatal abort. The uniqueId must resolve to a node within this instance. The pointer must remain valid throughout this function call. |
| uint32_t uniqueId | [in] Unique ID of the target node. The framework resolves this ID to the corresponding node within the uiContext instance. |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *command | [in] Command data. Must not be NULL. The data is carried by an [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) object created with [OH_ArkUI_NativeModule_UIJsonWrapperCreate](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate). The payload's top-level structure is: {"schemaVersion": 1, "cmd": {"type": "<command type>", "action_info": { ... }}} For supported command types, action_info field constraints, and examples, see the API development guide. The JSON data is internally copied before the function returns; if the caller owns command, it may release it with [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) after this function returns. |
| [OH_ArkUI_NativeModule_UIEventInjectionCallback](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback) callback | [in] Completion callback. Must not be NULL. After the request is accepted, it must remain callable until it returns, even if the caller's wait times out. |
| void *userData | [in] Custom user data pointer passed to the callback. Can be NULL. The data is managed by the caller. After acceptance, non-NULL data must remain valid until the callback returns, even if the caller's wait times out. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | A value of 0 means the request was accepted; its execution result is reported by callback. A nonzero value means the request was rejected without command execution or callback. <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the request is accepted.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if command or callback is NULL, the command data is invalid, or command submission failed.</li> <li>ARKUI_ERROR_CODE_NODE_NOT_FOUND if uniqueId does not resolve to a node within the uiContext instance.</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if uiContext is NULL, or the corresponding UI instance is being destroyed or is invalid.</li> <li>ARKUI_ERROR_CODE_COMMAND_UNFINISHED if a previous command still restricts acceptance of subsequent requests in this process. Once a command is accepted, other valid requests in the same process return this error. The restriction is lifted before the framework invokes the completion callback. The callback may submit another command subject to the parameter and UI-thread requirements. Rejected requests may be retried after the restriction is lifted; acceptance remains subject to other requests in the process.</li> </ul> |


