# VolumeEvent

音量改变时，应用接收到的事件。

**起始版本：** 9

<!--Device-audio-interface VolumeEvent--><!--Device-audio-interface VolumeEvent-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## networkId

```TypeScript
networkId: string
```

Device network id

**类型：** string

**起始版本：** 9

<!--Device-VolumeEvent-networkId: string--><!--Device-VolumeEvent-networkId: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## percentage

```TypeScript
percentage?: number
```

Volume percentage, which is an integer ranging from [0, 100].

**类型：** number

**起始版本：** 23

<!--Device-VolumeEvent-percentage?: int--><!--Device-VolumeEvent-percentage?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## volumeGroupId

```TypeScript
volumeGroupId: number
```

volumeGroup id

**类型：** number

**起始版本：** 9

<!--Device-VolumeEvent-volumeGroupId: int--><!--Device-VolumeEvent-volumeGroupId: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

