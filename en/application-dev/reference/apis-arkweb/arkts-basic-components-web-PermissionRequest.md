# Class (PermissionRequest)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @qq_42700029-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=1e9d7894dc2ab962288e1d5089fec42d46f9817c translatedAt=2026-11-04T11:20:27.190Z pushedAt=2026-11-04T11:28:00.127Z nl=1 -->

PermissionRequest is an object used by the Web component to grant or deny permission requests. When a web page attempts to access protected system resources (such as the camera, microphone, geolocation, and so on), the ArkWeb kernel sends a permission request to the application through the [onPermissionRequest](./arkts-basic-components-web-events.md#onpermissionrequest9) event callback, and the application uses the PermissionRequest object to decide whether to grant these requests. This object is suitable for scenarios where the application needs to manage web page access permissions to sensitive resources, protect user privacy, and ensure secure and controllable resource access, helping developers flexibly handle web page permission requests.

> **NOTE**
>
> - This component is supported since API version 8. For newly added APIs in later versions, the initial version of each API is marked separately with a superscript.
>
> - This class is supported since API version 9.
>
> - The sample effects are subject to the actual running on a real device.
>
> - The [grant](./arkts-basic-components-web-PermissionRequest.md#grant9)() and [deny](./arkts-basic-components-web-PermissionRequest.md#deny9)() methods are mutually exclusive. For the same PermissionRequest object, only one of them can be called.
>
> - After grant() or deny() is called, the PermissionRequest object has completed its response and cannot be called repeatedly.
>
> - A PermissionRequest object that has not called any method to respond will cause the permission request to time out.
>
> - The resources parameter of the grant() method usually uses the return value of the getAccessibleResource() method.
>
> - Typical usage flow: call getAccessibleResource() to obtain the requested resource list, select the resources to be authorized, and then call grant() to authorize them.

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