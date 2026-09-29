# VolumeEvent

```TypeScript
interface VolumeEvent
```

Describes the event received by the application when the volume is changed.

**Since:** 9

<!--Device-audio-interface VolumeEvent--><!--Device-audio-interface VolumeEvent-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## updateUi

```TypeScript
updateUi: boolean
```

Whether to show the volume change in UI. **true** to show, **false** otherwise.

**Type:** boolean

**Since:** 9

<!--Device-VolumeEvent-updateUi: boolean--><!--Device-VolumeEvent-updateUi: boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

## volume

```TypeScript
volume: number
```

Volume to set. The value range can be obtained by calling **getMinVolume** and **getMaxVolume**.

**Type:** number

**Since:** 9

<!--Device-VolumeEvent-volume: int--><!--Device-VolumeEvent-volume: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

## volumeMode

```TypeScript
volumeMode?: AudioVolumeMode
```

Audio volume mode. The default value is **SYSTEM_GLOBAL**.

**Type:** [AudioVolumeMode](arkts-audio-audio-audiovolumemode-e.md)

**Since:** 19

<!--Device-VolumeEvent-volumeMode?: AudioVolumeMode--><!--Device-VolumeEvent-volumeMode?: AudioVolumeMode-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

## volumeType

```TypeScript
volumeType: AudioVolumeType
```

Audio volume type.

**Type:** [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)

**Since:** 9

<!--Device-VolumeEvent-volumeType: AudioVolumeType--><!--Device-VolumeEvent-volumeType: AudioVolumeType-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume
