# ClearAction (System API)

```TypeScript
enum ClearAction
```

Enumerates the operations for clearing the downloaded cloud data locally.

**Since:** 10

<!--Device-cloudData-enum ClearAction--><!--Device-cloudData-enum ClearAction-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## CLEAR_CLOUD_DATA_AND_INFO

```TypeScript
CLEAR_CLOUD_DATA_AND_INFO = 1
```

Clear the data downloaded from the cloud, excluding the cloud data that has been modified locally.

**Since:** 10

<!--Device-ClearAction-CLEAR_CLOUD_DATA_AND_INFO = 1--><!--Device-ClearAction-CLEAR_CLOUD_DATA_AND_INFO = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## CLEAR_CLOUD_INFO

```TypeScript
CLEAR_CLOUD_INFO = 0
```

Clear the cloud identifier of the data downloaded from the cloud and retain the data locally.

**Since:** 10

<!--Device-ClearAction-CLEAR_CLOUD_INFO = 0--><!--Device-ClearAction-CLEAR_CLOUD_INFO = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## CLEAR_CLOUD_NONE

```TypeScript
CLEAR_CLOUD_NONE = 2
```

Does not clear any data.

**Since:** 23

<!--Device-ClearAction-CLEAR_CLOUD_NONE = 2--><!--Device-ClearAction-CLEAR_CLOUD_NONE = 2-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
