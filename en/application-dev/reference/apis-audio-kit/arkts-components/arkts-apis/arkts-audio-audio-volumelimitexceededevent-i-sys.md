# VolumeLimitExceededEvent (System API)

```TypeScript
interface VolumeLimitExceededEvent
```

Describes the notification event indicating that the volume exceeds the threshold. after receiving the notification, the app must send the acknowledgment result. through [confirmVolumeLimitExceeded](arkts-audio-audio-audiovolumemanager-i-sys.md#confirmvolumelimitexceeded) before continuing to adjust the volume.

**Since:** 26.0.1

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## currentVolume

```TypeScript
currentVolume: number
```

Current volume level.

The value is between the values obtained from [getMinSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getminsystemvolume) and [getMaxSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getmaxsystemvolume).

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

Indicates the UID of the process that triggers the volume threshold-crossing.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## volumeThreshold

```TypeScript
volumeThreshold: number
```

Volume threshold of current volume type.

The value is between the values obtained from [getMinSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getminsystemvolume) and [getMaxSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getmaxsystemvolume).

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## volumeType

```TypeScript
volumeType: AudioVolumeType
```

Current volume type.

**Type:** [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.
