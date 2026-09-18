# WebDownloadItem

WebDownloadItem is a class in the ArkWeb framework used to represent and manage a single download task. Through the callback parameters of [WebDownloadDelegate](arkts-arkweb-webview-webdownloaddelegate-c.md), an app can obtain a WebDownloadItem instance and then query and control the download task, including starting the download to a specified path, querying the download progress and status, pausing/resuming/canceling the task, and serializing failed tasks for later recovery.

> **NOTE:** 
> 
> - During the download process, the download progress is notified to the user through WebDownloadDelegate, and the user can operate the download task through the WebDownloadItem parameter.
> 
> - The maximum length of the download file path (including the file name) supported by WebDownloadItem is 255bytes&lt;!--RP1--&gt;&lt;!--RP1End--&gt;.

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## cancel

```TypeScript
cancel(): void
```

Cancels the download task.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## deserialize

```TypeScript
static deserialize(serializedData: Uint8Array): WebDownloadItem
```

Deserializes the serialized byte array into a **WebDownloadItem** object.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serializedData | Uint8Array | Yes | Serialized byte array. |

**Return value:**

| Type | Description |
| --- | --- |
| [WebDownloadItem](arkts-arkweb-webview-webdownloaditem-c.md) | **WebDownloadItem** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types.<br>2. Parameter verification failed. |

## getCurrentSpeed

```TypeScript
getCurrentSpeed(): number
```

Obtains the download speed, in bytes per second.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Download speed, in bytes per second. |

## getFullPath

```TypeScript
getFullPath(): string
```

Obtains the full path of the downloaded file on the disk.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Full path of the downloaded file on the disk. |

## getGuid

```TypeScript
getGuid(): string
```

Obtains the unique ID of this download task.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Unique ID of the download task. |

## getLastErrorCode

```TypeScript
getLastErrorCode(): WebDownloadErrorCode
```

Obtains the download error code.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [WebDownloadErrorCode](arkts-arkweb-webview-webdownloaderrorcode-e.md) | Error code when the download fails. |

## getMethod

```TypeScript
getMethod(): string
```

Obtains the request mode of this download task.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Request mode of the download task. |

## getMimeType

```TypeScript
getMimeType(): string
```

Obtains the MIME type of this download task (for example, a sound file may be marked as audio/ogg, and an image file may be image/png).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | MIME type (for example, audio/ogg for a sound file, and image/png for an image file). |

## getOriginalUrl

```TypeScript
getOriginalUrl(): string
```

Obtains the original URL address of the download file.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Original URL address of the download file. |

## getPercentComplete

```TypeScript
getPercentComplete(): number
```

Obtains the download progress. The value **100** indicates that the download is complete.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Download progress. The value **100** indicates that the download is complete, and the value **-1** indicates that the progress is unknown. |

## getReceivedBytes

```TypeScript
getReceivedBytes(): number
```

Obtains the number of received bytes.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of received bytes. |

## getReferrerUrl

```TypeScript
getReferrerUrl(): string
```

Obtains the referrer address of the download file.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Referrer address of the download file. |

## getState

```TypeScript
getState(): WebDownloadState
```

Obtains the download state.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [WebDownloadState](arkts-arkweb-webview-webdownloadstate-e.md) | Download state. |

## getSuggestedFileName

```TypeScript
getSuggestedFileName(): string
```

Obtains the suggested file name for this download task.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Suggested file name. |

## getTotalBytes

```TypeScript
getTotalBytes(): number
```

Obtains the total length of the file to be downloaded.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Total length of the file to be downloaded. The value -1 indicates that the total size is unknown. Unit: byte. |

## getUrl

```TypeScript
getUrl(): string
```

Obtains the download request URL.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Download request URL. |

## pause

```TypeScript
pause(): void
```

Pauses the download task.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100019](../errorcode-webview.md#17100019-download-not-started-yet) | The download task is not started yet. |

## resume

```TypeScript
resume(): void
```

Resumes a download task.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100016](../errorcode-webview.md#17100016-download-task-not-paused) | The download task is not paused. |

## serialize

```TypeScript
serialize(): Uint8Array
```

Serializes the failed download to a byte array.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Byte array into which the failed download is serialized. |

## start

```TypeScript
start(downloadPath: string): void
```

Starts downloading to the specified directory. The parameter specifies the disk storage path (including the file name) of the download file.

> **NOTE:** 
> 
> This API must be used in the **onBeforeDownload** callback of **WebDownloadDelegate**. If it is not called in
> the callback, the download task remains in the PENDING state and is downloaded to a temporary directory. After
> the target path is specified by **WebDownloadItem.start**, the temporary files are renamed to the target path
> and the unfinished files are directly downloaded to the target path. If you do not want to download the file to
> the temporary directory before invoking **WebDownloadItem.start**, you can call **WebDownloadItem.cancel** to
> cancel the current download task and then call **WebDownloadManager.resumeDownload** to resume the task.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| downloadPath | string | Yes | Path of the download file (including the file name). The path length is the same as that in the file manager, with a maximum of 255 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types.<br>2. Parameter verification failed. |
