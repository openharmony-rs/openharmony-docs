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

## autoPlay

```TypeScript
autoPlay(isAutoPlay: boolean): MovingPhotoViewAttribute
```

Sets whether to allow automatic play. If the value is true, the moving photo starts automatic after the resource is loaded.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isAutoPlay | boolean | Yes | Whether to automatic play |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## autoPlayPeriod

```TypeScript
autoPlayPeriod(startTime: number, endTime: number): MovingPhotoViewAttribute
```

Sets automatic play period, If not set, the moving photo plays in the full video duration. If set, the moving photo plays in the automatic play period.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startTime | number | Yes | video plays start time |
| endTime | number | Yes | video plays end time |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## enableAnalyzer

```TypeScript
enableAnalyzer(enabled: boolean): MovingPhotoViewAttribute
```

Sets whether to enable moving photo analyzer. If the value is true, the moving photo can be analyzed by AI.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | whether to enable moving photo analyzer |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## muted

```TypeScript
muted(isMuted: boolean): MovingPhotoViewAttribute
```

Called when judging whether the video is muted.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isMuted | boolean | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## objectFit

```TypeScript
objectFit(value: ImageFit): MovingPhotoViewAttribute
```

Called when determining the zoom type of the view.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageFit](../../apis-arkui/arkts-apis/arkts-arkui-imagefit-e.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## onComplete

```TypeScript
onComplete(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute
```

Called when the image load completed.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotovieweventcallback-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## onError

```TypeScript
onError(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute
```

Called when playback fails.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotovieweventcallback-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## onFinish

```TypeScript
onFinish(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute
```

Called when the video playback ends.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotovieweventcallback-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## onPause

```TypeScript
onPause(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute
```

Called when the video playback paused.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotovieweventcallback-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## onPrepared

```TypeScript
onPrepared(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute
```

Called when playback prepared.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotovieweventcallback-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## onStart

```TypeScript
onStart(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute
```

Called when the video is played.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotovieweventcallback-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## onStop

```TypeScript
onStop(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute
```

Called when the video playback stopped.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotovieweventcallback-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |

## repeatPlay

```TypeScript
repeatPlay(isRepeatPlay: boolean): MovingPhotoViewAttribute
```

Sets whether to allow repeat play. If the value is true, the moving photo plays repeat after the resource is loaded.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isRepeatPlay | boolean | Yes | Whether to repeat play |

**Return value:**

| Type | Description |
| --- | --- |
| [MovingPhotoViewAttribute](arkts-medialibrary-multimedia-movingphotoview-movingphotoviewattribute-c.md) |  |
