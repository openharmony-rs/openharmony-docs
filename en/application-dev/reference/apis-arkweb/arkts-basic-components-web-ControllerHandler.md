# Class (ControllerHandler)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @csliutt-private-->
<!--Designer: @ringking0-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=9c41f9fad7f6d910dff2a356347531b943719c3e translatedAt=2026-08-07T04:40:44.160Z pushedAt=2026-08-07T08:12:00.190Z -->

ControllerHandler is a helper class provided by ArkWeb for handling the allocation of controllers for newly created Web components. When a web page requests to create a new window through methods such as `window.open`, and the Web component has enabled the [multiWindowAccess](./arkts-basic-components-web-attributes.md#multiwindowaccess9) capability, the system provides the ControllerHandler object to the app through the [onWindowNew](./arkts-basic-components-web-events.md#onwindownew9) event. Developers need to call its [setWebController](#setwebcontroller9) method to set a valid [WebviewController](./arkts-apis-webview-WebviewController.md) object for the new window, associating the new window with the Web component actually created on the page. The web kernel blocks the render process while waiting for the setWebController call. If the app decides not to create a new window, it must call `setWebController(null)` to notify the web kernel; otherwise, the render process will remain blocked. Typical usage scenarios include opening a new web window in a custom dialog box, a new page, or a split screen, where the app needs to explicitly manage the URL display and security isolation of the new window.

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs a **ControllerHandler** API.

**System capability**: SystemCapability.Web.Webview.Core

## setWebController<sup>9+</sup>

setWebController(controller: WebviewController): void

Sets the WebviewController object for the newly created Web component. If the app decides not to create a new window, this parameter must be set to null to notify the web kernel; otherwise, the render process will be blocked.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type                                    | Mandatory| Description                                    |
| ---------- | ---------------------------------------- | ---- | ---------------------------------------- |
| controller | [WebviewController](./arkts-apis-webview-WebviewController.md) | Yes | **WebviewController** object of the **Web** component. If opening a new window is not needed, set it to **null**.|
<!--no_check-->