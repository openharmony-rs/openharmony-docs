# AlbumChangeData

Describes the change data of an album.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumAfterChange

```TypeScript
albumAfterChange: AlbumChangeInfo | null
```

Data of the album after change. In the case of album deletion, **albumAfterChange** is null.

**Type:** [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i.md) &#124; null

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumBeforeChange

```TypeScript
albumBeforeChange: AlbumChangeInfo | null
```

Data of the album before change. If an album is added, **albumBeforeChange** is null.

**Type:** [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i.md) &#124; null

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
