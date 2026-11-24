# Class (WebResourceError)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-11-06T11:32:20.429Z pushedAt=2026-11-13T09:08:49.927Z nl=1 -->

WebResourceError is a class that provides error information when resource loading fails in the **Web** component. The error object is provided to the app through the `onErrorReceive` and `onHttpErrorReceive` event callbacks, encapsulating error details for debugging and error handling. It is typically used together with WebResourceRequest to determine which resource failed to load. For sample code, see [onErrorReceive event](./arkts-basic-components-web-events.md#onerrorreceive).

> **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This class is supported since API version 8.
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

## getCustomErrorCode

getCustomErrorCode(): number

Gets the custom error code for loading the resource. The custom error code is set through [setCustomErrorCode](arkts-apis-webview-WebSchemeHandlerResponse.md#setcustomerrorcode) of [WebSchemeHandlerResponse](arkts-apis-webview-WebSchemeHandlerResponse.md), and is directly passed to the application through the [onErrorReceive](./arkts-basic-components-web-events.md#onerrorreceive) event.

**Since:** 26.0.1

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                         |
| ------ | ----------------------------------- |
| number | Returns the custom error code for loading the resource. |

**Example**

For the complete sample code, see the [onErrorReceive event](./arkts-basic-components-web-events.md#onerrorreceive).

