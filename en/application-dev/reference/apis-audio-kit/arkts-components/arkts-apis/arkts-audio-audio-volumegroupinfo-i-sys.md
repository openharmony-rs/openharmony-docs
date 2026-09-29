# VolumeGroupInfo (System API)

```TypeScript
interface VolumeGroupInfo
```

Describes an audio volume group.

**Since:** 9

<!--Device-audio-interface VolumeGroupInfo--><!--Device-audio-interface VolumeGroupInfo-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## groupId

```TypeScript
readonly groupId: number
```

Volume group id.

**Type:** number

**Since:** 9

<!--Device-VolumeGroupInfo-readonly groupId: int--><!--Device-VolumeGroupInfo-readonly groupId: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## groupName

```TypeScript
readonly groupName: string
```

Volume group name.

**Type:** string

**Since:** 9

<!--Device-VolumeGroupInfo-readonly groupName: string--><!--Device-VolumeGroupInfo-readonly groupName: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## mappingId

```TypeScript
readonly mappingId: number
```

Volume mapping group id.

**Type:** number

**Since:** 9

<!--Device-VolumeGroupInfo-readonly mappingId: int--><!--Device-VolumeGroupInfo-readonly mappingId: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## networkId

```TypeScript
readonly networkId: string
```

Device network id.

**Type:** string

**Since:** 9

<!--Device-VolumeGroupInfo-readonly networkId: string--><!--Device-VolumeGroupInfo-readonly networkId: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

## type

```TypeScript
readonly type: ConnectType
```

Connect type of device for this group.

**Type:** [ConnectType](arkts-audio-audio-connecttype-e-sys.md)

**Since:** 9

<!--Device-VolumeGroupInfo-readonly type: ConnectType--><!--Device-VolumeGroupInfo-readonly type: ConnectType-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.
