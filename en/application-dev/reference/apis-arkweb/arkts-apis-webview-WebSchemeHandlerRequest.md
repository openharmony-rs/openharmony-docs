# Class (WebSchemeHandlerRequest)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=c3549f5fc26f86afdb3e7a215c50ff6d6d5cab0c translatedAt=2026-08-07T04:47:57.193Z pushedAt=2026-08-07T08:11:46.696Z -->

The WebSchemeHandlerRequest class defines a wrapper object for resource requests intercepted through WebSchemeHandler. When a developer registers a custom protocol handler (WebSchemeHandler), the Web kernel creates a WebSchemeHandlerRequest instance and passes it to the callback method upon intercepting a request matching the protocol. This object provides the following request information query methods: getting request header information, request URL, request method, source URL, determining whether it is a main frame request, whether it is associated with a user gesture, getting the request body stream, resource type, and the frame URL that triggered the request, so as to determine whether to intercept the request and construct a corresponding response.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## getHeader<sup>12+</sup>

getHeader(): Array\<WebHeader\>

Obtains the information about the resource request header.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                        | Description        |
| -------------------------- | ---------- |
| Array\<[WebHeader](./arkts-apis-webview-i.md#webheader)\> | Information about the resource request header.|

**Example**

For the complete sample code, see [onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## getRequestUrl<sup>12+</sup>

getRequestUrl(): string

Obtains the URL of the resource request.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| string | URL of the resource request.|

**Example**

For the complete sample code, see [onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## getRequestMethod<sup>12+</sup>

getRequestMethod(): string

Obtains the request method.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| string | Request method.|

**Example**

For the complete sample code, see [onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## getReferrer<sup>12+</sup>

getReferrer(): string

Obtains the referrer.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| string | Obtained referrer.|

**Example**

For the complete sample code, see [onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## isMainFrame<sup>12+</sup>

isMainFrame(): boolean

Checks whether the resource request is from the main frame.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| boolean | Whether the resource request is for the main frame. The value **true** indicates the resource request is for the main frame, and **false** indicates otherwise. |

**Example**

For the complete sample code, see [onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## hasGesture<sup>12+</sup>

hasGesture(): boolean

Checks whether the resource request is associated with a gesture (for example, a tap).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| boolean | true if the resource request is associated with a gesture (such as a tap); false otherwise. |

**Example**

For the complete sample code, see [onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## getHttpBodyStream<sup>12+</sup>

getHttpBodyStream(): WebHttpBodyStream | null

Obtains the **WebHttpBodyStream** instance in this resource request.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| [WebHttpBodyStream](./arkts-apis-webview-WebHttpBodyStream.md) \| null | **WebHttpBodyStream** instance in the resource request. If there is no **WebHttpBodyStream** instance, **null** is returned.|

**Example**

For the complete sample code, see [onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## getRequestResourceType<sup>12+</sup>

getRequestResourceType(): WebResourceType

Obtains the resource type of this resource request.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| [WebResourceType](./arkts-apis-webview-e.md#webresourcetype12) | Resource type of the resource request.|

**Example**

For the complete sample code, see [onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## getFrameUrl<sup>12+</sup>

getFrameUrl(): string

Obtains the URL of the frame that triggers this request.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| string | URL of the frame that triggers the request.|

**Example**

For the complete sample code, see [onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).