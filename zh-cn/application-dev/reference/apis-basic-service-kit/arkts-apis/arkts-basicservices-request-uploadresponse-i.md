# UploadResponse

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [UploadConfig](arkts-basicservices-request-uploadconfig-i.md)

<!--Device-unnamed-export interface UploadResponse--><!--Device-unnamed-export interface UploadResponse-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## 导入模块

```TypeScript
import { UploadResponse, RequestData, DownloadRequestOptions, DownloadResponse, RequestFile, OnDownloadCompleteOptions, OnDownloadCompleteResponse, UploadRequestOptions } from '@kit.BasicServicesKit';
```

## code

```TypeScript
code: number
```

服务器返回的HTTP状态码。

**类型：** number

**起始版本：** 3

**废弃版本：** 9

**替代接口：** statusCode

<!--Device-UploadResponse-code: number--><!--Device-UploadResponse-code: number-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## data

```TypeScript
data: string
```

服务器返回的内容。根据返回头内容中的type决定该值的类型。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** extras

<!--Device-UploadResponse-data: string--><!--Device-UploadResponse-data: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## headers

```TypeScript
headers: Object
```

服务器返回的返回头内容。

**类型：** Object

**起始版本：** 3

**废弃版本：** 9

**替代接口：** headers

<!--Device-UploadResponse-headers: Object--><!--Device-UploadResponse-headers: Object-End-->

**系统能力：** SystemCapability.MiscServices.Upload

