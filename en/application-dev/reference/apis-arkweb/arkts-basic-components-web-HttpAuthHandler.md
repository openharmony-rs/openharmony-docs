# Class (HttpAuthHandler)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-07T04:49:06.367Z pushedAt=2026-08-07T08:12:22.388Z -->

HttpAuthHandler is a handler class used by the Web component to process HTTP authentication requests. When the server returns 401 Unauthorized to request authentication, the Web component obtains an HttpAuthHandler instance through the onHttpAuthRequest event callback, and the app decides whether to provide authentication credentials. For sample code, see [onHttpAuthRequest](./arkts-basic-components-web-events.md#onhttpauthrequest9).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs an **HttpAuthHandler**.

**System capability**: SystemCapability.Web.Webview.Core

## cancel<sup>9+</sup>

cancel(): void

Cancels HTTP authentication as requested by the user.

**System capability**: SystemCapability.Web.Webview.Core

## confirm<sup>9+</sup>

confirm(userName: string, password: string): boolean

Performs HTTP authentication with the user name and password provided by the user.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name     | Type  | Mandatory | Description      |
| -------- | ------ | ---- | ---------- |
| userName | string | Yes | HTTP authentication user name, which must be a non-empty string. |
| password      | string | Yes | HTTP authentication password, which must be a non-empty string.  |

**Return value**

| Type     | Description                   |
| ------- | --------------------- |
| boolean | Returns **true** if authentication succeeds; returns **false** otherwise. |

## isHttpAuthInfoSaved<sup>9+</sup>

isHttpAuthInfoSaved(): boolean

Checks whether the credentials stored for the current host are applicable. The credentials are not applicable if they have been rejected by the server in the current request.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description                       |
| ------- | ------------------------- |
| boolean | true if the stored credentials are applicable; false otherwise. |