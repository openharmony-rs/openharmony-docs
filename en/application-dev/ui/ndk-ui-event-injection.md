---
kits: ["ArkUI"]
description: "Describes how to use NDK APIs to asynchronously inject UI control commands into a target node of a specified UI instance, for in-app intelligent agents and UI automation."
keywords: [UI event injection, NDK, command injection, intelligent agent, UI automation, C API]
doctype: guide
status: active
---

# UI Event Injection (C/C++)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

UI event injection APIs provide UI control capabilities for in-app intelligent agents and UI automation scenarios. Through C APIs, an application can asynchronously inject control commands (click, scroll, content switch, back press, and key) into a target node of a specified UI instance. The execution result is reported asynchronously through a completion callback. A command is described in JSON, expressing a high-level intent of "what to do and where", and the system decides how to execute it.

## Constraints and Prerequisites

| Constraint | Description |
| --- | --- |
| Version requirement | These APIs start from API version 26.1.0. Confirm the device supports them before use. |
| Injection scope | Commands can only be injected into the application's own UI instances. Cross-application injection is not supported. |
| Thread requirement | The caller must be on the UI thread of the target uiContext. A detected thread violation triggers a fatal abort. |
| Concurrency restriction | Only one command is accepted at a time within a process. After a command is accepted and before its completion callback fires, other valid requests return ARKUI_ERROR_CODE_COMMAND_UNFINISHED. Another command can be submitted in the callback. |
| Cancellation and timeout | No cancellation operation or fixed completion timeout is provided. A caller-side wait timeout neither cancels an accepted request nor prevents its callback. |
| Instance destruction | Destroying the UI instance does not cancel completion callbacks of accepted requests. |
| Coordinate semantics | Coordinates are relative to the current window, in physical pixels (px). |

## Available APIs

| API | Description |
| --- | --- |
| [OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand) | Asynchronously injects a control command into a target UI node. This is the only entry of this capability. |
| [OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate) | Creates a command data object from a JSON string. |
| [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) | Destroys a command data object and releases its resources. |
| [OH_ArkUI_NodeUtils_GetNodeUniqueId](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getnodeuniqueid) | Obtains the unique ID of the target node, used as the uniqueId input of the injection API. |

The execution result is reported through the [OH_ArkUI_NativeModule_UIEventInjectionCallback](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback) callback, whose value is the [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode) enumeration.

## Command Format

The top-level structure of a command JSON is fixed:

```json
{
    "schemaVersion": 1,
    "cmd": {
        "type": "<command type>",
        "mode": "<execution mode, optional>",
        "action_info": { ... }
    }
}
```

The top-level schemaVersion field is mandatory and currently takes the value 1. A command is rejected if this field is missing or its version is unsupported. The cmd.type field supports the following five command types:

| Command type | mode (valid values) | Key action_info fields | Description |
| --- | --- | --- | --- |
| click | auto (default) / simulating / target | coordinates.x1, coordinates.y1 (mandatory) | Clicks the specified coordinates. |
| scroll | auto (default) / simulating / target | coordinates.x1, coordinates.y1 (mandatory); coordinates.x2, coordinates.y2 (optional, scroll end point) | Scrolls from the start point to the end point. |
| content_switch | target (mandatory) | coordinates.pos.x, coordinates.pos.y (mandatory); direction (forward (default) / backward, optional) | Performs a content switch (for example, page turning) at the specified position. |
| backpress | N/A | N/A | Performs the back operation. |
| key | N/A | code (mandatory, integer key code) | Injects a key event. |

JSON examples of each command are as follows:

```json
// click: click (100, 200)
{ "schemaVersion": 1, "cmd": { "type": "click", "mode": "auto",
    "action_info": { "coordinates": { "x1": 100.0, "y1": 200.0 } } } }

// scroll: scroll from (100, 200) to (100, 400)
{ "schemaVersion": 1, "cmd": { "type": "scroll", "mode": "auto",
    "action_info": { "coordinates": { "x1": 100.0, "y1": 200.0, "x2": 100.0, "y2": 400.0 } } } }

// content_switch: switch content forward at (100, 200)
{ "schemaVersion": 1, "cmd": { "type": "content_switch", "mode": "target",
    "action_info": { "coordinates": { "pos": { "x": 100.0, "y": 200.0 } }, "direction": "forward" } } }

// backpress: go back
{ "schemaVersion": 1, "cmd": { "type": "backpress" } }

// key: inject the key with code 2049
{ "schemaVersion": 1, "cmd": { "type": "key", "action_info": { "code": 2049 } } }
```

If the command JSON is invalid (not legal JSON, missing mandatory fields, or an unknown command type), the injection API synchronously returns ARKUI_ERROR_CODE_PARAM_INVALID, and no callback is triggered.

## How to Develop

### Adding Dynamic Libraries

Link libace_ndk.z.so in CMakeLists.txt:

```Text
target_link_libraries(entry PUBLIC libace_ndk.z.so)
```

### Including Header Files

```C++
#include <arkui/ui_event_injection.h>
#include <arkui/ui_json_wrapper.h>
#include <arkui/native_node.h>
```

### Complete Example

The following example injects a click into a target node of the current UI instance:

```C++
// 1. Define the completion callback: each accepted request is invoked exactly once,
//    on the originating (UI) thread.
static void OnInjectionResult(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void* userData)
{
    // result is the execution result: SUCCESS (0), TARGET_NOT_FOUND (1),
    // COMMAND_NOT_SUPPORTED (2), or INTERRUPTED_BY_USER (3).
    int* finished = static_cast<int*>(userData); // userData is managed by the caller
                                                  // and must remain valid until the callback returns.
    if (finished != nullptr) {
        *finished = 1;
    }
}

// 2. Obtain the uniqueId of the target node (targetNode is an obtained ArkUI_NodeHandle).
int32_t nodeId = -1;
if (OH_ArkUI_NodeUtils_GetNodeUniqueId(targetNode, &nodeId) != 0) {
    return; // Failed to obtain the ID. Handle the error.
}

// 3. Build the command JSON and create the command data object
//    (the JSON is internally copied).
const char* json = R"({"schemaVersion":1,"cmd":{"type":"click","mode":"auto",)"
                  R"("action_info":{"coordinates":{"x1":100.0,"y1":200.0}}}})";
OH_ArkUI_NativeModule_UIJsonWrapper* command = nullptr;
ArkUI_ErrorCode ret = OH_ArkUI_NativeModule_UIJsonWrapperCreate(json, strlen(json), &command);
if (ret != ARKUI_ERROR_CODE_NO_ERROR || command == nullptr) {
    return; // The JSON is invalid or memory allocation failed. command is nullptr.
}

// 4. Inject the command (must be called on the UI thread of the target uiContext).
int finished = 0;
ret = OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(
    uiContext, static_cast<uint32_t>(nodeId), command, OnInjectionResult, &finished);

// 5. The command JSON has been internally copied before the injection API returns,
//    so the command object can be destroyed immediately.
OH_ArkUI_NativeModule_UIJsonWrapperDestroy(command);

if (ret != ARKUI_ERROR_CODE_NO_ERROR) {
    return; // The request was synchronously rejected, and no callback will be triggered.
}
// 6. Wait for the callback to report the execution result (finished is set in the callback).
```

In the preceding example, uiContext is the ArkUI_ContextHandle of the target UI instance, and targetNode is the handle of the target node. A return value of ARKUI_ERROR_CODE_NO_ERROR only indicates that the request is accepted. The final execution result is reported through result in the callback.

## Result and Error Handling

The synchronous return value of the injection API and the callback result code have different meanings and must be handled separately:

**Synchronous return values (whether the request is accepted):**

| Return value | Description |
| --- | --- |
| ARKUI_ERROR_CODE_NO_ERROR | The request is accepted, and the execution result is reported through the callback. |
| ARKUI_ERROR_CODE_PARAM_INVALID | The command object is null, the command data is invalid, the callback is null, or the submission failed. |
| ARKUI_ERROR_CODE_NODE_NOT_FOUND | uniqueId cannot be resolved to a node within the target UI instance. |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID | uiContext is null, or the corresponding UI instance is being destroyed or invalid. |
| ARKUI_ERROR_CODE_COMMAND_UNFINISHED | A previous command has not completed (only one command is accepted at a time within a process). Retry after the restriction is lifted. |

**Callback result codes (command execution result):**

| Result code | Description |
| --- | --- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS | The command was executed successfully. |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND | No component or target could be found to respond to the command (for example, the click coordinates hit no component). |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED | The command cannot be executed in the current UI state (for example, the target required by the execution mode cannot be located). |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER | The command was interrupted by a user operation. |

**Lifecycle notes:**

- The command JSON is copied before the injection API returns. The caller can destroy the command object immediately after the API returns. To reuse the same command in a callback, create a new command object.
- After a callback is accepted, it must remain callable until it returns, even if the caller's wait times out.
- userData is managed by the caller. The framework only passes the pointer through; it does not access, copy, or free the data. After a request is accepted and until the callback returns, non-NULL userData must remain valid.

## References

- [ui_event_injection.h API reference](../reference/apis-arkui/capi-ui-event-injection-h.md)
- [ui_json_wrapper.h API reference](../reference/apis-arkui/capi-ui-json-wrapper-h.md)
- [NDK UI development overview](ndk-build-ui-overview.md)
