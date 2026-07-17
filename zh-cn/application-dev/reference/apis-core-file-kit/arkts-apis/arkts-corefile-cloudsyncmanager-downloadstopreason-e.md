# DownloadStopReason

全量下载停止原因的枚举，默认值为NO_STOP。

**起始版本：** 20

<!--Device-cloudSyncManager-enum DownloadStopReason--><!--Device-cloudSyncManager-enum DownloadStopReason-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## NO_STOP

```TypeScript
NO_STOP = 0
```

下载中未停止。

**起始版本：** 20

<!--Device-DownloadStopReason-NO_STOP = 0--><!--Device-DownloadStopReason-NO_STOP = 0-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## NETWORK_UNAVAILABLE

```TypeScript
NETWORK_UNAVAILABLE = 1
```

下载过程中，移动数据网络和WIFI均不可用。

**起始版本：** 20

<!--Device-DownloadStopReason-NETWORK_UNAVAILABLE = 1--><!--Device-DownloadStopReason-NETWORK_UNAVAILABLE = 1-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## LOCAL_STORAGE_FULL

```TypeScript
LOCAL_STORAGE_FULL = 2
```

下载过程中，当前设备空间不足。

**起始版本：** 20

<!--Device-DownloadStopReason-LOCAL_STORAGE_FULL = 2--><!--Device-DownloadStopReason-LOCAL_STORAGE_FULL = 2-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## TEMPERATURE_LIMIT

```TypeScript
TEMPERATURE_LIMIT = 3
```

下载过程中，设备温度过高。

**起始版本：** 20

<!--Device-DownloadStopReason-TEMPERATURE_LIMIT = 3--><!--Device-DownloadStopReason-TEMPERATURE_LIMIT = 3-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## USER_STOPPED

```TypeScript
USER_STOPPED = 4
```

下载过程中，客户端主动停止下载。

**起始版本：** 20

<!--Device-DownloadStopReason-USER_STOPPED = 4--><!--Device-DownloadStopReason-USER_STOPPED = 4-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## APP_UNLOAD

```TypeScript
APP_UNLOAD = 5
```

下载过程中，云文件所属应用被卸载。

**起始版本：** 20

<!--Device-DownloadStopReason-APP_UNLOAD = 5--><!--Device-DownloadStopReason-APP_UNLOAD = 5-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## OTHER_REASON

```TypeScript
OTHER_REASON = 6
```

下载过程中，因其他原因停止下载，如：云服务器未响应等。

**起始版本：** 20

<!--Device-DownloadStopReason-OTHER_REASON = 6--><!--Device-DownloadStopReason-OTHER_REASON = 6-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

