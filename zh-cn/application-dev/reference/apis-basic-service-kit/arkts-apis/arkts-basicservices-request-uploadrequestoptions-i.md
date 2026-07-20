# UploadRequestOptions

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [UploadConfig](arkts-basicservices-request-uploadconfig-i.md)

<!--Device-unnamed-export interface UploadRequestOptions--><!--Device-unnamed-export interface UploadRequestOptions-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## 导入模块

```TypeScript
import { UploadResponse, RequestData, DownloadRequestOptions, DownloadResponse, RequestFile, OnDownloadCompleteOptions, OnDownloadCompleteResponse, UploadRequestOptions } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

Called when the execution is completed.

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-UploadRequestOptions-complete?: () => void--><!--Device-UploadRequestOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## data

```TypeScript
data?: Array<RequestData>
```

Form data in the request body.

**类型：** Array&lt;RequestData&gt;

**起始版本：** 3

**废弃版本：** 9

**替代接口：** data

<!--Device-UploadRequestOptions-data?: Array<RequestData>--><!--Device-UploadRequestOptions-data?: Array<RequestData>-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when uploading fails.

**类型：** (data: any, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-UploadRequestOptions-fail?: (data: any, code: number) => void--><!--Device-UploadRequestOptions-fail?: (data: any, code: number) => void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## files

```TypeScript
files: Array<RequestFile>
```

List of files to upload, which is submitted through multipart/form-data.

**类型：** Array&lt;RequestFile&gt;

**起始版本：** 3

**废弃版本：** 9

**替代接口：** data

<!--Device-UploadRequestOptions-files: Array<RequestFile>--><!--Device-UploadRequestOptions-files: Array<RequestFile>-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## header

```TypeScript
header?: Object
```

Request header.

**类型：** Object

**起始版本：** 3

**废弃版本：** 9

**替代接口：** headers

<!--Device-UploadRequestOptions-header?: Object--><!--Device-UploadRequestOptions-header?: Object-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## method

```TypeScript
method?: string
```

Request methods available: POST and PUT. The default value is POST.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** method

<!--Device-UploadRequestOptions-method?: string--><!--Device-UploadRequestOptions-method?: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## success

```TypeScript
success?: (data: UploadResponse) => void
```

Called when the files are uploaded successfully.

**类型：** (data: UploadResponse) =&gt; void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

<!--Device-UploadRequestOptions-success?: (data: UploadResponse) => void--><!--Device-UploadRequestOptions-success?: (data: UploadResponse) => void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## url

```TypeScript
url: string
```

Resource URL.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** url

<!--Device-UploadRequestOptions-url: string--><!--Device-UploadRequestOptions-url: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

