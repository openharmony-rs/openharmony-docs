# Class (PermissionRequest)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @qq_42700029-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=8d7403adf09bf343974d6e2d17a0f01ca2f785fe translatedAt=2026-11-06T11:23:15.480Z pushedAt=2026-11-13T08:53:25.169Z nl=1 -->

PermissionRequest is an object used by the **Web** component to grant or deny permission requests. When a web page attempts to access protected system resources (such as camera, microphone, geolocation, etc.), the ArkWeb kernel sends a permission request to the app through the [onPermissionRequest](./arkts-basic-components-web-events.md#onpermissionrequest9) event callback. The app then uses the PermissionRequest object to decide whether to grant these requests. This object is applicable to scenarios where the app needs to manage web page access to sensitive resources, protect user privacy, and ensure secure and controllable resource access, helping developers flexibly handle web page permission requests.

> **NOTE**
>
> - This component is supported since API version 8. New APIs in later versions are marked with a superscript to indicate their initial version.
>
> - This class is supported since API version 9.
>
> - The example effects are subject to the actual running on a real device.
>
> - The [grant](./arkts-basic-components-web-PermissionRequest.md#grant9)() and [deny](./arkts-basic-components-web-PermissionRequest.md#deny9)() methods are mutually exclusive. For the same PermissionRequest object, only one of them can be called.
>
> - After grant() or deny() is called, the PermissionRequest object has completed its response and cannot be called repeatedly.
>
> - A PermissionRequest object that has not called any method to respond will cause the permission request to time out.
>
> - The resources parameter of the grant() method usually uses the return value of the getAccessibleResource() method.
>
> - Typical usage flow: call getAccessibleResource() to obtain the requested resource list, select the resources to be authorized, and then call grant() to authorize.

## constructor<sup>9+</sup>

constructor()

Constructs a **PermissionRequest** object.

**System capability**: SystemCapability.Web.Webview.Core

## deny<sup>9+</sup>

deny(): void

Denies the permission requested by the web page.

**System capability**: SystemCapability.Web.Webview.Core

## getOrigin<sup>9+</sup>

getOrigin(): string

Obtains the origin of this web page.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description          |
| ------ | ------------ |
| string | Origin of the web page that requests the permission.|

## getAccessibleResource<sup>9+</sup>

getAccessibleResource(): Array\<string\>

Obtains the list of permission resources requested by the web page. For details about the type, see [ProtectedResourceType](./arkts-basic-components-web-e.md#protectedresourcetype9).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type             | Description           |
| --------------- | ------------- |
| Array\<string\> | List of accessible resources requested by the web page.|

## grant<sup>9+</sup>

grant(resources: Array\<string\>): void

Grants the permission requested by the web page.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name      | Type           | Mandatory  | Description           |
| --------- | --------------- | ---- | --------------- |
| resources | Array\<string\> | Yes   | List of permission resources granted to the web page, which must be obtained through getAccessibleResource(). For the type, see [ProtectedResourceType](./arkts-basic-components-web-e.md#protectedresourcetype9). After this parameter is passed in, the web page will obtain access to the specified resources. If an empty list is passed in, all permission requests are denied. |