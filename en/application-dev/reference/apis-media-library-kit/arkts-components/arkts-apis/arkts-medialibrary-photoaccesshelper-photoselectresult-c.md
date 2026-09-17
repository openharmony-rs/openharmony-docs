# PhotoSelectResult

Defines information about the images or videos selected.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## contextRecoveryInfo

```TypeScript
contextRecoveryInfo: ContextRecoveryInfo
```

Information about the context of exiting the PhotoPicker. This information is returned when the selection process is complete and is used by the application within **PhotoSelectOptions** during the subsequent launch of the PhotoPicker to restore the state from the previous exit.

**Type:** [ContextRecoveryInfo](arkts-medialibrary-photoaccesshelper-contextrecoveryinfo-c.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isOriginalPhoto

```TypeScript
isOriginalPhoto: boolean
```

Whether the selected media file is the original image. **true** if yes, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## movingPhotoBadgeStates

```TypeScript
movingPhotoBadgeStates: Array<MovingPhotoBadgeStateType>
```

Array of moving photo badge states for the media files selected from Gallery.

If **isMovingPhotoBadgeShown** is set to **true**, this array contains the moving photo badge states. Otherwise, it is empty.

**Type:** Array&lt;[MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md)&gt;

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoUris

```TypeScript
photoUris: Array<string>
```

URIs of the media files selected.

This URI array can be used only by calling the [photoAccessHelper.getAssets](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets) API through temporary authorization. For details, see [Using a Media File URI](../../../file-management/user-file-uri-intro.md#using-a-media-file-uri).

**Type:** Array&lt;string&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
