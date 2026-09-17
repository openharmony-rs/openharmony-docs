# AlbumChangeInfos

Describes the notification information about the change of an album.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumChangeDatas

```TypeScript
albumChangeDatas: AlbumChangeData[] | null
```

Array of changed albums. If all albums need to be queried again, **albumChangeDatas** is null.

**Type:** [AlbumChangeData](arkts-medialibrary-photoaccesshelper-albumchangedata-i.md)[] &#124; null

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isForRecheck

```TypeScript
isForRecheck: boolean
```

Whether the application should query all media assets again. **true** if the application should query all assets again, **false** otherwise.

**NOTE:** 

In scenarios involving bulk asset operations or abnormal notifications, **isForRecheck** will be **true**. In this case, the application should query all assets again.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## type

```TypeScript
type: NotifyChangeType
```

Type of the album change.

**Type:** [NotifyChangeType](arkts-medialibrary-photoaccesshelper-notifychangetype-e.md)

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
