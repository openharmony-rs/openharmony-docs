# OnWindowNewEvent

```TypeScript
declare interface OnWindowNewEvent
```

Defines the callback triggered when the web page requests the user to create a window. Starting from API version 23, you can use [OnWindowNewExtEvent](arkts-arkweb-web-comp-onwindownewextevent-i.md) to obtain more window information.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: ControllerHandler
```

**WebviewController** instance for setting the new window.

**Type:** [ControllerHandler](arkts-arkweb-web-comp-controllerhandler-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## isAlert

```TypeScript
isAlert: boolean
```

Whether to open the target URL in a new window. The value **true** means to open the target URL in a new window, and **false** means to open the target URL in a new tab.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## isUserTrigger

```TypeScript
isUserTrigger: boolean
```

Whether the creation is triggered by the user. The value **true** means that the creation is triggered by the user, and **false** means the opposite.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## targetUrl

```TypeScript
targetUrl: string
```

Target URL.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
