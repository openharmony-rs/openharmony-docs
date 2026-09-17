# PhotoAssetChangeInfo

Describes the information about a media asset.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumUri

```TypeScript
albumUri: string
```

URI of the album that the media asset belongs to.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isFavorite

```TypeScript
isFavorite: boolean
```

Whether the media asset is marked as a favorite. **true** if marked, **false** otherwise.

**Type:** boolean

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mediaType

```TypeScript
mediaType: PhotoType
```

Type of the media asset (image or video).

**Type:** [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md)

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uri

```TypeScript
uri: string
```

URI of the media asset.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
