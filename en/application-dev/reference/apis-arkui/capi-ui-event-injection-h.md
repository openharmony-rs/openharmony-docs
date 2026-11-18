# ui_event_injection.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202 -->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-03T08:43:55.635Z pushedAt=2026-11-04T02:25:38.104Z nl=1 -->

## Overview

Declares the APIs for injecting control commands into specified UI nodes, for use by in-application agents and UI automation.

**File to include:** <arkui/ui_event_injection.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since:** 26.1.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](#oh_arkui_nativemodule_uieventinjection_resultcode) | OH_ArkUI_NativeModule_UIEventInjection_ResultCode | Enumerates the result codes of UI event injection.<br>All injection APIs share this enumeration, including loose interaction injection (non-precise) and precise injection for specified components. A non-zero result code indicates execution failure, and its specific value indicates the cause of the failure. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)](#oh_arkui_nativemodule_uieventinjectioncallback) | OH_ArkUI_NativeModule_UIEventInjectionCallback | Defines the callback for injection completion.<br>It is used to notify the dispatch result of the command and the immediate processing result of the component for the command, and does not wait for the component's delayed effect or rendering to complete. Each accepted request is called back exactly once on the original UI thread after the injection API returns. Callbacks on different UI threads are not guaranteed to be executed serially globally. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)](#oh_arkui_nativemodule_uieventinjectcompositecommand) | - | Asynchronously injects a control command into the target UI node.<br>This API does not provide cancellation or a fixed completion timeout; completion depends on the task processing of the UI thread. A timeout on the caller side does not cancel an accepted request. Instance destruction does not cancel the completion callback of an accepted request. |

### Variables

| Name | Description |
| -- | -- |
| void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData) | Callback for injection completion.<br>It is used to notify the dispatch result of the command and the immediate processing result of the component for the command, and does not wait for the component's delayed effect or rendering to complete. Each accepted request is called back exactly once on the original UI thread after the injection API returns. Callbacks on different UI threads are not guaranteed to be executed serially globally. |

## Enum Description

### OH_ArkUI_NativeModule_UIEventInjection_ResultCode

```c
enum OH_ArkUI_NativeModule_UIEventInjection_ResultCode
```

**Description**

Enumerates the result codes of UI event injection.<br>All injection APIs share this enumeration, including loose interaction injection (non-precise) and precise injection for a specified component. A non-zero result code indicates execution failure, and its specific value indicates the cause of the failure.

| Value | Description |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS = 0 | The injected command is executed successfully. |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND = 1 | No component or target that can respond to the injected command is found.<br>For example, the tap coordinates do not hit any component, or the target required by the execution mode cannot be located. |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED = 2 | The current UI context cannot execute the command.<br>The command structure is valid, but the current UI state does not support the command type or execution mode. |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER = 3 | The injected command is interrupted by a user operation. |

## Function Description

### OH_ArkUI_NativeModule_UIEventInjectionCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)
```

**Description**

Defines the callback for injection completion.<br>It is used to notify the dispatch result of the command and the immediate processing result of the component for the command, and does not wait for the component's delayed effect or rendering to complete. Each accepted request is called back exactly once on the original UI thread after the injection API returns. Callbacks on different UI threads are not guaranteed to be executed serially globally.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode) result | [Input parameter] Result code of the injection execution. For details, see [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode). |
| void *userData | [Input parameter] Pointer to the custom user data passed in during injection. If **NULL** is passed in during injection, this parameter is **NULL**. The framework only saves the pointer value for use by this callback, and does not access the data pointed to by the pointer, nor copy, release, or take ownership of the data. After the request is accepted, the caller must keep the non-**NULL** data valid until the callback returns. |

### OH_ArkUI_NativeModule_UIEventInjectCompositeCommand()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)
```

**Description**

Asynchronously injects a control command into the target UI node.<br>This API does not provide a cancellation operation or a fixed completion timeout. Completion depends on task processing on the UI thread. A caller timeout does not cancel an accepted request. Instance destruction does not cancel the completion callback of an accepted request.

The related declaration is located in `<arkui/ui_json_wrapper.h>`. Use the `OH_ArkUI_NativeModule_UIJsonWrapperCreate` API to create a JSON wrapper object.

`data` points to a JSON string, and `size` indicates the byte length excluding the trailing null character. After successful creation, the caller owns the object returned by `outOwned` and must call the `OH_ArkUI_NativeModule_UIJsonWrapperDestroy` API to release the object when it is no longer needed.

The creation API copies the JSON data, so the caller can release or reuse the original string after `OH_ArkUI_NativeModule_UIJsonWrapperCreate` returns. Passing `NULL` to the destroy API performs no operation.

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | [Input parameter] Pointer to the UI instance, which cannot be **NULL**. The caller must call this API on the UI thread of this instance. When a thread violation is detected, a fatal error is triggered and the process is terminated. **uniqueId** must be resolvable to a node within this instance. **uiContext** must remain valid during the call to this API. |
| uint32_t uniqueId | [Input parameter] ID of the target node. The framework resolves this node ID to the corresponding ArkUI node within the **uiContext** instance. |
| const OH_ArkUI_NativeModule_UIJsonWrapper *command | [Input parameter] Pointer to the command data, which cannot be **NULL**. It is carried by an **OH_ArkUI_NativeModule_UIJsonWrapper** object created by **OH_ArkUI_NativeModule_UIJsonWrapperCreate**.<br>The top-level structure of the command content is: `{"schemaVersion": 1, "cmd": {"type": "<command type>", "action_info": { ... }}}`<br>The JSON data is copied internally before the API returns. The command owned by the caller can be destroyed after this API returns. |
| [OH_ArkUI_NativeModule_UIEventInjectionCallback](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback) callback | [Input parameter] Completion callback, which cannot be **NULL**. After the request is accepted, it must remain callable until the callback returns. Even if the caller times out, the callback resources cannot be released in advance. |
| void *userData | [Input parameter] Pointer to the custom user data passed to the callback, which can be **NULL**. The user data is managed by the caller. After the request is accepted, non-**NULL** data must remain valid until the callback returns. Even if the caller times out, it cannot be released in advance. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns **0** if the request is accepted, and the execution result is reported through callback. Returns a non-zero value if the request is rejected, in which case the command is not executed and the callback is not triggered.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the request is accepted.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **command** or **callback** is **NULL**, the command data is invalid, or the command submission fails.<br>Returns [ARKUI_ERROR_CODE_NODE_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the ArkUI node corresponding to the node ID (**uniqueId**) is not found within the **uiContext** instance.<br>Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **uiContext** is **NULL**, or the corresponding UI instance is being destroyed or has become invalid.<br>Returns [ARKUI_ERROR_CODE_COMMAND_UNFINISHED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the following error occurs: In the current process, the restriction imposed by the previous command on subsequent requests has not been lifted. After a command is accepted, other valid requests in the same process return this error code.<br>The framework lifts this restriction before invoking the completion callback. A command can be submitted again in the callback, but the parameter and UI thread requirements must still be met. A rejected request can be retried after the restriction is lifted, and whether it can be accepted still depends on other requests in the process. |
