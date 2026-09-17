# ErrorType

Enumerates the device-cloud sync errors.

- In the current phase, **NETWORK_UNAVAILABLE** is returned only when the mobile data network and Wi-Fi are  
unavailable. If the mobile data network is available, the synchronization can be performed normally.  
- During the sync process, if the battery level is lower than 10% in non-charging scenarios, **BATTERY_LEVEL_LOW**  
will be return when the current upload is complete.  
- When sync is being triggered, if the battery level is lower than 10% in non-charging scenarios, sync is not  
allowed.  
- If the cloud space is insufficient when a file is uploaded, the upload will fail and there is no such a file in  
the cloud.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## NO_ERROR

```TypeScript
NO_ERROR = 0
```

No error.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## NETWORK_UNAVAILABLE

```TypeScript
NETWORK_UNAVAILABLE = 1
```

No network is available.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## WIFI_UNAVAILABLE

```TypeScript
WIFI_UNAVAILABLE = 2
```

Wi-Fi is unavailable.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## BATTERY_LEVEL_LOW

```TypeScript
BATTERY_LEVEL_LOW = 3
```

The battery level is lower than 10%.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## BATTERY_LEVEL_WARNING

```TypeScript
BATTERY_LEVEL_WARNING = 4
```

The battery level is lower than 15%.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## CLOUD_STORAGE_FULL

```TypeScript
CLOUD_STORAGE_FULL = 5
```

The cloud space is insufficient.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## LOCAL_STORAGE_FULL

```TypeScript
LOCAL_STORAGE_FULL = 6
```

The local space is insufficient.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## DEVICE_TEMPERATURE_TOO_HIGH

```TypeScript
DEVICE_TEMPERATURE_TOO_HIGH = 7
```

The device temperature is too high.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## REMOTE_SERVER_ABNORMAL

```TypeScript
REMOTE_SERVER_ABNORMAL = 8
```

The remote service is unavailable.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
