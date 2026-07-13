# OnOverrideErrorPageCallback

```TypeScript
type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string
```

The callback of onOverrideErrorPage.

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errorPageEvent | OnErrorReceiveEvent | 是 | The information of error. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Return an HTML text content encoded in Base64. |

