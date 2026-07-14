# WebDownloadItem

表示下载任务，您可以使用此对象来操作相应的下载任务。
当前WebDownloadItem支持的下载文件名最长长度为255字节。

**起始版本：** 11

**系统能力：** SystemCapability.Web.Webview.Core

## cancel

```TypeScript
cancel(): void
```

取消一个正在下载的下载任务。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## deserialize

```TypeScript
static deserialize(serializedData: Uint8Array): WebDownloadItem
```

将序列化后的字节数组反序列化为一个WebDownloadItem对象。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serializedData | Uint8Array | 是 | 序列化后的下载。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WebDownloadItem | - 从字节数组反序列化为一个WebDownloadItem对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types.<br>2. Parameter verification failed. |

## getCurrentSpeed

```TypeScript
getCurrentSpeed(): number
```

获取下载的速度，单位：字节每秒。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | - 下载的速度（字节每秒）。 |

## getFullPath

```TypeScript
getFullPath(): string
```

获取下载文件在磁盘上的全路径。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 下载文件在磁盘上的全路径。 |

## getGuid

```TypeScript
getGuid(): string
```

获取下载任务的唯一ID。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 下载任务的唯一ID。 |

## getLastErrorCode

```TypeScript
getLastErrorCode(): WebDownloadErrorCode
```

获取下载的错误码。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WebDownloadErrorCode | - 下载发生错误的时候的错误码。 |

## getMethod

```TypeScript
getMethod(): string
```

获取下载任务的请求方式。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 下载的请求方式。 |

## getMimeType

```TypeScript
getMimeType(): string
```

获取下载的媒体类型（例如，一个声音文件可能被标记为 audio/ogg ，一个图像文件可能是 image/png）。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 下载的媒体类型（例如，一个声音文件可能被标记为 audio/ogg ，一个图像文件可能是 image/png）。 |

## getOriginalUrl

```TypeScript
getOriginalUrl(): string
```

获取下载文件的原始URL地址。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 下载文件的原始URL地址。 |

## getPercentComplete

```TypeScript
getPercentComplete(): number
```

获取下载的进度，100代表下载完成。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | - 下载完成的进度，100代表下载完成，-1代表进度未知。 |

## getReceivedBytes

```TypeScript
getReceivedBytes(): number
```

获取已经接收的字节数。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | - 已经接收的字节数。 |

## getReferrerUrl

```TypeScript
getReferrerUrl(): string
```

获取下载文件的referrer地址。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 下载文件的referrer地址。 |

## getState

```TypeScript
getState(): WebDownloadState
```

获取下载的状态。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WebDownloadState | - 下载的状态。 |

## getSuggestedFileName

```TypeScript
getSuggestedFileName(): string
```

获取下载的建议文件名。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 下载的建议文件名。 |

## getTotalBytes

```TypeScript
getTotalBytes(): number
```

获取待下载文件的总长度。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | - 待下载文件的总长度，-1代表总大小未知。单位：字节。 |

## getUrl

```TypeScript
getUrl(): string
```

获取下载的请求地址。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 下载的请求地址。 |

## pause

```TypeScript
pause(): void
```

暂停一个正在下载的下载任务。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100019](../errorcode-webview.md#17100019-下载还没开始) | The download task is not started yet. |

## resume

```TypeScript
resume(): void
```

恢复一个暂停的下载任务。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100016](../errorcode-webview.md#17100016-下载任务没有处于暂停状态) | The download task is not paused. |

## serialize

```TypeScript
serialize(): Uint8Array
```

将失败的下载序列化到一个字节数组。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | - 失败的下载序列化后的字节数组。 |

## start

```TypeScript
start(downloadPath: string): void
```

开始下载到指定目录，参数为下载文件的磁盘存储路径（包含文件名）。

> **说明：**
>
> 该接口应在WebDownloadDelegate的onBeforeDownload回调中使用。若在WebDownloadDelegate的onBeforeDownload中未调用start('xxx')，则下载任务将保持在
> PENDING状态。处于PENDING状态的下载会将文件下载到临时目录，临时文件会在WebDownloadItem.start指定目标路径后被重命名为目标路径，未下载完成的部分会在WebDownloadItem.start
> 指定目标路径后直接下载到目标路径。如果在调用WebDownloadItem.start之前不希望下载到临时文件路径，可以先通过WebDownloadItem.cancel取消当前下载任务，随后通过
> WebDownloadManager.resumeDownload恢复被取消的下载任务。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| downloadPath | string | 是 | 下载文件的路径（包含文件名），路径长度与文件管理中长度一致，最长255字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types.<br>2. Parameter verification failed. |

