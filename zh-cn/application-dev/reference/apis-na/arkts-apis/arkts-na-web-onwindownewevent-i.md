# OnWindowNewEvent

Defines the triggered callback when web page requires the user to create a window.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface OnWindowNewEvent--><!--Device-unnamed-export declare interface OnWindowNewEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: ControllerHandler
```

Lets you set the WebviewController instance for creating a new window.

**类型：** [ControllerHandler](arkts-na-web-controllerhandler-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-OnWindowNewEvent-handler: ControllerHandler--><!--Device-OnWindowNewEvent-handler: ControllerHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isAlert

```TypeScript
isAlert: boolean
```

true indicates the request to create a dialog and false indicates a new tab.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-OnWindowNewEvent-isAlert: boolean--><!--Device-OnWindowNewEvent-isAlert: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isUserTrigger

```TypeScript
isUserTrigger: boolean
```

true indicates that it is triggered by the user, and false indicates that it is triggered by a non-user.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-OnWindowNewEvent-isUserTrigger: boolean--><!--Device-OnWindowNewEvent-isUserTrigger: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## targetUrl

```TypeScript
targetUrl: string
```

Destination URL.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-OnWindowNewEvent-targetUrl: string--><!--Device-OnWindowNewEvent-targetUrl: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

