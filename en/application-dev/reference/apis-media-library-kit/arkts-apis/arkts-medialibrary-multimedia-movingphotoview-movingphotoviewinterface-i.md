# MovingPhotoViewInterface

Defines the moving photo view interface.

@interface MovingPhotoViewInterface

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { MovingPhotoView, MovingPhotoViewController, MovingPhotoViewAttribute, PixelMapFormat, DynamicRangeMode } from '@kit.MediaLibraryKit';
```

## [[Call]]

```TypeScript
(options: MovingPhotoViewOptions): MovingPhotoViewAttribute
```

Set the options.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [MovingPhotoViewOptions](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewoptions-i.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |
