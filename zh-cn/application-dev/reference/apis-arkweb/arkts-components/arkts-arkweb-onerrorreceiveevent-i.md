# OnErrorReceiveEvent

定义网页加载遇到错误时触发的回调信息，包括请求和错误详情。适用于需要监控和处理网页加载错误的场景，提升错误处理的及时性和用户体验。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## error

```TypeScript
error: WebResourceError
```

网页加载资源错误的封装信息。

**类型：** [WebResourceError](arkts-arkweb-webresourceerror-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## request

```TypeScript
request: WebResourceRequest
```

网页请求的封装信息。

**类型：** [WebResourceRequest](arkts-arkweb-webresourcerequest-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
