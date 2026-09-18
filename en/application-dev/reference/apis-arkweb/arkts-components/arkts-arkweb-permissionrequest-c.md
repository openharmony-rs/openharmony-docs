# PermissionRequest

PermissionRequest is an object used by the **Web** component to grant or deny permission requests. When a web page attempts to access protected system resources (such as camera, microphone, geolocation, etc.), the ArkWeb kernel sends a permission request to the app through the [onPermissionRequest](arkts-arkweb-web-comp-attribute.md#onpermissionrequest) event callback. The app then uses the PermissionRequest object to decide whether to grant these requests. This object is applicable to scenarios where the app needs to manage web page access to sensitive resources, protect user privacy, and ensure secure and controllable resource access, helping developers flexibly handle web page permission requests.

> **NOTE:** 
> 
> - The [grant](#grant)() and [deny](#deny)() methods are mutually exclusive. For the same PermissionRequest object, only one of them can be called.
> 
> - After grant() or deny() is called, the PermissionRequest object has completed its response and cannot be called again.
> 
> - A PermissionRequest object that has not been responded to by calling any method will cause the permission request to time out.
> 
> - The resources parameter of the grant() method typically uses the return value of the getAccessibleResource()method.
> 
> - Typical usage flow: Call getAccessibleResource() to obtain the list of requested resources, select the resources to be authorized, and then call grant() for authorization.

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **PermissionRequest** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## deny

```TypeScript
deny(): void
```

Denies the permission requested by the web page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## getAccessibleResource

```TypeScript
getAccessibleResource(): Array<string>
```

Obtains the list of permission resources requested by the web page. For details about the type, see [ProtectedResourceType](arkts-arkweb-protectedresourcetype-e.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of accessible resources requested by the web page. |

## getOrigin

```TypeScript
getOrigin(): string
```

Obtains the origin of this web page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Origin of the web page that requests the permission. |

## grant

```TypeScript
grant(resources: Array<string>): void
```

Grants the permission requested by the web page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resources | Array&lt;string&gt; | Yes | List of permission resources granted to the web page, which must be obtained through getAccessibleResource(). For the type, see [ProtectedResourceType](arkts-arkweb-protectedresourcetype-e.md). After this parameter is passed in, the web page will obtain access to the specified resources. If an empty list is passed in, all permission requests are denied. |
