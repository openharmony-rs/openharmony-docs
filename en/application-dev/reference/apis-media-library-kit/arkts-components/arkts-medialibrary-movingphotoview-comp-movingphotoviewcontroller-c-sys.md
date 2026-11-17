# MovingPhotoViewController (System API)

```TypeScript
export class MovingPhotoViewController
```

Defines the MovingPhotoView controller.

**Since:** 12

<!--Device-unnamed-export class MovingPhotoViewController--><!--Device-unnamed-export class MovingPhotoViewController-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { MovingPhotoView, MovingPhotoViewController, MovingPhotoViewAttribute, PixelMapFormat, DynamicRangeMode, DisplayMode } from '@kit.MediaLibraryKit';
```

## enableAutoPlay

```TypeScript
enableAutoPlay(enabled: boolean)
```

Dynamically refresh the autoplay property, which will force to play after moving photo is initialized

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MovingPhotoViewController-enableAutoPlay(enabled: boolean)--><!--Device-MovingPhotoViewController-enableAutoPlay(enabled: boolean)-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to auto play |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |

## enableTransition

```TypeScript
enableTransition(enabled: boolean)
```

Enable or disable the zoom transition effect and can be set during initialization

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MovingPhotoViewController-enableTransition(enabled: boolean)--><!--Device-MovingPhotoViewController-enableTransition(enabled: boolean)-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable the transition effect |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |

## notifyMovingPhotoTransition

```TypeScript
notifyMovingPhotoTransition(): void
```

Notify the component to execute the picture transition animation.

**Since:** 23

<!--Device-MovingPhotoViewController-notifyMovingPhotoTransition(): void--><!--Device-MovingPhotoViewController-notifyMovingPhotoTransition(): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |

## pausePlayback

```TypeScript
pausePlayback()
```

Pause moving photo and show current frame, start playing from the current frame when playing again

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MovingPhotoViewController-pausePlayback()--><!--Device-MovingPhotoViewController-pausePlayback()-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |

## reset

```TypeScript
reset()
```

Reset moving photo playback options as default.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MovingPhotoViewController-reset()--><!--Device-MovingPhotoViewController-reset()-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |

## restart

```TypeScript
restart()
```

Restart to play the video with current options.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MovingPhotoViewController-restart()--><!--Device-MovingPhotoViewController-restart()-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |

## setDisplayMode

```TypeScript
setDisplayMode(mode: DisplayMode, callback: MovingPhotoViewEventCallback): void
```

Set display mode, and trigger callback completion.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-MovingPhotoViewController-setDisplayMode(mode: DisplayMode, callback: MovingPhotoViewEventCallback): void--><!--Device-MovingPhotoViewController-setDisplayMode(mode: DisplayMode, callback: MovingPhotoViewEventCallback): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [DisplayMode](arkts-medialibrary-movingphotoview-comp-displaymode-e-sys.md) | Yes | Display mode |
| callback | [MovingPhotoViewEventCallback](arkts-medialibrary-movingphotoview-comp-movingphotovieweventcallback-t.md) | Yes | Set display mode completion callback |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## setPlaybackPeriod

```TypeScript
setPlaybackPeriod(startTime: number, endTime: number)
```

Set moving photo playback period

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MovingPhotoViewController-setPlaybackPeriod(startTime: double, endTime: double)--><!--Device-MovingPhotoViewController-setPlaybackPeriod(startTime: double, endTime: double)-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startTime | number | Yes | video playback start time |
| endTime | number | Yes | video playback end time |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |

## startPlayback

```TypeScript
startPlayback(mode: DisplayMode): void
```

Start play moving photo.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-MovingPhotoViewController-startPlayback(mode: DisplayMode): void--><!--Device-MovingPhotoViewController-startPlayback(mode: DisplayMode): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [DisplayMode](arkts-medialibrary-movingphotoview-comp-displaymode-e-sys.md) | Yes | Display mode |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
