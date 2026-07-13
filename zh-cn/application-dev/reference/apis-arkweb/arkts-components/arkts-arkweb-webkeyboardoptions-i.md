# WebKeyboardOptions

Defines the web keyboard options when onInterceptKeyboardAttach event return.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## customKeyboard

```TypeScript
customKeyboard?: CustomBuilder
```

Set the custom keyboard builder when the custom keyboard is used.

**类型：** CustomBuilder

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## enterKeyType

```TypeScript
enterKeyType?: number
```

Set the enter key type when the system keyboard is used, the "enter" key related to the {@link inputMethodEngine}.

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## useSystemKeyboard

```TypeScript
useSystemKeyboard: boolean
```

Whether the system keyboard is used.

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

