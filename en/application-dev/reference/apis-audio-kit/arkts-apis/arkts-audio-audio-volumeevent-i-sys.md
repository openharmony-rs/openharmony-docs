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

## appUid

```TypeScript
appUid?: number
```

Application UID.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-VolumeEvent-appUid?: int--><!--Device-VolumeEvent-appUid?: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## networkId

```TypeScript
networkId: string
```

Device network id

**Type:** string

**Since:** 9

<!--Device-VolumeEvent-networkId: string--><!--Device-VolumeEvent-networkId: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## percentage

```TypeScript
percentage?: number
```

Volume percentage, which is an integer ranging from [0, 100].

**Type:** number

**Since:** 23

<!--Device-VolumeEvent-percentage?: int--><!--Device-VolumeEvent-percentage?: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## volumeGroupId

```TypeScript
volumeGroupId: number
```

volumeGroup id

**Type:** number

**Since:** 9

<!--Device-VolumeEvent-volumeGroupId: int--><!--Device-VolumeEvent-volumeGroupId: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.
