# CloudAssetDownloadProgressInfo (System API)

Describes the progress information about a batch download.

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## autoPauseReason

```TypeScript
readonly autoPauseReason: number
```

Reason for automatic pause.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## downloadEventType

```TypeScript
readonly downloadEventType: CloudAssetDownloadNotifyType
```

Type of event that triggers this update.

**Type:** [CloudAssetDownloadNotifyType](arkts-medialibrary-photoaccesshelper-cloudassetdownloadnotifytype-e-sys.md)

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## fileId

```TypeScript
readonly fileId: number
```

ID of the file being downloaded.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## percent

```TypeScript
readonly percent: number
```

Download completion percentage.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
