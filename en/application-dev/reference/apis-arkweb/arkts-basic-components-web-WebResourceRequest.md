# Class (WebResourceRequest)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:36:44.603Z pushedAt=2026-11-04T11:50:30.984Z nl=1 -->

WebResourceRequest is a class in the Web component that represents a network resource request, providing detailed metadata about the requested resource. This object is used in event callbacks such as `onErrorReceive`, `onHttpErrorReceive`, and request interception to help developers diagnose network errors, monitor request status, and implement resource interception control. By using this class, the app can improve error handling, enhance request controllability, and optimize user experience. For sample code, see [onErrorReceive event](./arkts-basic-components-web-events.md#onerrorreceive).

> **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This class is supported since API version 8.
>
> - The sample effect is subject to the actual device.

## constructor

constructor()

Constructs a **WebResourceRequest** object.

**System capability**: SystemCapability.Web.Webview.Core

## getRequestHeader

getRequestHeader(): Array\<Header\>

Obtains the information about the resource request header.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                        | Description        |
| -------------------------- | ---------- |
| Array<[Header](./arkts-basic-components-web-i.md#header)> | Returns an array containing the key-value pair information of the request headers. Each Header object contains the name and corresponding value of a request header, such as User-Agent, Content-Type, etc. |

## getRequestUrl

getRequestUrl(): string

Obtains the URL of the resource request.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| string | Returns the complete resource request URL string, including the protocol, domain name, path, and query parameters. |

## isMainFrame

isMainFrame(): boolean

Checks whether the resource request is for the main frame. Used to differentiate between main frame and subframe requests.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description              |
| ------- | ---------------- |
| boolean | Whether the resource request is a main frame request.<br>The value **true** indicates that the resource request is a main frame request, and **false** indicates that the resource request is not a main frame request. |

## isRedirect

isRedirect(): boolean

Determines whether the resource request is redirected by the server. It is used to check the request redirection chain and other scenarios.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description              |
| ------- | ---------------- |
| boolean | Whether the resource request is redirected by the server.<br>true indicates that the resource request is redirected by the server, and false indicates that the resource request is not redirected by the server. |

## isRequestGesture

isRequestGesture(): boolean

Checks whether the resource request is associated with a gesture (such as a tap).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description                  |
| ------- | -------------------- |
| boolean | Whether the resource request is associated with a gesture (for example, a tap).<br>The value **true** indicates that the resource request is associated with a gesture, and **false** indicates the opposite.|

## getRequestMethod<sup>9+</sup>

getRequestMethod(): string

Obtains the request method.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description     |
| ------ | ------- |
| string | HTTP request method string. Common values include GET, POST, PUT, DELETE, etc., indicating the HTTP method type used for the resource request. |