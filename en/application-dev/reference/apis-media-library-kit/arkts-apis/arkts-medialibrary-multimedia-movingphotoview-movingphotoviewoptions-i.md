# MovingPhotoViewOptions

Defines the moving photo view options.

@interface MovingPhotoViewOptions

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { MovingPhotoView, MovingPhotoViewController, MovingPhotoViewAttribute, PixelMapFormat, DynamicRangeMode } from '@kit.MediaLibraryKit';
```

## controller

```TypeScript
controller?: MovingPhotoViewController
```

controller of MovingPhotoView.

**Type:** [MovingPhotoViewController](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewcontroller-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

image ai options of MovingPhotoView.

**Type:** [ImageAIOptions](../../apis-arkui/arkts-apis/arkts-arkui-imageaioptions-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## movingPhoto

```TypeScript
movingPhoto: photoAccessHelper.MovingPhoto
```

moving photo data.

**Type:** [photoAccessHelper.MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
