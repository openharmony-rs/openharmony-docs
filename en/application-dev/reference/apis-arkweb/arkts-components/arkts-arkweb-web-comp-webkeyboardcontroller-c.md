# WebKeyboardController

```TypeScript
declare class WebKeyboardController
```

WebKeyboardController is a controller class provided by ArkWeb for controlling the custom keyboard behavior of the Web component. When an input field on a web page needs to display a keyboard, developers can intercept the mounting of the system default keyboard through the [onInterceptKeyboardAttach](arkts-arkweb-web-comp-attribute.md#oninterceptkeyboardattach) event, and use WebKeyboardController to perform operations such as inserting characters, forward/backward deletion, sending function keys like Enter, and closing the custom keyboard on the currently focused web input field. This class is suitable for apps that need to implement custom secure keyboards, emoji keyboards, handwriting keyboards, or business-specific input panels for web scenarios, enabling developers to fully take over the keyboard input logic of web input fields.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## close

```TypeScript
close(): void
```

Closes this custom keyboard.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **WebKeyboardController** API.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## deleteBackward

```TypeScript
deleteBackward(length: number): void
```

Deletes a specified length of characters after the cursor.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes | Number of characters to delete after the cursor.<br>Value range: [-2147483648, 2147483647]. If the parameter value is greater than the character length, all characters after the cursor are deleted by default. If the parameter value is negative, no deletion is performed. |

## deleteForward

```TypeScript
deleteForward(length: number): void
```

Deletes a specified length of characters before the cursor.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes | Deletes a specified length of characters before the cursor.<br>Value range: [-2147483648, 2147483647]. When the parameter value is greater than the character length, all characters before the cursor are deleted by default. When the parameter value is negative, no deletion is performed. |

## insertText

```TypeScript
insertText(text: string): void
```

Inserts characters into the **Web** component text box.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text inserted into the web input box at the current cursor position. If there is selected text, it is replaced with this text. An input event is triggered. The cursor moves to the end of the inserted text. |

## sendFunctionKey

```TypeScript
sendFunctionKey(key: number): void
```

Inserts a function key. Currently, only the Enter key type is supported. For details about the value, see [EnterKeyType](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod-enterkeytype-e.md).

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | number | Yes | Type of the function key. Only the Enter key is supported. |
