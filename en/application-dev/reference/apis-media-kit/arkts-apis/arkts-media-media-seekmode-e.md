# SeekMode

```TypeScript
enum SeekMode
```

Enumerates the video playback seek modes, which can be passed in the **seek** API.

**Since:** 8

<!--Device-media-enum SeekMode--><!--Device-media-enum SeekMode-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## SEEK_NEXT_SYNC

```TypeScript
SEEK_NEXT_SYNC = 0
```

Seeks to the next key frame at the specified position. You are advised to use this value for the rewind operation.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-SeekMode-SEEK_NEXT_SYNC = 0--><!--Device-SeekMode-SEEK_NEXT_SYNC = 0-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## SEEK_PREV_SYNC

```TypeScript
SEEK_PREV_SYNC = 1
```

Seeks to the previous key frame at the specified position. You are advised to use this value for the fast-forward operation.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-SeekMode-SEEK_PREV_SYNC = 1--><!--Device-SeekMode-SEEK_PREV_SYNC = 1-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## SEEK_CLOSEST

```TypeScript
SEEK_CLOSEST = 2
```

Seeks to the frame closest to the specified position. You are advised to use this value for accurate seek.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SeekMode-SEEK_CLOSEST = 2--><!--Device-SeekMode-SEEK_CLOSEST = 2-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## SEEK_CONTINUOUS

```TypeScript
SEEK_CONTINUOUS = 3
```

Offers a smooth and fluid visual experience for seeking. Applications can use a progress bar component to continuously invoke the **seek** method, and the AVPlayer will update the video frames smoothly in response to these calls.

Applications can call [isSeekContinuousSupported](arkts-media-media-avplayer-i.md#isseekcontinuoussupported) to check whether the video source supports this seeking mode.

If the video source does not support this mode, calling **seek** will result in an **AVERR_SEEK_CONTINUOUS_UNSUPPORTED** error (see [AVErrorCode](arkts-media-media-averrorcode-e.md)), and the smoothness of frame updates will be compromised.

This seek mode does not trigger the on('seekDone') event.

To exit this seeking mode, applications must call **seek(-1, SeekMode.SEEK_CONTINUOUS)** to end the seeking process.

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-SeekMode-SEEK_CONTINUOUS = 3--><!--Device-SeekMode-SEEK_CONTINUOUS = 3-End-->

**System capability:** SystemCapability.Multimedia.Media.Core
