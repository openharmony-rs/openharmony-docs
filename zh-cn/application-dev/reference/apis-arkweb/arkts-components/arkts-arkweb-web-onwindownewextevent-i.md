# OnWindowNewExtEvent

Defines the triggered callback when web page requires the user to create a window.

**起始版本：** 23

<!--Device-unnamed-declare interface OnWindowNewExtEvent--><!--Device-unnamed-declare interface OnWindowNewExtEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: ControllerHandler
```

Lets you set the WebviewController instance for creating a new window.

**类型：** ControllerHandler

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OnWindowNewExtEvent-handler: ControllerHandler--><!--Device-OnWindowNewExtEvent-handler: ControllerHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isAlert

```TypeScript
isAlert: boolean
```

true indicates the request to create a dialog and false indicates a new tab.

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OnWindowNewExtEvent-isAlert: boolean--><!--Device-OnWindowNewExtEvent-isAlert: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isUserTrigger

```TypeScript
isUserTrigger: boolean
```

true indicates that it is triggered by the user, and false indicates that it is triggered by a non-user.

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OnWindowNewExtEvent-isUserTrigger: boolean--><!--Device-OnWindowNewExtEvent-isUserTrigger: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## navigationPolicy

```TypeScript
navigationPolicy: NavigationPolicy
```

The navigation policy causing the new web view to be created.

**类型：** NavigationPolicy

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OnWindowNewExtEvent-navigationPolicy: NavigationPolicy--><!--Device-OnWindowNewExtEvent-navigationPolicy: NavigationPolicy-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## targetUrl

```TypeScript
targetUrl: string
```

Destination URL.

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OnWindowNewExtEvent-targetUrl: string--><!--Device-OnWindowNewExtEvent-targetUrl: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## windowFeatures

```TypeScript
windowFeatures: WindowFeatures
```

Contains the attributes that a webpage requests from its containing web view, the parameters of window.open.

**类型：** WindowFeatures

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OnWindowNewExtEvent-windowFeatures: WindowFeatures--><!--Device-OnWindowNewExtEvent-windowFeatures: WindowFeatures-End-->

**系统能力：** SystemCapability.Web.Webview.Core

