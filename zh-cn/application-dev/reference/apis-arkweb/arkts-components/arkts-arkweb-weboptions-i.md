# WebOptions

通过[接口](../../../reference/apis-arkweb/arkts-basic-components-web.md#接口)定义Web选项，包括网页资源地址、控制器、渲染方式等。

**起始版本：** 8

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## controller

```TypeScript
controller: WebController | WebviewController
```

控制器，通过controller可以控制Web组件各种行为，包括页面导航、生命周期状态、JavaScript交互等。从API version 9开始，WebController不再维护，建议使用 [WebviewController](arkts-arkweb-webviewcontroller-t.md)替代。

**类型：** [WebController](arkts-arkweb-webcontroller-c.md) \| [WebviewController](arkts-arkweb-webviewcontroller-t.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## emulateTouchFromMouseEvent

```TypeScript
emulateTouchFromMouseEvent? : boolean
```

设定鼠标事件是否转换为触摸事件。true表示转换成触摸事件，适用于需要统一触摸和鼠标交互行为的场景；false表示不转换成触摸事件。默认值：false。

**类型：** boolean

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## incognitoMode

```TypeScript
incognitoMode? : boolean
```

表示当前创建的Webview是否是隐私模式。true表示创建隐私模式，false表示创建正常模式。默认值：false。传入undefined或null时为false。<!--RP1--><!--RP1End-->

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## renderMode

```TypeScript
renderMode? : RenderMode
```

表示当前Web组件的渲染方式，`RenderMode.ASYNC_RENDER`表示Web组件异步渲染，`RenderMode.SYNC_RENDER`表示Web组件同步渲染，默认值 `RenderMode.ASYNC_RENDER`，该模式不支持动态调整。

**类型：** [RenderMode](arkts-arkweb-rendermode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## sharedRenderProcessToken

```TypeScript
sharedRenderProcessToken? : string
```

表示当前Web组件指定共享渲染进程的token，多渲染进程模式下，相同token的Web组件会优先尝试复用绑定的渲染进程。绑定发生在渲染进程的初始化阶段。当渲染进程没有关联的Web组件时，其绑定关系将被移除。默认值： ""。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## src

```TypeScript
src: string | Resource
```

网页资源地址。如果访问本地资源文件，请使用resource协议或\$rawfile资源引用。如果加载应用包外沙箱路径的本地资源文件（文件支持html和txt类型），请使用file://沙箱文件路径。src不能通过状态变量（例如：@State）动态更改地址，如需更改，请通过[loadUrl()](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#loadurl)重新加载。

**类型：** string \| Resource

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
