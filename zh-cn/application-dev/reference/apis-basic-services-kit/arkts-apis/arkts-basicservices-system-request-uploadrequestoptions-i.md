# UploadRequestOptions

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [UploadConfig](arkts-basicservices-request-uploadconfig-i.md)

**系统能力：** SystemCapability.MiscServices.Upload

## 导入模块

```TypeScript
import { Request, DownloadRequestOptions, DownloadResponse, OnDownloadCompleteOptions, OnDownloadCompleteResponse, RequestData, RequestFile, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

Called when the execution is completed.

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Upload

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when uploading fails.

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | any | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success?: (data: UploadResponse) => void
```

Called when the files are uploaded successfully.

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [UploadResponse](arkts-basicservices-system-request-uploadresponse-i.md) | 是 |  |

## data

```TypeScript
data?: Array<RequestData>
```

Form data in the request body.

**类型：** Array&lt;[RequestData](arkts-basicservices-system-request-requestdata-i.md)&gt;

**起始版本：** 3

**废弃版本：** 9

**替代接口：** data

**系统能力：** SystemCapability.MiscServices.Upload

## files

```TypeScript
files: Array<RequestFile>
```

List of files to upload, which is submitted through multipart/form-data.

**类型：** Array&lt;[RequestFile](arkts-basicservices-system-request-requestfile-i.md)&gt;

**起始版本：** 3

**废弃版本：** 9

**替代接口：** data

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

**系统能力：** SystemCapability.MiscServices.Upload
