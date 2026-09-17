# MovingPhotoViewAttribute

Defines the moving photo view attribute functions.

@extends CommonMethod&lt;MovingPhotoViewAttribute&gt;

**Inheritance/Implementation:** MovingPhotoViewAttribute extends CommonMethod<MovingPhotoViewAttribute>

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { MovingPhotoView, MovingPhotoViewController, MovingPhotoViewAttribute, PixelMapFormat, DynamicRangeMode } from '@kit.MediaLibraryKit';
```

## setPlaybackStrategy

```TypeScript
setPlaybackStrategy(strategy: media.PlaybackStrategy): MovingPhotoViewAttribute
```

Sets playback strategy.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [media.PlaybackStrategy](../../apis-media-kit/arkts-apis/arkts-media-media-playbackstrategy-i.md) | Yes | playback strategy |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |

**Examples**

```TypeScript
The system application can set the decoding format, HDR effect format, and strategy for processing a moving photo while playing it.
```
