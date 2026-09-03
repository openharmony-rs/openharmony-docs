# Class (WebResourceError)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-07T04:49:40.252Z pushedAt=2026-08-07T08:12:46.488Z -->

WebResourceError is a class that provides error information when resource loading fails in the **Web** component. The error object is provided to the app through the `onErrorReceive` and `onHttpErrorReceive` event callbacks, encapsulating error details for debugging and error handling. It is typically used together with WebResourceRequest to determine which resource failed to load. For sample code, see [onErrorReceive event](./arkts-basic-components-web-events.md#onerrorreceive).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 8.
>
> - The sample effect is subject to the actual device.

## constructor

constructor()

Constructor of WebResourceError. Creates a WebResourceError object to encapsulate error information when resource loading fails in the **Web** component.

**System capability**: SystemCapability.Web.Webview.Core

## getErrorCode

getErrorCode(): number

Obtains the error code of the resource loading. It is used to determine the specific cause of the resource loading failure (such as network errors, server errors, or permission issues), so that developers can take appropriate handling strategies based on the error type (such as retrying, prompting the user, or degrading the display).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description         |
| ------ | ----------- |
| number | Error code for loading the resource. For details about the error codes, see [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist) or HTTP status codes. |

## getErrorInfo

getErrorInfo(): string

Obtains the error information of the resource loading. It is used to describe the specific cause of the resource loading failure in detail. Developers can output the error information to logs for debugging and analysis, or display a user-friendly error message to users.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description          |
| ------ | ------------ |
| string | Error information about resource loading.|