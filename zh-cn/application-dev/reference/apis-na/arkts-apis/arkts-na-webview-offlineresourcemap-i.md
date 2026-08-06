# OfflineResourceMap

Define offline resource's content and info.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-webview-interface OfflineResourceMap--><!--Device-webview-interface OfflineResourceMap-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## resource

```TypeScript
resource: Uint8Array
```

Arraybuffer of resource. Size must less than 10Mb and cannot be empty.

**类型：** Uint8Array

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-OfflineResourceMap-resource: Uint8Array--><!--Device-OfflineResourceMap-resource: Uint8Array-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## responseHeaders

```TypeScript
responseHeaders: Array<WebHeader>
```

Response headers of resource.

**类型：** Array&lt;WebHeader&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-OfflineResourceMap-responseHeaders: Array<WebHeader>--><!--Device-OfflineResourceMap-responseHeaders: Array<WebHeader>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## type

```TypeScript
type: OfflineResourceType
```

Resource type

**类型：** OfflineResourceType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-OfflineResourceMap-type: OfflineResourceType--><!--Device-OfflineResourceMap-type: OfflineResourceType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## urlList

```TypeScript
urlList: Array<string>
```

Url list of resource. Url of urlList must be HTTP/HTTPS protocol and no longer than 2048.

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-OfflineResourceMap-urlList: Array<string>--><!--Device-OfflineResourceMap-urlList: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

