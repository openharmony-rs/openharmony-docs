# OnRefreshAccessedHistoryEvent

定义导航完成时触发。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame?: boolean
```

是否是主文档触发。
true表示是主文档触发，false表示不是主文档触发。

**类型：** boolean

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## isRefreshed

```TypeScript
isRefreshed: boolean
```

true表示该页面是被重新加载的（调用[refresh](../arkts-apis/arkts-arkweb-webviewcontroller-c.md#refresh-1)接口
），false表示该页面是新加载的。

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

访问的url。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

