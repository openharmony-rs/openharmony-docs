# VolumeEvent

音量改变时，应用接收的事件。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## networkId

```TypeScript
networkId: string
```

网络id。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## percentage

```TypeScript
percentage?: number
```

音量百分比，取值范围为[0, 100]。取值限定为整数。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## volumeGroupId

```TypeScript
volumeGroupId: number
```

音量组id，可用于getGroupManager入参。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。
