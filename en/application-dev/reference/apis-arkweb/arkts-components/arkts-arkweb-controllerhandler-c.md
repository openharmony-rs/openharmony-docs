# ControllerHandler

ControllerHandler is a helper class provided by ArkWeb for handling the allocation of controllers for newly created Web components. When a web page requests to create a new window through methods such as `window.open`, and the Web component has enabled the [multiWindowAccess](arkts-arkweb-web-comp-attribute.md#multiwindowaccess) capability, the system provides the ControllerHandler object to the app through the [onWindowNew](arkts-arkweb-web-comp-attribute.md#onwindownew) event. Developers need to call its [setWebController](#setwebcontroller) method to set a valid [WebviewController](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md) object for the new window, associating the new window with the Web component actually created on the page. The web kernel blocks the render process while waiting for the setWebController call. If the app decides not to create a new window, it must call `setWebController(null)` to notify the web kernel; otherwise, the render process will remain blocked. Typical usage scenarios include opening a new web window in a custom dialog box, a new page, or a split screen, where the app needs to explicitly manage the URL display and security isolation of the new window.

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **ControllerHandler** API.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## setWebController

```TypeScript
setWebController(controller: WebviewController): void
```

Sets the WebviewController object for the newly created Web component. If the app decides not to create a new window, this parameter must be set to null to notify the web kernel; otherwise, the render process will be blocked.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [WebviewController](arkts-arkweb-webviewcontroller-t.md) | Yes | **WebviewController** object of the **Web** component. If opening a new window is not needed, set it to **null**. |
