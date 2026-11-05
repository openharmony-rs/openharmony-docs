# AIPageResult
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @hwt00888022-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=a40d54eb841d3251f24cd251233d70758a16c2e7 translatedAt=2026-11-02T14:04:51.108Z pushedAt=2026-11-03T03:32:37.187Z nl=1 -->

`AIPageResult` defines the general format and result code values of the result returned by [executeAIPageCommand](./arkts-apis-webview-WebviewController.md#executeaipagecommand), which are shared by the commands in [AIPageCommand](./arkts-apis-webview-AIPageCommand.md) and [AIPageInteraction](./arkts-apis-webview-AIPageInteraction.md).

## CommandResult

Commands such as scroll, select, input, dispatchMouseEvent, dispatchKeyEvent, uploadFile, and setZoomLevel in [AIPageInteraction](./arkts-apis-webview-AIPageInteraction.md) return the following JSON format; commands such as getUrlHistory, goBack, goForward, navigate, getZoomLevel, addPageAnnotation, and removePageAnnotation in [AIPageCommand](./arkts-apis-webview-AIPageCommand.md) also contain the `code` and `message` fields, and append other result fields depending on the command.

| Field | Type | Description |
| ---- | ---- | ---- |
| code | number | Command execution result code. For the value, see [Command Execution Result Code Description](#command-execution-result-code-description). |
| message | string | Command execution result description. It is `"success"` on success; when a non-blocking warning exists, the `"; warnings: "` prefix and warning information are appended, in the format `"success; warnings: <path1>: <reason1>, <path2>: <reason2>"`; it is the error description on failure. |
| result | Object | Carried when the command succeeds and result data needs to be returned. The `result` structure differs for different commands, subject to the description in the corresponding command section. |

## Command Execution Result Code Description

| Value | Description |
| ---- | ---- |
| 10 | Operation success. |
| 11 | Execution failed. |
| 110 | Invalid JSON. |
| 114 | The `xpath` or node identifier field is missing. |
| 115 | Invalid value of the `xpath` field. |
| 130 | Command execution timed out. |
| 131 | The element does not exist. |
| 132 | browser or host is empty. |
| 160 | The page is not ready. |
| 161 | Element type mismatch. |
| 200 | Invalid `xpath` field of the input command. |
| 201 | Invalid `value` field of the input command. |
| 202 | Invalid input type. |
| 203 | Invalid input value format. |
| 204 | Input event type mismatch. |
| 250 | Invalid `xpath` field of the select command. |
| 251 | Invalid select option (neither indexes nor values are provided). |
| 252 | select index out of range. |
| 253 | select value not found. |
| 254 | select does not support multiple selection. |
| 255 | The select option is disabled. |
| 256 | The select option is empty. |
| 300 | Invalid `x` field of the gesture command. |
| 301 | Invalid `y` field of the gesture command. |
| 302 | Invalid `distance` field of the gesture command. |
| 303 | Invalid `scale` field of the gesture command. |
| 304 | Invalid `duration` field of the gesture command. |
| 305 | Invalid `tapCount` field of the gesture command. |
| 306 | Invalid `speed` field of the gesture command. |
| 307 | Invalid coordinate field of the gesture command. |
| 350 | Failed to deliver the command. |
| 351 | The command channel is not ready. |
| 352 | Command execution failed. |
| 353 | Command response parsing error. |
| 370 | The file path cannot be resolved. |
| 371 | The file path is empty. |
| 372 | The file list is empty. |
| 390 | Unsupported command. |
| 391 | Required parameter missing. |
| 392 | Invalid parameter type. |
| 400 | Input method handler not found. |
| 401 | Unknown command name (the value of the `method` field cannot be recognized). |
| 402 | Input method not bound. |
| 420 | The `params` field is not provided for click/focus. |
| 421 | `xpath`/`nodeid` is not provided for click/focus, or its value is an empty string. |
| 422 | The locating field of click/focus is empty after parsing. |
| 423 | The Web instance of click/focus is unavailable. |
| 424 | The target element of click/focus is not found. |
| 440 | The `params` field is not provided for type. |
| 441 | `xpath`/`nodeid` is not provided for type. |
| 442 | The `text` parameter is not provided for type. |
| 443 | `xpath` is provided for type but its value is empty. |
| 444 | The Web instance of type is unavailable. |
| 445 | The target element of type is not found. |
| 460 | The `params` field is not provided for send_keys. |
| 461 | The `key` field is not provided for send_keys. |
| 462 | The `key` of send_keys is an empty string or contains no valid key. |
| 463 | The `key` value of send_keys cannot be recognized. |
| 480 | zoomLevel is out of the valid range. |
| 481 | Invalid zoomLevel value (negative or zero). |
| 482 | Zoom control has been disabled by the application. |

> **NOTE**
>
> - Distinction between a missing and an empty element locating field: if the locating field is not provided, or its value is an empty string, the corresponding `*_NODEID_MISSING` of the command is returned (for example, 421/441); if `xpath` is provided but its value is empty, `*_XPATH_EMPTY` is returned (for example, 443).
> - The `key` field of send_keys: if the `key` field is not provided, 461 is returned; if `key` is an empty string, 462 is returned; if the `key` value cannot be recognized, 463 is returned.
