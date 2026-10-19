# Class (PermissionRequest)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @qq_42700029-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=be1a9e2c0a61a2192f9a05391ef1df5f29636290 translatedAt=2026-08-07T04:25:50.794Z pushedAt=2026-08-07T08:12:29.205Z -->

PermissionRequest is an object used by the **Web** component to grant or deny permission requests. When a web page attempts to access protected system resources (such as camera, microphone, geolocation, etc.), the ArkWeb kernel sends a permission request to the app through the [onPermissionRequest](./arkts-basic-components-web-events.md#onpermissionrequest9) event callback. The app then uses the PermissionRequest object to decide whether to grant these requests. This object is applicable to scenarios where the app needs to manage web page access to sensitive resources, protect user privacy, and ensure secure and controllable resource access, helping developers flexibly handle web page permission requests.

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual running on a real device.
>
> - The [grant](./arkts-basic-components-web-PermissionRequest.md#grant9)() and [deny](./arkts-basic-components-web-PermissionRequest.md#deny9)() methods are mutually exclusive. For the same PermissionRequest object, only one of them can be called.
>
> - After grant() or deny() is called, the PermissionRequest object has completed its response and cannot be called again.
>
> - A PermissionRequest object that has not been responded to by calling any method will cause the permission request to time out.
>
> - The resources parameter of the grant() method typically uses the return value of the getAccessibleResource() method.
>
> - Typical usage flow: Call getAccessibleResource() to obtain the list of requested resources, select the resources to be authorized, and then call grant() for authorization.

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
<!--no_check-->