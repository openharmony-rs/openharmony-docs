# WebDownloadManager

可以通过该类提供的接口来恢复失败的下载任务。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-webview-class WebDownloadManager--><!--Device-webview-class WebDownloadManager-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## resumeDownload

```TypeScript
static resumeDownload(webDownloadItem: WebDownloadItem): void
```

恢复一个失败的下载任务。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadManager-static resumeDownload(webDownloadItem: WebDownloadItem): void--><!--Device-WebDownloadManager-static resumeDownload(webDownloadItem: WebDownloadItem): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDownloadItem | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 待恢复的下载任务。 |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadManager-static setDownloadDelegate(delegate: WebDownloadDelegate): void--><!--Device-WebDownloadManager-static setDownloadDelegate(delegate: WebDownloadDelegate): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用来接收下载进度的委托。 |

