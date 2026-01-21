# @ohos.file.cloudSyncManager (Device-Cloud Sync Management)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @Hermits; @reminder2352-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

The **cloudSyncManager** module provides APIs for managing device-cloud synergy for applications. You can use the APIs to enable or disable device-cloud synergy, change the device-cloud sync switch for an application, notify cloud data changes, and clear or retain cloud files when a cloud account exits.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { cloudSyncManager } from '@kit.CoreFileKit';
```
## DownloadStopReason<sup>20+</sup>

Enumerates the reasons why the download stops. The default value is **NO_STOP**.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| Name               | Value | Description                                                  |
| ------------------- | --- | ------------------------------------------------------ |
| NO_STOP             | 0   | Downloading.                                        |
| NETWORK_UNAVAILABLE | 1   | Downloading. Mobile network and Wi-Fi are unavailable.              |
| LOCAL_STORAGE_FULL  | 2   | Downloading. The device storage is full.                        |
| TEMPERATURE_LIMIT   | 3   | Downloading. The device temperature exceeds the upper limit.                            |
| USER_STOPPED        | 4   | Downloading. The user stops the download.                      |
| APP_UNLOAD          | 5   | Downloading. The application is uninstalled.                    |
| OTHER_REASON        | 6   | Downloading. The download stops due to other reasons, for example, the cloud server does not respond.|

## DownloadState<sup>20+</sup>

Enumerates the download states.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| Name     | Value | Description      |
| --------- | --- | ---------- |
| RUNNING   | 0   | Downloading.  |
| COMPLETED | 1   | Downloaded.|
| STOPPED   | 2   | Downloading stopped.|

## DownloadProgress<sup>20+</sup>

Represents the downgrade download progress.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

### Properties

| Name           | Type                                       | Read-Only| Optional| Description                                                                         |
| --------------- | ------------------------------------------- | ---- | ---- | ----------------------------------------------------------------------------- |
| state           | [DownloadState](#downloadstate20)           | No  | No  | Download state.                                                             |
| successfulCount | number                                      | No  | No  | Number of downloaded files. The value range is [0, INT32_MAX]. If the progress is abnormal, **-1** is returned.       |
| failedCount     | number                                      | No  | No  | Number of files that fail to be downloaded. The value range is [0, INT32_MAX]. If the progress is abnormal, **-1** is returned.     |
| totalCount      | number                                      | No  | No  | Total number of files to be downloaded. The value range is [0, INT32_MAX]. If the progress is abnormal, **-1** is returned.       |
| downloadedSize  | number                                      | No  | No  | Size of the downloaded data, in bytes. The value range is [0, INT64_MAX). If the progress is abnormal, **INT64_MAX** is returned.|
| totalSize       | number                                      | No  | No  | Total size of the files to be downloaded, in bytes. The value range is [0, INT64_MAX). If the progress is abnormal, **INT64_MAX** is returned.|
| stopReason      | [DownloadStopReason](#downloadstopreason20) | No  | No  | Reason why the download stops.                                                             |

## CloudFileInfo<sup>20+</sup>

Represents the number and size of local and cloud files of an application.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

### Properties

| Name              | Type  | Read-Only| Optional| Description                                                            |
| ------------------ | ------ | ---- | ---- | ---------------------------------------------------------------- |
| cloudFileCount     | number | No  | No  | Total number of cloud files that are not downloaded locally. The value range is [0, INT32_MAX].  |
| cloudFileTotalSize | number | No  | No  | Total size of cloud files that are not downloaded locally, in bytes. The value range is [0, INT64_MAX].|
| localFileCount     | number | No  | No  | Total number of local files that are not uploaded to the cloud. The value range is [0, INT32_MAX].  |
| localFileTotalSize | number | No  | No  | Total size of local files that are not uploaded to the cloud, in bytes. The value range is [0, INT64_MAX].|
| bothFileCount      | number | No  | No  | Total number of local files that have been uploaded to the cloud. The value range is [0, INT32_MAX].  |
| bothFileTotalSize | number | No  | No  | Total size of local files that have been uploaded to the cloud, in bytes. The value range is [0, INT64_MAX].|
