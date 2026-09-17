# MediaAssetsChangeRequest

Represents a request for changing multiple assets.

**Inheritance/Implementation:** MediaAssetsChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## constructor

```TypeScript
constructor(assets: Array<PhotoAsset>)
```

Constructor.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Assets to change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setFavorite

```TypeScript
setFavorite(favoriteState: boolean): void
```

Favorites or unfavorites this file asset.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| favoriteState | boolean | Yes | Whether to favorite the file. **true** to favorite, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```
