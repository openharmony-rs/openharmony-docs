# Class (WebResourceRequest)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-07T04:49:58.980Z pushedAt=2026-08-07T08:12:48.399Z -->

WebResourceRequest is a class in the Web component that represents a network resource request, providing detailed metadata about the requested resource. This object is used in event callbacks such as `onErrorReceive`, `onHttpErrorReceive`, and request interception to help developers diagnose network errors, monitor request status, and implement resource interception control. By using this class, the app can improve error handling, enhance request controllability, and optimize user experience. For sample code, see [onErrorReceive event](./arkts-basic-components-web-events.md#onerrorreceive).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 8.
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
| Array<[Header](./arkts-basic-components-web-i.md#header)> | Array containing the key-value pair information of the request headers. Each **Header** object contains the name and corresponding value of a request header, such as User-Agent and Content-Type. |

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

Checks whether the resource request is redirected by the server. Used to inspect the request redirect chain and identify malicious redirects.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description              |
| ------- | ---------------- |
| boolean | Whether the resource request is redirected by the server.<br>The value **true** indicates that the resource request is redirected by the server, and **false** indicates that the resource request is not redirected by the server. |

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