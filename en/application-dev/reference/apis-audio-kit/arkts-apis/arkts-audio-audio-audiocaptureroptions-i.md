# AudioCapturerOptions

Describes audio capturer configurations.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## capturerInfo

```TypeScript
capturerInfo: AudioCapturerInfo
```

Audio capturer information.

**Type:** [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## playbackCaptureConfig

```TypeScript
playbackCaptureConfig?: AudioPlaybackCaptureConfig
```

Defines configuration for capturing played audio.

This API is supported since API version 10 and deprecated since API version 12. You are advised to use [AVScreenCapture](../../../reference/apis-media-kit/capi-avscreencapture.md) instead.

**Type:** [AudioPlaybackCaptureConfig](arkts-audio-audio-audioplaybackcaptureconfig-i.md)

**Since:** 10

**Deprecated since:** 12

**Substitutes:** OH_AVScreenCapture in native interface.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## playbackCaptureMode

```TypeScript
playbackCaptureMode?: AudioPlaybackCaptureMode
```

The playback capture mode for audio capturer. This can be a combination of the available [AudioPlaybackCaptureMode](arkts-audio-audio-audioplaybackcapturemode-e.md).

**Type:** [AudioPlaybackCaptureMode](arkts-audio-audio-audioplaybackcapturemode-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## streamInfo

```TypeScript
streamInfo: AudioStreamInfo
```

Audio stream information.

**Type:** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer
