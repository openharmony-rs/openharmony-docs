# Request(上传下载)

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [request](arkts-basicservices-request-n.md)

<!--Device-unnamed-export default class Request--><!--Device-unnamed-export default class Request-End-->

**系统能力：** SystemCapability.MiscServices.Download

## 导入模块

```TypeScript
import { Request, DownloadRequestOptions, DownloadResponse, OnDownloadCompleteOptions, OnDownloadCompleteResponse, RequestData, RequestFile, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';
```

## download

```TypeScript
static download(options: DownloadRequestOptions): void
```

下载文件，无返回值。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [downloadFile](arkts-basicservices-request-downloadfile-f.md)(context: BaseContext, config: DownloadConfig)

<!--Device-Request-static download(options: DownloadRequestOptions): void--><!--Device-Request-static download(options: DownloadRequestOptions): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DownloadRequestOptions](arkts-basicservices-system-request-downloadrequestoptions-i.md) | 是 | 下载的配置信息。 |

## onDownloadComplete

```TypeScript
static onDownloadComplete(options: OnDownloadCompleteOptions): void
```

获取下载任务状态，无返回值。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** show(id: string)

<!--Device-Request-static onDownloadComplete(options: OnDownloadCompleteOptions): void--><!--Device-Request-static onDownloadComplete(options: OnDownloadCompleteOptions): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [OnDownloadCompleteOptions](arkts-basicservices-system-request-ondownloadcompleteoptions-i.md) | 是 | 监听下载任务的配置信息。 |

## upload

```TypeScript
static upload(options: UploadRequestOptions): void
```

上传文件，无返回值。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [uploadFile](arkts-basicservices-request-uploadfile-f.md)(context: BaseContext, config: UploadConfig)

<!--Device-Request-static upload(options: UploadRequestOptions): void--><!--Device-Request-static upload(options: UploadRequestOptions): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [UploadRequestOptions](arkts-basicservices-system-request-uploadrequestoptions-i.md) | 是 | 上传的配置信息。 |

