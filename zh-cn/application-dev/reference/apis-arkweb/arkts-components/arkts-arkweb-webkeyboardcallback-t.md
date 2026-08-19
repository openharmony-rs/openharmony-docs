# WebKeyboardCallback

```TypeScript
type WebKeyboardCallback = (keyboardCallbackInfo: WebKeyboardCallbackInfo) => WebKeyboardOptions
```

拦截网页可编辑元素拉起软键盘的回调，一般在点击网页input标签时触发。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type WebKeyboardCallback = (keyboardCallbackInfo: WebKeyboardCallbackInfo) => WebKeyboardOptions--><!--Device-unnamed-type WebKeyboardCallback = (keyboardCallbackInfo: WebKeyboardCallbackInfo) => WebKeyboardOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyboardCallbackInfo | [WebKeyboardCallbackInfo](arkts-arkweb-webkeyboardcallbackinfo-i.md) | 是 | 拦截网页拉起软键盘回调通知的入参，其中包括WebKeyboardController、可 编辑元素的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebKeyboardOptions](arkts-arkweb-webkeyboardoptions-i.md) | 回调函数通过返回[WebKeyboardOptions]{ |

