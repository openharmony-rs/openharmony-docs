# DownloadStopReason

```TypeScript
enum DownloadStopReason
```

Enumerates the reasons why the full download stops. The default value is **NO_STOP**.

**Since:** 20

<!--Device-cloudSyncManager-enum DownloadStopReason--><!--Device-cloudSyncManager-enum DownloadStopReason-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## APP_UNLOAD

```TypeScript
APP_UNLOAD = 5
```

Downloading. The application is uninstalled.

**Since:** 20

<!--Device-DownloadStopReason-APP_UNLOAD = 5--><!--Device-DownloadStopReason-APP_UNLOAD = 5-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## LOCAL_STORAGE_FULL

```TypeScript
LOCAL_STORAGE_FULL = 2
```

Downloading. The device storage is full.

**Since:** 20

<!--Device-DownloadStopReason-LOCAL_STORAGE_FULL = 2--><!--Device-DownloadStopReason-LOCAL_STORAGE_FULL = 2-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## NETWORK_UNAVAILABLE

```TypeScript
NETWORK_UNAVAILABLE = 1
```

Downloading. Mobile network and Wi-Fi are unavailable.

**Since:** 20

<!--Device-DownloadStopReason-NETWORK_UNAVAILABLE = 1--><!--Device-DownloadStopReason-NETWORK_UNAVAILABLE = 1-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## NO_STOP

```TypeScript
NO_STOP = 0
```

Downloading.

**Since:** 20

<!--Device-DownloadStopReason-NO_STOP = 0--><!--Device-DownloadStopReason-NO_STOP = 0-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## OTHER_REASON

```TypeScript
OTHER_REASON = 6
```

Downloading. The download stops due to other reasons, for example, the cloud server does not respond.

**Since:** 20

<!--Device-DownloadStopReason-OTHER_REASON = 6--><!--Device-DownloadStopReason-OTHER_REASON = 6-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## TEMPERATURE_LIMIT

```TypeScript
TEMPERATURE_LIMIT = 3
```

Downloading. The device temperature exceeds the upper limit.

**Since:** 20

<!--Device-DownloadStopReason-TEMPERATURE_LIMIT = 3--><!--Device-DownloadStopReason-TEMPERATURE_LIMIT = 3-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## USER_STOPPED

```TypeScript
USER_STOPPED = 4
```

Downloading. The user stops the download.

**Since:** 20

<!--Device-DownloadStopReason-USER_STOPPED = 4--><!--Device-DownloadStopReason-USER_STOPPED = 4-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager
