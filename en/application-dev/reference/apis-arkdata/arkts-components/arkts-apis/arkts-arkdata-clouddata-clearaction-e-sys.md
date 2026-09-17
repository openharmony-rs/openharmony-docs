# ClearAction (System API)

Enumerates the operations for clearing the downloaded cloud data locally.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## CLEAR_CLOUD_INFO

```TypeScript
CLEAR_CLOUD_INFO = 0
```

Clear the cloud identifier of the data downloaded from the cloud and retain the data locally.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## CLEAR_CLOUD_DATA_AND_INFO

```TypeScript
CLEAR_CLOUD_DATA_AND_INFO = 1
```

Clear the data downloaded from the cloud, excluding the cloud data that has been modified locally.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## CLEAR_CLOUD_NONE

```TypeScript
CLEAR_CLOUD_NONE = 2
```

Does not clear any data.

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
