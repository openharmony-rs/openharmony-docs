# OnDownloadStartEvent

定义通知主应用开始下载文件的回调信息，包括URL、用户代理和文件详情。适用于需要监控和管理文件下载的场景，提升下载流程的可控性和用户体验。

**起始版本：** 12

<!--Device-unnamed-declare interface OnDownloadStartEvent--><!--Device-unnamed-declare interface OnDownloadStartEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## contentDisposition

```TypeScript
contentDisposition: string
```

服务器返回的 Content-Disposition响应头，服务器可能返回空。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnDownloadStartEvent-contentDisposition: string--><!--Device-OnDownloadStartEvent-contentDisposition: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## contentLength

```TypeScript
contentLength: number
```

服务器返回文件的长度。单位：字节。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnDownloadStartEvent-contentLength: number--><!--Device-OnDownloadStartEvent-contentLength: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## mimetype

```TypeScript
mimetype: string
```

服务器返回内容媒体类型（MIME）信息。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnDownloadStartEvent-mimetype: string--><!--Device-OnDownloadStartEvent-mimetype: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

文件下载的URL。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnDownloadStartEvent-url: string--><!--Device-OnDownloadStartEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## userAgent

```TypeScript
userAgent: string
```

用于下载的用户代理。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnDownloadStartEvent-userAgent: string--><!--Device-OnDownloadStartEvent-userAgent: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

