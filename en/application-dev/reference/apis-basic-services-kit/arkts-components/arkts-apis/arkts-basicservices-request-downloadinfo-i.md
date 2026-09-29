# DownloadInfo

```TypeScript
interface DownloadInfo
```

Defines the download task information, which is the callback parameter of the [getTaskInfo](arkts-basicservices-request-downloadtask-i.md#gettaskinfo) API.

**Since:** 7

<!--Device-request-interface DownloadInfo--><!--Device-request-interface DownloadInfo-End-->

**System capability:** SystemCapability.MiscServices.Download

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## description

```TypeScript
description: string
```

Description of the download task.

**Type:** string

**Since:** 7

<!--Device-DownloadInfo-description: string--><!--Device-DownloadInfo-description: string-End-->

**System capability:** SystemCapability.MiscServices.Download

## downloadedBytes

```TypeScript
downloadedBytes: number
```

Real-time download size, in bytes.

**Type:** number

**Since:** 7

<!--Device-DownloadInfo-downloadedBytes: long--><!--Device-DownloadInfo-downloadedBytes: long-End-->

**System capability:** SystemCapability.MiscServices.Download

## downloadId

```TypeScript
downloadId: number
```

Download task ID.

**Type:** number

**Since:** 7

<!--Device-DownloadInfo-downloadId: long--><!--Device-DownloadInfo-downloadId: long-End-->

**System capability:** SystemCapability.MiscServices.Download

## downloadTitle

```TypeScript
downloadTitle: string
```

Name of the download task.

**Type:** string

**Since:** 7

<!--Device-DownloadInfo-downloadTitle: string--><!--Device-DownloadInfo-downloadTitle: string-End-->

**System capability:** SystemCapability.MiscServices.Download

## downloadTotalBytes

```TypeScript
downloadTotalBytes: number
```

Total size of the files to download, in bytes.

**Type:** number

**Since:** 7

<!--Device-DownloadInfo-downloadTotalBytes: long--><!--Device-DownloadInfo-downloadTotalBytes: long-End-->

**System capability:** SystemCapability.MiscServices.Download

## failedReason

```TypeScript
failedReason: number
```

Cause of the download failure. The value can be any constant in [Download Error Codes](../../../reference/apis-basic-services-kit/js-apis-request.md#constants).

**Type:** number

**Since:** 7

<!--Device-DownloadInfo-failedReason: int--><!--Device-DownloadInfo-failedReason: int-End-->

**System capability:** SystemCapability.MiscServices.Download

## fileName

```TypeScript
fileName: string
```

Name of the downloaded file.

**Type:** string

**Since:** 7

<!--Device-DownloadInfo-fileName: string--><!--Device-DownloadInfo-fileName: string-End-->

**System capability:** SystemCapability.MiscServices.Download

## filePath

```TypeScript
filePath: string
```

URI of the saved file.

**Type:** string

**Since:** 7

<!--Device-DownloadInfo-filePath: string--><!--Device-DownloadInfo-filePath: string-End-->

**System capability:** SystemCapability.MiscServices.Download

## pausedReason

```TypeScript
pausedReason: number
```

Cause of download pause. The value can be any constant in [Causes of Download Pause](../../../reference/apis-basic-services-kit/js-apis-request.md#constants).

**Type:** number

**Since:** 7

<!--Device-DownloadInfo-pausedReason: int--><!--Device-DownloadInfo-pausedReason: int-End-->

**System capability:** SystemCapability.MiscServices.Download

## status

```TypeScript
status: number
```

Download task status code. The value can be any constant in [Download Task Status Codes](../../../reference/apis-basic-services-kit/js-apis-request.md#constants).

**Type:** number

**Since:** 7

<!--Device-DownloadInfo-status: int--><!--Device-DownloadInfo-status: int-End-->

**System capability:** SystemCapability.MiscServices.Download

## targetURI

```TypeScript
targetURI: string
```

URI of the downloaded file.

**Type:** string

**Since:** 7

<!--Device-DownloadInfo-targetURI: string--><!--Device-DownloadInfo-targetURI: string-End-->

**System capability:** SystemCapability.MiscServices.Download
