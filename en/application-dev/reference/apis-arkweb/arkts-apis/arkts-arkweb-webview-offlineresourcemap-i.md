# OfflineResourceMap

Implements an **OfflineResourceMap** object, which is used to set information related to local offline resources that will be injected into memory cache through the [injectOfflineResources](arkts-arkweb-webview-webviewcontroller-c.md#injectofflineresources) API. The ArkWeb engine will generate resource caches based on this information and control the validity period of the cache accordingly.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## resource

```TypeScript
resource: Uint8Array
```

Content of a local offline resource.

**Type:** Uint8Array

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## responseHeaders

```TypeScript
responseHeaders: Array<WebHeader>
```

HTTP response headers corresponding to the resources. The Cache-Control or Expires response header provided is used to control the validity period of the resources in the memory cache. If not provided, the default validity period is 86400 seconds, that is, 1 day. The Content-Type response header provided is used to define the MIME type of the resources. MODULE_JS must provide a valid MIME type. Other types may not provide one, and there is no default value. A non-standard MIME type will cause the memory cache to become invalid. If the script tag in the service web page uses the crossorigin attribute, the Cross-Origin response header must be set to **anonymous** or **use-credentials** in the responseHeaders parameter of this API. Otherwise, the memory cache may become invalid.

**Type:** Array&lt;[WebHeader](arkts-arkweb-webview-webheader-i.md)&gt;

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## type

```TypeScript
type: OfflineResourceType
```

Type of the resources. Currently, only JavaScript, image, and CSS resources are supported.

**Type:** [OfflineResourceType](arkts-arkweb-webview-offlineresourcetype-e.md)

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## urlList

```TypeScript
urlList: Array<string>
```

List of network addresses corresponding to the local offline resources. The first item in the list serves as the origin of the resources. If only one network address is provided, it is used as the origin of the resources. The URL supports only HTTP or HTTPS and cannot exceed 2048 characters. If the preceding restrictions are not met, the resource injection fails.

**Type:** Array&lt;string&gt;

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core
