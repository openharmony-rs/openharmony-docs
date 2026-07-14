# WebDownloadManager

可以通过该类提供的接口来恢复失败的下载任务。

**起始版本：** 11

**系统能力：** SystemCapability.Web.Webview.Core

## resumeDownload

```TypeScript
static resumeDownload(webDownloadItem: WebDownloadItem): void
```

恢复一个失败的下载任务。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDownloadItem | WebDownloadItem | 是 | 待恢复的下载任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100018](../errorcode-webview.md#17100018-没有设置一个委托类来接收下载状态) | No WebDownloadDelegate has been set yet. |

## setDownloadDelegate

```TypeScript
static setDownloadDelegate(delegate: WebDownloadDelegate): void
```

设置用于接收从WebDownloadManager触发的下载进度的委托。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | WebDownloadDelegate | 是 | 用来接收下载进度的委托。 |

