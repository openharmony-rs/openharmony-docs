# OnOverrideErrorPageCallback

```TypeScript
export type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string
```

The callback of onOverrideErrorPage.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string--><!--Device-unnamed-export type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errorPageEvent | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The information of error.  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Return an HTML text content encoded in Base64. |

