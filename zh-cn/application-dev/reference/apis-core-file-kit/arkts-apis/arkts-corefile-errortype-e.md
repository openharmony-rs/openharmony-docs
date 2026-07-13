# ErrorType

端云同步失败类型，为枚举类型。

- 当前阶段，同步过程中，当开启无限量使用移动数据网络，移动数据网络和WIFI均不可用时，才会返回NETWORK_UNAVAILABLE；开启无限量使用移动数据网络，若有一种类型网络可用，则能正常同步。
- 同步过程中，非充电场景下，电量低于10%，完成当前批上行同步后停止同步，返回低电量；
- 触发同步时，非充电场景下，若电量低于10%，则不允许同步
- 上行时，若云端空间不足，则文件上行失败，云端无该文件记录。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## NO_ERROR

```TypeScript
NO_ERROR = 0
```

没有错误。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## NETWORK_UNAVAILABLE

```TypeScript
NETWORK_UNAVAILABLE = 1
```

所有网络不可用。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## WIFI_UNAVAILABLE

```TypeScript
WIFI_UNAVAILABLE = 2
```

WIFI不可用。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## BATTERY_LEVEL_LOW

```TypeScript
BATTERY_LEVEL_LOW = 3
```

低电量（低于10%）。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## BATTERY_LEVEL_WARNING

```TypeScript
BATTERY_LEVEL_WARNING = 4
```

告警电量（低于15%）。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## CLOUD_STORAGE_FULL

```TypeScript
CLOUD_STORAGE_FULL = 5
```

云端空间不足。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## LOCAL_STORAGE_FULL

```TypeScript
LOCAL_STORAGE_FULL = 6
```

本地空间不足。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## DEVICE_TEMPERATURE_TOO_HIGH

```TypeScript
DEVICE_TEMPERATURE_TOO_HIGH = 7
```

设备温度过高。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## REMOTE_SERVER_ABNORMAL

```TypeScript
REMOTE_SERVER_ABNORMAL = 8
```

远端服务不可用。

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

