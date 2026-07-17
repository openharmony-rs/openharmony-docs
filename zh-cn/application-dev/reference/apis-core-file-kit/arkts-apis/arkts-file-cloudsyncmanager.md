# @ohos.file.cloudSyncManager

该模块向云盘管理应用提供端云同步管理能力：包括全量下载的状态和停止原因，以及应用本地和云端文件数量信息。

**起始版本：** 10

<!--Device-unnamed-declare namespace cloudSyncManager--><!--Device-unnamed-declare namespace cloudSyncManager-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## 导入模块

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [changeAppCloudSwitch](arkts-corefile-cloudsyncmanager-changeappcloudswitch-f-sys.md#changeappcloudswitch-1) | 异步方法修改应用的端云文件同步开关。使用Promise异步回调。 |
| [changeAppCloudSwitch](arkts-corefile-cloudsyncmanager-changeappcloudswitch-f-sys.md#changeappcloudswitch-2) | 异步方法修改应用的端云文件同步开关。使用callback异步回调。 |
| [clean](arkts-corefile-cloudsyncmanager-clean-f-sys.md#clean-1) | 异步方法清理本地云相关数据。使用Promise异步回调。 |
| [clean](arkts-corefile-cloudsyncmanager-clean-f-sys.md#clean-2) | 异步方法清理本地云相关数据。使用callback异步回调。 |
| [disableCloud](arkts-corefile-cloudsyncmanager-disablecloud-f-sys.md#disablecloud-1) | 异步方法去使能端云协同能力。使用Promise异步回调。 |
| [disableCloud](arkts-corefile-cloudsyncmanager-disablecloud-f-sys.md#disablecloud-2) | 异步方法去使能端云协同能力。使用callback异步回调。 |
| [enableCloud](arkts-corefile-cloudsyncmanager-enablecloud-f-sys.md#enablecloud-1) | 异步方法使能端云协同能力。使用Promise异步回调。 |
| [enableCloud](arkts-corefile-cloudsyncmanager-enablecloud-f-sys.md#enablecloud-2) | 异步方法使能端云协同能力。使用callback异步回调。 |
| [getBundlesLocalFilePresentStatus](arkts-corefile-cloudsyncmanager-getbundleslocalfilepresentstatus-f-sys.md#getbundleslocalfilepresentstatus-1) | 对接入云盘的应用，检测其在云盘存储空间内是否存在未上云文件，支持同时查询多个应用。使用Promise异步回调。 |
| [getDowngradeDownloadTaskState](arkts-corefile-cloudsyncmanager-getdowngradedownloadtaskstate-f-sys.md#getdowngradedownloadtaskstate-1) | 查询接入云盘的应用的全量下载任务状态。使用Promise异步回调。由于返回的DownloadProgress对象中不包含包名信息，因此在批量查询多个应用时，调用方需自行记录应用包名。 |
| [notifyDataChange](arkts-corefile-cloudsyncmanager-notifydatachange-f-sys.md#notifydatachange-1) | 通知端云服务指定账号下的特定应用云数据已发生变更。使用Promise异步回调。 |
| [notifyDataChange](arkts-corefile-cloudsyncmanager-notifydatachange-f-sys.md#notifydatachange-2) | 通知端云服务指定账号下的特定应用云数据已发生变更。使用callback异步回调。 |
| [notifyDataChange](arkts-corefile-cloudsyncmanager-notifydatachange-f-sys.md#notifydatachange-3) | 通知端云服务应用指定用户的云数据变更信息。使用Promise异步回调。 |
| [notifyDataChange](arkts-corefile-cloudsyncmanager-notifydatachange-f-sys.md#notifydatachange-4) | 通知端云服务应用指定用户的云数据变更信息。使用callback异步回调。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [DownloadProgress](arkts-corefile-cloudsyncmanager-downloadprogress-c.md) | 全量下载任务的进度信息。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DowngradeDownload](arkts-corefile-cloudsyncmanager-downgradedownload-c-sys.md) | 全量下载：为云盘管理应用提供集中下载云端数据的能力。云盘全量下载对象，用于支撑云盘管理应用完成云盘文件的全量下载流程。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CloudFileInfo](arkts-corefile-cloudsyncmanager-cloudfileinfo-i.md) | 应用本地和云端文件个数以及大小信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ExtraData](arkts-corefile-cloudsyncmanager-extradata-i-sys.md) | 云端数据变更信息。 |
| [LocalFilePresentStatus](arkts-corefile-cloudsyncmanager-localfilepresentstatus-i-sys.md) | 检测结果对象，包含应用包名及其在云盘存储空间内是否存在未上云文件的状态信息。 |
| [TransferProgress](arkts-corefile-cloudsyncmanager-transferprogress-i-sys.md) | 搬迁任务的进度信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DownloadState](arkts-corefile-cloudsyncmanager-downloadstate-e.md) | 全量下载任务状态的枚举。 |
| [DownloadStopReason](arkts-corefile-cloudsyncmanager-downloadstopreason-e.md) | 全量下载停止原因的枚举，默认值为NO_STOP。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Action](arkts-corefile-cloudsyncmanager-action-e-sys.md) | 清理本地云相关数据时的Action，为枚举类型。 |
| [DownloadState](arkts-corefile-cloudsyncmanager-downloadstate-e-sys.md) | 全量下载任务状态的枚举。 |
| [TransferState](arkts-corefile-cloudsyncmanager-transferstate-e-sys.md) | 搬迁任务状态的枚举。 |
| [TransferStopReason](arkts-corefile-cloudsyncmanager-transferstopreason-e-sys.md) | 搬迁停止原因的枚举。 |
<!--DelEnd-->

