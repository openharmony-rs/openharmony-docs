# WebKeyboardCallback

```TypeScript
type WebKeyboardCallback = (keyboardCallbackInfo: WebKeyboardCallbackInfo) => WebKeyboardOptions
```

The callback of onInterceptKeyboardAttach event.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyboardCallbackInfo | WebKeyboardCallbackInfo | 是 | callback information of onInterceptKeyboardAttach. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WebKeyboardOptions | Return the web keyboard options of this web component. |

