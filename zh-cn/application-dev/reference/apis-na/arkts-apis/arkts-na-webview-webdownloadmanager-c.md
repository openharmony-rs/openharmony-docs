# WebDownloadManager

You can trigger download manually through this interface, or resume failed or canceled downloads.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class WebDownloadManager--><!--Device-webview-class WebDownloadManager-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## resumeDownload

```TypeScript
static resumeDownload(webDownloadItem: WebDownloadItem): void
```

Resume the canceled or failed download.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebDownloadManager-static resumeDownload(webDownloadItem: WebDownloadItem): void--><!--Device-WebDownloadManager-static resumeDownload(webDownloadItem: WebDownloadItem): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDownloadItem | [WebDownloadItem](arkts-na-webview-webdownloaditem-c.md) | 是 | Download that need to be resume. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100018](../../apis-arkweb/errorcode-webview.md#17100018-没有设置一个委托类来接收下载状态) | No WebDownloadDelegate has been set yet. |

## setDownloadDelegate

```TypeScript
static setDownloadDelegate(delegate: WebDownloadDelegate): void
```

Set a delegate used to receive the progress of the download triggered from WebDownloadManager.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebDownloadManager-static setDownloadDelegate(delegate: WebDownloadDelegate): void--><!--Device-WebDownloadManager-static setDownloadDelegate(delegate: WebDownloadDelegate): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | [WebDownloadDelegate](arkts-na-webview-webdownloaddelegate-c.md) | 是 | Delegate used for download triggered from WebDownloadManager. |

