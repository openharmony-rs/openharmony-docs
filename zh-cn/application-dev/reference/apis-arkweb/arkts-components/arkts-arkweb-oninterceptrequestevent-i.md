# OnInterceptRequestEvent

定义Web组件加载URL之前触发的回调信息，包括请求详情。适用于需要拦截或修改网络请求的场景，提升请求控制的灵活性和安全性。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare interface OnInterceptRequestEvent--><!--Device-unnamed-declare interface OnInterceptRequestEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## request

```TypeScript
request: WebResourceRequest
```

url请求的相关信息。

**类型：** [WebResourceRequest](arkts-arkweb-webresourcerequest-c.md)

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnInterceptRequestEvent-request: WebResourceRequest--><!--Device-OnInterceptRequestEvent-request: WebResourceRequest-End-->

**系统能力：** SystemCapability.Web.Webview.Core

