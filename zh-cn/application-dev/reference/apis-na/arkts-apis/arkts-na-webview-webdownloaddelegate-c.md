# WebDownloadDelegate

The download state is notified through this delegate.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class WebDownloadDelegate--><!--Device-webview-class WebDownloadDelegate-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onBeforeDownload

```TypeScript
onBeforeDownload(callback: Callback<WebDownloadItem>): void
```

Callback will be triggered before web download start.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebDownloadDelegate-onBeforeDownload(callback: Callback<WebDownloadItem>): void--><!--Device-WebDownloadDelegate-onBeforeDownload(callback: Callback<WebDownloadItem>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[WebDownloadItem](arkts-na-webview-webdownloaditem-c.md)&gt; | 是 | The callback of download will be start. |

## onDownloadFailed

```TypeScript
onDownloadFailed(callback: Callback<WebDownloadItem>): void
```

Callback will be triggered when web download is interrupted or canceled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebDownloadDelegate-onDownloadFailed(callback: Callback<WebDownloadItem>): void--><!--Device-WebDownloadDelegate-onDownloadFailed(callback: Callback<WebDownloadItem>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[WebDownloadItem](arkts-na-webview-webdownloaditem-c.md)&gt; | 是 | The callback of download did fail. |

## onDownloadFinish

```TypeScript
onDownloadFinish(callback: Callback<WebDownloadItem>): void
```

Callback will be triggered when web download is completed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebDownloadDelegate-onDownloadFinish(callback: Callback<WebDownloadItem>): void--><!--Device-WebDownloadDelegate-onDownloadFinish(callback: Callback<WebDownloadItem>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[WebDownloadItem](arkts-na-webview-webdownloaditem-c.md)&gt; | 是 | The callback of download did finish. |

## onDownloadUpdated

```TypeScript
onDownloadUpdated(callback: Callback<WebDownloadItem>): void
```

Callback will be triggered when web download is processing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebDownloadDelegate-onDownloadUpdated(callback: Callback<WebDownloadItem>): void--><!--Device-WebDownloadDelegate-onDownloadUpdated(callback: Callback<WebDownloadItem>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[WebDownloadItem](arkts-na-webview-webdownloaditem-c.md)&gt; | 是 | The callback of download did update. |

