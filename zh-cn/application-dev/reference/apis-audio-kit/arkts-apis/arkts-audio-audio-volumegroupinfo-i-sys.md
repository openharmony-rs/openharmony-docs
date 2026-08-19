# VolumeGroupInfo（系统接口）

Describes an audio volume group.

**起始版本：** 23

<!--Device-audio-interface VolumeGroupInfo--><!--Device-audio-interface VolumeGroupInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
import { audioHaptic } from '@kit.AudioKit';
```

## groupId

```TypeScript
readonly groupId: int
```

Volume group id.

**类型：** int

**起始版本：** 23

<!--Device-VolumeGroupInfo-readonly groupId: int--><!--Device-VolumeGroupInfo-readonly groupId: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## groupName

```TypeScript
readonly groupName: string
```

Volume group name.

**类型：** string

**起始版本：** 23

<!--Device-VolumeGroupInfo-readonly groupName: string--><!--Device-VolumeGroupInfo-readonly groupName: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## mappingId

```TypeScript
readonly mappingId: int
```

Volume mapping group id.

**类型：** int

**起始版本：** 23

<!--Device-VolumeGroupInfo-readonly mappingId: int--><!--Device-VolumeGroupInfo-readonly mappingId: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
readonly networkId: string
```

Device network id.

**类型：** string

**起始版本：** 23

<!--Device-VolumeGroupInfo-readonly networkId: string--><!--Device-VolumeGroupInfo-readonly networkId: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## type

```TypeScript
readonly type: ConnectType
```

Connect type of device for this group.

**类型：** [ConnectType](arkts-audio-audio-connecttype-e-sys.md)

**起始版本：** 23

<!--Device-VolumeGroupInfo-readonly type: ConnectType--><!--Device-VolumeGroupInfo-readonly type: ConnectType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

