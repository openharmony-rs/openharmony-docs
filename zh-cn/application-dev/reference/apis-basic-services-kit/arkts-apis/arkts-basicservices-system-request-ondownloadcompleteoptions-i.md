# OnDownloadCompleteOptions

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

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

接口调用失败的回调函数。返回header信息与HTTP状态码。

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
success?: (data: OnDownloadCompleteResponse) => void
```

接口调用成功的回调函数。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [OnDownloadCompleteResponse](arkts-basicservices-system-request-ondownloadcompleteresponse-i.md) | 是 |  |

## token

```TypeScript
token: string
```

download 接口返回的结果 token。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** tid

**系统能力：** SystemCapability.MiscServices.Download
