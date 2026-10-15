# Action (System API)

```TypeScript
enum Action
```

Enumerates the actions that can be taken to clear local cloud data.

**Since:** 10

<!--Device-cloudSyncManager-enum Action--><!--Device-cloudSyncManager-enum Action-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## CLEAR_DATA

```TypeScript
CLEAR_DATA = 1
```

Clear the cloud identifier and the files cached locally.

**Since:** 10

<!--Device-Action-CLEAR_DATA = 1--><!--Device-Action-CLEAR_DATA = 1-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## RETAIN_DATA

```TypeScript
RETAIN_DATA = 0
```

Clear the cloud identifier but retain the files cached locally.

**Since:** 10

<!--Device-Action-RETAIN_DATA = 0--><!--Device-Action-RETAIN_DATA = 0-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.
