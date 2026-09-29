# OnDownloadStartEvent

```TypeScript
declare interface OnDownloadStartEvent
```

Defines the callback information for notifying the host app that a file download has started, including the URL, user agent, and file details. It is suitable for scenarios where monitoring and managing file downloads are required, improving download process controllability and user experience.

**Since:** 12

<!--Device-unnamed-declare interface OnDownloadStartEvent--><!--Device-unnamed-declare interface OnDownloadStartEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## contentDisposition

```TypeScript
contentDisposition: string
```

Content-Disposition response header returned by the server, which may be empty.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnDownloadStartEvent-contentDisposition: string--><!--Device-OnDownloadStartEvent-contentDisposition: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## contentLength

```TypeScript
contentLength: number
```

Length of the file returned by the server. Unit: byte.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnDownloadStartEvent-contentLength: number--><!--Device-OnDownloadStartEvent-contentLength: number-End-->

**System capability:** SystemCapability.Web.Webview.Core

## mimetype

```TypeScript
mimetype: string
```

MIME type of the content returned by the server.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnDownloadStartEvent-mimetype: string--><!--Device-OnDownloadStartEvent-mimetype: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL for the download task.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnDownloadStartEvent-url: string--><!--Device-OnDownloadStartEvent-url: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## userAgent

```TypeScript
userAgent: string
```

User agent used for download.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnDownloadStartEvent-userAgent: string--><!--Device-OnDownloadStartEvent-userAgent: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
