# LocalFilePresentStatus (System API)

Specifies a result object that contains the application bundle name and the status information about whether there are files that have not been uploaded to the cloud in the cloud storage space.

**Since:** 23

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## isLocalFilePresent

```TypeScript
isLocalFilePresent: boolean
```

Whether there are local files that have not been synchronized to the cloud in the cloud storage space of the application. The value **true** indicates that such file exists, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.
