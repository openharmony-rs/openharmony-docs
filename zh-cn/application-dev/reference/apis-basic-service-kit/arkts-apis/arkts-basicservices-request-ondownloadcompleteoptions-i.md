# OnDownloadCompleteOptions

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-unnamed-export interface OnDownloadCompleteOptions--><!--Device-unnamed-export interface OnDownloadCompleteOptions-End-->

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

**类型：** () => void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-OnDownloadCompleteOptions-complete?: () => void--><!--Device-OnDownloadCompleteOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.MiscServices.Download

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

接口调用失败的回调函数。返回header信息与HTTP状态码。

**类型：** (data: any, code: number) => void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-OnDownloadCompleteOptions-fail?: (data: any, code: number) => void--><!--Device-OnDownloadCompleteOptions-fail?: (data: any, code: number) => void-End-->

**系统能力：** SystemCapability.MiscServices.Download

## success

```TypeScript
success?: (data: OnDownloadCompleteResponse) => void
```

接口调用成功的回调函数。

**类型：** (data: OnDownloadCompleteResponse) => void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-OnDownloadCompleteOptions-success?: (data: OnDownloadCompleteResponse) => void--><!--Device-OnDownloadCompleteOptions-success?: (data: OnDownloadCompleteResponse) => void-End-->

**系统能力：** SystemCapability.MiscServices.Download

## token

```TypeScript
token: string
```

download 接口返回的结果 token。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** tid

<!--Device-OnDownloadCompleteOptions-token: string--><!--Device-OnDownloadCompleteOptions-token: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

