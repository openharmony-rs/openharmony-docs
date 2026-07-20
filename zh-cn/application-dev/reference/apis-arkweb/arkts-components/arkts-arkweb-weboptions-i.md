# WebOptions

Defines the Web options.

**起始版本：** 12

<!--Device-unnamed-declare interface WebOptions--><!--Device-unnamed-declare interface WebOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## controller

```TypeScript
controller: WebController | WebviewController
```

Sets the controller of the Web.

**类型：** WebController \| WebviewController

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebOptions-controller: WebController | WebviewController--><!--Device-WebOptions-controller: WebController | WebviewController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## emulateTouchFromMouseEvent

```TypeScript
emulateTouchFromMouseEvent? : boolean
```

设定鼠标事件是否被转换成触摸事件。

默认值：false。

**类型：** boolean

**起始版本：** 22

<!--Device-WebOptions-emulateTouchFromMouseEvent? : boolean--><!--Device-WebOptions-emulateTouchFromMouseEvent? : boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## incognitoMode

```TypeScript
incognitoMode? : boolean
```

Sets the incognito mode of the Web, the parameter is optional and default value is false.When the Web is in incognito mode, cookies, records of websites, geolocation permissions will not save in persistent files.

**类型：** boolean

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-WebOptions-incognitoMode? : boolean--><!--Device-WebOptions-incognitoMode? : boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## renderMode

```TypeScript
renderMode? : RenderMode
```

Sets the render mode of the web.

**类型：** RenderMode

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebOptions-renderMode? : RenderMode--><!--Device-WebOptions-renderMode? : RenderMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## sharedRenderProcessToken

```TypeScript
sharedRenderProcessToken? : string
```

Sets the shared render process token of the web.When the web is in multiprocess mode, web with the same sharedRenderProcessToken will attempt to reuse the same render process.The shared render process will remain active until all associated web are destroyed.

**类型：** string

**起始版本：** 12

<!--Device-WebOptions-sharedRenderProcessToken? : string--><!--Device-WebOptions-sharedRenderProcessToken? : string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## src

```TypeScript
src: string | Resource
```

Sets the address of the web page to be displayed.

**类型：** string \| Resource

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebOptions-src: string | Resource--><!--Device-WebOptions-src: string | Resource-End-->

**系统能力：** SystemCapability.Web.Webview.Core

