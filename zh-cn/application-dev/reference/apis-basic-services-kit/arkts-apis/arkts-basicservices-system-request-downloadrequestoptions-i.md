# DownloadRequestOptions

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [UploadConfig](arkts-basicservices-request-uploadconfig-i.md)

**系统能力：** SystemCapability.MiscServices.Download

## 导入模块

```TypeScript
import { Request, DownloadRequestOptions, DownloadResponse, OnDownloadCompleteOptions, OnDownloadCompleteResponse, RequestData, RequestFile, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Download

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when downloading fails.

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | any | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success?: (data: DownloadResponse) => void
```

Called when the files are successfully downloaded.

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DownloadResponse](arkts-basicservices-system-request-downloadresponse-i.md) | 是 |  |

## description

```TypeScript
description?: string
```

Download description. The default value is the file name.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** description

**系统能力：** SystemCapability.MiscServices.Download

## filename

```TypeScript
filename?: string
```

Name of the file to downloaded. The value is obtained from the current request or resource URL by default.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** saveas

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

**系统能力：** SystemCapability.MiscServices.Download
