# OnWindowNewExtEvent

```TypeScript
declare interface OnWindowNewExtEvent
```

Defines the callback information triggered when the web page requests to create a window, including the window feature information and window opening method. It is suitable for scenarios where fine-grained control of new window behavior is required, improving window management customization and user experience.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: ControllerHandler
```

**WebviewController** instance for setting the new window.

**Type:** [ControllerHandler](arkts-arkweb-web-comp-controllerhandler-c.md)

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Web.Webview.Core

## isAlert

```TypeScript
isAlert: boolean
```

The value **true** indicates that a dialog box is requested to be created, and the value **false** indicates that a new tab page is requested to be created.

**Type:** boolean

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Web.Webview.Core

## isUserTrigger

```TypeScript
isUserTrigger: boolean
```

Whether the creation is triggered by the user. The value **true** means that the creation is triggered by the user, and **false** means the opposite.

**Type:** boolean

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Web.Webview.Core

## navigationPolicy

```TypeScript
navigationPolicy: NavigationPolicy
```

Window opening mode when the web page requests a user to create a new window.

**Type:** [NavigationPolicy](arkts-arkweb-web-comp-navigationpolicy-e.md)

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Web.Webview.Core

## targetUrl

```TypeScript
targetUrl: string
```

URL to be opened in the new window.

**Type:** string

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Web.Webview.Core

## windowFeatures

```TypeScript
windowFeatures: WindowFeatures
```

Feature information of the new window requested to be created by the web page.

**Type:** [WindowFeatures](arkts-arkweb-web-comp-windowfeatures-i.md)

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Web.Webview.Core
