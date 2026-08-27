# OnBeforeUnloadEvent

定义刷新或关闭场景下，在即将离开当前页面时触发此回调。适用于表单编辑等场景，允许开发者拦截离开动作并弹窗确认，从而避免用户未提交的数据意外丢失。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## isReload

```TypeScript
isReload?: boolean
```

页面是否刷新。当页面因刷新即将离开时，isReload为true；当页面因关闭即将离开时，isReload为false。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## message

```TypeScript
message: string
```

弹窗中显示的信息。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## result

```TypeScript
result: JsResult
```

通知Web组件用户操作行为。

**类型：** [JsResult](arkts-arkweb-jsresult-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

当前显示弹窗所在网页的URL。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
