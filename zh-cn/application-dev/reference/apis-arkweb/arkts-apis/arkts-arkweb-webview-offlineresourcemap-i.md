# OfflineResourceMap

本地离线资源配置对象，用于配置将被[injectOfflineResources](arkts-arkweb-webview-webviewcontroller-c.md#injectofflineresources-1)接口注入到内存缓存的本地离线资源的相关信息，内核会根据此信息生成资源缓存，并据此控制缓存的有效期。

**起始版本：** 12

<!--Device-webview-interface OfflineResourceMap--><!--Device-webview-interface OfflineResourceMap-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## resource

```TypeScript
resource: Uint8Array
```

Content of a local offline resource.

**类型：** Uint8Array

**起始版本：** 12

<!--Device-OfflineResourceMap-resource: Uint8Array--><!--Device-OfflineResourceMap-resource: Uint8Array-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## responseHeaders

```TypeScript
responseHeaders: Array<WebHeader>
```

HTTP response headers corresponding to the resources. The **Cache-Control** or **Expires** response header is used to control the validity period of the resource in the memory cache. If neither of the headers is provided, a default validity time of 86400 seconds (1 day) will be applied. The **Content-Type** response header is used to define the MIME type of the resource. For resources of type MODULE_JS, a valid MIME type must be provided. For other types, the MIME type is optional, with no default value. A non-standard MIME type can lead to the resource being invalidated in the memory cache. If a **script** tag on the web page uses the **crossorigin** attribute,the **Cross-Origin** response header must be set in the **responseHeaders** parameter of the API. The value for this header should be **anonymous** or **use-credentials**.

**类型：** Array<WebHeader>

**起始版本：** 12

<!--Device-OfflineResourceMap-responseHeaders: Array<WebHeader>--><!--Device-OfflineResourceMap-responseHeaders: Array<WebHeader>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## type

```TypeScript
type: OfflineResourceType
```

资源的类型，目前仅支持Javascript、图片和CSS类型的资源。

**类型：** OfflineResourceType

**起始版本：** 12

<!--Device-OfflineResourceMap-type: OfflineResourceType--><!--Device-OfflineResourceMap-type: OfflineResourceType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## urlList

```TypeScript
urlList: Array<string>
```

List of network addresses of the local offline resources. The first item in the list is used as the resources'origin. If only one network address is provided, this single address is used for the resources' origin. The URL supports only the HTTP and HTTPS protocols and contains a maximum of 2048 characters.

**类型：** Array<string>

**起始版本：** 12

<!--Device-OfflineResourceMap-urlList: Array<string>--><!--Device-OfflineResourceMap-urlList: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

