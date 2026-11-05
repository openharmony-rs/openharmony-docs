# @ohos.file.cloudSyncManager (Device-Cloud Sync Management)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @reminder2352-->
<!--Tester: @zsyztt-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=b485e0a7070e3ab71efde69376bb2fde9696c0bc translatedAt=2026-11-03T04:21:19.842Z pushedAt=2026-11-04T03:11:33.512Z nl=1 -->

This module provides cloud drive management applications with device-cloud synchronization management capabilities, including the status and stop reasons of full download, as well as the quantity information of local and cloud files of applications. Developers can use this module in cloud drive management applications to monitor the full download progress of cloud files of applications, handle download stop reasons, and count the quantity and size of local and cloud files of applications.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { cloudSyncManager } from '@kit.CoreFileKit';
```
## DownloadStopReason<sup>20+</sup>

Enumerates the reasons why the full download stops. The default value is **NO_STOP**.

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

Enumerates the full download states.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| Name     | Value | Description      |
| --------- | --- | ---------- |
| RUNNING   | 0   | Downloading.  |
| COMPLETED | 1   | Downloaded.|
| STOPPED   | 2   | Downloading stopped.|

## DownloadProgress<sup>20+</sup>

Describes the full download progress.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

### Properties

| Name           | Type                                       | Read-Only| Optional| Description                                                                         |
| --------------- | ------------------------------------------- | ---- | ---- | ----------------------------------------------------------------------------- |
| state           | [DownloadState](#downloadstate20)           | No  | No  | Download state.                                                             |
| successfulCount | number                                      | No   | No   | Number of successfully downloaded files. Normal value range: [0, INT32_MAX], unit: items. Returns -1 when a progress exception occurs. |
| failedCount     | number                                      | No   | No   | Number of files that failed to download. Normal value range: [0, INT32_MAX], unit: items. Returns -1 when a progress exception occurs. |
| totalCount      | number                                      | No   | No   | Total number of files to be downloaded. Normal value range: [0, INT32_MAX], unit: items. Returns -1 when a progress exception occurs. |
| downloadedSize  | number                                      | No   | No   | Size of downloaded data. Normal value range: [0, INT64_MAX), unit: Byte. Returns INT64_MAX when a progress exception occurs. |
| totalSize       | number                                      | No   | No   | Total size of files to be downloaded. Normal value range: [0, INT64_MAX), unit: Byte. Returns INT64_MAX when a progress exception occurs. |
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
| bothFileCount      | number | No   | No   | Total number of files that exist both locally and in the cloud. Value range: [0, INT32_MAX], unit: count. |
| bothFileTotalSize  | number | No   | No   | Total size of files that exist both locally and in the cloud. Value range: [0, INT64_MAX], unit: Byte. |
