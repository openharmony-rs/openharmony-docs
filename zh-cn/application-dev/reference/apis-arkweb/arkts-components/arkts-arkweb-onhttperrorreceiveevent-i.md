# OnHttpErrorReceiveEvent

定义网页收到资源加载HTTP错误时触发的回调信息，包括请求和响应详情。适用于需要监控和处理HTTP错误的场景，提升网络错误诊断的准确性和用户体验。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## request

```TypeScript
request: WebResourceRequest
```

网页请求的封装信息。

**类型：** [WebResourceRequest](arkts-arkweb-webresourcerequest-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## response

```TypeScript
response: WebResourceResponse
```

资源响应的封装信息。

**类型：** [WebResourceResponse](arkts-arkweb-webresourceresponse-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
