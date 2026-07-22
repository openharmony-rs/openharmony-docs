# DownloadInfo

下载任务信息，[getTaskInfo](arkts-basicservices-request-downloadtask-i.md#gettaskinfo)接口的回调参数。

**起始版本：** 7

<!--Device-request-interface DownloadInfo--><!--Device-request-interface DownloadInfo-End-->

**系统能力：** SystemCapability.MiscServices.Download

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## description

```TypeScript
description: string
```

待下载任务的描述信息。

**类型：** string

**起始版本：** 7

<!--Device-DownloadInfo-description: string--><!--Device-DownloadInfo-description: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## downloadId

```TypeScript
downloadId: number
```

下载任务id。

**类型：** number

**起始版本：** 7

<!--Device-DownloadInfo-downloadId: long--><!--Device-DownloadInfo-downloadId: long-End-->

**系统能力：** SystemCapability.MiscServices.Download

## downloadTitle

```TypeScript
downloadTitle: string
```

下载任务名称。

**类型：** string

**起始版本：** 7

<!--Device-DownloadInfo-downloadTitle: string--><!--Device-DownloadInfo-downloadTitle: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## downloadTotalBytes

```TypeScript
downloadTotalBytes: number
```

下载的文件的总大小，单位为字节（B）。

**类型：** number

**起始版本：** 7

<!--Device-DownloadInfo-downloadTotalBytes: long--><!--Device-DownloadInfo-downloadTotalBytes: long-End-->

**系统能力：** SystemCapability.MiscServices.Download

## downloadedBytes

```TypeScript
downloadedBytes: number
```

实时下载大小，单位为字节（B）。

**类型：** number

**起始版本：** 7

<!--Device-DownloadInfo-downloadedBytes: long--><!--Device-DownloadInfo-downloadedBytes: long-End-->

**系统能力：** SystemCapability.MiscServices.Download

## failedReason

```TypeScript
failedReason: number
```

下载失败原因，可以是任何[下载任务的错误码](../../../reference/apis-basic-services-kit/js-apis-request.md#constants)常量。

**类型：** number

**起始版本：** 7

<!--Device-DownloadInfo-failedReason: int--><!--Device-DownloadInfo-failedReason: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## fileName

```TypeScript
fileName: string
```

下载的文件名。

**类型：** string

**起始版本：** 7

<!--Device-DownloadInfo-fileName: string--><!--Device-DownloadInfo-fileName: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## filePath

```TypeScript
filePath: string
```

存储文件的URI。

**类型：** string

**起始版本：** 7

<!--Device-DownloadInfo-filePath: string--><!--Device-DownloadInfo-filePath: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## pausedReason

```TypeScript
pausedReason: number
```

会话暂停的原因，可以是任何[下载任务暂停原因](../../../reference/apis-basic-services-kit/js-apis-request.md#constants)常量。

**类型：** number

**起始版本：** 7

<!--Device-DownloadInfo-pausedReason: int--><!--Device-DownloadInfo-pausedReason: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## status

```TypeScript
status: number
```

下载状态码，可以是任何[下载任务状态码](../../../reference/apis-basic-services-kit/js-apis-request.md#constants)常量。

**类型：** number

**起始版本：** 7

<!--Device-DownloadInfo-status: int--><!--Device-DownloadInfo-status: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## targetURI

```TypeScript
targetURI: string
```

下载文件的URI。

**类型：** string

**起始版本：** 7

<!--Device-DownloadInfo-targetURI: string--><!--Device-DownloadInfo-targetURI: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

