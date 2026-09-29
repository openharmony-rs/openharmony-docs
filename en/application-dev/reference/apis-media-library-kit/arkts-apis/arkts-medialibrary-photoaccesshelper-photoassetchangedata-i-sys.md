# PhotoAssetChangeData

```TypeScript
interface PhotoAssetChangeData
```

Describes the change data of a media asset.

**Since:** 20

<!--Device-photoAccessHelper-interface PhotoAssetChangeData--><!--Device-photoAccessHelper-interface PhotoAssetChangeData-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## thumbnailChangeStatus

```TypeScript
thumbnailChangeStatus: ThumbnailChangeStatus
```

Change status of the thumbnail (image/video).

**Type:** [ThumbnailChangeStatus](arkts-medialibrary-photoaccesshelper-thumbnailchangestatus-e-sys.md)

**Since:** 20

<!--Device-PhotoAssetChangeData-thumbnailChangeStatus: ThumbnailChangeStatus--><!--Device-PhotoAssetChangeData-thumbnailChangeStatus: ThumbnailChangeStatus-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## version

```TypeScript
version: number
```

Version number of the media asset notification, which is used to determine the order of notifications.

**Type:** number

**Since:** 20

<!--Device-PhotoAssetChangeData-version: long--><!--Device-PhotoAssetChangeData-version: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
