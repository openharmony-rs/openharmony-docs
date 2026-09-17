# MovingPhotoViewOptions

Defines the moving photo view options.

@interface MovingPhotoViewOptions

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { MovingPhotoView, MovingPhotoViewController, MovingPhotoViewAttribute, PixelMapFormat, DynamicRangeMode } from '@kit.MediaLibraryKit';
```

## dynamicRangeMode

```TypeScript
dynamicRangeMode?: DynamicRangeMode
```

range mode of MovingPhotoView.

**Type:** [DynamicRangeMode](arkts-medialibrary-multimedia-movingphotoview-dynamicrangemode-e-sys.md)

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## movingPhotoFormat

```TypeScript
movingPhotoFormat?: PixelMapFormat
```

format of MovingPhotoView.

**Type:** [PixelMapFormat](arkts-medialibrary-multimedia-movingphotoview-pixelmapformat-e-sys.md)

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## playWithMask

```TypeScript
playWithMask?: boolean
```

the watermask of the cover photo whether to contain during movingphoto playback

**Type:** boolean

**Since:** 19

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
