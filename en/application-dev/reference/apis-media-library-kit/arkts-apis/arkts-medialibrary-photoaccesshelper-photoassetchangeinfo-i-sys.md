# PhotoAssetChangeInfo

Describes the information about a media asset.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumChangeInfos

```TypeScript
albumChangeInfos?: AlbumChangeInfo[] | null
```

Smart album change information.

**Type:** [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i.md)[] &#124; null

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## assetSourceType

```TypeScript
assetSourceType?: AssetSourceType
```

The asset source type. Default value: 0.

**Type:** [AssetSourceType](arkts-medialibrary-photoaccesshelper-assetsourcetype-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateAddedMs

```TypeScript
dateAddedMs: number
```

Unix timestamp when the media asset was created, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateDay

```TypeScript
dateDay: string
```

Date when the media asset was created.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateModifiedMs

```TypeScript
dateModifiedMs?: number
```

The modified time of asset. <br>Unit:milliseconds.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateTakenMs

```TypeScript
dateTakenMs: number
```

Unix timestamp when the media asset was captured, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateTrashedMs

```TypeScript
dateTrashedMs: number
```

Unix timestamp when the media asset was deleted, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## displayName

```TypeScript
displayName?: string
```

Display name of the media asset.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## fileId

```TypeScript
fileId: number
```

ID of the media asset.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## hiddenTime

```TypeScript
hiddenTime?: number
```

The hidden time of asset. <br>Unit:milliseconds.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## isHidden

```TypeScript
isHidden: boolean
```

Whether the media asset is hidden. **true** if hidden, **false** otherwise.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## photoVisibility

```TypeScript
photoVisibility?: number
```

The visibility of photo. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## position

```TypeScript
position?: PositionType
```

Position of the media asset.

**Type:** [PositionType](arkts-medialibrary-photoaccesshelper-positiontype-e.md)

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## shareDateDay

```TypeScript
shareDateDay?: number
```

The date day of the share album asset to be shared. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## shareGroup

```TypeScript
shareGroup?: number
```

The group of the share album assets to be shared. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## shareRiskStatus

```TypeScript
shareRiskStatus?: ShareAlbumRiskStatus
```

The risk status of share album asset. The value should be an integer.

**Type:** [ShareAlbumRiskStatus](arkts-medialibrary-photoaccesshelper-sharealbumriskstatus-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## size

```TypeScript
size?: number
```

File size of the media asset, in bytes. The size of a moving photo includes the total size of the image and video.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## strongAssociation

```TypeScript
strongAssociation: StrongAssociationType
```

Strong association type of the media asset.

**Type:** [StrongAssociationType](arkts-medialibrary-photoaccesshelper-strongassociationtype-e-sys.md)

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## thumbnailVisible

```TypeScript
thumbnailVisible: ThumbnailVisibility
```

Accessibility status of the thumbnail.

**Type:** [ThumbnailVisibility](arkts-medialibrary-photoaccesshelper-thumbnailvisibility-e-sys.md)

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
