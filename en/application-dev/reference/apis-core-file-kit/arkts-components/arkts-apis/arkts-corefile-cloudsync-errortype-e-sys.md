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

## RESPONSE_TIME_OUT

```TypeScript
RESPONSE_TIME_OUT = 9
```

Upload aborted due to cloud response time out.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## UNKNOWN_ERROR

```TypeScript
UNKNOWN_ERROR = 10
```

Upload aborted due to unknown error.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.
