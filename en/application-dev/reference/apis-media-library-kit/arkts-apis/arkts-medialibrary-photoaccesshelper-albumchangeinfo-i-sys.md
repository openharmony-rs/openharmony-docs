# AlbumChangeInfo

```TypeScript
interface AlbumChangeInfo
```

Describes the information about an album.

**Since:** 20

<!--Device-photoAccessHelper-interface AlbumChangeInfo--><!--Device-photoAccessHelper-interface AlbumChangeInfo-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumOrder

```TypeScript
albumOrder?: number
```

Sorting value of the album.

**Type:** number

**Since:** 23

<!--Device-AlbumChangeInfo-albumOrder?: int--><!--Device-AlbumChangeInfo-albumOrder?: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## coverInfo

```TypeScript
coverInfo?: PhotoAssetChangeInfo
```

Information of the album cover asset.

**Type:** [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i.md)

**Since:** 20

<!--Device-AlbumChangeInfo-coverInfo?: PhotoAssetChangeInfo--><!--Device-AlbumChangeInfo-coverInfo?: PhotoAssetChangeInfo-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## hidden

```TypeScript
hidden?: boolean
```

Whether the album is hidden. **true** if hidden, **false** otherwise.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-AlbumChangeInfo-hidden?: boolean--><!--Device-AlbumChangeInfo-hidden?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## hiddenCount

```TypeScript
hiddenCount: number
```

Number of hidden assets in the album.

**Type:** number

**Since:** 20

<!--Device-AlbumChangeInfo-hiddenCount: int--><!--Device-AlbumChangeInfo-hiddenCount: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## hiddenCoverInfo

```TypeScript
hiddenCoverInfo?: PhotoAssetChangeInfo
```

Information of the hidden album cover asset.

**Type:** [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i.md)

**Since:** 20

<!--Device-AlbumChangeInfo-hiddenCoverInfo?: PhotoAssetChangeInfo--><!--Device-AlbumChangeInfo-hiddenCoverInfo?: PhotoAssetChangeInfo-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## hiddenCoverUri

```TypeScript
hiddenCoverUri: string
```

URI of the hidden cover asset in the album.

**Type:** string

**Since:** 20

<!--Device-AlbumChangeInfo-hiddenCoverUri: string--><!--Device-AlbumChangeInfo-hiddenCoverUri: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## isCoverChanged

```TypeScript
isCoverChanged: boolean
```

Whether the file content of the album cover has changed. **true** if changed, **false** otherwise.

**Type:** boolean

**Since:** 20

<!--Device-AlbumChangeInfo-isCoverChanged: boolean--><!--Device-AlbumChangeInfo-isCoverChanged: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## isHiddenCoverChanged

```TypeScript
isHiddenCoverChanged: boolean
```

Whether the file content of the hidden album cover has changed. **true** if changed, **false** otherwise.

**Type:** boolean

**Since:** 20

<!--Device-AlbumChangeInfo-isHiddenCoverChanged: boolean--><!--Device-AlbumChangeInfo-isHiddenCoverChanged: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## lpath

```TypeScript
lpath?: string
```

The virtual path of album.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AlbumChangeInfo-lpath?: string--><!--Device-AlbumChangeInfo-lpath?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## orderSection

```TypeScript
orderSection?: number
```

Section that defines the order of the album, specifying where the album is displayed in the Gallery.

**Type:** number

**Since:** 23

<!--Device-AlbumChangeInfo-orderSection?: int--><!--Device-AlbumChangeInfo-orderSection?: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## shareRiskStatus

```TypeScript
shareRiskStatus?: ShareAlbumRiskStatus
```

The risk status of share album.

**Type:** [ShareAlbumRiskStatus](arkts-medialibrary-photoaccesshelper-sharealbumriskstatus-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AlbumChangeInfo-shareRiskStatus?: ShareAlbumRiskStatus--><!--Device-AlbumChangeInfo-shareRiskStatus?: ShareAlbumRiskStatus-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
