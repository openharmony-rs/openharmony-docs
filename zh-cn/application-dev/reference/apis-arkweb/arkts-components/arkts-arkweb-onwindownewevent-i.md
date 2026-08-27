# OnWindowNewEvent

定义网页要求用户创建窗口时触发的回调。从API version 23开始，如需获取更多窗口信息，可使用[OnWindowNewExtEvent](arkts-arkweb-onwindownewextevent-i.md)。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## handler

```TypeScript
handler: ControllerHandler
```

用于设置新建窗口的WebviewController实例。

**类型：** [ControllerHandler](arkts-arkweb-controllerhandler-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isAlert

```TypeScript
isAlert: boolean
```

true代表请求创建对话框，false代表新标签页。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isUserTrigger

```TypeScript
isUserTrigger: boolean
```

true代表用户触发，false代表非用户触发。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## targetUrl

```TypeScript
targetUrl: string
```

目标url。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
