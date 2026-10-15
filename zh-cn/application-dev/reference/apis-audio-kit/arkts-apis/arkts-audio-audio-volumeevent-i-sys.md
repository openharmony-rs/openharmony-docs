# VolumeEvent

```TypeScript
interface VolumeEvent
```

音量改变时，应用接收的事件。

**起始版本：** 9

<!--Device-audio-interface VolumeEvent--><!--Device-audio-interface VolumeEvent-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## appUid

```TypeScript
appUid?: number
```

应用的UID.

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VolumeEvent-appUid?: int--><!--Device-VolumeEvent-appUid?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
networkId: string
```

网络id。

**类型：** string

**起始版本：** 9

<!--Device-VolumeEvent-networkId: string--><!--Device-VolumeEvent-networkId: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## percentage

```TypeScript
percentage?: number
```

音量百分比，为整数值，取值范围为[0, 100]。

**类型：** number

**起始版本：** 23

<!--Device-VolumeEvent-percentage?: int--><!--Device-VolumeEvent-percentage?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## volumeGroupId

```TypeScript
volumeGroupId: number
```

音量组id，可用于getGroupManager入参。

**类型：** number

**起始版本：** 9

<!--Device-VolumeEvent-volumeGroupId: int--><!--Device-VolumeEvent-volumeGroupId: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。
