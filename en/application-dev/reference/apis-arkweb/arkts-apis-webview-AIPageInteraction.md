# AIPageInteraction

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhu-sheng-le-->
<!--Designer: @yyyiye-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=dcc0abdade92c0b802a40194e56aabc12b399ebe translatedAt=2026-08-07T04:41:03.794Z pushedAt=2026-08-07T07:45:37.168Z -->

Starting from API version 26.0.0, `AIPageInteraction` defines the page interaction JSON command protocol supported by [executeAIPageCommand](./arkts-apis-webview-WebviewController.md#executeaipagecommand), including element-level input operations such as click, focus, type text, and send keyboard events, as well as operations that change the page state, such as page scrolling, dropdown option selection, file upload, and zoom control. Before calling this API, the app needs to serialize the command object into a JSON string.

> **NOTE**
>
> - `command` must be a JSON object string.
> - The `method` field value is case-sensitive. Use the values listed in [Command Overview](#command-overview).
> - The return value is a JSON string. Different commands have different return formats. For commands whose return format is listed as [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult), see AIPageResult. For commands whose return format is listed as [Return Format](#return-format), see the Return Format section on this page. The app can parse it using `JSON.parse`.
> - When the command cannot be dispatched or no result is returned, the API may return an empty string. When the command fails during execution, the return format specified in the corresponding command section applies.
> - For query commands, see [AIPageCommand](./arkts-apis-webview-AIPageCommand.md).

## Command Overview

| method | Function | Input Parameter Format | Return Format | Description |
| ---- | ---- | ---- | ---- | ---- |
| [click](#click) | Clicks the target element | [ClickCommand](#clickcommand) | [Return Format](#return-format) | Makes the target element respond to a click event, regardless of whether a real mouse event is generated. |
| [focus](#focus) | Makes the target element gain focus | [FocusCommand](#focuscommand) | [Return Format](#return-format) | Moves focus to the target element so that it can receive subsequent interactions such as keyboard input. |
| [cursor_position](#cursor_position) | Gets the current caret position | None | [CursorPositionResult](#cursorpositionresult) | Gets the position of the caret in the current page, with coordinates relative to the Web component. |
| [type](#type) | Inputs text to the target element | [TypeCommand](#typecommand) | [Return Format](#return-format) | Inserts text at the specified position of the target element, supporting clearing before input. If the target element does not have focus, it gains focus first before input. |
| [send_keys](#send_keys) | Sends keyboard events | [SendKeysCommand](#sendkeyscommand) | [Return Format](#return-format) | Sends keyboard events to the frontend, supporting function keys, number keys, letter keys, symbol keys, editing keys, navigation keys, modifier keys, and key combinations. |
| [dispatchMouseEvent](#dispatchmouseevent) | Injects mouse events | [DispatchMouseEventCommand](#dispatchmouseeventcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Injects mouse events by viewport coordinates. |
| [dispatchKeyEvent](#dispatchkeyevent) | Injects keyboard events | [DispatchKeyEventCommand](#dispatchkeyeventcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Injects keyboard events. |
| [input](#input) | Sets the input box content | [InputCommand](#inputcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Sets the value of the specified `input` element. |
| [scroll](#scroll) | Scrolls the page | [ScrollCommand](#scrollcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Scrolls the page by coordinates or node identifier. |
| [select](#select) | Selects a dropdown option | [SelectCommand](#selectcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Selects the specified `<select>` element option. |
| [uploadFile](#uploadfile) | Uploads a file | [UploadFileCommand](#uploadfilecommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Sets the file list of the `<input type='file'>` tag. |
| [setZoomLevel](#setzoomlevel) | Sets the web page zoom level | [SetZoomLevelCommand](#setzoomlevelcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Sets the zoom level of the current web page, equivalent to CTRL+Wheel zooming. |

## Target Element Locating

The `click`, `focus`, and `type` commands need to specify the operation target through target element locator parameters. Two mutually exclusive methods are supported:

| Name | Type | Description |
| ---- | ---- | ---- |
| xpath | string | XPath of the target element, which can be obtained from the `xpath` field returned by [getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom) or [getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom). |
| nodeid | string | Node identifier of the target element, which can be obtained from the `id` field returned by [getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom) or [getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom). This value is encoded from the frame identifier, document scope identifier, and DOM node identifier. |

> **NOTE**
>
> `xpath` and `nodeid` are mutually exclusive. When both are passed, `nodeid` takes precedence.

## Return Format

### Success

Operation commands (click, focus, type, send_keys) return the following on success:

```json
{
  "code": 10,
  "message": "success"
}
```

Query commands (cursor_position) return a result object on success. See the description of each command.

### Failure

For commands whose return format is listed in [Return Format](#return-format) of this section, a JSON object containing the `code` and `error` fields is returned on failure. The following uses the `click` command without the `params` field as an example:

```json
{
  "code": 420,
  "error": "click/focus params not found"
}
```

For error code values, see [Command Execution Result Code Description](./arkts-apis-webview-AIPageResult.md#command-execution-result-code-description).

## click

Clicks the target element to make it respond to a click event, regardless of whether a real mouse event is generated.

### ClickCommand

Locate the target element by XPath:

```json
{
  "method": "click",
  "params": {
    "xpath": "/html[1]/body[1]/button[1]"
  }
}
```

Locate the target element by node identifier:

```json
{
  "method": "click",
  "params": {
    "nodeid": "frameToken|documentToken|12"
  }
}
```

### Input Parameter Description

| Name | Subparameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, which is fixed to `click`. |
| params | - | - | Object | Yes | Command parameter. |
| params | - | xpath | string | No | XPath of the target element. `xpath` and `nodeid` are mutually exclusive. When both are passed, `nodeid` takes precedence. |
| params | - | nodeid | string | No | Node identifier of the target element. `xpath` and `nodeid` are mutually exclusive. When both are passed, `nodeid` takes precedence. |

> **NOTE**
>
> - `params` must contain one of `xpath` or `nodeid`, which is used for locating the target element.

### Return Description

Returns `{"code":10,"message":"success"}` on success; returns an error code JSON on failure. Common error codes are listed in the table below:

| Error Code | Trigger Condition |
| ---- | ---- |
| 420 | The `params` field is not provided. |
| 421 | `xpath`/`nodeid` is not provided or its value is an empty string. |
| 422 | The locator field is empty after parsing. |
| 423 | The Web instance is unavailable. Check that the Web component is correctly loaded and associated with a valid Web instance. |
| 424 | Target element not found. |

### Request Example

```json
{
  "method": "click",
  "params": {
    "xpath": "/html[1]/body[1]/button[1]"
  }
}
```

### Response Example

Success:

```json
{
  "code": 10,
  "message": "success"
}
```

Failure:

`420` (`params` field not provided):

```json
{
  "code": 420,
  "error": "click/focus params not found"
}
```

`421` (`xpath`/`nodeid` not provided or its value is an empty string):

```json
{
  "code": 421,
  "error": "click/focus nodeid not found"
}
```

`422` (Locator field is empty after parsing):

```json
{
  "code": 422,
  "error": "click/focus nodeid is empty"
}
```

`423` (Web instance unavailable):

```json
{
  "code": 423,
  "error": "click/focus delegate not initialized"
}
```

`424` (Target element not found):

```json
{
  "code": 424,
  "error": "click/focus element not exist"
}
```

## focus

Makes the target element obtain focus.

### FocusCommand

Locate the target element by XPath:

```json
{
  "method": "focus",
  "params": {
    "xpath": "/html[1]/body[1]/input[1]"
  }
}
```

Locate the target element by node identifier:

```json
{
  "method": "focus",
  "params": {
    "nodeid": "frameToken|documentToken|12"
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed to `focus`. |
| params | - | - | Object | Yes | Command parameter. |
| params | - | xpath | string | No | XPath of the target element. `xpath` and `nodeid` are mutually exclusive. When both are passed, `nodeid` takes precedence. |
| params | - | nodeid | string | No | Node identifier of the target element. `xpath` and `nodeid` are mutually exclusive. When both are passed, `nodeid` takes precedence. |

> **NOTE**
>
> - `params` must contain one of `xpath` or `nodeid`, used for locating the target element.

### Return Description

Returns `{"code":10,"message":"success"}` on successful command execution; returns error code JSON on failure. Error codes are the same as those in [click](#return-description-1) (420-424).

### Request Example

```json
{
  "method": "focus",
  "params": {
    "nodeid": "frameToken|documentToken|12"
  }
}
```

### Response Example

Success:

```json
{
  "code": 10,
  "message": "success"
}
```

Failure (error codes same as click):

`420` (`params` field not provided):

```json
{
  "code": 420,
  "error": "click/focus params not found"
}
```

`421` (`xpath`/`nodeid` not provided or its value is an empty string):

```json
{
  "code": 421,
  "error": "click/focus nodeid not found"
}
```

`422` (the locator field is empty after parsing):

```json
{
  "code": 422,
  "error": "click/focus nodeid is empty"
}
```

`423` (the Web instance is unavailable):

```json
{
  "code": 423,
  "error": "click/focus delegate not initialized"
}
```

`424` (the target element is not found):

```json
{
  "code": 424,
  "error": "click/focus element not exist"
}
```

## cursor_position

Obtains the position of the caret in the current page. The returned coordinates are the offset relative to the top-left corner of the Web component.

### Request Description

This command does not require the `params` parameter.

### CursorPositionResult

```json
{
  "result": {
    "x": 100,
    "y": 200
  }
}
```

### Return Description

| Field | Subfield | Type | Description |
| ---- | ---- | ---- | ---- |
| result | - | Object | Caret position information. |
| result | x | number | The x-coordinate of the caret, relative to the Web component. |
| result | y | number | The y-coordinate of the caret, relative to the Web component. |

> **NOTE**
>
> - The coordinates are relative to the Web component, not the absolute coordinates of the page.
> - Returns an error code JSON on failure. Common error codes: 400 (input function unavailable), 401 (unknown command name), 402 (input method not bound).

### Request Example

```json
{
  "method": "cursor_position"
}
```

### Response Example

Success:

```json
{
  "result": {
    "x": 100,
    "y": 200
  }
}
```

Failure:

`400` (Input function unavailable, input method handler not found):

```json
{
  "code": 400,
  "error": "method not found"
}
```

`401` (Unknown command name, the value of the `method` field is unrecognized):

```json
{
  "code": 401,
  "error": "unknown method"
}
```

`402` (input method not bound):

```json
{
  "code": 402,
  "error": "input method not bound"
}
```

## type

Inputs text into the target element. Supports inserting text at a specified position in the target element, and supports clearing before input. If the target element has not obtained focus, it will first be focused before input.

### TypeCommand

```json
{
  "method": "type",
  "params": {
    "xpath": "/html[1]/body[1]/input[1]",
    "text": "Text to be entered.",
    "index": 0,
    "clear": false
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `type`. |
| params | - | - | Object | Yes | Command parameters. |
| params | - | xpath | string | No | XPath of the target element. `xpath` and `nodeid` are mutually exclusive. When both are passed, `nodeid` takes precedence. |
| params | - | nodeid | string | No | Node identifier of the target element. `xpath` and `nodeid` are mutually exclusive. When both are passed, `nodeid` takes precedence. |
| params | - | text | string | Yes | Text content to be input. |
| params | - | index | number | No | Text insertion position, starting from 0. If the length of existing text in the input box is less than `index`, the text is appended at the end. The default value is **0**. |
| params | - | clear | boolean | No | Whether to clear the existing text in the target element before input. The default value is **false**. |

> **NOTE**
>
> - `params` must contain one of `xpath` or `nodeid`, used for locating the target element.
> - If the target element does not have focus, it will first be focused before performing the input operation.
> - When `index` is **0**, the text is inserted at the very beginning of the existing text.
> - When `clear` is **true**, all text in the target element is cleared first, and then `text` is inserted at the `index` position.

### Return Description

Returns `{"code":10,"message":"success"}` on success; returns an error code JSON on failure. Common error codes are listed in the table below:

| Error Code | Trigger Condition |
| ---- | ---- |
| 440 | `params` field not provided |
| 441 | `xpath`/`nodeid` not provided |
| 442 | `text` parameter not provided |
| 443 | `xpath` provided but its value is empty |
| 444 | Web instance unavailable. Ensure the Web component is properly loaded and associated with a valid Web instance. |
| 445 | Target element not found |

### Request Example

```json
{
  "method": "type",
  "params": {
    "xpath": "/html[1]/body[1]/input[1]",
    "text": "Hello World",
    "index": 0,
    "clear": false
  }
}
```

### Return Example

Success:

```json
{
  "code": 10,
  "message": "success"
}
```

Failure:

`440` (the `params` field is not provided):

```json
{
  "code": 440,
  "error": "type params not found"
}
```

`441` (`xpath`/`nodeid` is not provided):

```json
{
  "code": 441,
  "error": "type nodeid not found"
}
```

`442` (`text` parameter not provided):

```json
{
  "code": 442,
  "error": "type text not found"
}
```

`443` (`xpath` provided but its value is empty):

```json
{
  "code": 443,
  "error": "type xpath is empty"
}
```

`444` (Web instance unavailable):

```json
{
  "code": 444,
  "error": "type delegate not initialized"
}
```

`445` (target element not found):

```json
{
  "code": 445,
  "error": "type element not exist"
}
```

## send_keys

Injects keyboard events to the frontend, supporting single keys and key combinations.

### SendKeysCommand

Single key:

```json
{
  "method": "send_keys",
  "params": {
    "key": "Enter"
  }
}
```

Key combination (modifier key + key, connected by `+`):

```json
{
  "method": "send_keys",
  "params": {
    "key": "Control+c"
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `send_keys`. |
| params | - | - | Object | Yes | Command parameter. |
| params | - | key | string | Yes | Key name to send. For values, see [Description of params.key Field Values for send_keys](#description-of-paramskey-field-values-for-send_keys). Supports composite keys in the format of `modifier key+key` (for example, `Control+c`). Case-sensitive when sending letters. |

> **NOTE**
>
> - When sending letters, it is case-sensitive. For example, `KeyA` and `Keya` represent different keys.
> - The composite key format is `modifier key+key`, for example, `Control+c` and `Shift+ArrowLeft`.

### Description of params.key Field Values for send_keys

| Category | Supported Keys |
| ---- | ---- |
| Function Keys | F1, F2, F3, F4, F5, F6, F7, F8, F9, F10, F11, F12 |
| Number Keys | Digit0, Digit1, Digit2, Digit3, Digit4, Digit5, Digit6, Digit7, Digit8, Digit9 |
| Letter Keys | KeyA ~ KeyZ, Keya ~ Keyz (case-sensitive) |
| Symbol Keys | Backquote, Minus, Equal, Backslash |
| Editing Keys | Backspace, Tab, Delete, Insert, Enter, Escape |
| Navigation Keys | ArrowDown, ArrowUp, ArrowLeft, ArrowRight, Home, End, PageUp, PageDown |
| Modifier Keys | Shift, Control, Alt, ShiftLeft |
| Combination Keys | `Modifier Key + Key`, for example, `Control+c`, `Shift+ArrowLeft` |

### Return Description

Returns `{"code":10,"message":"success"}` on successful command execution; returns an error code JSON on failure. Common error codes see the table below:

| Error Code | Trigger Condition |
| ---- | ---- |
| 460 | The `params` field is not provided. |
| 461 | The `key` field is not provided. |
| 462 | `key` is an empty string or has no valid key. |
| 463 | The `key` value is unrecognized (unknown key name). |

### Request Example

```json
{
  "method": "send_keys",
  "params": {
    "key": "PageDown"
  }
}
```

### Response Example

Success:

```json
{
  "code": 10,
  "message": "success"
}
```

Failure:

`460` (`params` field not provided):

```json
{
  "code": 460,
  "error": "send_keys params not found"
}
```

`461` (`key` field not provided):

```json
{
  "code": 461,
  "error": "send_keys keys not found"
}
```

`462` (`key` is an empty string or has no valid key):

```json
{
  "code": 462,
  "error": "send_keys no valid keys"
}
```

`463` (`key` value is unrecognizable):

```json
{
  "code": 463,
  "error": "send_keys unknown main key"
}
```

## dispatchMouseEvent

Injects a mouse event by viewport coordinates.

### DispatchMouseEventCommand

```json
{
  "method": "dispatchMouseEvent",
  "params": {
    "type": "mouseWheel",
    "x": 500,
    "y": 300,
    "deltaX": 0,
    "deltaY": 100,
    "pointerType": "mouse"
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `dispatchMouseEvent`. |
| params | - | - | Object | Yes | Command parameter. |
| params | type | - | string | Yes | Mouse event type. Supports `mousePressed`, `mouseReleased`, `mouseMoved`, and `mouseWheel`. |
| params | x | - | number | Yes | Viewport x coordinate. |
| params | y | - | number | Yes | Viewport y coordinate. |
| params | button | - | string | No | Mouse button. Supports `none`, `left`, `middle`, `right`, `back`, and `forward`. |
| params | clickCount | - | number | No | Number of clicks. Must be an integer. |
| params | deltaX | - | number | No | Horizontal scroll distance, commonly used for `mouseWheel`. |
| params | deltaY | - | number | No | Vertical scroll distance, commonly used for `mouseWheel`. |
| params | pointerType | - | string | No | Pointer type. Currently only `mouse` is supported. When not passed, it is treated as `mouse`. |
| params | timestamp | - | number | No | Event timestamp. |
| params | modifiers | - | number | No | Keyboard modifier key bitmask. Must be an integer. |
| params | buttons | - | number | No | Mouse button bitmask when in pressed state at the time of event triggering. Must be an integer. When not passed, this field is treated as 0. For bit value descriptions, see the table below. |
| params | force | - | number | No | Pressing force. |
| params | tangentialPressure | - | number | No | Tangential pressure. |
| params | tiltX | - | number | No | Tilt angle of the pointer relative to the x-axis. |
| params | tiltY | - | number | No | Tilt angle of the pointer relative to the y-axis. |
| params | twist | - | number | No | Pointer rotation angle. Must be an integer. |

The bit values of `buttons` are as follows:

| Bit Value | Button State |
| ---- | ---- |
| 0 | No mouse button is in pressed state. |
| 1 | Left button is in pressed state. |
| 2 | Right button is in pressed state. |
| 4 | Middle button is in pressed state. |
| 8 | Back button is in pressed state. |
| 16 | Forward button is in pressed state. |

When multiple buttons are in pressed state simultaneously, perform a bitwise OR on the corresponding bit values. For example, `3` indicates that the left and right buttons are in pressed state simultaneously, and `5` indicates that the left and middle buttons are in pressed state simultaneously. `buttons` represents all buttons in pressed state at the time of event triggering, while `button` represents the single button corresponding to this event. The current implementation only reads the five button bits listed above and does not additionally validate the mask range; other bits are not mapped to mouse button states.

> **NOTE**
>
> - When `type`, `x`, or `y` is missing, a parameter missing result is returned.
> - When the field type is incorrect, the `type` value is unsupported, the `button` value is unsupported, or `pointerType` is not `mouse`, a parameter error result is returned.
> - The fields listed in the Input Parameter Description are public parameters that the current implementation validates and dispatches. Whether a parameter produces observable page behavior depends on the event type, the target element state, and how the page script/browser input pipeline processes the field.
> - Fields not listed in the Input Parameter Description are not treated as public parameters of this command.

### Return Description

Returns `{"code":10,"message":"success"}` on successful command execution.

Failure results are as follows:

| Error Code | Trigger Condition |
| ---- | ---- |
| 110 | `params` is missing or is not an Object. |
| 132 | browser or browser host is empty. |
| 350 | Failed to deliver the mouse event command. |
| 391 | A mandatory parameter is missing, or `type` is an empty string. |
| 392 | Apart from the case described in 391, the type or value of a field listed in the input parameter description does not meet the constraints; among them, `pointerType` only supports `mouse`. |

### Response Example

Returns on Success

```json
{
  "code": 10,
  "message": "success"
}
```

Returns on Parameter Error

```json
{
  "code": 392,
  "message": "pointerType must be mouse"
}
```

## dispatchKeyEvent

Injects a keyboard event.

### DispatchKeyEventCommand

```json
{
  "method": "dispatchKeyEvent",
  "params": {
    "type": "keyDown",
    "key": "A",
    "code": "KeyA",
    "windowsVirtualKeyCode": 65
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `dispatchKeyEvent`. |
| params | - | - | Object | Yes | Command parameter. |
| params | type | - | string | Yes | Keyboard event type. Supports `keyDown`, `keyUp`, `rawKeyDown`, and `char`. |
| params | text | - | string | No | Text generated by the event. |
| params | unmodifiedText | - | string | No | Text without modifier key effects. |
| params | key | - | string | No | Key value. |
| params | code | - | string | No | Physical key code. |
| params | timestamp | - | number | No | Event timestamp. |
| params | modifiers | - | number | No | Keyboard modifier key bitmask. Must be an integer. |
| params | windowsVirtualKeyCode | - | number | No | Compatible virtual key code, used to describe the logical key. Must be an integer. |
| params | nativeVirtualKeyCode | - | number | No | Platform native virtual key code. Must be an integer. |
| params | location | - | number | No | Key location. Must be an integer. |
| params | autoRepeat | - | boolean | No | Whether it is an auto-repeat key. |
| params | isKeypad | - | boolean | No | Whether it is from the numeric keypad. |
| params | isSystemKey | - | boolean | No | Whether it is a system key. |
| params | isForwarded | - | boolean | No | Whether it is a forwarded event. |
| params | commands | - | Array\<string> | No | List of editing commands. |

> **NOTE**
>
> - When `type` is missing, a parameter missing result is returned.
> - When the field type is incorrect or the `type` value is not supported, a parameter error result is returned.
> - The fields listed in the input parameter description are public parameters that the current implementation validates and dispatches. Whether a parameter produces observable page behavior depends on the event type, the target element state, and how the page script or browser input pipeline processes the field.
> - Fields not listed in the input parameter description are not treated as public parameters of this command.

### Return Description

Returns `{"code":10,"message":"success"}` on successful command execution.

Failure results are as follows:

| Error Code | Trigger Condition |
| ---- | ---- |
| 110 | `params` is missing or is not an Object. |
| 132 | browser or browser host is empty. |
| 350 | Failed to deliver the keyboard event command. |
| 391 | `type` is missing or is an empty string. |
| 392 | Apart from the case described in 391, the type or value of a field listed in the input parameter description does not meet the constraints; `commands` not being an array or containing non-string members also falls under this error. |

### Response Example

Returns on Success

```json
{
  "code": 10,
  "message": "success"
}
```

Returns on Parameter Error

```json
{
  "code": 392,
  "message": "invalid key event type"
}
```

## input

Sets the value of the specified `input` element. This command replaces the current content of the input box rather than appending to the original content.

### InputCommand

Locate the target input box by XPath:

```json
{
  "method": "input",
  "params": {
    "xpath": "//input[@id='username']",
    "type": "text",
    "value": "ArkWeb"
  }
}
```

Locate the target input box by node identifier:

```json
{
  "method": "input",
  "params": {
    "id": "frameToken|documentToken|12",
    "type": "text",
    "value": "ArkWeb"
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, which is fixed to `input`. |
| params | - | - | Object | Yes | Command parameter. |
| params | xpath | - | string | No | XPath of the target `input` element. Either this or `id`. |
| params | id | - | string | No | Node identifier returned by [getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom) or [getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom). Either this or `xpath`. This value is not the HTML `id` attribute. |
| params | type | - | string | Yes | Input box type. Supports `default`, `text`, `password`, `email`, `url`, `tel`, `search`, `number`, `date`, `datetime-local`, `month`, `range`, `time`, and `week`. |
| params | value | - | string | Yes | New value to set. |

> **NOTE**
>
> - Either `id` or `xpath` must be selected. They cannot be passed at the same time.
> - When `type` is `default`, the passed type is not precisely matched against the actual type of the target input box, but the target element must still be an `input` element that can be set with a string value.
> - When `type` is not `default`, the passed type must match the actual type of the target input box.
> - `value` must meet the value format requirements of the target input box type.

### Return Description

Returns `{"code":10,"message":"success"}` on successful command execution.

The following are failure results:

| Error Code | Trigger Condition |
| ---- | ---- |
| 11 | Input command execution timed out, or the execution object on the renderer side is unavailable. |
| 110 | `params` is missing or is not an Object. |
| 131 | XPath did not match any element, or the frame, document, or DOM node corresponding to the node identifier has become invalid. |
| 132 | The browser or browser host is empty. |
| 160 | The main frame is invalid, the frame is not ready, or the renderer communication channel is not ready. |
| 161 | The located target element is not an `input` element. |
| 201 | `value` is passed but is not a string. |
| 202 | `type` is a non-empty string but not in the supported range, or the actual type of the target `input` element does not support setting a string value. |
| 203 | `value` does not meet the value format requirements of the actual type of the target `input` element. |
| 204 | `type` is not `default` and does not match the actual type of the target `input` element. |
| 391 | A locator parameter, `type`, or `value` is missing; this error also applies when `type` is an empty string. |
| 392 | Other than the cases described in 391, the type, combination, or format of the locator parameters does not comply with the input parameter description, or `type` is not a string. |

### Response Example

Returns on Success

```json
{
  "code": 10,
  "message": "success"
}
```

Returns when an unsupported input box type is passed

```json
{
  "code": 202,
  "message": "unsupported input type"
}
```

Returns when both `id` and `xpath` are passed

```json
{
  "code": 392,
  "message": "id and xpath are mutually exclusive"
}
```

## scroll

Scrolls the page by viewport coordinates or node identifier. When using a node identifier, the command scrolls to the target element's position.

### ScrollCommand

```json
{
  "method": "scroll",
  "params": {
    "x": 400,
    "y": 200,
    "deltaX": 0,
    "deltaY": -200,
    "speed": 1000
  }
}
```

Scroll by node identifier:

```json
{
  "method": "scroll",
  "params": {
    "id": "frameToken|documentToken|12",
    "deltaY": -200
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `scroll`. |
| params | - | - | Object | Yes | Command parameter. |
| params | - | id | string | No | Node identifier returned by [getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom) or [getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom). Mutually exclusive with `x` and `y`. When `id` is passed, `x` or `y` cannot be passed at the same time. This value is not the HTML `id` attribute. |
| params | - | x | number | No | Mutually exclusive with `id`. The mouse X coordinate at which the wheel event is triggered. Viewport coordinate system, with the origin (0, 0) at the top-left corner, increasing to the right, in CSS pixels. Returns `{"code":391}` when missing. If the coordinate falls inside a scrollable element, that element is scrolled; if it falls on a blank area of the page, the page root is scrolled. |
| params | - | y | number | No | Mutually exclusive with `id`. The mouse Y coordinate at which the wheel event is triggered. Viewport coordinate system, with the origin (0, 0) at the top-left corner, increasing downward, in CSS pixels. Returns `{"code":391}` when missing. If the coordinate falls inside a scrollable element, that element is scrolled; if it falls on a blank area of the page, the page root is scrolled. |
| params | - | deltaX | number | No | Horizontal wheel event delta. A negative value scrolls the page to the right (revealing content on the right, i.e., `scrollLeft` increases), and a positive value scrolls the page to the left (revealing content on the left, i.e., `scrollLeft` decreases). In CSS pixels. When not passed, defaults to 0 (no horizontal scrolling). |
| params | - | deltaY | number | No | Vertical wheel event delta. A negative value scrolls the page downward (revealing content below, i.e., `scrollTop` increases), and a positive value scrolls the page upward (revealing content above, i.e., `scrollTop` decreases). In CSS pixels. When not passed, defaults to 0 (no vertical scrolling). |
| params | - | speed | number | No | Scroll speed. Must be an integer. Value range [-2147483648, 2147483647]: a negative value immediately reaches the target position without scroll animation; 0 returns `{"code":392}`; a positive value performs scroll animation at the specified speed. When not passed, defaults to 800. |

> **NOTE**
>
> - `id` is mutually exclusive with `x` and `y`.
> - When `id` is not passed, both `x` and `y` must be passed.
> - The `scroll` command operates in fire-and-forget mode. The result is returned immediately after the command is sent successfully, without waiting for the gesture to complete.
> - Consecutive scroll commands are queued and executed sequentially by the Chromium gesture controller, and no commands are lost.
> - The final scroll distance may have a slight deviation (usually less than 1 pixel) due to floating-point rounding.

### Return Description

Returns `{"code":10,"message":"success"}` on successful command execution; returns an error code JSON on failure. Common error codes are listed in the following table:

| Error Code | Trigger Condition |
| ---- | ---- |
| 110 | The `params` field is not a JSON object. |
| 130 | Timeout when resolving the target element position via `id`. |
| 131 | Failed to resolve the target element position via `id`, the element does not exist, or the element has no valid rectangle. |
| 132 | The browser or host is empty, usually indicating that the Web instance is unavailable. |
| 350 | Failed to deliver the scroll command. |
| 391 | The required parameter `x` or `y` is missing when `id` is not passed. |
| 392 | The `id` is invalid, the value or type of `x`/`y`/`deltaX`/`deltaY`/`speed` is invalid (for example, `speed=0`), or both `id` and `x`/`y` are passed. |

### Request Example

```json
{
  "method": "scroll",
  "params": {
    "x": 180,
    "y": 320,
    "deltaY": -300
  }
}
```

Scroll by node identifier:

```json
{
  "method": "scroll",
  "params": {
    "id": "frameToken|documentToken|12",
    "deltaY": -300
  }
}
```

### Response Example

Success:

```json
{
  "code": 10,
  "message": "success"
}
```

Failure:

`391` (id not passed and coordinates not passed):

```json
{
  "code": 391,
  "message": "missing id or x/y"
}
```

`391` (the coordinate path is missing the required parameter `x` or `y`):

```json
{
  "code": 391,
  "message": "missing x or y"
}
```

`392` (`speed` value or type is invalid, for example `speed=0`):

```json
{
  "code": 392,
  "message": "invalid param: speed"
}
```

Returned when `id` and coordinates are passed simultaneously:

```json
{
  "code": 392,
  "message": "id is mutually exclusive with x/y"
}
```

## select

Selects the specified `<select>` element option. Locates the `<select>` element by XPath or node identifier, and selects the `<option>` element by index or value.

### SelectCommand

```json
{
  "method": "select",
  "params": {
    "xpath": "//select[@id='country']",
    "indexes": [2]
  }
}
```

Locate the select element by node identifier:

```json
{
  "method": "select",
  "params": {
    "id": "frameToken|documentToken|12",
    "values": ["us"]
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed to `select`. |
| params | - | - | Object | Yes | Command parameter. |
| params | - | xpath | string | No | XPath 1.0 expression, matches the first node. Choose one between this and `id`. |
| params | - | id | string | No | Node identifier returned by [getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom) or [getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom). Choose one between this and `xpath`. This value is not the HTML `id` attribute. |
| params | - | indexes | Array\<number\> | No | Index list of `<option>` child elements. Array items must be integers, starting from 0, corresponding to `<option>` child elements under `<select>` in DOM order (excluding `<optgroup>` level offset). At least one of `indexes` and `values` must be provided. If neither is provided, `{"code":251}` is returned. When both are provided, `indexes` takes precedence. |
| params | - | values | Array\<string\> | No | List of `value` attribute values of `<option>` elements. Iterates through all `<option>` child elements of `<select>` and compares `option.value` with the passed values. At least one of `indexes` and `values` must be provided. If neither is provided, `{"code":251}` is returned. When both are provided, `indexes` takes precedence. |

> **NOTE**
>
> - Either `id` or `xpath` must be selected; they cannot be passed at the same time.
> - Members with mismatched types in the `indexes` or `values` array are ignored.
> - If the XPath expression is invalid or does not match any target element, it is treated as target element not found.
> - If the selected option includes a disabled item, `{"code":255}` is returned.
> - For a multi-select element (`<select multiple>`), multiple indexes can be passed. For a single-select element, passing multiple indexes returns an error.

### Return Description

Returns `{"code":10,"message":"success"}` on success; returns an error code JSON on failure. For common error codes, see the table below:

| Error Code | Trigger Condition |
| ---- | ---- |
| 110 | The `params` field is not a JSON object. |
| 115 | Neither `id` nor `xpath` locator parameter is provided. |
| 131 | Target element does not exist. |
| 132 | browser or host is empty, usually indicating that the Web instance is unavailable. |
| 161 | Target element is not a `<select>` element. |
| 251 | Neither `indexes` nor `values` is provided, or they are not arrays, or no valid items after parsing. |
| 252 | `indexes` index out of bounds (less than 0 or greater than or equal to the number of options). |
| 253 | Values in `values` have no match in the option list. |
| 254 | Multiple indexes passed for a single-select `<select>`. |
| 255 | Selected option is disabled. |
| 256 | `<select>` element has no option child elements. |
| 392 | Both `id` and `xpath` are passed, or the `id`/`xpath` field is not a string or is an empty string. |

### Request Example

```json
{
  "method": "select",
  "params": {
    "xpath": "//select[@id='country']",
    "indexes": [1, 3]
  }
}
```

Select an option by node identifier:

```json
{
  "method": "select",
  "params": {
    "id": "frameToken|documentToken|12",
    "values": ["us"]
  }
}
```

### Response Example

Success:

```json
{
  "code": 10,
  "message": "success"
}
```

Failure:

`115` (neither `id` nor `xpath` locator parameter provided):

```json
{
  "code": 115,
  "message": "missing or empty xpath"
}
```

`392` (`xpath` is an empty string):

```json
{
  "code": 392,
  "message": "invalid id or xpath"
}
```

`131` (Target element does not exist):

```json
{
  "code": 131,
  "message": "select command failed"
}
```

`161` (Target element is not a `<select>` element):

```json
{
  "code": 161,
  "message": "select command failed"
}
```

`251` (Neither `indexes` nor `values` is provided):

```json
{
  "code": 251,
  "message": "both indexes and values are empty"
}
```

`252` (Index out of bounds):

```json
{
  "code": 252,
  "message": "select command failed"
}
```

`255` (The selected option is disabled):

```json
{
  "code": 255,
  "message": "select command failed"
}
```

Returns when both `id` and `xpath` are passed:

```json
{
  "code": 392,
  "message": "id and xpath are mutually exclusive"
}
```

## uploadFile

Sets the file path for input[type=file] elements. Locates elements via XPath, and supports setting single or multiple file paths.

### UploadFileCommand

```json
{
  "method": "uploadFile",
  "params": {
    "xpath": "//input[@type='file']",
    "files": ["/data/local/tmp/test.pdf"]
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed to `uploadFile`. |
| params | - | - | Object | Yes | Command parameter. |
| params | - | xpath | string | Yes | XPath 1.0 locator expression, matching the first node. Returns `{"code":391}` when missing or is an empty string. |
| params | - | files | Array\<string\> | Yes | List of absolute file paths. Paths are normalized. Returns `{"code":372}` when missing or is an empty array. Array elements must be non-empty strings; empty strings return `{"code":371}`. |

> **NOTE**
>
> - File paths are normalized (symbolic links resolved). Returns `{"code":370,"message":"failed to resolve file path: <path>"}` when the path cannot be resolved.
> - Path existence and readability are non-blocking warnings and do not affect command execution. Warning information is appended to the `message` field in the format `"success; warnings: <path>: <reason>"`.
> - When `xpath` matches a non-`input[type=file]` element, the upload is rejected and `{"code":352,"message":"upload target is not file input"}` is returned.

### Return Description

Returns `{"code":10,"message":"success"}` on successful command execution (warning information is appended to the `message` field when non-blocking warnings exist); returns an error code JSON on failure. Common error codes are listed in the table below:

| Error Code | Trigger Condition |
| ---- | ---- |
| 110 | The `params` field is not a JSON object. |
| 131 | The element matching `xpath` does not exist, or the DOM search yields no result. |
| 132 | browser or host is empty, usually indicating that the Web instance is unavailable. |
| 350 | File upload command delivery failed. |
| 351 | File upload channel initialization failed. |
| 352 | File upload execution failed (including when `xpath` matches a non-`<input type='file'>` element and the upload is rejected). |
| 353 | Element search response parsing failed. |
| 370 | File path cannot be resolved (including path traversal component `..`). |
| 371 | File path is an empty string. |
| 372 | File list is empty or not provided. |
| 391 | `xpath` is missing or is an empty string. |

### Request Example

```json
{
  "method": "uploadFile",
  "params": {
    "xpath": "//input[@type='file' and @name='upload']",
    "files": ["/data/local/tmp/file1.pdf", "/data/local/tmp/file2.pdf"]
  }
}
```

### Response Example

On success:

```json
{
  "code": 10,
  "message": "success"
}
```

On success with warnings:

```json
{
  "code": 10,
  "message": "success; warnings: /path/file.pdf: path does not exist"
}
```

On failure:

`131` (the element matched by `xpath` does not exist):

```json
{
  "code": 131,
  "message": "element not found"
}
```

`352` (`xpath` matched to a non-`<input type='file'>` element):

```json
{
  "code": 352,
  "message": "upload target is not file input"
}
```

`370` (file path cannot be resolved):

```json
{
  "code": 370,
  "message": "failed to resolve file path: /data/local/tmp/missing.pdf"
}
```

`371` (file path is an empty string):

```json
{
  "code": 371,
  "message": "file path is empty"
}
```

`372` (file list is empty or not provided):

```json
{
  "code": 372,
  "message": "files list is empty"
}
```

`391` (missing `xpath` or is an empty string):

```json
{
  "code": 391,
  "message": "missing param: xpath"
}
```

## setZoomLevel

Sets the zoom level of the current web page. This command is equivalent to the user manually zooming with CTRL+Wheel, scaling the entire web page (CSS page zoom). The zoom level is persisted to the Chromium HostZoomMap and shares storage with manual zoom.

### SetZoomLevelCommand

```json
{
  "method": "setZoomLevel",
  "params": {
    "zoomLevel": 1.5
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed to `setZoomLevel`. |
| params | - | - | Object | Yes | Command parameter. |
| params | - | zoomLevel | number | Yes | Web page zoom level. 1.0 indicates 100% (original size), 2.0 indicates 200%, and 0.5 indicates 50%. Value range: [0.25, 5.0]. |

> **NOTE**
>
> - When the app disables zoom via [zoomControlAccess](./arkts-basic-components-web-attributes.md#zoomcontrolaccess22), this command returns `{"code":482}`.
> - When `zoomLevel` is a non-numeric type (string, array, object, or null), it is treated uniformly as a missing field, and `{"code":391}` is returned.
> - NaN, Infinity, and -Infinity are not valid JSON values and will be rejected at the JSON parsing stage, so they will not enter this command.

### Return Description

Returns `{"code":10,"message":"success"}` on successful command execution; returns an error code JSON on failure. Common error codes are listed in the table below:

| Error Code | Trigger Condition |
| ---- | ---- |
| 110 | The `params` field is not a JSON object. |
| 132 | browser or host is empty, usually indicating that the Web instance is unavailable. |
| 391 | `zoomLevel` is missing or is a non-numeric type (string, array, object, null). |
| 480 | The value exceeds the range `[0.25, 5.0]`, and the page zoom ratio remains unchanged. |
| 481 | The value is invalid, such as a negative number, zero, or NaN, and the page zoom ratio remains unchanged. |
| 482 | The app has disabled zoom control (`zoomControlAccess=false`), and the page zoom ratio remains unchanged. |

### Test Page

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
  <body>
    <h1>Zoom Level Demo</h1>
    <p>The current zoom level can be queried via getZoomLevel and modified via setZoomLevel.</p>
  </body>
</html>
```

### Request Example

```json
{
  "method": "setZoomLevel",
  "params": {
    "zoomLevel": 1.5
  }
}
```

### Response Example

On success (page zoomed to 150%):

```json
{
  "code": 10,
  "message": "success"
}
```

On failure:

`391` (missing `zoomLevel` or not a numeric type):

```json
{
  "code": 391,
  "message": "missing param: zoomLevel"
}
```

`480` (value out of range `[0.25, 5.0]`, page zoom ratio unchanged):

```json
{
  "code": 480,
  "message": "zoom level out of range"
}
```

`481` (invalid value, e.g., negative or zero, page zoom level unchanged):

```json
{
  "code": 481,
  "message": "zoom level invalid"
}
```

`482` (app disabled zoom control, page zoom level unchanged):

```json
{
  "code": 482,
  "message": "zoom control is disabled"
}
```
<!--no_check-->