# Class (HttpAuthHandler)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:18:00.848Z pushedAt=2026-11-04T11:23:46.552Z nl=1 -->

HttpAuthHandler is a handler class used by the Web component to process HTTP authentication requests. When the server returns 401 Unauthorized to request authentication, the Web component obtains an HttpAuthHandler instance through the onHttpAuthRequest event callback, and the app decides whether to provide authentication credentials. For sample code, see [onHttpAuthRequest](./arkts-basic-components-web-events.md#onhttpauthrequest9).

> **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This class is supported since API version 9.
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
| userName | string | Yes | HTTP authentication user name. It is recommended to pass a non-empty string. |
| password      | string | Yes | HTTP authentication password. It is recommended to pass a non-empty string.  |

**Return value**

| Type     | Description                   |
| ------- | --------------------- |
| boolean | The return value only indicates the API call status, not the authentication result. true indicates that the call is successful, and false indicates that the call fails. |

## isHttpAuthInfoSaved<sup>9+</sup>

isHttpAuthInfoSaved(): boolean

Checks whether the credentials stored for the current host are applicable. The credentials are not applicable if they have been rejected by the server in the current request.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description                       |
| ------- | ------------------------- |
| boolean | Returns true when the stored credentials are applicable, and returns false otherwise. |