# OfflineResourceMap

本地离线资源配置对象，用于配置将被[injectOfflineResources](arkts-arkweb-webview-webviewcontroller-c.md#injectofflineresources)接口注入到内存缓存的本地离线资源的相 关信息，内核会根据此信息生成资源缓存，并据此控制缓存的有效期。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## resource

```TypeScript
resource: Uint8Array
```

本地离线资源的内容。

**类型：** Uint8Array

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## responseHeaders

```TypeScript
responseHeaders: Array<WebHeader>
```

资源对应的HTTP响应头。其中提供的Cache-Control或Expires响应头将被用于控制资源在内存缓存中的有效期。如果不提供，默认的有效期为86400秒，即1天。其中提供的Content-Type响应头将被用于定义资源 的MIMEType，MODULE_JS必须提供有效的MIMEType，其他类型可不提供，无默认值，不符合标准的MIMEType会导致内存缓存失效。如果业务网页中的script标签使用了crossorigin属性，则必须在接口的 responseHeaders参数中设置Cross-Origin响应头的值为anonymous或use-credentials，否则可能导致内存缓存失效。

**类型：** Array&lt;WebHeader&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## type

```TypeScript
type: OfflineResourceType
```

资源的类型，目前仅支持JavaScript、图片和CSS类型的资源。

**类型：** [OfflineResourceType](arkts-arkweb-webview-offlineresourcetype-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## urlList

```TypeScript
urlList: Array<string>
```

本地离线资源对应的网络地址列表，列表的第一项将作为资源的源（Origin），如果仅提供一个网络地址，则使用该地址作为这个资源的源。url仅支持HTTP或HTTPS协议，长度不超过2048。不符合上述限制时，该资源注入失败。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core
