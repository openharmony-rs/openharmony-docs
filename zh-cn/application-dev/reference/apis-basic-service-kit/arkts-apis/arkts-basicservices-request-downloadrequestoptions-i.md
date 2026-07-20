# DownloadRequestOptions

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [UploadConfig](arkts-basicservices-request-uploadconfig-i.md)

<!--Device-unnamed-export interface DownloadRequestOptions--><!--Device-unnamed-export interface DownloadRequestOptions-End-->

**系统能力：** SystemCapability.MiscServices.Download

## 导入模块

```TypeScript
import { UploadResponse, RequestData, DownloadRequestOptions, DownloadResponse, RequestFile, OnDownloadCompleteOptions, OnDownloadCompleteResponse, UploadRequestOptions } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-DownloadRequestOptions-complete?: () => void--><!--Device-DownloadRequestOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.MiscServices.Download

## description

```TypeScript
description?: string
```

Download description.The default value is the file name.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** description

<!--Device-DownloadRequestOptions-description?: string--><!--Device-DownloadRequestOptions-description?: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when downloading fails.

**类型：** (data: any, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-DownloadRequestOptions-fail?: (data: any, code: number) => void--><!--Device-DownloadRequestOptions-fail?: (data: any, code: number) => void-End-->

**系统能力：** SystemCapability.MiscServices.Download

## filename

```TypeScript
filename?: string
```

Name of the file to downloaded.The value is obtained from the current request or resource URL by default.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** saveas

<!--Device-DownloadRequestOptions-filename?: string--><!--Device-DownloadRequestOptions-filename?: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## header

```TypeScript
header?: string
```

Request header.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** headers

<!--Device-DownloadRequestOptions-header?: string--><!--Device-DownloadRequestOptions-header?: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## success

```TypeScript
success?: (data: DownloadResponse) => void
```

Called when the files are successfully downloaded.

**类型：** (data: DownloadResponse) =&gt; void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-DownloadRequestOptions-success?: (data: DownloadResponse) => void--><!--Device-DownloadRequestOptions-success?: (data: DownloadResponse) => void-End-->

**系统能力：** SystemCapability.MiscServices.Download

## url

```TypeScript
url: string
```

Resource URL.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** url

<!--Device-DownloadRequestOptions-url: string--><!--Device-DownloadRequestOptions-url: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

