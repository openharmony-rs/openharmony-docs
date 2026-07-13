# OnWindowNewEvent

定义网页要求用户创建窗口时触发的回调。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: ControllerHandler
```

Lets you set the WebviewController instance for creating a new window.

**类型：** ControllerHandler

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isAlert

```TypeScript
isAlert: boolean
```

true indicates the request to create a dialog and false indicates a new tab.

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isUserTrigger

```TypeScript
isUserTrigger: boolean
```

true indicates that it is triggered by the user, and false indicates that it is triggered by a non-user.

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## targetUrl

```TypeScript
targetUrl: string
```

Destination URL.

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

