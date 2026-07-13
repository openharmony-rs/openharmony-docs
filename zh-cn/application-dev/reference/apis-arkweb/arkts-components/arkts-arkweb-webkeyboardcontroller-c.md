# WebKeyboardController

Define the controller to interact with a custom keyboard, related to the {@link onInterceptKeyboardAttach} event.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## close

```TypeScript
close(): void
```

Close the custom keyboard.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## deleteBackward

```TypeScript
deleteBackward(length: number): void
```

Delete text from front to back.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | length of text, which will be deleted from front to back. |

## deleteForward

```TypeScript
deleteForward(length: number): void
```

Delete text from back to front.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | length of text, which will be deleted from back to front. |

## insertText

```TypeScript
insertText(text: string): void
```

Insert text into Editor.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | text which will be inserted. |

## sendFunctionKey

```TypeScript
sendFunctionKey(key: number): void
```

Send the function of the key.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | number | 是 | action indicates the "enter" key related to the {@link inputMethodEngine} |

