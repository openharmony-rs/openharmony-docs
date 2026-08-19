# WebKeyboardController

Define the controller to interact with a custom keyboard, related to the onInterceptKeyboardAttach event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class WebKeyboardController--><!--Device-unnamed-export declare class WebKeyboardController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## close

```TypeScript
close(): void
```

Close the custom keyboard.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebKeyboardController-close(): void--><!--Device-WebKeyboardController-close(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebKeyboardController-constructor()--><!--Device-WebKeyboardController-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deleteBackward

```TypeScript
deleteBackward(length: int): void
```

Delete the specified length of characters in the Web input field from the beginning to the end.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebKeyboardController-deleteBackward(length: int): void--><!--Device-WebKeyboardController-deleteBackward(length: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | int | 是 | length of text, which will be deleted from front to back. |

## deleteForward

```TypeScript
deleteForward(length: int): void
```

Deletes the specified length of characters from the back to the front in the Web input field.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebKeyboardController-deleteForward(length: int): void--><!--Device-WebKeyboardController-deleteForward(length: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | int | 是 | length of text, which will be deleted from back to front. |

## insertText

```TypeScript
insertText(text: string): void
```

Insert characters in the Web input field.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebKeyboardController-insertText(text: string): void--><!--Device-WebKeyboardController-insertText(text: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | text which will be inserted. |

## sendFunctionKey

```TypeScript
sendFunctionKey(key: int): void
```

Send the function of the key.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebKeyboardController-sendFunctionKey(key: int): void--><!--Device-WebKeyboardController-sendFunctionKey(key: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | int | 是 | action indicates the "enter" key related to the [inputMethodEngine](../../apis-ime-kit/arkts-apis/arkts-inputmethodengine.md) |

