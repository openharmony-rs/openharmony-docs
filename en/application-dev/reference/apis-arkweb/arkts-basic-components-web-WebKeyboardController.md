# Class (WebKeyboardController)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=97514042d8acb624815178d3627a209c868aad1f translatedAt=2026-08-07T04:39:27.070Z pushedAt=2026-08-07T08:12:44.202Z -->

WebKeyboardController is a controller class provided by ArkWeb for controlling the custom keyboard behavior of the Web component. When an input field on a web page needs to display a keyboard, developers can intercept the mounting of the system default keyboard through the [onInterceptKeyboardAttach](./arkts-basic-components-web-events.md#oninterceptkeyboardattach12) event, and use WebKeyboardController to perform operations such as inserting characters, forward/backward deletion, sending function keys like Enter, and closing the custom keyboard on the currently focused web input field. This class is suitable for apps that need to implement custom secure keyboards, emoji keyboards, handwriting keyboards, or business-specific input panels for web scenarios, enabling developers to fully take over the keyboard input logic of web input fields.

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## constructor<sup>12+</sup>

constructor()

Constructs a **WebKeyboardController** API.

**System capability**: SystemCapability.Web.Webview.Core

## insertText<sup>12+</sup>

insertText(text: string): void

Inserts characters into the **Web** component text box.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | -------- | ---- | --------------------- |
| text | string | Yes | Text inserted into the web input box at the current cursor position. If there is selected text, it is replaced with this text. An input event is triggered. The cursor moves to the end of the inserted text. |

## deleteForward<sup>12+</sup>

deleteForward(length: number): void

Deletes a specified length of characters before the cursor.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description                                                                                                  |
| ------ | -------- | ---- |------------------------------------------------------------------------------------------------------|
| length | number | Yes | Deletes a specified length of characters before the cursor.<br>Value range: [-2147483648, 2147483647]. When the parameter value is greater than the character length, all characters before the cursor are deleted by default. When the parameter value is negative, no deletion is performed. |

## deleteBackward<sup>12+</sup>

deleteBackward(length: number): void

Deletes a specified length of characters after the cursor.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description                |
| ------ | -------- | ---- | ------------------------ |
| length | number | Yes | Number of characters to delete after the cursor.<br>Value range: [-2147483648, 2147483647]. If the parameter value is greater than the character length, all characters after the cursor are deleted by default. If the parameter value is negative, no deletion is performed. |

## sendFunctionKey<sup>12+</sup>

sendFunctionKey(key: number): void

Inserts a function key. Currently, only the Enter key type is supported. For details about the value, see [EnterKeyType](../apis-ime-kit/js-apis-inputmethod.md#enterkeytype10).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description                                  |
| ------ | -------- | ---- | ------------------------------------------ |
| key    | number   | Yes   | Type of the function key. Only the Enter key is supported. |

## close<sup>12+</sup>

close(): void

Closes this custom keyboard.

**System capability**: SystemCapability.Web.Webview.Core
<!--no_check-->