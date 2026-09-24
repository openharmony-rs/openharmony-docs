# PhotoAssetChangeInfos

```TypeScript
interface PhotoAssetChangeInfos
```

Describes the notification information about the change of a media asset.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## assetChangeDatas

```TypeScript
assetChangeDatas: PhotoAssetChangeData[] | null
```

Array of changed media assets. If all media assets need to be queried again, **assetChangeDatas** is null.

**Type:** [PhotoAssetChangeData](arkts-medialibrary-photoaccesshelper-photoassetchangedata-i.md)[] &#124; null

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

Type of the media asset change.

**Type:** [NotifyChangeType](arkts-medialibrary-photoaccesshelper-notifychangetype-e.md)

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
