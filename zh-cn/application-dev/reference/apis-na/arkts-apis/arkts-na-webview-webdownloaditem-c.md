# WebDownloadItem

Represents a download task, You can use this object to operate the corresponding download task.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-class WebDownloadItem--><!--Device-webview-class WebDownloadItem-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## cancel

```TypeScript
cancel(): void
```

Cancel the web download.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-cancel(): void--><!--Device-WebDownloadItem-cancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deserialize

```TypeScript
static deserialize(serializedData: Uint8Array): WebDownloadItem
```

Deserialize web download from typed array.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-static deserialize(serializedData: Uint8Array): WebDownloadItem--><!--Device-WebDownloadItem-static deserialize(serializedData: Uint8Array): WebDownloadItem-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serializedData | Uint8Array | 是 | The serialized data. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebDownloadItem](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webdownloaditem-c.md) | Deserialize the serialized data into a WebDownloadItem. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types. <br>2. Parameter verification failed. |

## getCurrentSpeed

```TypeScript
getCurrentSpeed(): int
```

Get current speed, in bytes per second.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getCurrentSpeed(): int--><!--Device-WebDownloadItem-getCurrentSpeed(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Returns the current download speed. |

## getFullPath

```TypeScript
getFullPath(): string
```

Get full path of the web download.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getFullPath(): string--><!--Device-WebDownloadItem-getFullPath(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the full path of the download. |

## getGuid

```TypeScript
getGuid(): string
```

Get guid.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getGuid(): string--><!--Device-WebDownloadItem-getGuid(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the download's guid. |

## getLastErrorCode

```TypeScript
getLastErrorCode(): WebDownloadErrorCode
```

Get last error code of the web download.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getLastErrorCode(): WebDownloadErrorCode--><!--Device-WebDownloadItem-getLastErrorCode(): WebDownloadErrorCode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebDownloadErrorCode](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webdownloaderrorcode-e.md) | Returns the last error code. |

## getMethod

```TypeScript
getMethod(): string
```

Get http method of the web download request.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getMethod(): string--><!--Device-WebDownloadItem-getMethod(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the http request method. |

## getMimeType

```TypeScript
getMimeType(): string
```

Get mime type of the web download.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getMimeType(): string--><!--Device-WebDownloadItem-getMimeType(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the mimetype. |

## getOriginalUrl

```TypeScript
getOriginalUrl(): string
```

Get the original url of the web download.

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebDownloadItem-getOriginalUrl(): string--><!--Device-WebDownloadItem-getOriginalUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the original url of the download. |

## getPercentComplete

```TypeScript
getPercentComplete(): int
```

Get percent complete.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getPercentComplete(): int--><!--Device-WebDownloadItem-getPercentComplete(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Returns -1 if progress is unknown. 100 if the download is already complete. |

## getReceivedBytes

```TypeScript
getReceivedBytes(): long
```

Get received bytes.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getReceivedBytes(): long--><!--Device-WebDownloadItem-getReceivedBytes(): long-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the received bytes. |

## getReferrerUrl

```TypeScript
getReferrerUrl(): string
```

Get the referrer url of the web download.

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebDownloadItem-getReferrerUrl(): string--><!--Device-WebDownloadItem-getReferrerUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the referrer url of the download. |

## getState

```TypeScript
getState(): WebDownloadState
```

Get state of the web download.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getState(): WebDownloadState--><!--Device-WebDownloadItem-getState(): WebDownloadState-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebDownloadState](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webdownloadstate-e.md) | Returns the current download state. |

## getSuggestedFileName

```TypeScript
getSuggestedFileName(): string
```

Get suggested file name of the web download request.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getSuggestedFileName(): string--><!--Device-WebDownloadItem-getSuggestedFileName(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the suggested file name. |

## getTotalBytes

```TypeScript
getTotalBytes(): long
```

Get total bytes.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getTotalBytes(): long--><!--Device-WebDownloadItem-getTotalBytes(): long-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the total bytes received, -1 if the total size is unknown. |

## getUrl

```TypeScript
getUrl(): string
```

Get url of the web download request.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-getUrl(): string--><!--Device-WebDownloadItem-getUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the url. |

## pause

```TypeScript
pause(): void
```

Pause the web download.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-pause(): void--><!--Device-WebDownloadItem-pause(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100019](../../apis-arkweb/errorcode-webview.md#17100019-下载还没开始) | The download task is not started yet. |

## resume

```TypeScript
resume(): void
```

Resume the web download. Use WebDownloadManager.resumeDownload to resume deserialized downloads. WebDownloadItem.resume is only used to resume the currently paused download.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-resume(): void--><!--Device-WebDownloadItem-resume(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100016](../../apis-arkweb/errorcode-webview.md#17100016-下载任务没有处于暂停状态) | The download task is not paused. |

## serialize

```TypeScript
serialize(): Uint8Array
```

Serialize web download to typed array.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-serialize(): Uint8Array--><!--Device-WebDownloadItem-serialize(): Uint8Array-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | Returns the serialized data. |

## start

```TypeScript
start(downloadPath: string): void
```

Start the web download. Used in onBeforeDownload, If you want to start the current download, call this function.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDownloadItem-start(downloadPath: string): void--><!--Device-WebDownloadItem-start(downloadPath: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| downloadPath | string | 是 | The content will be downloaded to this file. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types. <br>2. Parameter verification failed. |

