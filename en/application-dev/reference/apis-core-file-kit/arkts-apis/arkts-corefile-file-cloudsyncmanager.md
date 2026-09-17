# @ohos.file.cloudSyncManager(Device-Cloud Sync Management)

The **cloudSyncManager** module provides APIs for managing device-cloud sync for applications. You can use the APIs to manage the full download state, the reason why the full download stops, and number of local and cloud files.

**Since:** 10

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## Modules to Import

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [changeAppCloudSwitch](arkts-corefile-cloudsyncmanager-changeappcloudswitch-f-sys.md) | Changes the device-cloud file sync switch for an application. This API uses a promise to return the result. |
| [changeAppCloudSwitch](arkts-corefile-cloudsyncmanager-changeappcloudswitch-f-sys.md) | Changes the device-cloud file sync switch for an application. This API uses an asynchronous callback to return the result. |
| [clean](arkts-corefile-cloudsyncmanager-clean-f-sys.md) | Callback used to clear the cloud data locally. This API uses a promise to return the result. |
| [clean](arkts-corefile-cloudsyncmanager-clean-f-sys.md) | Callback used to clear the cloud data locally. This API uses an asynchronous callback to return the result. |
| [disableCloud](arkts-corefile-cloudsyncmanager-disablecloud-f-sys.md) | Disables device-cloud sync. This API uses a promise to return the result. |
| [disableCloud](arkts-corefile-cloudsyncmanager-disablecloud-f-sys.md) | Disables device-cloud sync. This API uses an asynchronous callback to return the result. |
| [enableCloud](arkts-corefile-cloudsyncmanager-enablecloud-f-sys.md) | Enables device-cloud sync. This API uses a promise to return the result. |
| [enableCloud](arkts-corefile-cloudsyncmanager-enablecloud-f-sys.md) | Enables device-cloud sync. This API uses an asynchronous callback to return the result. |
| [getBundlesLocalFilePresentStatus](arkts-corefile-cloudsyncmanager-getbundleslocalfilepresentstatus-f-sys.md) | Obtains the existence status of local files for multiple applications and checks whether there are files that have not been uploaded to the cloud in the cloud storage space. This API uses a promise to return the result. |
| [getDowngradeDownloadTaskState](arkts-corefile-cloudsyncmanager-getdowngradedownloadtaskstate-f-sys.md) | Supports querying the execution status of full data download tasks for integrated cloud drive applications. |
| [notifyDataChange](arkts-corefile-cloudsyncmanager-notifydatachange-f-sys.md) | Notifies the device-cloud service that the cloud data of a specific application under a specified account has been changed. This API uses a promise to return the result. |
| [notifyDataChange](arkts-corefile-cloudsyncmanager-notifydatachange-f-sys.md) | Notifies the device-cloud service that the cloud data of a specific application under a specified account has been changed. This API uses an asynchronous callback to return the result. |
| [notifyDataChange](arkts-corefile-cloudsyncmanager-notifydatachange-f-sys.md) | Notifies the device-cloud service of the cloud data change information of a specified user. This API uses a promise to return the result. |
| [notifyDataChange](arkts-corefile-cloudsyncmanager-notifydatachange-f-sys.md) | Notifies the device-cloud service of the cloud data change information of a specified user. This API uses an asynchronous callback to return the result. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [DownloadProgress](arkts-corefile-cloudsyncmanager-downloadprogress-c.md) | Describes the full download progress. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [DowngradeDownload](arkts-corefile-cloudsyncmanager-downgradedownload-c-sys.md) | Full download: provides the capability of downloading cloud data for applications. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CloudFileInfo](arkts-corefile-cloudsyncmanager-cloudfileinfo-i.md) | Represents the number and size of local and cloud files of an application. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ExtraData](arkts-corefile-cloudsyncmanager-extradata-i-sys.md) | Represents the cloud data change information. |
| [LocalFilePresentStatus](arkts-corefile-cloudsyncmanager-localfilepresentstatus-i-sys.md) | Specifies a result object that contains the application bundle name and the status information about whether there are files that have not been uploaded to the cloud in the cloud storage space. |
| [TransferProgress](arkts-corefile-cloudsyncmanager-transferprogress-i-sys.md) | Defines the TransferProgress data structure. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [DownloadState](arkts-corefile-cloudsyncmanager-downloadstate-e.md) | Enumerates the full download states. |
| [DownloadStopReason](arkts-corefile-cloudsyncmanager-downloadstopreason-e.md) | Enumerates the reasons why the full download stops. The default value is **NO_STOP**. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [Action](arkts-corefile-cloudsyncmanager-action-e-sys.md) | Enumerates the actions that can be taken to clear local cloud data. |
| [DownloadState](arkts-corefile-cloudsyncmanager-downloadstate-e-sys.md) | Enumerates the full download states. |
| [TransferState](arkts-corefile-cloudsyncmanager-transferstate-e-sys.md) | Describes the state type of transfer task. |
| [TransferStopReason](arkts-corefile-cloudsyncmanager-transferstopreason-e-sys.md) | Describes the state type of transfer stop reason. |
<!--DelEnd-->
