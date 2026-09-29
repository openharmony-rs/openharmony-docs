# MovingPhotoView properties/events

```TypeScript
declare class MovingPhotoViewAttribute extends CommonMethod<MovingPhotoViewAttribute>
```

Defines the moving photo view attribute functions.

@extends CommonMethod&lt;MovingPhotoViewAttribute&gt;

**Inheritance/Implementation:** MovingPhotoViewAttribute extends CommonMethod<MovingPhotoViewAttribute>

**Since:** 12

<!--Device-unnamed-declare class MovingPhotoViewAttribute extends CommonMethod<MovingPhotoViewAttribute>--><!--Device-unnamed-declare class MovingPhotoViewAttribute extends CommonMethod<MovingPhotoViewAttribute>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { MovingPhotoView, MovingPhotoViewController, MovingPhotoViewAttribute, PixelMapFormat, DynamicRangeMode } from '@kit.MediaLibraryKit';
```

## autoPlay

```TypeScript
autoPlay(isAutoPlay: boolean)
```

Sets whether to allow automatic play. If the value is true, the moving photo starts automatic after the resource is loaded.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-MovingPhotoViewAttribute-autoPlay(isAutoPlay: boolean): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-autoPlay(isAutoPlay: boolean): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isAutoPlay | boolean | Yes | Whether to automatic play |

## autoPlayPeriod

```TypeScript
autoPlayPeriod(startTime: number, endTime: number)
```

Sets automatic play period, If not set, the moving photo plays in the full video duration. If set, the moving photo plays in the automatic play period.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-MovingPhotoViewAttribute-autoPlayPeriod(startTime: double, endTime: double): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-autoPlayPeriod(startTime: double, endTime: double): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startTime | number | Yes | video plays start time |
| endTime | number | Yes | video plays end time |

## enableAnalyzer

```TypeScript
enableAnalyzer(enabled: boolean)
```

Sets whether to enable moving photo analyzer. If the value is true, the moving photo can be analyzed by AI.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-MovingPhotoViewAttribute-enableAnalyzer(enabled: boolean): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-enableAnalyzer(enabled: boolean): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | whether to enable moving photo analyzer |

## muted

```TypeScript
muted(isMuted: boolean)
```

Called when judging whether the video is muted.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MovingPhotoViewAttribute-muted(isMuted: boolean): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-muted(isMuted: boolean): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isMuted | boolean | Yes |  |

## objectFit

```TypeScript
objectFit(value: ImageFit)
```

Called when determining the zoom type of the view.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MovingPhotoViewAttribute-objectFit(value: ImageFit): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-objectFit(value: ImageFit): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageFit](../../apis-arkui/arkts-apis/arkts-arkui-imagefit-e.md) | Yes |  |

## onComplete

```TypeScript
onComplete(callback: MovingPhotoViewEventCallback)
```

Called when the image load completed.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-MovingPhotoViewAttribute-onComplete(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-onComplete(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotoview-comp-movingphotovieweventcallback-t.md) | Yes |  |

## onError

```TypeScript
onError(callback: MovingPhotoViewEventCallback)
```

Called when playback fails.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MovingPhotoViewAttribute-onError(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-onError(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotoview-comp-movingphotovieweventcallback-t.md) | Yes |  |

## onFinish

```TypeScript
onFinish(callback: MovingPhotoViewEventCallback)
```

Called when the video playback ends.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MovingPhotoViewAttribute-onFinish(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-onFinish(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotoview-comp-movingphotovieweventcallback-t.md) | Yes |  |

## onPause

```TypeScript
onPause(callback: MovingPhotoViewEventCallback)
```

Called when the video playback paused.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MovingPhotoViewAttribute-onPause(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-onPause(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotoview-comp-movingphotovieweventcallback-t.md) | Yes |  |

## onPrepared

```TypeScript
onPrepared(callback: MovingPhotoViewEventCallback)
```

Called when playback prepared.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MovingPhotoViewAttribute-onPrepared(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-onPrepared(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotoview-comp-movingphotovieweventcallback-t.md) | Yes |  |

## onStart

```TypeScript
onStart(callback: MovingPhotoViewEventCallback)
```

Called when the video is played.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MovingPhotoViewAttribute-onStart(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-onStart(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotoview-comp-movingphotovieweventcallback-t.md) | Yes |  |

## onStop

```TypeScript
onStop(callback: MovingPhotoViewEventCallback)
```

Called when the video playback stopped.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MovingPhotoViewAttribute-onStop(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-onStop(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotoview-comp-movingphotovieweventcallback-t.md) | Yes |  |

## repeatPlay

```TypeScript
repeatPlay(isRepeatPlay: boolean)
```

Sets whether to allow repeat play. If the value is true, the moving photo plays repeat after the resource is loaded.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-MovingPhotoViewAttribute-repeatPlay(isRepeatPlay: boolean): MovingPhotoViewAttribute--><!--Device-MovingPhotoViewAttribute-repeatPlay(isRepeatPlay: boolean): MovingPhotoViewAttribute-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isRepeatPlay | boolean | Yes | Whether to repeat play |
