# OnWindowNewExtEvent

定义网页请求创建窗口时触发的回调信息，包括窗口特征信息和窗口打开方式。适用于需要精细控制新窗口行为的场景，提升窗口管理的定制性和用户体验。

**起始版本：** 23

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

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isAlert

```TypeScript
isAlert: boolean
```

true代表请求创建对话框，false代表请求创建新标签页。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isUserTrigger

```TypeScript
isUserTrigger: boolean
```

true代表用户触发，false代表非用户触发。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## navigationPolicy

```TypeScript
navigationPolicy: NavigationPolicy
```

网页请求用户创建新窗口时的窗口打开方式。

**类型：** [NavigationPolicy](arkts-arkweb-navigationpolicy-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## targetUrl

```TypeScript
targetUrl: string
```

请求的新窗口中需要打开的url。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## windowFeatures

```TypeScript
windowFeatures: WindowFeatures
```

网页请求创建的新窗口特征信息。

**类型：** [WindowFeatures](arkts-arkweb-windowfeatures-i.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
