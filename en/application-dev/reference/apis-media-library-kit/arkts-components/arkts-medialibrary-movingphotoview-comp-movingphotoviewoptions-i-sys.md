# MovingPhotoViewOptions

```TypeScript
declare interface MovingPhotoViewOptions
```

Defines the moving photo view options.

@interface MovingPhotoViewOptions

**Since:** 12

<!--Device-unnamed-declare interface MovingPhotoViewOptions--><!--Device-unnamed-declare interface MovingPhotoViewOptions-End-->

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

**Type:** [DynamicRangeMode](arkts-medialibrary-movingphotoview-comp-dynamicrangemode-e-sys.md)

**Since:** 14

<!--Device-MovingPhotoViewOptions-dynamicRangeMode?: DynamicRangeMode--><!--Device-MovingPhotoViewOptions-dynamicRangeMode?: DynamicRangeMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## movingPhotoFormat

```TypeScript
movingPhotoFormat?: PixelMapFormat
```

format of MovingPhotoView.

**Type:** [PixelMapFormat](arkts-medialibrary-movingphotoview-comp-pixelmapformat-e-sys.md)

**Since:** 14

<!--Device-MovingPhotoViewOptions-movingPhotoFormat?: PixelMapFormat--><!--Device-MovingPhotoViewOptions-movingPhotoFormat?: PixelMapFormat-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## playWithMask

```TypeScript
playWithMask?: boolean
```

the watermask of the cover photo whether to contain during movingphoto playback

**Type:** boolean

**Since:** 19

<!--Device-MovingPhotoViewOptions-playWithMask?: boolean--><!--Device-MovingPhotoViewOptions-playWithMask?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
