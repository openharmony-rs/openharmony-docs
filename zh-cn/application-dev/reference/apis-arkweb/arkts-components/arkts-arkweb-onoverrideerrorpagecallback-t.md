# OnOverrideErrorPageCallback

```TypeScript
type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string
```

onOverrideErrorPage的回调函数，网页加载失败时触发。

**起始版本：** 20

<!--Device-unnamed-type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string--><!--Device-unnamed-type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errorPageEvent | [OnErrorReceiveEvent](arkts-arkweb-onerrorreceiveevent-i.md) | 是 | 网页加载遇到错误时返回的相关信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回以Base64编码的HTML文本内容。 |

