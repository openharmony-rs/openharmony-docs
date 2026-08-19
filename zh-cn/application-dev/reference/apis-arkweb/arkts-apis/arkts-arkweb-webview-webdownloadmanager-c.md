# WebDownloadManager

WebDownloadManager是ArkWeb框架下Web组件下载任务的静态管理类，负责管理所有通过Web组件触发的文件下载流程。开发者可以通过该类设置下载委托以接收下载进度回调，以及恢复失败的下载任务。该类的所有方法均为静态 方法，在整个应用范围内全局生效。 WebDownloadManager与[WebDownloadDelegate](arkts-arkweb-webview-webdownloaddelegate-c.md)、 [WebDownloadItem](arkts-arkweb-webview-webdownloaditem-c.md)配合使用：WebDownloadManager负责下载任务的生命周期管理和委托设置，WebDownloadDelegate负责向应用层 报告下载进度和状态变更事件，WebDownloadItem代表单个下载任务实体，支持暂停、恢复、取消等操作。

**起始版本：** 11

<!--Device-webview-class WebDownloadManager--><!--Device-webview-class WebDownloadManager-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## resumeDownload

```TypeScript
static resumeDownload(webDownloadItem: WebDownloadItem): void
```

恢复一个失败的下载任务，需通过[WebDownloadItem.deserialize](arkts-arkweb-webview-webdownloaditem-c.md#deserialize)方法获取反序列化后的对象，仅适用于之前失败的下载任 务。 > **说明：** > > - 在调用本接口前，若尚未创建Web组件且未执行initializeWebEngine方法完成Web内核初始化，必须先调用initializeWebEngine方法进行初始化，否则接口调用无效。 > > - 必须先调用[setDownloadDelegate](#setdownloaddelegate)设置下载委托，否则会抛出错误码17100018。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadManager-static resumeDownload(webDownloadItem: WebDownloadItem): void--><!--Device-WebDownloadManager-static resumeDownload(webDownloadItem: WebDownloadItem): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDownloadItem | [WebDownloadItem](arkts-arkweb-webview-webdownloaditem-c.md) | 是 | 从序列化数据恢复的下载任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100018](../errorcode-webview.md#17100018-没有设置一个委托类来接收下载状态) | No WebDownloadDelegate has been set yet. |

## setDownloadDelegate

```TypeScript
static setDownloadDelegate(delegate: WebDownloadDelegate): void
```

设置接收从WebDownloadManager触发的下载进度的委托。 > **说明：** > > - 在调用本接口前，若尚未创建Web组件且未执行[initializeWebEngine](arkts-arkweb-webview-webviewcontroller-c.md#initializewebengine)方法，必须先调用该方法完成 > Web内核初始化，否则接口调用无效。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadManager-static setDownloadDelegate(delegate: WebDownloadDelegate): void--><!--Device-WebDownloadManager-static setDownloadDelegate(delegate: WebDownloadDelegate): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | [WebDownloadDelegate](arkts-arkweb-webview-webdownloaddelegate-c.md) | 是 | 用来接收下载进度的委托。 |

