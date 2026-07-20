# OnBeforeUnloadEvent

Defines the triggered function when the web page wants to confirm navigation from JavaScript onbeforeunload.

**起始版本：** 12

<!--Device-unnamed-declare interface OnBeforeUnloadEvent--><!--Device-unnamed-declare interface OnBeforeUnloadEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isReload

```TypeScript
isReload?: boolean
```

页面是否刷新。<br>当页面因刷新即将离开时，isReload参数被设置为true；当页面因关闭即将离开时，isReload参数被设置为false。

**类型：** boolean

**起始版本：** 20

<!--Device-OnBeforeUnloadEvent-isReload?: boolean--><!--Device-OnBeforeUnloadEvent-isReload?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## message

```TypeScript
message: string
```

弹窗中显示的信息。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnBeforeUnloadEvent-message: string--><!--Device-OnBeforeUnloadEvent-message: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## result

```TypeScript
result: JsResult
```

通知Web组件用户操作行为。

**类型：** JsResult

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnBeforeUnloadEvent-result: JsResult--><!--Device-OnBeforeUnloadEvent-result: JsResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

当前显示弹窗所在网页的URL。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnBeforeUnloadEvent-url: string--><!--Device-OnBeforeUnloadEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

